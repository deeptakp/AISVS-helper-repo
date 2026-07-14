# Prompts Index — AISVS Mode and Control Matrix

This directory organizes prompts by task mode first, then control family.

Structure:
- `architecture/` for system and control design
- `coding/` for implementation work
- `review/` for design/code review
- `assessment/` for control testing and verification

Each mode contains `C01` through `C12` folders, each with a `prompts.md` file.

## Category Paths

| Directory | Purpose |
|---|---|
| [architecture](./architecture/) | Design and architecture prompts |
| [coding](./coding/) | Implementation prompts |
| [review](./review/) | Review prompts |
| [assessment](./assessment/) | Assessment prompts |

## Control Families

| Control | Family | Typical Risks |
|---|---|---|
| C1 | Training Data Integrity & Traceability | Data poisoning, provenance loss |
| C2 | Input Validation | Prompt injection, jailbreaks |
| C3 | Model Lifecycle Management | Unauthorized model changes |
| C4 | Infrastructure & Deployment Security | Unsafe runtime, model theft |
| C5 | Access Control & Identity | Privilege escalation, cross-tenant leakage |
| C6 | Supply Chain Security | Backdoored model artifacts |
| C7 | Model Behavior & Output Safety | Unsafe outputs, prompt leakage |
| C8 | Memory, Embeddings & Vector Security | RAG poisoning, memory abuse |
| C9 | Orchestration & Agentic Security | Budget bypass, unsafe autonomy |
| C10 | MCP Security | Token misuse, schema abuse |
| C11 | Adversarial Robustness | Evasion, extraction, inversion |
| C12 | Monitoring, Logging & Detection | Blind spots, weak auditability |

## Prompt Selection Rule

Select prompts using this pattern:

`prompts/<mode>/Cxx-<family>/prompts.md`

Examples:

```text
# Architecture design for model registry controls
prompts/architecture/C03-model-lifecycle/prompts.md

# Coding work for RAG authorization controls
prompts/coding/C05-access-control/prompts.md

# Security verification for prompt injection controls
prompts/assessment/C02-input-validation/prompts.md
```

## Minimal Workflow

1. Pick mode (`architecture`, `coding`, `review`, `assessment`).
2. Pick AISVS control family (`C01`-`C12`).
3. Load `prompts.md` for that pair.
4. Map output to explicit AISVS control IDs.
