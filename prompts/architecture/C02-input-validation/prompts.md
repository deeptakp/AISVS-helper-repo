# C2 — Input Validation: Architecture Prompts

> AISVS Reference: C2.1–C2.2 | Controls: 2.1.1–2.2.4

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C2-ARCH-01: Implement Prompt Injection Defense Layer

**Objective**
- You are designing the input processing pipeline for an LLM-based application.

**Required Controls**
- Apply AISVS C2.1.1 through C2.1.5.

**Execution Steps**
- Normalize all inputs: Unicode NFC normalization, strip null bytes, collapse excessive whitespace.
- Apply an allow-list character set — permit only characters required for the application's stated use case.
- Reject (do not truncate) any input that exceeds the configured token limit. Return HTTP 400.
- Screen every input against a prompt injection detection ruleset or classifier before it enters the model context.
- Use a layered approach: pattern-matching rules + a dedicated injection classifier.
- Log and block flagged inputs; return a safe error response to the caller.
- Detect encoding/representation smuggling: detect and reject Base64, URL encoding, homoglyph substitution,
- and zero-width character injection in inputs.
- Output: InputValidationMiddleware class/module with unit tests for each defense.

**Expected Artifacts**
- InputValidationMiddleware class/module with unit tests for each defense.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are designing the input processing pipeline for an LLM-based application.
Apply AISVS C2.1.1 through C2.1.5.

Requirements:
- Normalize all inputs: Unicode NFC normalization, strip null bytes, collapse excessive whitespace.
- Apply an allow-list character set — permit only characters required for the application's stated use case.
- Reject (do not truncate) any input that exceeds the configured token limit. Return HTTP 400.
- Screen every input against a prompt injection detection ruleset or classifier before it enters the model context.
  - Use a layered approach: pattern-matching rules + a dedicated injection classifier.
  - Log and block flagged inputs; return a safe error response to the caller.
- Detect encoding/representation smuggling: detect and reject Base64, URL encoding, homoglyph substitution,
  and zero-width character injection in inputs.

Output: InputValidationMiddleware class/module with unit tests for each defense.
```

