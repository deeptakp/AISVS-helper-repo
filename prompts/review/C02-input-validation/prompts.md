# C2 — Input Validation: Prompts

> AISVS Reference: C2.1–C2.2 | Controls: 2.1.1–2.2.4

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C2-REVIEW-01: Review Prompt Injection Defenses

**Objective**
- You are reviewing an LLM application's input handling code for AISVS C2.1 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C2.1.1 — Is input normalization applied before tokenization? (Unicode normalization, whitespace collapse)
- C2.1.2 — Is encoding/representation smuggling detected? (Base64, URL encoding, homoglyphs, zero-width chars)
- C2.1.3 — Are all inputs screened by a prompt injection classifier before reaching the model?
- C2.1.4 — Are inputs that exceed token limits rejected (not silently truncated)?
- C2.1.5 — Is an allow-list character set restriction applied to all inputs?
- C2.1.6 — Is an instruction hierarchy enforced? Can users override system prompt instructions?
- C2.1.7 — Are reserved special tokens (control tokens) protected from user injection?
- C2.1.8 (L3) — Does the system detect many-shot jailbreaking patterns across multi-turn conversations?
- For each FAIL: state the gap, the specific AISVS control ID, and a concrete remediation with example code.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an LLM application's input handling code for AISVS C2.1 compliance.

Check each item:
[ ] C2.1.1 — Is input normalization applied before tokenization? (Unicode normalization, whitespace collapse)
[ ] C2.1.2 — Is encoding/representation smuggling detected? (Base64, URL encoding, homoglyphs, zero-width chars)
[ ] C2.1.3 — Are all inputs screened by a prompt injection classifier before reaching the model?
[ ] C2.1.4 — Are inputs that exceed token limits rejected (not silently truncated)?
[ ] C2.1.5 — Is an allow-list character set restriction applied to all inputs?
[ ] C2.1.6 — Is an instruction hierarchy enforced? Can users override system prompt instructions?
[ ] C2.1.7 — Are reserved special tokens (control tokens) protected from user injection?
[ ] C2.1.8 (L3) — Does the system detect many-shot jailbreaking patterns across multi-turn conversations?

For each FAIL: state the gap, the specific AISVS control ID, and a concrete remediation with example code.
```


### C2-REVIEW-02: Review Content Policy Screening

**Objective**
- You are reviewing an LLM application's content screening implementation for AISVS C2.2 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C2.2.1 — Is a content classifier applied to every prompt before model inference?
- C2.2.1 — Are violence, self-harm, hate, and sexual content categories covered with configurable thresholds?
- C2.2.2 — Are prompts in unsupported languages handled with a safe fallback policy?
- C2.2.3 (L2) — Are non-text inputs (images, audio, video) checked for adversarial perturbations and steganographic payloads?
- C2.2.4 (L3) — Are coordinated multi-modal attacks (e.g., steganographic image + injected text) detected?
- For each FAIL: state the gap, risk, and remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an LLM application's content screening implementation for AISVS C2.2 compliance.

Check each item:
[ ] C2.2.1 — Is a content classifier applied to every prompt before model inference?
[ ] C2.2.1 — Are violence, self-harm, hate, and sexual content categories covered with configurable thresholds?
[ ] C2.2.2 — Are prompts in unsupported languages handled with a safe fallback policy?
[ ] C2.2.3 (L2) — Are non-text inputs (images, audio, video) checked for adversarial perturbations and steganographic payloads?
[ ] C2.2.4 (L3) — Are coordinated multi-modal attacks (e.g., steganographic image + injected text) detected?

For each FAIL: state the gap, risk, and remediation.
```


---
