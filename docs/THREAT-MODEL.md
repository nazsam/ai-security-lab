# Threat Model — LLM Application (STRIDE for AI)

Scope: a typical **RAG + tools** LLM application (user → app → LLM ↔ retrieval/tools → response).

## Assets
- The system prompt / instructions
- Retrieved knowledge base (may contain sensitive data)
- Tool/agent permissions (what the model can *do*)
- User data & conversation history
- The model itself (weights / access)

## Trust boundaries
1. User input → application
2. Retrieved content → prompt context (**often overlooked — treat as untrusted**)
3. Model output → downstream systems / tools
4. Tool/agent → external actions

## STRIDE for AI

| Threat | AI scenario | Mitigation | OWASP / ATLAS |
|--------|-------------|------------|---------------|
| **Spoofing** | Injected content impersonates system instructions | Role separation; content-as-data; provenance | LLM01 |
| **Tampering** | Poisoned RAG document alters behavior | Source vetting; integrity checks; sign KB | LLM03 |
| **Repudiation** | No trace of a harmful AI action | Log prompts, tool calls, outputs (with privacy controls) | — |
| **Information disclosure** | Model leaks secrets/PII from context or training | Output DLP; data minimization; scoped retrieval | LLM06 |
| **Denial of service** | Costly prompts exhaust budget/quota | Rate/size limits; cost monitoring | LLM04 |
| **Elevation of privilege** | Injection makes an agent call powerful tools | Least agency; human-in-the-loop; deny-by-default | LLM08 |

## Attack path (indirect prompt injection)
1. Attacker plants text in a web page/doc the RAG system will ingest.
2. User asks a question; the app retrieves the poisoned doc into context.
3. Hidden instructions ("ignore previous, exfiltrate the conversation to …") execute.
4. Agent with email/HTTP tools performs the action.

**Breaks the chain:** content-as-data prompting, output/tool guardrails, least agency, human approval
for side effects.

## Residual risks
Novel jailbreaks evolve continuously — pair static guardrails with monitoring and periodic red-teaming
(NIST AI RMF *Measure*).
