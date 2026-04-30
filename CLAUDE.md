# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **personal learning and portfolio development plan** for building expertise in enterprise security and compliance architecture over 12 weeks. The project is tracked via GitHub Issues at https://github.com/Fuchs-IT-Solutions/planning/issues.

**Goal**: Transition from Senior Developer to Compliance & Security Architect with expertise in NIS2, ISO 27001, and EU AI Act.

**Structure**:
- **Phase 1 (Weeks 1-6)**: Knowledge building (~60-70h) — study regulatory frameworks, security standards, and architecture patterns
- **Phase 2 (Weeks 7-10)**: Portfolio project (~32-37h) — build "Compliance-Driven Microservices Architecture" on GitHub
- **Phase 3 (Weeks 11-12)**: Marketing & outreach (~31-37h) — LinkedIn optimization, cold outreach to target companies

## How Claude Code Can Help

### Phase 1: Learning
- **Summarize long regulatory documents** (PDFs, EU directives) into structured notes
- **Extract key compliance requirements** from NIS2, AI Act, ISO 27001 documentation
- **Create comparison matrices** (e.g., NIS2 vs ISO 27001 controls)
- **Find and evaluate learning resources** from the links in this plan

### Phase 2: Portfolio Project
When the `compliance-driven-microservices` repo is created, Claude Code should help with:
- **Spring Boot microservices** (`auth-service`, `data-service`, `ai-service`)
  - OAuth2/OIDC implementation
  - API-Key management with audit trails
  - Vault integration for secrets management
  - Prompt injection prevention in AI service
- **Kubernetes manifests** with security hardening
  - RBAC (Role-Based Access Control) with least-privilege
  - NetworkPolicies (deny-all default)
  - Pod Security Standards (restricted)
- **PostgreSQL schema** with row-level security and encryption
- **OpenTelemetry instrumentation** for observability and audit logging
- **GitHub Actions CI/CD** with security scanning (Dependency-Check, SonarCloud, Snyk)
- **Documentation**: Architecture Decision Records (ADRs), compliance control mapping, threat models (STRIDE)

### Phase 3: Marketing
- **LinkedIn content**: Help draft posts about compliance, security, and portfolio learnings
- **Email outreach templates**: Structure personalized cold emails to target companies
- **Website content** (if building portfolio site): Copy for hero section, services, case studies

## Key Technologies & Frameworks

**Core Stack**:
- Spring Boot (authentication, API security)
- Spring Security (OAuth2/OIDC)
- PostgreSQL (data layer with RLS)
- Kubernetes (orchestration & security)
- HashiCorp Vault (secrets management)
- OpenTelemetry (observability)

**Security & Compliance Tools**:
- OWASP Dependency Check (CVE scanning)
- SonarCloud (code quality & security hotspots)
- Snyk (container scanning)
- Kubernetes CIS Benchmark validation

**Regulatory Frameworks** (Study materials, not code):
- **NIS2 Directive**: EU Network & Information Security Directive 2
- **EU AI Act**: Regulation (EU) 2024/1689
- **ISO 27001:2022**: Information Security Management System
- **OWASP Top 10** & **OWASP LLM Top 10** (security vulnerability classes)

## Important Context

1. **This is self-directed learning**, not a client project. Pace and depth can be adjusted based on what resonates.
2. **The portfolio project is the centerpiece** of Phase 2 — it must demonstrate:
   - Understanding of regulatory requirements (controls mapped to code)
   - Security-first design (zero-trust architecture, defense-in-depth)
   - Production-ready practices (CI/CD, monitoring, documentation)
3. **Compliance is about auditability** — code, logs, and documentation must support compliance reviews.
4. **Target audience**: CTOs, Security Leads, Compliance Officers at regulated companies (Telcos, Banks, Insurers — NIS2/ISO27001 is mandatory)

## Resources & Links

All official resources are listed in the main planning document:
- **EU Regulations**: EUR-Lex (official texts), ENISA (implementation guides), BSI (German guidance)
- **Training**: Coursera (ISO 27001), Udemy courses
- **Frameworks**: OWASP, Kubernetes Docs, Spring Security Docs
- **Tools**: HashiCorp Vault, OpenTelemetry, Prometheus, Grafana

## What Not to Do

- Don't create production deployments or expose real infrastructure
- Don't store sensitive data (API keys, credentials) in the repo — use Vault
- Don't skip documentation — compliance audits depend on it
- Don't rush Phase 1 — shallow understanding will show in Phase 2

## When in Doubt

- Refer back to the main plan (3-Monats-Plan-Compliance-Architect.md) for detailed issue descriptions and time allocations
- Check GitHub Issues for current task status and progress
- Prioritize Phase 2 portfolio work — that's what demonstrates competence to potential clients
