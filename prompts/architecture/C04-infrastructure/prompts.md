# C4 — Infrastructure, Configuration & Deployment Security: Architecture Prompts

> AISVS Reference: C4.1–C4.3 | Controls: 4.1.1–4.3.5

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C4-ARCH-01: Implement AI Model Sandboxed Execution

**Objective**
- You are designing the runtime environment for AI model inference.

**Required Controls**
- Apply AISVS C4.1.1 and C4.1.2.

**Execution Steps**
- Run each AI model in an isolated sandbox:
- Use container-level isolation (Kubernetes Pod with seccomp profile, no privileged mode).
- Restrict file system access to model artifact paths only (read-only mount).
- Restrict network egress to approved inference endpoints only.
- Restrict syscalls using a seccomp allowlist.
- Enforce an explicit allowlist of model serialization formats that are safe to load:
- ALLOWED: SafeTensors, ONNX (with signature validation), TorchScript (signed)
- BLOCKED: Pickle (.pkl), Python-serialized formats that execute code on load
- Implement a format validator that rejects any model artifact not in the allowlist before loading.
- Include a scan step (e.g., ModelScan) for known malicious serialization payloads.
- Output: Kubernetes manifest + format validator + pre-load scan integration.

**Expected Artifacts**
- Kubernetes manifest + format validator + pre-load scan integration.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are designing the runtime environment for AI model inference.
Apply AISVS C4.1.1 and C4.1.2.

Requirements:
- Run each AI model in an isolated sandbox:
  - Use container-level isolation (Kubernetes Pod with seccomp profile, no privileged mode).
  - Restrict file system access to model artifact paths only (read-only mount).
  - Restrict network egress to approved inference endpoints only.
  - Restrict syscalls using a seccomp allowlist.
- Enforce an explicit allowlist of model serialization formats that are safe to load:
  - ALLOWED: SafeTensors, ONNX (with signature validation), TorchScript (signed)
  - BLOCKED: Pickle (.pkl), Python-serialized formats that execute code on load
- Implement a format validator that rejects any model artifact not in the allowlist before loading.
- Include a scan step (e.g., ModelScan) for known malicious serialization payloads.

Output: Kubernetes manifest + format validator + pre-load scan integration.
```

