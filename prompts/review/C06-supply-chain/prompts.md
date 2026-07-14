# C6 — Supply Chain Security for Models: Prompts

> AISVS Reference: C6.1–C6.2 | Controls: 6.1.1–6.2.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C6-REVIEW-01: Review Model Artifact Integrity Controls

**Objective**
- You are reviewing a model import and deployment pipeline for AISVS C6.1 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C6.1.1 — Are models scanned for malicious code before import? What scanner is used?
- C6.1.2 — Are model weights, datasets, and adapters downloaded only from an approved source allowlist?
- C6.1.3 — Can every third-party model artifact be integrity-verified (hash + signature)?
- C6.1.4 — Do models pass a behavioral acceptance test suite before promotion to non-dev environments?

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing a model import and deployment pipeline for AISVS C6.1 compliance.

Check each item:
[ ] C6.1.1 — Are models scanned for malicious code before import? What scanner is used?
[ ] C6.1.2 — Are model weights, datasets, and adapters downloaded only from an approved source allowlist?
[ ] C6.1.3 — Can every third-party model artifact be integrity-verified (hash + signature)?
[ ] C6.1.4 — Do models pass a behavioral acceptance test suite before promotion to non-dev environments?

Look for:
- Model artifacts downloaded from arbitrary URLs without source validation.
- Missing hash or signature verification in the import pipeline.
- Models promoted to staging/production without test gate results.

For each FAIL: state gap, control ID, and remediation.
```


### C6-REVIEW-02: Review AI BOM Controls

**Objective**
- You are reviewing an AI system's supply chain transparency for AISVS C6.2 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C6.2.1 — Does every model artifact publish a version-controlled, machine-readable AI BOM?
- C6.2.1 — Does the BOM list datasets, weights, licenses, and data-origin statements?
- C6.2.2 — Is the AI BOM cryptographically signed before deployment?
- C6.2.3 — Does the build fail if any BOM component has missing metadata?

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an AI system's supply chain transparency for AISVS C6.2 compliance.

Check each item:
[ ] C6.2.1 — Does every model artifact publish a version-controlled, machine-readable AI BOM?
[ ] C6.2.1 — Does the BOM list datasets, weights, licenses, and data-origin statements?
[ ] C6.2.2 — Is the AI BOM cryptographically signed before deployment?
[ ] C6.2.3 — Does the build fail if any BOM component has missing metadata?

Look for:
- AI systems deployed without an AI BOM.
- BOMs that are human-readable documents (not machine-readable formats like CycloneDX).
- Unsigned BOMs.
- BOMs with missing license or data-origin fields.

For each FAIL: state gap, control ID, and remediation.
```


---
