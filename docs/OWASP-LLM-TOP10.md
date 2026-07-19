# OWASP Top 10 for LLM Applications

Summary with practical mitigations. Based on the OWASP Top 10 for LLM Applications.

| ID | Risk | What it is | Key mitigations |
|----|------|------------|-----------------|
| **LLM01** | Prompt Injection | Untrusted input overrides intended instructions (direct or via retrieved content). | Treat all external content as data, not instructions; separate system/user roles; input & output guardrails; least agency. |
| **LLM02** | Insecure Output Handling | Model output used downstream without validation (XSS, SSRF, code exec). | Encode/validate output; never `eval` model output; sandbox; treat output as untrusted. |
| **LLM03** | Training Data Poisoning | Malicious/biased data corrupts the model. | Vet data sources; provenance; integrity checks; anomaly detection on training sets. |
| **LLM04** | Model Denial of Service | Resource-exhausting inputs. | Rate limits; input size caps; cost/quota monitoring. |
| **LLM05** | Supply Chain | Compromised models, datasets, or plugins. | Verify model/plugin provenance; SBOM for ML; pin & scan dependencies. |
| **LLM06** | Sensitive Information Disclosure | Model reveals secrets/PII from context or training. | Output filtering/DLP; data minimization; don't put secrets in prompts; scoped retrieval. |
| **LLM07** | Insecure Plugin Design | Plugins with weak input validation / excess permissions. | Strict input validation; least privilege; authenticate plugin calls. |
| **LLM08** | Excessive Agency | Agent has too much permission/autonomy. | Minimal tool scope; human-in-the-loop for side effects; deny-by-default. |
| **LLM09** | Overreliance | Blindly trusting model output. | Human review; cite sources; communicate uncertainty; validate facts. |
| **LLM10** | Model Theft | Unauthorized model exfiltration. | Access controls; rate limiting; watermarking; monitor extraction patterns. |

## Priorities for most teams
1. **LLM01 / LLM02** — the highest-frequency issues; get guardrails in first.
2. **LLM06 / LLM08** — highest blast radius in agentic/RAG systems.
3. **LLM05** — the emerging supply-chain frontier.

See [../examples/prompt-injection/](../examples/prompt-injection/) for LLM01/LLM02 in practice.
