# EU AI Act — Regulation (EU) 2024/1689

**EU AI Act** = Erste rechtsverbindliche KI-Regulierung weltweit.

## 📋 Überblick

- **In Kraft**: Seit Mai 2024
- **Vollständig gültig**: Januar 2026
- **Zweck**: Risikobewertung und Governance von KI-Systemen
- **Geltung**: Alle KI-Systeme in der EU (auch von außerhalb)

## 🎯 Risk-Based Approach

KI-Systeme werden nach Risiko klassifiziert:

| Kategorie | Beschreibung | Beispiele | Anforderungen |
|-----------|-------------|----------|---------------|
| **Prohibited Risk** | Verbotene KI | Biometrische Massenüberwachung | ❌ Nicht erlaubt |
| **High Risk** | Hohe Risiken | Kreditvergabe, Recruitment | ⚠️ Streng reguliert |
| **Limited Risk** | Transparenz-Anforderungen | Chatbots, KI-generierte Inhalte | ℹ️ Disclosure erforderlich |
| **Minimal Risk** | Gering/unbekannt | Bildbearbeitung, Spam-Filter | ✅ Minimal Regulierung |

## 🎯 Kernverpflichtungen (High-Risk AI)

### 1. Transparenz & Dokumentation
- [ ] Trainings-Daten dokumentieren
- [ ] Model Card erstellen
- [ ] Bias-Assessment durchführen

### 2. Testing & Validierung
- [ ] Adversarial Testing
- [ ] Robustness Testing
- [ ] Fairness & Bias Evaluation

### 3. Human Oversight
- [ ] Monitoring durch Menschen
- [ ] Audit Trails
- [ ] Abschaltmechanismus

### 4. Governance
- [ ] Responsible AI Officer
- [ ] Impact Assessments
- [ ] Compliance Documentation

## 📊 "OWASP LLM Top 10" für AI Security

Sicherheitsrisiken bei Large Language Models:

1. **Prompt Injection** — Manipulation durch Eingaben
2. **Insecure Output Handling** — Ungefilterter Output
3. **Training Data Poisoning** — Böswillige Trainingsdaten
4. **Model Denial of Service** — Überlastung
5. **Supply Chain Vulnerabilities** — Unsichere Abhängigkeiten
6. **Sensitive Information Disclosure** — Datenlecks
7. **Insecure Plugin Design** — Unsichere Integrationen
8. **Excessive Agency** — Unkontrollierte Autonomie
9. **Overreliance** — Zu viel Vertrauen in KI
10. **Model Theft** — Unbefugter Zugriff

## 📚 Gelernte Inhalte

*Deine Notizen hier*

### Woche 5-6: AI Act Grundlagen
- [ ] Risk Classification verstanden
- [ ] High-Risk Requirements erfasst
- [ ] OWASP LLM Top 10 durchgelesen

### Woche 7-8: Praktische Implementierung
- [ ] Bias Detection implementiert
- [ ] Prompt Injection Prevention
- [ ] Audit Trails für AI Decisions

---

## 🔧 Praktische Architektur für AI Services

```
User Input → Prompt Injection Prevention
  ↓
LLM API (z.B. OpenAI, Anthropic)
  ↓
Output Validation & Filtering
  ↓
Audit Logging (alle Inputs/Outputs)
  ↓
Human Review (für kritische Decisions)
  ↓
Response to User
```

### Code-Beispiel: Prompt Injection Prevention
```python
# ❌ UNSICHER
response = openai.ChatCompletion.create(
    messages=[{"role": "user", "content": user_input}]  # Direkt vom User!
)

# ✅ SICHER
sanitized_input = sanitize_prompt(user_input)
response = openai.ChatCompletion.create(
    system="You are a helpful assistant for X. Respond only about X.",
    messages=[{"role": "user", "content": sanitized_input}]
)
audit_log(user_input, response, user_id, timestamp)
```

---

## 📖 Ressourcen

- [EU AI Act — Official Text](https://eur-lex.europa.eu/)
- [OWASP LLM Top 10](https://owasp.org/www-project-llm-top-10/)
- [ENISA AI Security Recommendations](https://www.enisa.europa.eu/)

---

**Status:** 🚧 In Bearbeitung  
**Letzte Aktualisierung:** 2026-05-12
