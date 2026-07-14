# C6 — Supply Chain Security for Models: Architecture Prompts

> AISVS Reference: C6.1–C6.2 | Controls: 6.1.1–6.2.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C6-ARCH-01: Implement Model Artifact Scanner

**Objective**
- You are designing a model import pipeline that consumes third-party model artifacts.

**Required Controls**
- Apply AISVS C6.1.1 and C6.1.2.

**Execution Steps**
- Implement a pre-import scanner that runs before any model artifact is registered or loaded:
- Verify the artifact's source URL is in the organization's approved-source allowlist.
- Run a model security scanner (e.g., ModelScan) to detect malicious serialization payloads.
- Verify cryptographic hash against the published hash from the source registry.
- Verify the artifact's digital signature against the provider's public key.
- Reject any artifact that:
- Comes from a non-approved source
- Fails the malicious code scan
- Has a hash mismatch
- Has an invalid or missing signature
- Log all scan results with: artifact name, source, scan tool version, outcome, timestamp.
- Output: ModelImportScanner with allowlist enforcement, malware scan, hash + signature verification.

**Expected Artifacts**
- ModelImportScanner with allowlist enforcement, malware scan, hash + signature verification.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are designing a model import pipeline that consumes third-party model artifacts.
Apply AISVS C6.1.1 and C6.1.2.

Requirements:
- Implement a pre-import scanner that runs before any model artifact is registered or loaded:
  1. Verify the artifact's source URL is in the organization's approved-source allowlist.
  2. Run a model security scanner (e.g., ModelScan) to detect malicious serialization payloads.
  3. Verify cryptographic hash against the published hash from the source registry.
  4. Verify the artifact's digital signature against the provider's public key.
- Reject any artifact that:
  - Comes from a non-approved source
  - Fails the malicious code scan
  - Has a hash mismatch
  - Has an invalid or missing signature
- Log all scan results with: artifact name, source, scan tool version, outcome, timestamp.

Output: ModelImportScanner with allowlist enforcement, malware scan, hash + signature verification.
```

