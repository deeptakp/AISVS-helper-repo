# C11 — Adversarial Robustness: Architecture Prompts

> AISVS Reference: C11.1–C11.4 | Controls: 11.1.1–11.4.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C11-ARCH-01: Implement Alignment Test Suite Automation

**Objective**
- You are designing a continuous model evaluation pipeline.

**Required Controls**
- Apply AISVS C11.1.2 and C11.1.3.

**Execution Steps**
- Implement a version-controlled alignment test suite that runs on every model update or release.
- The suite must cover:
- Safety categories: violence, self-harm, hate speech, sexual content, dangerous instructions.
- Adversarial attack techniques relevant to the model's modality:
- Text: prompt injection, jailbreak patterns, many-shot override, token smuggling
- Image (if applicable): adversarial perturbations, steganographic payloads
- Refusal capability: the model must refuse requests in defined disallowed categories.
- Alignment regression: compare pass rate vs. previous model version.
- Gate model promotion on achieving a minimum pass rate per category (configurable threshold).
- Generate a signed test report recording: model hash, test suite version, per-category results, overall status.
- (L3) Implement an automated harmful-content rate evaluator that flags regressions beyond a defined threshold.
- Output: alignment test runner + signed report generator + promotion gate integration.

**Expected Artifacts**
- alignment test runner + signed report generator + promotion gate integration.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are designing a continuous model evaluation pipeline.
Apply AISVS C11.1.2 and C11.1.3.

Requirements:
- Implement a version-controlled alignment test suite that runs on every model update or release.
- The suite must cover:
  1. Safety categories: violence, self-harm, hate speech, sexual content, dangerous instructions.
  2. Adversarial attack techniques relevant to the model's modality:
     - Text: prompt injection, jailbreak patterns, many-shot override, token smuggling
     - Image (if applicable): adversarial perturbations, steganographic payloads
  3. Refusal capability: the model must refuse requests in defined disallowed categories.
  4. Alignment regression: compare pass rate vs. previous model version.
- Gate model promotion on achieving a minimum pass rate per category (configurable threshold).
- Generate a signed test report recording: model hash, test suite version, per-category results, overall status.
- (L3) Implement an automated harmful-content rate evaluator that flags regressions beyond a defined threshold.

Output: alignment test runner + signed report generator + promotion gate integration.
```

