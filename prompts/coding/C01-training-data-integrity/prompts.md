# C1 — Training Data Integrity & Traceability: Prompts

> AISVS Reference: C1.1–C1.3 | Controls: 1.1.1–1.3.5

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C1-CODE-02: Implement Data Integrity Verification

**Objective**
- You are implementing integrity controls for a training data pipeline.

**Required Controls**
- Apply AISVS C1.1.3 and C1.1.4.

**Execution Steps**
- Compute cryptographic hashes (SHA-256 minimum) for all training data files at ingest.
- Store hashes in a separate integrity manifest file, signed with HMAC or digital signature.
- Implement a pre-training integrity check that re-hashes all files and compares against the manifest.
- Fail the pipeline with a detailed error if any hash mismatch is detected.
- Alert on unauthorized modification attempts.
- Output: integrity check module with ingest hashing and pre-training verification.

**Expected Artifacts**
- integrity check module with ingest hashing and pre-training verification.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing integrity controls for a training data pipeline.
Apply AISVS C1.1.3 and C1.1.4.

Requirements:
- Compute cryptographic hashes (SHA-256 minimum) for all training data files at ingest.
- Store hashes in a separate integrity manifest file, signed with HMAC or digital signature.
- Implement a pre-training integrity check that re-hashes all files and compares against the manifest.
- Fail the pipeline with a detailed error if any hash mismatch is detected.
- Alert on unauthorized modification attempts.

Output: integrity check module with ingest hashing and pre-training verification.
```


### C1-CODE-03: Implement Labeling Platform Access Control

**Objective**
- You are implementing security controls for a data labeling platform.

**Required Controls**
- Apply AISVS C1.2.1 and C1.2.3.

**Execution Steps**
- Implement role-based access control with roles: Labeler, Reviewer, Approver, Admin.
- Labelers can create annotations; only Reviewers and above can modify or approve them.
- Enforce PII/sensitive data detection before labels are stored — use a configurable redaction policy.
- All label changes must be audit-logged with user identity, timestamp, and change diff.
- Implement cryptographic signing of finalized labeling artifacts (C1.2.2).
- Output: RBAC implementation + PII redaction integration + audit logging.

**Expected Artifacts**
- RBAC implementation + PII redaction integration + audit logging.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing security controls for a data labeling platform.
Apply AISVS C1.2.1 and C1.2.3.

Requirements:
- Implement role-based access control with roles: Labeler, Reviewer, Approver, Admin.
- Labelers can create annotations; only Reviewers and above can modify or approve them.
- Enforce PII/sensitive data detection before labels are stored — use a configurable redaction policy.
- All label changes must be audit-logged with user identity, timestamp, and change diff.
- Implement cryptographic signing of finalized labeling artifacts (C1.2.2).

Output: RBAC implementation + PII redaction integration + audit logging.
```


### C1-CODE-04: Implement Poisoning Detection in Training Pipeline

**Objective**
- You are implementing security controls in an ML training pipeline.

**Required Controls**
- Apply AISVS C1.3.1 and C1.3.4.

**Execution Steps**
- Integrate a data poisoning detection step before model training begins.
- Detect statistical outliers in the dataset that may indicate injected poisoned samples.
- Run a content classifier to detect disallowed content (CSAM, hate speech, PII, etc.) and remove flagged samples.
- Generate a pre-training report summarizing: total samples, flagged samples, removal actions.
- Fail the training run if the flagged-sample rate exceeds a configurable threshold.
- Output: pipeline stage with outlier detection, content filtering, and pre-training report.

**Expected Artifacts**
- pipeline stage with outlier detection, content filtering, and pre-training report.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing security controls in an ML training pipeline.
Apply AISVS C1.3.1 and C1.3.4.

Requirements:
- Integrate a data poisoning detection step before model training begins.
- Detect statistical outliers in the dataset that may indicate injected poisoned samples.
- Run a content classifier to detect disallowed content (CSAM, hate speech, PII, etc.) and remove flagged samples.
- Generate a pre-training report summarizing: total samples, flagged samples, removal actions.
- Fail the training run if the flagged-sample rate exceeds a configurable threshold.

Output: pipeline stage with outlier detection, content filtering, and pre-training report.
```


---
