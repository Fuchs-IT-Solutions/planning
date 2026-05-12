# Security Patterns — Key Requirements

## Zero Trust Architecture

**Prinzip:** "Never trust, always verify" — Niemandem vertrauen, immer verifizieren.

### Traditionell (perimetral)
```
Firewall
    ↓
  [Trusted Network]
    ↓
(Apps können sich trauen)
```

### Zero Trust
```
Every Request:
    ↓
1. Authenticate (WHO sind Sie?)
2. Authorize (WAS dürfen Sie tun?)
3. Encrypt (Sichere Kommunikation)
4. Log & Monitor (Audit Trail)
    ↓
dann: Access gewähren
```

---

## Defense in Depth (Mehrschichtige Sicherheit)

```
Layer 1: Network
├── DDoS Protection
├── WAF (Web Application Firewall)
└── VPN/Proxies

Layer 2: Perimeter
├── Firewalls
├── NetworkPolicies (Kubernetes)
└── API Gateway (Rate Limiting, Logging)

Layer 3: Authentication
├── Strong Passwords (min 12 chars)
├── MFA (Multi-Factor Authentication)
├── OAuth2/OIDC (Delegation)
└── mTLS (Service-to-Service)

Layer 4: Authorization
├── RBAC (Role-Based Access Control)
├── ABAC (Attribute-Based Access Control)
└── Least Privilege (Minimale Rechte)

Layer 5: Data Layer
├── Encryption in Transit (TLS 1.3)
├── Encryption at Rest (AES-256)
├── RLS (Row-Level Security — DB)
└── Key Management (Vault)

Layer 6: Application
├── Input Validation
├── Output Encoding
├── Secure Coding Practices
└── OWASP Top 10 Defense

Layer 7: Monitoring
├── Audit Logging (Immutable)
├── Alerting (Anomalies)
├── Threat Detection (IDS/IPS)
└── Incident Response
```

---

## Authentication Patterns

### Pattern 1: OAuth2 + OIDC (Modern)
```
Web/Mobile App
    ↓
User clicks "Login with Google/GitHub"
    ↓
Redirect to Authorization Server
    ↓
User authenticates (Passwort, MFA)
    ↓
Authorization Server issues:
  - ID Token (WHO)
  - Access Token (WHAT permissions)
  - Refresh Token
    ↓
App uses Access Token für API Requests
```

**Best for:** Modern Web/Mobile Apps

### Pattern 2: mTLS (Mutual TLS)
```
Service A ←→ Service B

Each service has:
- Client Certificate (uniquely identifies Service A)
- Server Certificate (uniquely identifies Service B)

Connection:
1. Service A → presents Client Cert
2. Service B → validates Client Cert signature
3. Service B → presents Server Cert
4. Service A → validates Server Cert signature
5. Secure channel established
```

**Best for:** Service-to-Service Communication (Kubernetes)

### Pattern 3: API Keys (Legacy)
```
Client
    ↓
API Key (stored in Vault, NOT in code!)
    ↓
GET /api/data
Authorization: Bearer sk_live_abc123xyz
    ↓
Server validates Key → grants access
```

**Best for:** Simple integrations, but less secure than OAuth2

---

## Authorization Patterns

### RBAC (Role-Based Access Control)
```
User "john" has Role "DataAnalyst"
    ↓
Role "DataAnalyst" has Permissions:
  - read:dashboards
  - read:reports
  - write:filters
    ↓
Request: john wants read:dashboards?
Answer: Check if "DataAnalyst" has "read:dashboards"
    ↓
✅ ALLOWED
```

**Implementation:**
```sql
-- User -> Role mapping
CREATE TABLE user_roles (
  user_id UUID,
  role_id UUID
);

-- Role -> Permission mapping
CREATE TABLE role_permissions (
  role_id UUID,
  permission_id UUID
);

-- Permission names
CREATE TABLE permissions (
  id UUID,
  name VARCHAR (e.g., "read:dashboards")
);
```

### ABAC (Attribute-Based Access Control)
```
Request: Can User "john" access Document "contract_X"?

Attributes to check:
- User.department == Document.owner_department?
- User.clearance_level >= Document.classification_level?
- Time < Document.expiry_date?
- IP in allowed_cidrs?

If ALL conditions met: ✅ ALLOWED
```

**More flexible than RBAC, but more complex.**

---

## Encryption Patterns

### In Transit (TLS 1.3)
```
Client ←(HTTPS)→ Server

Handshake:
1. Client Hello (supported algorithms)
2. Server Hello (chosen algorithm)
3. Key Exchange (establish shared secret)
4. Finished (verify integrity)

Result: Encrypted channel
```

**Best practices:**
- [ ] Use TLS 1.3 (not 1.2)
- [ ] Strong ciphers (AES-256-GCM)
- [ ] Valid certificates (not self-signed)
- [ ] Certificate pinning (for sensitive endpoints)

### At Rest (AES-256)
```
Plaintext Data
    ↓
AES-256 Encryption (with key from Vault)
    ↓
Encrypted Data (stored in DB)
    ↓
Query:
  SELECT decrypted_field FROM table
  WHERE user_id = ?
    ↓
PostgreSQL decrypts using Vault-managed key
    ↓
Return plaintext (only to authorized user)
```

**Implementation (PostgreSQL):**
```sql
-- Store encrypted data
CREATE TABLE users (
  id UUID,
  name VARCHAR,
  ssn BYTEA  -- encrypted
);

-- Function to decrypt (requires Vault key)
SELECT 
  id,
  name,
  pgcrypto.decrypt(ssn) AS ssn
FROM users
WHERE id = ?;
```

---

## Logging & Audit Trail

### Requirements
- ✅ **Immutable:** Logs können nicht gelöscht/geändert werden
- ✅ **Centralized:** Ein Ort für alle Logs
- ✅ **Retention:** Mindestens 1 Jahr
- ✅ **Structured:** JSON format für Parsing
- ✅ **Sensitive Data:** Keine PII in Logs (oder masked)

### Architecture
```
Application
  ↓ (structured logging)
{"timestamp": "...", "user_id": "...", "action": "login", "result": "success"}
  ↓
OpenTelemetry SDK
  ↓
Elasticsearch / Datadog / CloudWatch
  ↓
Retention Policy (90 days hot, 1 year archived)
  ↓
Grafana Dashboards + Alerts
  ↓
Compliance Audits (query logs by user_id, action, etc.)
```

### Audit Log Example
```json
{
  "timestamp": "2026-05-12T10:30:00Z",
  "trace_id": "abc123",
  "event": "data_access",
  "user_id": "550e8400-e29b-41d4-a716-446655440000",
  "resource": "document_xyz",
  "action": "read",
  "result": "success",
  "ip_address": "192.168.1.100",
  "mfa_used": true,
  "timestamp_processed": "2026-05-12T10:30:05Z"
}
```

---

## Summary: Die 5 Säulen

| Säule | Was | Wie |
|-------|-----|-----|
| **Authentifizierung** | WHO sind Sie? | OAuth2/OIDC, MFA, mTLS |
| **Autorisierung** | WHAT dürfen Sie? | RBAC, ABAC, Least Privilege |
| **Verschlüsselung** | Sichere Daten? | TLS 1.3, AES-256 |
| **Logging** | Audit Trail? | OpenTelemetry, Centralized Logs |
| **Monitoring** | Anormale Aktivität? | Alerting, Threat Detection |

---

[← Zurück zu Resources](resources.md)
