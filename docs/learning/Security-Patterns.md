# Security Patterns & Best Practices

Architektur-Patterns für sichere, compliance-ready Systeme.

## 🎯 Zero Trust Architecture

**Prinzip:** Niemandem vertrauen, immer verifizieren.

```
┌─────────────────────────────────────┐
│  External User / Service Request    │
└────────────────┬────────────────────┘
                 │
         ✅ Authenticate
         (OAuth2, OIDC, mTLS)
                 │
         ✅ Verify Identity
         (Certificates, Tokens)
                 │
         ✅ Authorize (RBAC)
         (What can this user DO?)
                 │
         ✅ Encrypt Transit + Storage
         (TLS 1.3, AES-256)
                 │
         ✅ Log & Audit
         (Immutable audit trail)
                 │
          Application Logic
```

## 🔐 Defense in Depth

Mehrschichtige Sicherheit:

1. **Netzwerk-Ebene**: NetworkPolicies, WAF, DDoS Protection
2. **Authentifizierung**: OAuth2/OIDC, MFA
3. **Autorisierung**: RBAC, ABAC
4. **Daten-Ebene**: Encryption, RLS (Row-Level Security)
5. **Applikations-Ebene**: Input Validation, Secure Coding
6. **Monitoring**: Audit Logging, Intrusion Detection

## 📊 Authentication & Authorization Patterns

### OAuth2 + OIDC Flow
```
User Login → Authorization Server
  ↓
Issue ID Token + Access Token
  ↓
API Request mit Token
  ↓
Verify Token Signature
  ↓
Extract User Claims → RBAC Decision
  ↓
Grant / Deny Access
```

### Service-to-Service (mTLS)
```
Service A → (mutual TLS)
  ↓
Verify Service Certificate
  ↓
Check Service Permissions
  ↓
Service B
```

### API Key Management (Legacy)
```
Secrets Manager (Vault)
  ↓
API Key Generation + Rotation
  ↓
Store in Vault (NOT in code!)
  ↓
Audit Trail (wer hat key genutzt?)
```

## 🔐 Data Protection

### Encryption in Transit
- **TLS 1.3+** für alle HTTP-Requests
- **mTLS** für Service-to-Service Communication
- Certificate Pinning für sensible Endpoints

### Encryption at Rest
```
User Data → AES-256 Encryption
  ↓
Key stored in Vault (NOT in Database!)
  ↓
Key Rotation Policy (z.B. jedes Jahr)
  ↓
Encrypted Data in PostgreSQL
```

### Row-Level Security (PostgreSQL)
```sql
-- Nur Benutzer können ihre eigenen Daten sehen
CREATE POLICY user_data_isolation ON user_profiles
  USING (user_id = current_user_id());

SELECT * FROM user_profiles;
-- Gibt nur Daten des aktuellen Users zurück!
```

## 📋 Compliance-Ready Logging

```
Application Events
  ↓
Structured Logging (JSON)
{
  "timestamp": "2026-05-12T10:00:00Z",
  "event_type": "user_login",
  "user_id": "uuid",
  "ip_address": "192.168.1.1",
  "status": "success",
  "mfa_used": true
}
  ↓
Elasticsearch / Datadog
  ↓
Long-Term Storage (immutable)
  ↓
Audit Reports (für NIS2/ISO27001 Audits)
```

## 🛡️ Secrets Management (Vault)

```
┌─────────────────────────────┐
│   Application             │
└────────────┬────────────────┘
             │
    ┌────────▼────────┐
    │  Authenticate   │
    │  to Vault       │
    └────────┬────────┘
             │
    ┌────────▼────────┐
    │ Request Secret  │
    │ (e.g., DB pwd)  │
    └────────┬────────┘
             │
    ┌────────▼────────┐
    │  Vault Issues   │
    │  Lease + TTL    │
    └────────┬────────┘
             │
    ┌────────▼────────┐
    │  App uses       │
    │  Secret         │
    └────────┬────────┘
             │
     (Lease expires)
             │
    Secret is revoked
```

## 📚 Gelernte Inhalte

*Deine Notizen hier*

### Zero Trust Implementation
- [ ] Authentication Flow verstanden
- [ ] RBAC Design
- [ ] Encryption Strategy

### Compliance-Logging
- [ ] OpenTelemetry setup
- [ ] Audit Trail design
- [ ] Retention Policies

---

## 🔗 Related Standards

- NIST Cybersecurity Framework
- OWASP Top 10
- CIS Kubernetes Benchmark

---

**Status:** 🚧 In Bearbeitung  
**Letzte Aktualisierung:** 2026-05-12
