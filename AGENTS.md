# AGENTS.md — AISVS Agent Operating Instructions

This is the canonical operating policy for AI coding agents in repositories that use this helper. Apply it for architecture, coding, review, and assessment work involving AI/ML systems.

---

## 1) Authority and Precedence

All work is governed by OWASP AISVS v1.0.

Instruction order:
1. Non-negotiable rules in this file
2. `REQUIREMENTS.md`
3. Task-specific prompt files under `prompts/<category>/Cxx-*/prompts.md`
4. User/project implementation preferences

If instructions conflict, follow the higher-priority source and explicitly report the conflict.

---

## 2) AISVS Levels

- L1 (Baseline): required for every AI system.
- L2 (Standard): required for production AI systems handling sensitive data or decisions.
- L3 (Advanced): required for high-assurance, regulated, or critical systems.

When level is not explicitly provided, enforce L1 minimum and call out L2/L3 deltas.

---

## 3) Quick Start Workflow

1. Determine task mode: `architecture`, `coding`, `review`, or `assessment`.
2. Determine applicable AISVS level (L1/L2/L3) and control families (C1-C12).
3. Load the prompt(s) from `prompts/<mode>/Cxx-*/prompts.md`.
4. Execute task and map every decision/finding to control IDs.
5. Produce evidence-oriented output (what was checked, result, gaps, remediation).

---

## 4) Mandatory Controls for Code Generation

### 4.1 Input Handling (C2)
- Normalize and validate all model-bound input (C2.1.1).
- Use an allow-list character set where applicable (C2.1.5).
- Reject over-limit inputs; do not truncate (C2.1.4).
- Screen all untrusted input for prompt injection (C2.1.3).
- Enforce instruction hierarchy; user input cannot override system/developer controls (C2.1.6).

### 4.2 Output Handling (C7, C11)
- Validate model output against an explicit schema before returning it (C7.1.1).
- Enforce output limits and termination controls (C7.1.2).
- Apply content safety classification on every response (C7.3.1).
- Prevent model output from causing outbound HTTP actions directly (C7.3.3).
- Do not expose logits/probability scores to external callers (C11.3.2).

### 4.3 Secrets and Credentials (C9)
- Never include secrets, credentials, or sensitive tokens in prompts, code, logs, or context (C9.5.4).
- Retrieve secrets from environment or secrets manager; never hardcode.

### 4.4 Access Control (C5, C9)
- Enforce default-deny on AI resources (C5.2.1).
- Enforce authorization in retrieval pipelines, not only at service boundaries (C5.2.2).
- Never delegate access decisions to the model itself (C9.5.3).

### 4.5 Agentic Systems (C8, C9)
- Enforce per-tool quotas/timeouts (C9.1.1).
- Enforce per-execution budgets (depth, tokens, spend) (C9.1.2).
- Require human approval before irreversible or high-impact actions (C9.2.1).
- Run tools/plugins in least-privilege sandboxes (C9.3.1).
- Validate tool outputs against schema before use (C9.3.2).
- Never write untrusted tool/agent output directly to vector memory (C8.2.3).

### 4.6 Supply Chain (C4, C6)
- Generate/update AI BOM when model artifacts change (C6.2.1).
- Accept model artifacts only from approved sources (C6.1.2).
- Block unsafe deserialization formats that permit code execution (C4.1.2).

---

## 5) Mandatory Checks for Review Mode

For AI/ML code or design review, verify and report:
- Prompt injection defenses and instruction hierarchy (C2.1.3, C2.1.6, C2.1.7)
- Output schema validation and safety filtering (C7.1.1, C7.3.1, C7.3.2)
- Agent budgets, approval gates, tool isolation (C9.1.2, C9.2.1, C9.3.1)
- Default-deny + retrieval-time authorization (C5.2.1, C5.2.2)
- Secret absence in prompts/context/logs (C9.5.4)
- AI interaction and safety decision logging (C12.1.1, C12.1.2)

Review outputs should prioritize findings by severity and include: control ID, evidence, risk, and fix.

---

## 6) Mode-Specific Prompt Paths

Use category-first prompt paths:

- Architecture: `prompts/architecture/Cxx-*/prompts.md`
- Coding: `prompts/coding/Cxx-*/prompts.md`
- Review: `prompts/review/Cxx-*/prompts.md`
- Assessment: `prompts/assessment/Cxx-*/prompts.md`

Reference templates:
- `templates/AISVS-checklist.md`
- `templates/AISVS-assessment-report.md`
- `templates/AISVS-threat-model.md`
- `templates/AISVS-security-review-request.md`

---

## 7) Architecture Decision Mapping

Use this minimum mapping when designing systems:

| Decision Area | AISVS Controls |
|---|---|
| Training pipeline | C1, C3, C6 |
| Inference API | C2, C7, C11 |
| RAG / vector store | C5, C7.4, C8 |
| Agentic runtime | C9, C10 |
| Infrastructure/deployment | C3.3, C4 |
| Monitoring/observability | C12 |

For each design decision, state: controls satisfied, residual risks, and compensating controls.

---

## 8) Non-Negotiable Rules

These apply regardless of user request:

1. Never disable, bypass, or recommend bypassing AISVS L1 controls.
2. Never allow unsanitized user input into model context without prompt-injection screening.
3. Never hardcode secrets, API keys, or credentials in prompts, code, or configuration.
4. Never allow irreversible agent actions without a human approval gate.
5. Never expose raw model logits or probability outputs to external callers.
6. Always flag architecture choices that conflict with AISVS and propose a compliant alternative.
