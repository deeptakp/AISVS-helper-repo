# C3 — Model Lifecycle Management & Change Control: Prompts

> AISVS Reference: C3.1–C3.5 | Controls: 3.1.1–3.5.4

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C3-CODE-02: Implement Pre-Deployment Model Testing Gate

**Objective**
- You are implementing a CI/CD gate for AI model deployment.

**Required Controls**
- Apply AISVS C3.2.1 and C3.2.2.

**Execution Steps**
- Implement a deployment gate that runs before any model reaches staging or production.
- The gate must execute:
- Input validation tests: test the model rejects/handles out-of-spec inputs.
- Safety evaluation tests: run the organization's alignment/safety test suite.
- Output sanitization tests: verify outputs pass the content safety classifier.
- For quantized models: re-run the full safety and alignment test suite on the compressed artifact.
- Gate fails (and blocks deployment) if any test suite does not achieve the required pass threshold.
- Generate a signed test report artifact recording: model hash, test suite version, pass/fail per test.
- Output: deployment gate pipeline stage + signed test report generator.

**Expected Artifacts**
- deployment gate pipeline stage + signed test report generator.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing a CI/CD gate for AI model deployment.
Apply AISVS C3.2.1 and C3.2.2.

Requirements:
- Implement a deployment gate that runs before any model reaches staging or production.
- The gate must execute:
  1. Input validation tests: test the model rejects/handles out-of-spec inputs.
  2. Safety evaluation tests: run the organization's alignment/safety test suite.
  3. Output sanitization tests: verify outputs pass the content safety classifier.
- For quantized models: re-run the full safety and alignment test suite on the compressed artifact.
- Gate fails (and blocks deployment) if any test suite does not achieve the required pass threshold.
- Generate a signed test report artifact recording: model hash, test suite version, pass/fail per test.

Output: deployment gate pipeline stage + signed test report generator.
```


### C3-CODE-03: Implement Canary Rollout with Auto-Rollback

**Objective**
- You are implementing a model deployment controller.

**Required Controls**
- Apply AISVS C3.3.1 and C3.3.2.

**Execution Steps**
- Implement a canary rollout controller:
- Deploy new model version to 5% of traffic initially.
- Monitor error rate, safety classifier rejection rate, and latency P99 during canary.
- Automatically promote to 100% if metrics remain within thresholds after a configurable soak period.
- Automatically rollback to the previous model version if any metric breaches its threshold.
- Rollback must restore the complete model state: weights, tokenizer, configuration, adapter weights.
- Log all rollout events (promotion steps, rollback triggers, soak times) with model version identifiers.
- Output: rollout controller with metric monitoring and auto-rollback.

**Expected Artifacts**
- rollout controller with metric monitoring and auto-rollback.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing a model deployment controller.
Apply AISVS C3.3.1 and C3.3.2.

Requirements:
- Implement a canary rollout controller:
  - Deploy new model version to 5% of traffic initially.
  - Monitor error rate, safety classifier rejection rate, and latency P99 during canary.
  - Automatically promote to 100% if metrics remain within thresholds after a configurable soak period.
  - Automatically rollback to the previous model version if any metric breaches its threshold.
- Rollback must restore the complete model state: weights, tokenizer, configuration, adapter weights.
- Log all rollout events (promotion steps, rollback triggers, soak times) with model version identifiers.

Output: rollout controller with metric monitoring and auto-rollback.
```


### C3-CODE-04: Implement Environment Isolation Enforcement

**Objective**
- You are implementing infrastructure-as-code for an AI training and deployment environment.

**Required Controls**
- Apply AISVS C3.4.1 and C3.4.2.

**Execution Steps**
- Define separate infrastructure environments: development, staging, production.
- Enforce that AI-specific runtime components (inference endpoints, vector stores, model caches)
- are NOT shared across environment boundaries.
- Enforce that training and fine-tuning workloads run in an isolated environment
- with no network path to production inference infrastructure.
- Implement an environment tag enforcement policy that rejects cross-environment resource sharing.
- Include network segmentation rules that prevent dev/staging model artifacts from being loaded
- into production runtimes.
- Output: IaC configuration (Terraform/Kubernetes) with environment isolation policies.

**Expected Artifacts**
- IaC configuration (Terraform/Kubernetes) with environment isolation policies.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing infrastructure-as-code for an AI training and deployment environment.
Apply AISVS C3.4.1 and C3.4.2.

Requirements:
- Define separate infrastructure environments: development, staging, production.
- Enforce that AI-specific runtime components (inference endpoints, vector stores, model caches)
  are NOT shared across environment boundaries.
- Enforce that training and fine-tuning workloads run in an isolated environment
  with no network path to production inference infrastructure.
- Implement an environment tag enforcement policy that rejects cross-environment resource sharing.
- Include network segmentation rules that prevent dev/staging model artifacts from being loaded
  into production runtimes.

Output: IaC configuration (Terraform/Kubernetes) with environment isolation policies.
```


---
