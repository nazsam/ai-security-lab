<div align="center">

# 🤖 AI Security Lab

**A hands-on lab for securing AI/LLM systems — OWASP LLM Top 10 demonstrations, prompt-injection examples (vulnerable vs. guarded), a STRIDE-for-AI threat model, and NIST AI RMF / ISO 42001 governance mappings.**

![OWASP LLM Top 10](https://img.shields.io/badge/OWASP_LLM_Top_10-000000?style=for-the-badge&logo=owasp&logoColor=white)
![NIST AI RMF](https://img.shields.io/badge/NIST_AI_RMF-Mapped-005EA2?style=for-the-badge)
![MITRE ATLAS](https://img.shields.io/badge/MITRE_ATLAS-Mapped-C00?style=for-the-badge)
![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)

</div>

---

## 📖 Overview

AI systems introduce a new attack surface — prompt injection, data poisoning, model theft, insecure
output handling — that classic AppSec doesn't fully cover. This lab makes those risks concrete:
**vulnerable-vs-guarded examples**, a threat model, defensive patterns (guardrails), and mappings to
the frameworks that govern AI risk (**OWASP LLM Top 10, MITRE ATLAS, NIST AI RMF, ISO/IEC 42001**).

> ⚠️ All examples are for **defensive education** — understanding attacks to build guardrails. No
> working exploits against third-party systems.

## 🔟 OWASP LLM Top 10

Full breakdown with mitigations → **[docs/OWASP-LLM-TOP10.md](docs/OWASP-LLM-TOP10.md)**

| # | Risk | Covered here |
|---|------|--------------|
| LLM01 | Prompt Injection | [examples/prompt-injection/](examples/prompt-injection/) |
| LLM02 | Insecure Output Handling | guardrails + docs |
| LLM03 | Training Data Poisoning | docs / threat model |
| LLM06 | Sensitive Information Disclosure | output filtering |
| LLM08 | Excessive Agency | least-privilege tools (docs) |
| LLM10 | Model Theft | governance (docs) |

## 🧪 Prompt injection: vulnerable vs. guarded

**[examples/prompt-injection/](examples/prompt-injection/)** shows a naive system prompt that leaks/obeys
injected instructions, a hardened system prompt, injection payloads to test with, and a Python
**input/output guardrail** you can run.

## 🛡️ Defensive patterns
- **Trust boundary:** treat all retrieved/user content as untrusted data, never as instructions.
- **Input & output guardrails:** filter/validate on the way in *and* out.
- **Least agency:** give tools/agents the minimum permissions and require confirmation for side effects.
- **Human-in-the-loop** for high-impact actions.
- **Provenance & isolation** for training and inference data.

## 🏛️ AI governance
- **[docs/NIST-AI-RMF.md](docs/NIST-AI-RMF.md)** — Govern / Map / Measure / Manage, mapped to controls.
- **ISO/IEC 42001** — AI management system alignment.
- **[docs/THREAT-MODEL.md](docs/THREAT-MODEL.md)** — STRIDE adapted for an LLM application.

## ▶️ Run the guardrail demo
```bash
python examples/prompt-injection/guardrail.py
```
(Pure standard-library Python — no external calls; it demonstrates detection logic on sample inputs.)

## 📚 Contents
```
ai-security-lab/
├── docs/
│   ├── OWASP-LLM-TOP10.md · NIST-AI-RMF.md · THREAT-MODEL.md
├── examples/prompt-injection/
│   ├── system-prompt-vulnerable.txt · system-prompt-hardened.txt
│   ├── injection-payloads.md · guardrail.py
└── README · LICENSE · CONTRIBUTING
```

## 🤝 License
**[MIT](LICENSE)** © 2026 devsecforge (S. Naz). For defensive research and education only.
