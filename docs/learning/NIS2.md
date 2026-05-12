# NIS2 Directive — EU Network & Information Security

**NIS2** = Netzwerk- und Informationssicherheitsrichtlinie 2, Nachfolger von NIS1.

## 📋 Überblick

- **Gültig ab**: Januar 2025
- **Geltung**: Alle Länder der EU
- **Adressaten**: Essential Services, Important Service Operators
- **Ziel**: Erhöhung des Cybersecurity-Standards in der EU

## 🎯 Kernverpflichtungen

### Organisatorisch
- [ ] Governance & Risikomanagement
- [ ] Incident Response & Reporting
- [ ] Supply Chain Management

### Technisch
- [ ] Access Control (Authentifizierung, Autorisierung)
- [ ] Encryption (In Transit & at Rest)
- [ ] Monitoring & Logging
- [ ] Vulnerability Management

### Audit & Compliance
- [ ] Regelmäßige Sicherheitsaudits
- [ ] Zertifizierung durch akkreditierte Auditor:innen
- [ ] Incident Reporting an Behörden (72h)

## 📊 Branchenspezifische Anforderungen

| Branche | Besonderheiten |
|---------|---------------|
| **Telekommunikation** | Netzwerk-Sicherheit, Peering-Anforderungen |
| **Energie** | SCADA-Sicherheit, Kritische Infrastruktur |
| **Verkehr** | Automatisierung, Autonome Systeme |
| **Banking** | Finanzielle Stabilität, Datenschutz |
| **Healthcare** | Patientendaten, Verfügbarkeit kritisch |

## 🔗 NIS2 vs. ISO 27001

[→ Vergleich](../resources/NIS2-ISO27001-Comparison.md)

## 📚 Gelernte Inhalte

*Deine Notizen hier — was hast du gelernt?*

### Woche 1-2: NIS2-Grundlagen
- [ ] Richtlinie gelesen (NIST/ENISA Guides)
- [ ] Kernverpflichtungen verstanden
- [ ] Beispiel: Telco-Anforderungen recherchiert

### Woche 3-4: Praktische Umsetzung
- [ ] Risikomanagement-Framework
- [ ] Incident Response Planning
- [ ] Access Control Design

---

## 🔧 Praktische Architektur-Beispiele

*Wie implementiere ich NIS2 im Code/in der Infrastruktur?*

### Authentifizierung & Authorization (ISO/IEC 27001 A.8.2)
```
OAuth2 + OIDC → Service-to-Service Token Management
  ↓
Vault (HashiCorp) → Secrets Management
  ↓
RBAC in Kubernetes → Fine-Grained Access Control
```

### Logging & Monitoring (ISO/IEC 27001 A.12.4)
```
Application Logs → OpenTelemetry
  ↓
Structured Logging (JSON) → Elastic/Grafana
  ↓
Audit Trail → PostgreSQL (immutable append-only)
```

---

## 📖 Ressourcen

- [ENISA NIS2 Implementation Guide](https://www.enisa.europa.eu/)
- [EUR-Lex Richtlinientext](https://eur-lex.europa.eu/)
- [BSI NIS2 Guidance (German)](https://www.bsi.bund.de/)

---

**Status:** 🚧 In Bearbeitung  
**Letzte Aktualisierung:** 2026-05-12
