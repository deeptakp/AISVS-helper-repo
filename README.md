# AISVS Helper Repo

This repo helps teams use OWASP AISVS v1.0 in real AI work.

You can use it when you design systems and write code and review changes and run security checks.

Primary policy files:
- `AGENTS.md` (main rules for AI agents)
- `CLAUDE.md` (Claude specific guide that points to `AGENTS.md`)
- `REQUIREMENTS.md` (control reference)

## Quick Start

1. Pick a task mode: `architecture` `coding` `review` or `assessment`.
2. Pick a security level: `L1` `L2` or `L3`.
3. Load prompts from `prompts/<mode>/Cxx-*/prompts.md`.
4. Map outputs and findings to AISVS control IDs.
5. Use templates in `templates/` for reports and release checks.

## Repository Layout

```
aisvs-helper-repo/
├── README.md
├── AGENTS.md
├── CLAUDE.md
├── REQUIREMENTS.md
├── prompts/
│   ├── README.md
│   ├── architecture/C01-.../prompts.md ... architecture/C12-.../prompts.md
│   ├── coding/C01-.../prompts.md ... coding/C12-.../prompts.md
│   ├── review/C01-.../prompts.md ... review/C12-.../prompts.md
│   └── assessment/C01-.../prompts.md ... assessment/C12-.../prompts.md
└── templates/
    ├── AISVS-checklist.md
    ├── AISVS-assessment-report.md
    ├── AISVS-threat-model.md
    └── AISVS-security-review-request.md
```

## AISVS Levels

- `L1`: Baseline (required for all AI systems)
- `L2`: Standard (production systems with sensitive data/decisions)
- `L3`: Advanced (high-assurance, regulated, or critical systems)

If you are not sure about the level start with `L1` and then list what is needed for `L2` and `L3`.

## Control Families

| ID | Family | Example Risks |
|---|---|---|
| C1 | Training Data Integrity & Traceability | Data poisoning, provenance loss |
| C2 | Input Validation | Prompt injection, jailbreaks |
| C3 | Model Lifecycle Management | Unauthorized model changes |
| C4 | Infrastructure & Deployment Security | Model theft, unsafe runtime |
| C5 | Access Control & Identity | Privilege escalation, data leakage |
| C6 | Supply Chain Security | Backdoored artifacts |
| C7 | Model Behavior & Output Safety | Unsafe outputs, leakage |
| C8 | Memory, Embeddings & Vector Security | RAG poisoning, cross-tenant leaks |
| C9 | Orchestration & Agentic Security | Budget bypass, unsafe autonomy |
| C10 | MCP Security | Token misuse, protocol injection |
| C11 | Adversarial Robustness | Evasion, extraction, inversion |
| C12 | Monitoring, Logging & Detection | Undetected abuse, weak forensics |

## Templates

- `templates/AISVS-checklist.md`: security checklist for sprint or release
- `templates/AISVS-assessment-report.md`: formal assessment report
- `templates/AISVS-threat-model.md`: architecture threat model
- `templates/AISVS-security-review-request.md`: security review request

## References

- [OWASP AISVS GitHub](https://github.com/OWASP/AISVS)
- [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
- [MITRE ATLAS](https://atlas.mitre.org/)
- [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework)
