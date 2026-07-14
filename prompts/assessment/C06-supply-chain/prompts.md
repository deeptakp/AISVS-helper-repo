# C6 — Supply Chain Security for Models: Prompts

> AISVS Reference: C6.1–C6.2 | Controls: 6.1.1–6.2.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C6-ASSESS-01: Model Supply Chain Assessment

**Objective**
- You are conducting an AISVS assessment of model supply chain security.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Request the approved model source allowlist — verify it exists and is enforced in the import pipeline.
- Attempt to import a test model from a non-approved URL — verify rejection.
- Import a test model artifact with a tampered hash — verify the scanner rejects it.
- Review the last 3 model imports: confirm scan results exist and are linked to the deployed artifact.
- Review behavioral acceptance test results for the last production model promotion.

**Expected Artifacts**
- Approved source allowlist
- Rejection log for non-approved source test
- Scan results for 3 recent imports
- Behavioral test report for last production promotion
- PASS criteria: All imports source-validated; all artifacts scanned; behavioral gate enforced.

**Pass/Fail Rule**
- All imports source-validated; all artifacts scanned; behavioral gate enforced.

**Source Prompt**
```text
You are conducting an AISVS assessment of model supply chain security.
Scope: C6.1 — Model Artifact Integrity.

Assessment tasks:
1. Request the approved model source allowlist — verify it exists and is enforced in the import pipeline.
2. Attempt to import a test model from a non-approved URL — verify rejection.
3. Import a test model artifact with a tampered hash — verify the scanner rejects it.
4. Review the last 3 model imports: confirm scan results exist and are linked to the deployed artifact.
5. Review behavioral acceptance test results for the last production model promotion.

Evidence to collect:
- Approved source allowlist
- Rejection log for non-approved source test
- Scan results for 3 recent imports
- Behavioral test report for last production promotion

PASS criteria: All imports source-validated; all artifacts scanned; behavioral gate enforced.
```


### C6-ASSESS-02: AI BOM Completeness and Signing Assessment

**Objective**
- You are conducting an AISVS assessment of AI BOM controls.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Obtain the AI BOM for the 2 most recent production model deployments.
- Verify BOM format is machine-readable (CycloneDX, SPDX, or equivalent).
- Verify the BOM signature against the organization's published signing key.
- Check BOM completeness: datasets, weights, licenses, data-origin statements, dependencies.
- Trigger a test build with a model component missing its license field — verify build failure.

**Expected Artifacts**
- AI BOM artifacts (2 most recent deployments)
- Signature verification output
- Completeness check failure log from test build
- PASS criteria: BOMs exist for all production models; signed; complete; missing-field check enforced.

**Pass/Fail Rule**
- BOMs exist for all production models; signed; complete; missing-field check enforced.

**Source Prompt**
```text
You are conducting an AISVS assessment of AI BOM controls.
Scope: C6.2 — AI BOM & Supply Chain Monitoring.

Assessment tasks:
1. Obtain the AI BOM for the 2 most recent production model deployments.
2. Verify BOM format is machine-readable (CycloneDX, SPDX, or equivalent).
3. Verify the BOM signature against the organization's published signing key.
4. Check BOM completeness: datasets, weights, licenses, data-origin statements, dependencies.
5. Trigger a test build with a model component missing its license field — verify build failure.

Evidence to collect:
- AI BOM artifacts (2 most recent deployments)
- Signature verification output
- Completeness check failure log from test build

PASS criteria: BOMs exist for all production models; signed; complete; missing-field check enforced.
```

