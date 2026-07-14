# C4 — Infrastructure, Configuration & Deployment Security: Prompts

> AISVS Reference: C4.1–C4.3 | Controls: 4.1.1–4.3.5

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C4-REVIEW-01: Review AI Workload Sandboxing

**Objective**
- You are reviewing the infrastructure configuration for AI model inference workloads.

**Required Controls**
- Apply AISVS C4.1.

**Execution Steps**
- C4.1.1 — Do AI models execute in isolated sandboxes (containers with restrictive security contexts)?
- C4.1.2 — Is there an explicit allowlist of safe serialization formats? Are pickle/unsafe formats blocked?
- C4.1.3 (L3) — Is workload attestation performed before model loading?
- C4.1.4 (L3) — Are confidential inference services using TEEs to protect model weights at runtime?

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing the infrastructure configuration for AI model inference workloads.
Apply AISVS C4.1.

Check each item:
[ ] C4.1.1 — Do AI models execute in isolated sandboxes (containers with restrictive security contexts)?
[ ] C4.1.2 — Is there an explicit allowlist of safe serialization formats? Are pickle/unsafe formats blocked?
[ ] C4.1.3 (L3) — Is workload attestation performed before model loading?
[ ] C4.1.4 (L3) — Are confidential inference services using TEEs to protect model weights at runtime?

Look for:
- Models loaded from untrusted sources without format validation.
- Containers running as root or with privileged flags.
- Pickle or Python object deserialization of model artifacts.

For each FAIL: state gap, control ID, and remediation.
```


### C4-REVIEW-02: Review Edge and Distributed AI Deployment Security

**Objective**
- You are reviewing edge AI deployment configuration for AISVS C4.3 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C4.3.1 — Do edge AI devices use strong authentication (mTLS or equivalent) to central infrastructure?
- C4.3.2 — Are models deployed to edge/mobile devices cryptographically signed and signature-verified before loading?
- C4.3.3 (L3) — Do inference runtimes enforce process, memory, and file access isolation?
- C4.3.4 (L3) — Are model weights on-device encrypted with hardware-backed key storage?
- C4.3.5 (L3) — Are models in mobile/IoT app packages encrypted at rest and decrypted only inside trusted runtime?
- For each FAIL: state gap, control ID, and remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing edge AI deployment configuration for AISVS C4.3 compliance.

Check each item:
[ ] C4.3.1 — Do edge AI devices use strong authentication (mTLS or equivalent) to central infrastructure?
[ ] C4.3.2 — Are models deployed to edge/mobile devices cryptographically signed and signature-verified before loading?
[ ] C4.3.3 (L3) — Do inference runtimes enforce process, memory, and file access isolation?
[ ] C4.3.4 (L3) — Are model weights on-device encrypted with hardware-backed key storage?
[ ] C4.3.5 (L3) — Are models in mobile/IoT app packages encrypted at rest and decrypted only inside trusted runtime?

For each FAIL: state gap, control ID, and remediation.
```


---
