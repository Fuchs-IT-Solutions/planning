# ISO 27001:2022 — Key Requirements

## Was ist ISO 27001?

**ISO 27001:2022 = Information Security Management System Standard**
- Internationaler Standard für ISMS
- Zertifizierbar durch akkreditierte Auditor:innen
- Anwendbar auf alle Organisationen & Industrien
- Fokus: Umfassender Sicherheitsansatz

## Die 14 Kontrollbereiche (A.5 – A.18)

### A.5 — Organizational Controls
- Information Security Policies
- Organization of Information Security
- Human Resource Security

### A.6 — People Controls
- Awareness & Training
- Supplier Relationship Management
- Incident Management (Personnel)

### A.7 — Physical Controls
- Physical & Environmental Security
- Secure Areas & Perimeter Security

### A.8 — Asset Management
- Asset Inventory
- Information Classification
- Media Handling (DVDs, USB, etc.)

### A.9 — Access Control (★ Kritisch)
- User Access Management
- Authentication (Passwords, MFA, OAuth2)
- Authorization (RBAC)
- Special Access Rights (Admin, Service Accounts)

### A.10 — Cryptography (★ Kritisch)
- Encryption in Transit (TLS 1.3)
- Encryption at Rest (AES-256)
- Key Management (Vault, HSM)
- Crypto Algorithm Standards

### A.11 — Physical Security
- Physical Entry Controls
- CCTV, Access Logs
- Secure Facilities

### A.12 — Operations (★ Kritisch)
- Change Management
- Capacity & Performance Management
- System Development & Maintenance
- Backup & Recovery
- Logging & Monitoring (Audit Trails)

### A.13 — Communications
- Network Security
- Segregation (VLAN, Firewalls, NetworkPolicies)
- Encryption in Transit
- Mail & Web Security

### A.14 — System Development
- Software Development Security
- Security Testing
- Vulnerability Management
- Deployment Controls

### A.15 — Supplier Relationships
- Vendor Security Assessment
- SLAs & Contract Terms
- Vendor Incident Management

### A.16 — Incident Management (★ Kritisch)
- Incident Detection & Response
- Reporting (Internal & External)
- Forensics & Evidence Preservation
- Post-Incident Review

### A.17 — Business Continuity (★ Kritisch)
- Backup & Recovery Plans
- Disaster Recovery Tests
- RTO/RPO Definition

### A.18 — Compliance
- Legal & Regulatory Compliance
- Intellectual Property
- Data Protection (GDPR, etc.)
- Audit & Inspection Rights

---

## Implementation Approach

```
Plan (Policies) → Do (Implement) → Check (Audit) → Act (Improve)

Cycle:
1. Risk Assessment
2. Select Controls (14 Bereiche)
3. Implementieren
4. Interne Audits
5. Management Review
6. External Audit (für Zertifizierung)
```

## Kernmaßnahmen (Quick Start)

### Technisch
- [ ] Authentication: Starke Passwörter + MFA
- [ ] Authorization: RBAC (Least Privilege)
- [ ] Encryption: TLS + AES-256
- [ ] Logging: Zentrale Audit Trails
- [ ] Monitoring: Anomaly Detection
- [ ] Backup: Tägliche Backups, RTO/RPO definiert

### Organisatorisch
- [ ] Information Security Policy
- [ ] Risk Assessment durchführen
- [ ] Incident Response Plan
- [ ] Vendor Management
- [ ] Training & Awareness

### Dokumentation
- [ ] Asset Inventory
- [ ] Classification Scheme
- [ ] Change Log
- [ ] Incident Register
- [ ] Audit Reports

---

## Zertifizierungsprozess

1. **Scoping:** Welche Systeme/Prozesse sind im Scope?
2. **Gap Analysis:** Was fehlt noch?
3. **Implementation:** Alle Controls einbauen
4. **Internal Audit:** Selbst prüfen
5. **Management Review:** Vorstand sign-off
6. **External Audit (Stage 1):** Dokumentations-Review
7. **External Audit (Stage 2):** Vor-Ort Audit
8. **Zertifikat:** Gültig für 3 Jahre

---

[← Zurück zu Resources](resources.md)
