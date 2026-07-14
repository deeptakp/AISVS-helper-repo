# C7 — Model Behavior, Output Control & Safety Assurance: Architecture Prompts

> AISVS Reference: C7.1–C7.4 | Controls: 7.1.1–7.4.4

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C7-ARCH-01: Implement Output Schema Validation

**Objective**
- You are designing the output processing layer for an LLM-based application.

**Required Controls**
- Apply AISVS C7.1.1 and C7.1.2.

**Execution Steps**
- Define a JSON schema (or equivalent typed schema) for every model response type in the application.
- Implement an OutputValidator that:
- Validates every model response against the declared schema — reject (do not return) non-conforming outputs.
- Enforces output length limits (max tokens, max characters) with hard truncation at the schema limit.
- Enforces termination controls: detect and strip unsafe stop sequences or repeated output loops.
- Returns a safe fallback response when validation fails — never return raw rejected output to callers.
- Log every validation failure with: model identifier, failure reason, output hash, timestamp.
- Output: OutputValidator with schema enforcement, length limits, and fallback handling.

**Expected Artifacts**
- OutputValidator with schema enforcement, length limits, and fallback handling.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are designing the output processing layer for an LLM-based application.
Apply AISVS C7.1.1 and C7.1.2.

Requirements:
- Define a JSON schema (or equivalent typed schema) for every model response type in the application.
- Implement an OutputValidator that:
  1. Validates every model response against the declared schema — reject (do not return) non-conforming outputs.
  2. Enforces output length limits (max tokens, max characters) with hard truncation at the schema limit.
  3. Enforces termination controls: detect and strip unsafe stop sequences or repeated output loops.
  4. Returns a safe fallback response when validation fails — never return raw rejected output to callers.
- Log every validation failure with: model identifier, failure reason, output hash, timestamp.

Output: OutputValidator with schema enforcement, length limits, and fallback handling.
```

