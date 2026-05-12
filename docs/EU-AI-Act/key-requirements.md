# EU AI Act — Key Requirements

## Was ist die EU AI Act?

**EU AI Act = Regulation (EU) 2024/1689**
- Erste weltweit **rechtsverbindliche KI-Regulierung**
- In Kraft: Mai 2024
- Vollständig gültig: Januar 2026
- Geltung: Alle KI-Systeme in der EU (auch von außerhalb)
- Ziel: Risikobewertung & Governance von KI

## Risk-Based Classification

KI-Systeme werden nach **Risiko** klassifiziert:

### 🚫 Prohibited Risk (Verboten)
Beispiele:
- Biometrische Massenüberwachung
- Manipulation von Kindern
- Kredit-Scoring basierend auf Ethnizität

**Anforderung:** ❌ Nicht erlaubt

### ⚠️ High Risk (Streng reguliert)
Beispiele:
- Kreditvergabe-Entscheidungen
- Recruitment & Hiring
- Polizei-Einsätze
- Medizinische Diagnosen

**Anforderungen:**
- [ ] Trainings-Daten dokumentieren
- [ ] Model Card erstellen (Capabilities & Limitations)
- [ ] Bias-Assessment durchführen
- [ ] Adversarial Testing
- [ ] Human Oversight Prozess
- [ ] Audit Trail (Alle Inputs/Outputs loggen)

### ℹ️ Limited Risk (Transparenz)
Beispiele:
- Chatbots (müssen disclosed sein: "You're talking to AI")
- KI-generierte Inhalte (watermarking, disclosure)
- Deepfakes (müssen gekennzeichnet sein)

**Anforderung:** Nutzer müssen wissen, dass sie mit KI interagieren

### ✅ Minimal Risk (Gering/Unbekannt)
Beispiele:
- Bildbearbeitung
- Spam-Filter
- Gaming AI

**Anforderung:** Minimal bis keine Regulierung

---

## OWASP LLM Top 10 (Security Risks)

| # | Risiko | Beschreibung | Mitigation |
|---|--------|-------------|-----------|
| 1 | **Prompt Injection** | User manipuliert LLM durch spezielle Prompts | Input validation, Prompt engineering, Guardrails |
| 2 | **Insecure Output Handling** | LLM-Output wird nicht validiert | Output filtering, HTML escaping |
| 3 | **Training Data Poisoning** | Böswillige Daten im Training | Data validation, Source verification |
| 4 | **Model Denial of Service** | Überlastung des Models | Rate limiting, Request throttling |
| 5 | **Supply Chain Vulnerabilities** | Unsichere Dependencies | Dependency scanning, Vendor assessment |
| 6 | **Sensitive Information Disclosure** | Model gibt PII preis | Data masking, Fine-tuning, Monitoring |
| 7 | **Insecure Plugin Design** | Unsichere API-Integrationen | Permission model, Input validation |
| 8 | **Excessive Agency** | LLM hat zu viel Autonomie | Human review loops, Limited actions |
| 9 | **Overreliance** | Zu viel Vertrauen in LLM | Human oversight, Dual validation |
| 10 | **Model Theft** | Unbefugter Zugriff auf das Model | Access controls, Monitoring |

---

## Implementation Requirements (High-Risk AI)

### 1. Governance
- [ ] Verantwortlicher benannt ("AI Officer")
- [ ] Policies für KI-Einsatz
- [ ] Impact Assessments durchgeführt

### 2. Transparency & Documentation
- [ ] Training-Daten dokumentiert
- [ ] Model Card erstellt
- [ ] Limitations & Capabilities offengeleget
- [ ] Bias-Reports verfügbar

### 3. Testing & Validation
- [ ] Adversarial Testing (böswillige Eingaben)
- [ ] Robustness Testing (Edge Cases)
- [ ] Fairness & Bias Evaluation
- [ ] Performance Metrics

### 4. Human Oversight
- [ ] Menschen überprüfen kritische Entscheidungen
- [ ] Audit Trail (Logs aller Aktivitäten)
- [ ] Abschaltmechanismus (Human kann überriden)
- [ ] User Feedback Loop

### 5. Audit & Monitoring
- [ ] Regelmäßige Audits
- [ ] Compliance Monitoring
- [ ] Incident Reporting

---

## Praktische Architektur für High-Risk LLM

```
User Input
    ↓
1. Input Validation & Sanitization
    ↓
2. Prompt Engineering (Guard Rails)
    System Prompt: "You are an X. Only discuss Y."
    ↓
3. LLM API Call (OpenAI, Anthropic, etc.)
    ↓
4. Output Validation
   - Sensitive Information Check
   - Toxicity Detection
   - Relevance Check
    ↓
5. Human Review (für kritische Entscheidungen)
    ↓
6. Audit Logging (Immutable Trail)
{
  "timestamp": "2026-05-12T10:00:00Z",
  "user_id": "uuid",
  "input": "sanitized_input",
  "output": "model_output",
  "decision": "approved|rejected",
  "reviewer": "human_id"
}
    ↓
Response to User
```

## Code Example (Pseudocode)

```python
# High-Risk LLM Implementation
class HighRiskLLMService:
    def process_request(self, user_input, user_id):
        # 1. Input Validation
        sanitized = self.sanitize(user_input)
        
        # 2. Audit Log Input
        self.audit_log.record(
            event="user_query",
            user_id=user_id,
            input=sanitized
        )
        
        # 3. Call LLM with Guard Rails
        system_prompt = """You are a helpful financial advisor.
        ONLY discuss banking topics. NEVER discuss political topics."""
        
        response = self.llm_client.chat(
            system=system_prompt,
            messages=[{"role": "user", "content": sanitized}],
            max_tokens=500
        )
        
        # 4. Validate Output
        if self.contains_pii(response):
            raise SecurityException("Output contains PII")
        
        # 5. Human Review (for critical decisions)
        if self.is_high_impact(response):
            self.queue_for_human_review(response)
            return {"status": "pending_review"}
        
        # 6. Audit Log Output
        self.audit_log.record(
            event="model_response",
            user_id=user_id,
            output=response
        )
        
        return response
```

---

[← Zurück zu Resources](resources.md)
