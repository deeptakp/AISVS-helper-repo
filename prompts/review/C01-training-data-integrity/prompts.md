# C1 — Training Data Integrity & Traceability: Prompts

> AISVS Reference: C1.1–C1.3 | Controls: 1.1.1–1.3.5

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C1-REVIEW-01: Review Training Data Provenance Controls

**Objective**
- You are performing a security review of a training data pipeline.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C1.1.1 — Does the pipeline filter out features/fields not required for the model's stated purpose?
- C1.1.2 — Is there a data source inventory capturing origin, license, responsible party, and processing history?
- C1.1.3 — Are all training data files integrity-verified (hashed) during storage and transfer?
- C1.1.4 — Is there active monitoring for unauthorized modifications to stored training data?
- C1.1.5 (L3) — Are datasets watermarked to support attribution and unauthorized-use detection?
- For each FAIL: state the gap, risk, and a concrete remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are performing a security review of a training data pipeline.
Review the following code/configuration for AISVS C1.1 compliance.

Check each item:
[ ] C1.1.1 — Does the pipeline filter out features/fields not required for the model's stated purpose?
[ ] C1.1.2 — Is there a data source inventory capturing origin, license, responsible party, and processing history?
[ ] C1.1.3 — Are all training data files integrity-verified (hashed) during storage and transfer?
[ ] C1.1.4 — Is there active monitoring for unauthorized modifications to stored training data?
[ ] C1.1.5 (L3) — Are datasets watermarked to support attribution and unauthorized-use detection?

For each FAIL: state the gap, risk, and a concrete remediation.
```


### C1-REVIEW-02: Review Labeling Security

**Objective**
- You are performing a security review of a data annotation/labeling system.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C1.2.1 — Are labeling platform access controls role-based, with restricted ability to create, modify, and approve annotations?
- C1.2.2 — Are labeling artifacts cryptographically integrity-protected?
- C1.2.3 — Is sensitive information in labels redacted, anonymized, or encrypted before storage?
- For each FAIL: state the gap, risk, and a concrete remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are performing a security review of a data annotation/labeling system.
Review for AISVS C1.2 compliance.

Check each item:
[ ] C1.2.1 — Are labeling platform access controls role-based, with restricted ability to create, modify, and approve annotations?
[ ] C1.2.2 — Are labeling artifacts cryptographically integrity-protected?
[ ] C1.2.3 — Is sensitive information in labels redacted, anonymized, or encrypted before storage?

For each FAIL: state the gap, risk, and a concrete remediation.
```


### C1-REVIEW-03: Review Data Quality & Poisoning Controls

**Objective**
- You are reviewing an ML training pipeline for data quality and security assurance.

**Required Controls**
- Apply AISVS C1.3.

**Execution Steps**
- C1.3.1 — Does the pipeline run poisoning detection before training starts?
- C1.3.2 — Are auto-generated labels subject to confidence thresholds and consistency checks?
- C1.3.3 — Is the training dataset evaluated for bias patterns before use in security-relevant decisions?
- C1.3.4 — Is disallowed content detected and removed before training?
- C1.3.5 (L3) — Are there defenses against clean-label poisoning attacks?
- For each FAIL: state the gap, risk, and a concrete remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an ML training pipeline for data quality and security assurance.
Apply AISVS C1.3.

Check each item:
[ ] C1.3.1 — Does the pipeline run poisoning detection before training starts?
[ ] C1.3.2 — Are auto-generated labels subject to confidence thresholds and consistency checks?
[ ] C1.3.3 — Is the training dataset evaluated for bias patterns before use in security-relevant decisions?
[ ] C1.3.4 — Is disallowed content detected and removed before training?
[ ] C1.3.5 (L3) — Are there defenses against clean-label poisoning attacks?

For each FAIL: state the gap, risk, and a concrete remediation.
```


---
