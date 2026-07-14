# C3 — Model Lifecycle Management & Change Control: Prompts

> AISVS Reference: C3.1–C3.5 | Controls: 3.1.1–3.5.4

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C3-REVIEW-01: Review Model Registry and Integrity Controls

**Objective**
- You are reviewing an AI deployment pipeline for AISVS C3.1 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C3.1.1 — Does a model registry exist that inventories all deployed model artifacts and their origins?
- C3.1.2 — Are all model artifacts (weights, tokenizers, adapters, safety models) cryptographically signed?
- C3.1.3 — Are signatures verified at deployment admission AND at model load time?

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an AI deployment pipeline for AISVS C3.1 compliance.

Check each item:
[ ] C3.1.1 — Does a model registry exist that inventories all deployed model artifacts and their origins?
[ ] C3.1.2 — Are all model artifacts (weights, tokenizers, adapters, safety models) cryptographically signed?
[ ] C3.1.3 — Are signatures verified at deployment admission AND at model load time?

Look for:
- Deployment scripts that load models without signature verification.
- Registry entries that lack origin information or hash fields.
- Models deployed outside the registry process (manual uploads, ad-hoc scripts).

For each FAIL: state the gap, control ID, and remediation.
```


### C3-REVIEW-02: Review Deployment Testing and Change Control

**Objective**
- You are reviewing an AI deployment pipeline for AISVS C3.2 and C3.3 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C3.2.1 — Do models undergo automated input validation, safety evaluation, and output sanitization testing before deployment?
- C3.2.2 — Are quantized models re-evaluated against the full safety test suite?
- C3.2.3 (L3) — Do provider model, version, or routing changes trigger security re-evaluation?
- C3.3.1 — Is a controlled rollout mechanism in place with automated rollback triggers?
- C3.3.2 — Does rollback restore the complete model state (not just weights)?
- C3.3.3 — Are parallel model versions isolated in runtime state?
- For each FAIL: state the gap, control ID, and remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an AI deployment pipeline for AISVS C3.2 and C3.3 compliance.

Check each item:
[ ] C3.2.1 — Do models undergo automated input validation, safety evaluation, and output sanitization testing before deployment?
[ ] C3.2.2 — Are quantized models re-evaluated against the full safety test suite?
[ ] C3.2.3 (L3) — Do provider model, version, or routing changes trigger security re-evaluation?
[ ] C3.3.1 — Is a controlled rollout mechanism in place with automated rollback triggers?
[ ] C3.3.2 — Does rollback restore the complete model state (not just weights)?
[ ] C3.3.3 — Are parallel model versions isolated in runtime state?

For each FAIL: state the gap, control ID, and remediation.
```


---
