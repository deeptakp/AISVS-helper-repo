# C6 — Supply Chain Security for Models: Prompts

> AISVS Reference: C6.1–C6.2 | Controls: 6.1.1–6.2.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C6-CODE-02: Generate and Sign AI BOM

**Objective**
- You are implementing supply chain transparency for an AI model deployment pipeline.

**Required Controls**
- Apply AISVS C6.2.1, C6.2.2, and C6.2.3.

**Execution Steps**
- Generate a machine-readable AI Bill of Materials (AI BOM) in CycloneDX ML BOM format for every model artifact.
- The BOM must include:
- Base model identifier and version
- Training datasets (name, version, license, origin)
- Fine-tuning adapters (name, version, training data reference)
- Safety/policy model components
- Dependencies (inference framework, quantization library, tokenizer)
- Cryptographically sign the BOM using the organization's code-signing key.
- Implement a CI/CD build gate that fails the build if any BOM component is missing required metadata fields.
- Store the signed BOM alongside the model artifact in the registry.
- Output: AI BOM generator + signing workflow + completeness check build gate.

**Expected Artifacts**
- AI BOM generator + signing workflow + completeness check build gate.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing supply chain transparency for an AI model deployment pipeline.
Apply AISVS C6.2.1, C6.2.2, and C6.2.3.

Requirements:
- Generate a machine-readable AI Bill of Materials (AI BOM) in CycloneDX ML BOM format for every model artifact.
  The BOM must include:
  - Base model identifier and version
  - Training datasets (name, version, license, origin)
  - Fine-tuning adapters (name, version, training data reference)
  - Safety/policy model components
  - Dependencies (inference framework, quantization library, tokenizer)
- Cryptographically sign the BOM using the organization's code-signing key.
- Implement a CI/CD build gate that fails the build if any BOM component is missing required metadata fields.
- Store the signed BOM alongside the model artifact in the registry.

Output: AI BOM generator + signing workflow + completeness check build gate.
```


### C6-CODE-03: Implement Behavioral Acceptance Test Suite

**Objective**
- You are implementing the behavioral validation gate for a model supply chain.

**Required Controls**
- Apply AISVS C6.1.4.

**Execution Steps**
- Implement a behavioral acceptance test suite that runs on every model before promotion to non-dev environments.
- The suite must include:
- Functional correctness tests (model produces expected outputs on reference inputs).
- Safety alignment tests (model refuses disallowed content categories).
- Output format compliance tests (model outputs match declared schema).
- Regression tests vs. the previous production model version.
- Test results must be recorded in a signed artifact tied to the model's hash.
- Promotion to staging or production is blocked if any test fails.
- On provider model changes (new version, new routing): trigger automatic re-evaluation (C3.2.3).
- Output: behavioral test suite + signed result artifact + promotion gate integration.

**Expected Artifacts**
- behavioral test suite + signed result artifact + promotion gate integration.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing the behavioral validation gate for a model supply chain.
Apply AISVS C6.1.4.

Requirements:
- Implement a behavioral acceptance test suite that runs on every model before promotion to non-dev environments.
- The suite must include:
  1. Functional correctness tests (model produces expected outputs on reference inputs).
  2. Safety alignment tests (model refuses disallowed content categories).
  3. Output format compliance tests (model outputs match declared schema).
  4. Regression tests vs. the previous production model version.
- Test results must be recorded in a signed artifact tied to the model's hash.
- Promotion to staging or production is blocked if any test fails.
- On provider model changes (new version, new routing): trigger automatic re-evaluation (C3.2.3).

Output: behavioral test suite + signed result artifact + promotion gate integration.
```


---
