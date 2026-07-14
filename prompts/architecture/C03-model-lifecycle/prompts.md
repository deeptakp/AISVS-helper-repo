# C3 — Model Lifecycle Management & Change Control: Architecture Prompts

> AISVS Reference: C3.1–C3.5 | Controls: 3.1.1–3.5.4

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C3-ARCH-01: Implement Model Registry

**Objective**
- You are designing a model registry for an AI system deployment pipeline.

**Required Controls**
- Apply AISVS C3.1.1 and C3.1.2.

**Execution Steps**
- Create a model registry that maintains an inventory of all deployed model artifacts.
- Each registry entry must record:
- Model name and version
- Artifact types (weights, tokenizer, configuration, adapters, safety/policy models)
- Origin (training job ID, source repository, or third-party provider)
- Cryptographic hash (SHA-256) of each artifact
- Cryptographic signature (verify against a trusted signing key) — C3.1.2
- Deployment history (deployed-to environments, timestamps, deployer identity)
- Current status (active, retired, rolled back)
- Expose a query API and a CLI for listing and verifying artifacts.
- Fail deployment if an artifact's hash or signature does not match the registry.
- Output: model registry schema + registration API + signature verification module.

**Expected Artifacts**
- model registry schema + registration API + signature verification module.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are designing a model registry for an AI system deployment pipeline.
Apply AISVS C3.1.1 and C3.1.2.

Requirements:
- Create a model registry that maintains an inventory of all deployed model artifacts.
- Each registry entry must record:
  - Model name and version
  - Artifact types (weights, tokenizer, configuration, adapters, safety/policy models)
  - Origin (training job ID, source repository, or third-party provider)
  - Cryptographic hash (SHA-256) of each artifact
  - Cryptographic signature (verify against a trusted signing key) — C3.1.2
  - Deployment history (deployed-to environments, timestamps, deployer identity)
  - Current status (active, retired, rolled back)
- Expose a query API and a CLI for listing and verifying artifacts.
- Fail deployment if an artifact's hash or signature does not match the registry.

Output: model registry schema + registration API + signature verification module.
```

