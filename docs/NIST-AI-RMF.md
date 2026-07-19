# NIST AI Risk Management Framework (AI RMF 1.0)

The AI RMF organizes AI risk work into four functions. This maps them to practical actions and to
**ISO/IEC 42001** (AI management system) and the **OWASP LLM Top 10**.

## The four functions

### 1. GOVERN (culture & accountability)
- AI policy, roles, and accountability; risk tolerance defined.
- Model inventory and an approval/registration process.
- *ISO 42001:* leadership, policy, roles. *Evidence:* AI register, policy docs.

### 2. MAP (context & risk identification)
- Document each AI system's purpose, data, users, and potential harms.
- Identify threats (see [THREAT-MODEL.md](THREAT-MODEL.md)) and impacted stakeholders.
- *OWASP:* enumerate LLM01–LLM10 applicability.

### 3. MEASURE (assess & track)
- Test for the identified risks: red-team prompt injection, evaluate for bias, measure robustness.
- Metrics: guardrail catch rate, jailbreak success rate, PII-leak rate, hallucination rate.
- *Evidence:* red-team reports, eval results.

### 4. MANAGE (respond & monitor)
- Prioritize and treat risks; deploy guardrails; monitor in production.
- Incident response for AI (prompt-injection incidents, model abuse).
- Continuous monitoring & periodic re-assessment.

## Trustworthiness characteristics (design goals)
Valid & reliable · Safe · Secure & resilient · Accountable & transparent · Explainable · Privacy-enhanced · Fair (bias managed).

## Putting it together
| Function | Do this | Maps to |
|----------|---------|---------|
| Govern | AI policy + model registry | ISO 42001 §5 |
| Map | Per-system risk assessment | OWASP LLM Top 10 |
| Measure | Red-team + evals | MITRE ATLAS TTPs |
| Manage | Guardrails + monitoring + IR | This lab's examples |
