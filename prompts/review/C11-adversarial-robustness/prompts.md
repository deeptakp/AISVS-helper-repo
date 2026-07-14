# C11 — Adversarial Robustness: Prompts

> AISVS Reference: C11.1–C11.4 | Controls: 11.1.1–11.4.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C11-REVIEW-01: Review Adversarial Robustness Controls

**Objective**
- You are reviewing an AI system's robustness controls for AISVS C11.1 and C11.4 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C11.1.1 — Has the model undergone alignment/safety training to prevent disallowed content generation?
- C11.1.2 — Is a version-controlled alignment test suite run on every model update?
- C11.1.3 — Are models evaluated against known adversarial attack techniques relevant to their modality?
- C11.1.4 — Is the model hardened against adversarial inputs (not just tested but actually hardened)?
- C11.4.1 — Do inputs from external/untrusted sources pass through anomaly detection before inference?
- C11.4.2 — Do anomalous inputs trigger gating actions (block or review)?
- C11.1.5 (L3) — Is there an automated evaluator tracking harmful-content rate for regression detection?
- For each FAIL: state gap, control ID, and remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an AI system's robustness controls for AISVS C11.1 and C11.4 compliance.

Check each item:
[ ] C11.1.1 — Has the model undergone alignment/safety training to prevent disallowed content generation?
[ ] C11.1.2 — Is a version-controlled alignment test suite run on every model update?
[ ] C11.1.3 — Are models evaluated against known adversarial attack techniques relevant to their modality?
[ ] C11.1.4 — Is the model hardened against adversarial inputs (not just tested but actually hardened)?
[ ] C11.4.1 — Do inputs from external/untrusted sources pass through anomaly detection before inference?
[ ] C11.4.2 — Do anomalous inputs trigger gating actions (block or review)?
[ ] C11.1.5 (L3) — Is there an automated evaluator tracking harmful-content rate for regression detection?

For each FAIL: state gap, control ID, and remediation.
```


### C11-REVIEW-02: Review Extraction and Inference Attack Defenses

**Objective**
- You are reviewing an AI inference API for AISVS C11.2 and C11.3 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C11.2.1 — Are model-inferred sensitive attributes absent from API outputs?
- C11.2.2 — Are per-principal and global rate limits enforced, sized to the extraction threat model?
- C11.2.3 — Are model outputs calibrated (no raw logits/probabilities exposed externally)?
- C11.3.1 — Does query-pattern analysis feed an extraction-attempt detector?
- C11.3.2 — Are raw model outputs prevented from reaching external callers?
- C11.2.4 (L3) — Is differentially-private optimization used for training on sensitive datasets?
- C11.3.3 (L3) — Is model watermarking applied so unauthorized copies can be identified?
- C11.3.4 (L3) — Do extraction detection triggers cause response measures?
- For each FAIL: state gap, control ID, and remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an AI inference API for AISVS C11.2 and C11.3 compliance.

Check each item:
[ ] C11.2.1 — Are model-inferred sensitive attributes absent from API outputs?
[ ] C11.2.2 — Are per-principal and global rate limits enforced, sized to the extraction threat model?
[ ] C11.2.3 — Are model outputs calibrated (no raw logits/probabilities exposed externally)?
[ ] C11.3.1 — Does query-pattern analysis feed an extraction-attempt detector?
[ ] C11.3.2 — Are raw model outputs prevented from reaching external callers?
[ ] C11.2.4 (L3) — Is differentially-private optimization used for training on sensitive datasets?
[ ] C11.3.3 (L3) — Is model watermarking applied so unauthorized copies can be identified?
[ ] C11.3.4 (L3) — Do extraction detection triggers cause response measures?

For each FAIL: state gap, control ID, and remediation.
```


---
