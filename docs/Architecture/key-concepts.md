# Enterprise Architecture — Key Concepts

## Was ist Enterprise Architecture (EA)?

**Enterprise Architecture** = Ganzheitliche Sicht auf Geschäft, Prozesse, Systeme, Daten und Technologie.

```
Business Strategy
    ↓
Business Architecture (Processes, Functions)
    ↓
Information Architecture (Data, Systems)
    ↓
Application Architecture (Software, APIs)
    ↓
Technology Architecture (Infrastructure, Cloud, Networks)
    ↓
Security Architecture (Controls, Governance, Risk)
```

---

## Die 4 Ebenen der TOGAF ADM

### 1. Business Architecture
- **Was tun wir?** (Geschäftsprozesse, Services)
- **Für wen?** (Stakeholder, Customers)
- **Wie verdienen wir Geld?** (Value Streams)

**Compliance-Beispiel:**
```
Business Process: "Kundenkredit genehmigen"
    ↓
Compliance Requirement: "NIS2 A.8.2 - Authentifizierung erforderlich"
    ↓
Architecture Requirement: "OAuth2 + MFA vor Creditcheck"
```

### 2. Information Architecture
- **Welche Daten brauchen wir?** (Data Model, Classification)
- **Wo werden sie gespeichert?** (Systems, Databases)
- **Wer darf sie sehen?** (Access Control, RLS)

**Compliance-Beispiel (ISO 27001 A.10):**
```
Data: Kundenkredithistorie (Sensitive)
    ↓
Encryption at Rest: AES-256
Encryption in Transit: TLS 1.3
Key Management: Vault (rotation yearly)
Row-Level Security: Only authorized staff
Audit Logging: All access logged
```

### 3. Application Architecture
- **Welche Apps brauchen wir?** (System Catalog)
- **Wie kommunizieren sie?** (APIs, Integrations)
- **Wer nutzt sie?** (User Groups, SSO)

**Compliance-Beispiel (NIS2 Governance):**
```
Auth Service → OAuth2/OIDC
Data Service → PostgreSQL with RLS
Admin Dashboard → RBAC, Audit Logging
API Gateway → Rate Limiting, Input Validation
```

### 4. Technology Architecture
- **Welche Infrastruktur?** (Kubernetes, Cloud, On-Prem)
- **Welche Tools?** (Vault, OpenTelemetry, Prometheus)
- **Wie secure?** (Firewalls, NetworkPolicies, mTLS)

**Compliance-Beispiel (Zero Trust):**
```
Netzwerk Layer: NetworkPolicies (Deny-All Default)
Authentifizierung: mTLS für Service-to-Service
Autorisierung: RBAC in Kubernetes
Monitoring: All traffic logged
Incident Response: Automated alerts on anomalies
```

---

## Compliance → Architecture Mapping (Beispiel NIS2)

```
NIS2 Anforderung: "Access Control müssen implementiert sein"
    ↓
What does this mean?
├── A.8.2.1: User access management
├── A.8.2.2: Privileged access management (PAM)
├── A.8.2.3: User registration/de-registration
└── A.8.2.4: Access rights review

Architecture Translation:
├── Business: Define roles (Admin, User, Auditor)
├── Information: Define what each role can access (RLS policies)
├── Application: OAuth2 Authorization with RBAC
└── Technology: Kubernetes RBAC + Network Policies

Implementation:
├── Spring Boot OAuth2 Resource Server
├── PostgreSQL Row-Level Security (RLS)
├── Kubernetes ServiceAccounts + RBAC
├── Vault for credential management
└── OpenTelemetry for audit logging
```

---

## Architecture Decision Records (ADRs)

**Warum?** Compliance-Anforderungen dokumentieren und nachverfolgen

### ADR Template

```markdown
# ADR-001: OAuth2 für Authentifizierung wählen

## Context
NIS2 A.8.2 verlangt "access control policies".
Wir brauchen ein modernes Authentication System.

## Decision
Wir implementieren OAuth2 + OIDC mit Spring Security.

## Rationale
1. Industry standard für Security
2. Unterstützt MFA (NIS2 Anforderung)
3. Audit trail integriert
4. Compliant mit ISO 27001 A.9.2

## Consequences
- Neue Abhängigkeit zu Authorization Server
- Zusätzliche Token Management Komplexität
- ✅ Aber: Compliance erreichbar

## Compliance Mapping
- NIS2 A.8.2 ✅ (Access Control)
- ISO 27001 A.9.2 ✅ (User Access Management)
- EU AI Act ✅ (Audit Trail for Decisions)
```

---

## Layered Security Architecture

```
┌─────────────────────────────────────────┐
│     Compliance Requirement              │
│     (NIS2, ISO27001, AI Act)            │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│   Architecture Layer                     │
│   (TOGAF: Business → Tech)              │
└──────────────────┬──────────────────────┘
                   │
    ┌──────────────┼──────────────┐
    │              │              │
┌───▼────┐  ┌──────▼──────┐  ┌───▼────┐
│Physical│  │ Logical     │  │Security │
│Network │  │ (APIs,Svcs) │  │Controls │
└────────┘  └─────────────┘  └────────┘
    │              │              │
    └──────────────┼──────────────┘
                   │
    ┌──────────────▼──────────────┐
    │ Implementation              │
    │ (Code, Infrastructure,K8s)  │
    └─────────────────────────────┘
```

---

## Enterprise Architecture für Compliance

### Governance Structure

```
Board/Executive
    ↓
Risk Committee
    ├── CTO (Technology)
    ├── CISO (Security)
    ├── Compliance Officer
    └── Legal/Privacy
    ↓
Architecture Review Board (ARB)
    ├── Enterprise Architect
    ├── Security Architect
    ├── Data Architect
    └── DevOps Lead
    ↓
Architecture Decisions
    ├── ADRs written
    ├── Compliance reviewed
    └── Implementation planned
```

### Compliance Review in Architecture

```
Neue Feature angefordert:
    ↓
1. Business Requirements klar?
2. Compliance Requirements identifizieren
   └── NIS2? ISO27001? GDPR? AI Act?
3. Architecture Design + Compliance Mapping
   └── ADR: Welche Controls?
4. Security Review
   └── CISO/Architect approves
5. Implementation
   └── Controls in Code/Config
6. Audit
   └── Verify controls are working
```

---

## Key Takeaway

**Enterprise Architecture ist die Brücke:**
```
Compliance Requirement (abstract)
         ↓
Architecture Decision (structured thinking)
         ↓
Code Implementation (concrete, auditable)
```

**Ohne EA:** Compliance wird ad-hoc, inkonsistent, schwer zu auditen.  
**Mit EA:** Compliance ist strukturiert, dokumentiert, nachprüfbar.

---

[← Zurück zu Resources](resources.md)
