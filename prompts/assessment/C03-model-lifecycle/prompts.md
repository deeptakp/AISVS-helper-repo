# C3 — Model Lifecycle Management & Change Control: Prompts

> AISVS Reference: C3.1–C3.5 | Controls: 3.1.1–3.5.4

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C3-ASSESS-01: Model Registry and Integrity Assessment

**Objective**
- You are conducting an AISVS assessment of model lifecycle controls.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Request the model registry export. Verify it covers all models currently in production.
- Select 3 production model artifacts. Verify their cryptographic signatures using the published signing key.
- Attempt to deploy a model artifact with a tampered hash — verify the pipeline rejects it.
- Attempt to deploy a model artifact without a signature — verify rejection.
- Review the registry for artifacts with missing origin information.

**Expected Artifacts**
- Model registry export (all production models)
- Signature verification output for 3 sampled artifacts
- Pipeline rejection logs for tampered artifacts
- PASS criteria: All artifacts signed, all deployments verified, no unsigned artifacts in production.

**Pass/Fail Rule**
- All artifacts signed, all deployments verified, no unsigned artifacts in production.

**Source Prompt**
```text
You are conducting an AISVS assessment of model lifecycle controls.
Scope: C3.1 — Model Authorization & Integrity.

Assessment tasks:
1. Request the model registry export. Verify it covers all models currently in production.
2. Select 3 production model artifacts. Verify their cryptographic signatures using the published signing key.
3. Attempt to deploy a model artifact with a tampered hash — verify the pipeline rejects it.
4. Attempt to deploy a model artifact without a signature — verify rejection.
5. Review the registry for artifacts with missing origin information.

Evidence to collect:
- Model registry export (all production models)
- Signature verification output for 3 sampled artifacts
- Pipeline rejection logs for tampered artifacts

PASS criteria: All artifacts signed, all deployments verified, no unsigned artifacts in production.
```


### C3-ASSESS-02: Deployment Gate and Rollback Assessment

**Objective**
- You are conducting an AISVS assessment of model deployment controls.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Review the last 5 model deployment pipeline runs — confirm each ran the full test gate.
- Request signed test reports for the 2 most recent production deployments.
- Simulate a canary rollback: push a model with a deliberately degraded safety score and verify automatic rollback.
- Verify that rollback restores all state (weights, tokenizer, configuration, adapters) — not just primary weights.
- Review environment isolation: confirm no shared runtime components between dev and production.

**Expected Artifacts**
- Pipeline run logs (last 5 deployments)
- Signed test report artifacts
- Rollback test result
- Network segmentation configuration
- PASS criteria: All L1/L2 controls verified; rollback tested and functional.

**Pass/Fail Rule**
- All L1/L2 controls verified; rollback tested and functional.

**Source Prompt**
```text
You are conducting an AISVS assessment of model deployment controls.
Scope: C3.2–C3.3 — Model Validation, Testing, and Controlled Deployment.

Assessment tasks:
1. Review the last 5 model deployment pipeline runs — confirm each ran the full test gate.
2. Request signed test reports for the 2 most recent production deployments.
3. Simulate a canary rollback: push a model with a deliberately degraded safety score and verify automatic rollback.
4. Verify that rollback restores all state (weights, tokenizer, configuration, adapters) — not just primary weights.
5. Review environment isolation: confirm no shared runtime components between dev and production.

Evidence to collect:
- Pipeline run logs (last 5 deployments)
- Signed test report artifacts
- Rollback test result
- Network segmentation configuration

PASS criteria: All L1/L2 controls verified; rollback tested and functional.
```

