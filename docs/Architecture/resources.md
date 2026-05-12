# Enterprise Architecture — Resources & Standards

## Enterprise Architecture Frameworks

### TOGAF (The Open Group Architecture Framework)
- [TOGAF Official](https://www.opengroup.org/togaf) — Industry Standard für Enterprise Architecture
- [TOGAF 9.2 Certification](https://www.opengroup.org/certifications/togaf) — Zertifizierung
- [TOGAF ADM (Architecture Development Method)](https://www.opengroup.org/togaf) — Strukturierter Prozess
- **Anwendung:** Governance, Compliance-Mapping, Security Architecture Design

### Zachman Framework
- [Zachman Institute](https://www.zachman.com/) — Original Zachman Framework
- [Zachman Enterprise Architecture](https://www.zachman.com/resources) — Ressourcen & Trainings
- **Anwendung:** Holistische Sicht auf IT, Compliance Requirements Mapping

### ArchiMate (Architecture Modelling Language)
- [ArchiMate Specification](https://www.opengroup.org/archi) — Standard Modellierungssprache
- [ArchiMate Tools](https://www.opengroup.org/archi/tools) — Modellierungs-Tools
- **Anwendung:** Visuelle Architecture Dokumentation, Stakeholder Communication

---

## Standards & Frameworks für Security Architecture

### ISO/IEC/IEEE Standards

- [ISO/IEC/IEEE 42010](https://www.iso.org/standard/74393.html) — Systems and Software Engineering Architecture Description
- [ISO/IEC 27001 + Architecture](https://www.iso.org/standard/82875.html) — ISMS Architecture Design
- [ISO/IEC 27035](https://www.iso.org/standard/60803.html) — Security Incident Management Architecture

### NIST Standards

- [NIST SP 800-39: Risk Management Framework](https://csrc.nist.gov/publications/detail/sp/800/39) — RMF für Enterprise
- [NIST SP 800-37: RMF Revision 2](https://csrc.nist.gov/publications/detail/sp/800/37/rev-2) — Governance & Compliance
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework) — Überblick Security Architecture
- [NIST SP 800-64: Security Considerations in System Development Life Cycle](https://csrc.nist.gov/publications/detail/sp/800/64/rev-2) — DevSecOps Architecture

### Zero Trust Architecture (NIST SP 800-207)

- [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800/207) — Offizieller Standard
- Zero Trust Design Principles (Verify + Validate + Monitor)

---

## Cloud Architecture & Patterns

### AWS Well-Architected Framework
- [AWS Well-Architected](https://aws.amazon.com/architecture/well-architected/) — Best Practices
- [AWS Security Pillar](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/) — Security-fokussiert
- [AWS Reference Architecture](https://aws.amazon.com/architecture/reference-architecture-diagrams/) — Vorgefertigt

### Azure Architecture
- [Azure Architecture Center](https://learn.microsoft.com/en-us/azure/architecture/) — Microsoft Reference
- [Azure Security Architecture](https://learn.microsoft.com/en-us/azure/security/fundamentals/architecture) — Security Patterns
- [Azure CAF (Cloud Adoption Framework)](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/) — Governance

### Google Cloud Architecture
- [Google Cloud Architecture Framework](https://cloud.google.com/architecture) — Google Best Practices
- [Google Cloud Security Best Practices](https://cloud.google.com/architecture/security-best-practices) — Security-fokussiert

---

## Microservices & Distributed Systems Architecture

### Books & References

- **"Building Microservices" (Sam Newman)** — Klassisch für Microservices Design
- **"The Microservices Architecture" (O'Reilly)** — Patterns & Practices
- [O'Reilly Microservices Architecture](https://www.oreilly.com/library/view/microservices-architecture/9781491950340/) — Online

### Kubernetes Architecture

- [Kubernetes Architecture](https://kubernetes.io/docs/concepts/architecture/) — Offizielle Docs
- [Cloud Native Security Whitepaper](https://www.cncf.io/blog/2021/12/15/supply-chain-security/) — CNCF
- [OWASP Kubernetes Top 10](https://owasp.org/www-project-kubernetes-top-ten/) — Security Patterns

---

## Compliance-Driven Architecture

### Mapping Standards to Architecture

- [TOGAF Security Architecture](https://www.opengroup.org/togaf) — Security in TOGAF ADM
- [NIS2 Architecture Requirements](https://www.enisa.europa.eu/topics/nis-directive) — ENISA Guidance
- [ISO 27001 Architecture Design](https://www.iso.org/standard/82875.html) — Controls to Architecture
- [EU AI Act Architecture](https://digital-strategy.ec.europa.eu/en/policies/eu-artificial-intelligence-act) — AI-spezifisch

### Architecture Decision Records (ADRs)

- [ADR GitHub Template](https://github.com/joelparkerhenderson/architecture-decision-record) — Standard Format
- [ADR Best Practices](https://adr.github.io/) — Community
- **Anwendung:** Dokumentation von Compliance-Anforderungen → Architecture Decisions

---

## Threat Modeling & Risk-Based Architecture

- [STRIDE Methodology](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats) — Threat-Driven Design
- [Attack Trees](https://en.wikipedia.org/wiki/Attack_tree) — Visual Risk Analysis
- [OWASP Threat Dragon](https://www.threatdragon.com/) — Architecture Threat Modeling Tool
- [Security Architecture Review Board](https://www.cisecurity.org/) — Governance

---

## Trainings & Certifications

### TOGAF Certification Path
1. TOGAF 9.2 Foundation (Level 1)
2. TOGAF 9.2 Certified (Level 2)
- [TOGAF Training Partner](https://www.opengroup.org/togaf) — Offizielle Kurse

### Microservices Architecture Certified (MSAC)
- [The Linux Foundation — Microservices Arch](https://www.linuxfoundation.org/training/microservices-architecture-for-enterprises/) — Certification

### AWS Solutions Architect
- [AWS Certified Solutions Architect](https://aws.amazon.com/certification/certified-solutions-architect-associate/) — Associate/Professional
- Fokus auf compliant, secure architecture

---

## Key Enterprise Architecture Concepts

| Concept | Beschreibung | Relevanz für Compliance |
|---------|-------------|----------------------|
| **Layered Architecture** | Physical, Logical, Business Layers | TOGAF ADM Struktur |
| **Segmentation & Zoning** | Network/Application Isolation | NIS2, Zero Trust |
| **Identity & Access** | IAM Architecture (Centralized vs Federated) | ISO 27001 A.9 |
| **Data Architecture** | Data Classification, Encryption, RLS | ISO 27001 A.10, GDPR |
| **Resilience & DR** | Backup, Failover, RTO/RPO | ISO 27001 A.17 |
| **Monitoring & Observability** | Centralized Logging, Alerting | ISO 27001 A.12.4, NIS2 |
| **Governance Framework** | CAM, Risk Committees, Review Boards | ISO 27001 A.5, NIS2 |

---

## Recommended Reading Order

1. **Start:** TOGAF Overview + Zachman Framework Intro
2. **Deepen:** NIST SP 800-39 Risk Management
3. **Apply:** ISO/IEC 42010 + ArchiMate Modeling
4. **Specialize:** Cloud-Specific (AWS/Azure/GCP) + Kubernetes
5. **Advanced:** Threat Modeling + ADRs + Compliance Mapping

---

**Wichtig:** Enterprise Architecture ist die Brücke zwischen **Business Requirements** (Compliance, Security) und **Technical Implementation** (Code, Infrastructure).

