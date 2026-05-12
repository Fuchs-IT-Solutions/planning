# NIS2 — Key Requirements

## Was ist NIS2?

**NIS2 = Network & Information Security Directive 2**
- Nachfolger von NIS1 (2016)
- Gültig ab: **Januar 2025**
- Geltung: Alle EU-Länder
- Betroffen: Kritische Infrastruktur + wichtige Dienstleister

## Wer ist betroffen?

### Essential Services
- Energie (Strom, Gas, Wärme)
- Wasser & Abwasser
- Gesundheitswesen
- Verkehr
- Banking & Finanzmarktinfrastruktur
- Digitale Infrastruktur (DNS, IXP)

### Important Operators
- Telekommunikation
- Digitale Services (Suchmaschinen, Cloud, Marktplätze)
- Raumfahrt & Navigation

## 3 Kernverpflichtungen

### 1. Governance & Risk Management
- Risikobewertung durchführen
- Cybersecurity-Governance etablieren
- Vorstand/Management-Involvement
- Incident Response Plan

### 2. Technische Maßnahmen
| Bereich | Anforderungen |
|---------|--------------|
| **Authentication** | Starke Authentifizierung (MFA), OAuth2/OIDC |
| **Encryption** | Daten in Transit (TLS 1.3) und at Rest (AES-256) |
| **Access Control** | Zero Trust, RBAC, Least Privilege |
| **Logging** | Audit Trails, immutable Logs, Monitoring |
| **Vulnerability Mgmt** | Regelmäßige Scans, Patch Management |
| **Supply Chain** | Vendor Security Assessment |

### 3. Incident Management & Reporting
- Incident Response Plan (< 72h Reporting)
- Benachrichtigung von Behörden
- Öffentliche Disclosure bei Bedarf

## NIS2 vs ISO 27001

| Aspekt | NIS2 | ISO 27001 |
|--------|------|----------|
| **Scope** | Kritische Infrastruktur (Telco, Energy, Banking) | Alle Organisationen |
| **Regulierung** | Gesetzliche Verpflichtung (EU) | Freiwillige Zertifizierung |
| **Fokus** | Nationale Cybersecurity | Umfassendes ISMS |
| **Anforderungen** | Governance, Technologie, Incident Mgmt | 14 Kontrollbereiche (A.5-A.18) |
| **Audit** | Nationale Behörden | Akkreditierte Auditor:innen |

**Praktisch:** NIS2 ist **gesetzlich** für bestimmte Branchen, ISO 27001 ist **Standard-Framework** für alle.

## Implementation Roadmap

### Phase 1: Assessment (Jan-Mar 2025)
- [ ] Prüfe: Sind wir "Essential" oder "Important"?
- [ ] Risikobewertung durchführen
- [ ] Gap-Analyse vs. aktuelle Security

### Phase 2: Planung (Apr-Jun 2025)
- [ ] Governance-Struktur definieren
- [ ] Technische Controls planen
- [ ] Incident Response Plan erstellen

### Phase 3: Implementierung (Jul-Dez 2025)
- [ ] Authentication/Authorization hardening
- [ ] Encryption überall
- [ ] Monitoring & Logging
- [ ] Vendor Assessment

### Phase 4: Audit & Zertifizierung (2026)
- [ ] Interne Audits
- [ ] Externe Audit durch akkreditierte Stellen

---

## Wichtigste Architektur-Pattern

```
Zero Trust Model
├── Authentication (OAuth2/OIDC, MFA)
├── Authorization (RBAC, Least Privilege)
├── Encryption (TLS, AES-256)
├── Logging (Immutable Audit Trail)
└── Monitoring (Anomaly Detection)
```

---

[← Zurück zu Resources](resources.md)
