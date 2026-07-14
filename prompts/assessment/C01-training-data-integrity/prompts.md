# C1 — Training Data Integrity & Traceability: Prompts

> AISVS Reference: C1.1–C1.3 | Controls: 1.1.1–1.3.5

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C1-ASSESS-01: Training Data Traceability Assessment

**Objective**
- You are conducting an AISVS security assessment of an AI system's training data controls.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Request the training data inventory. Verify it exists, is current, and covers all training sources.
- Verify that integrity hashes exist for all training data files and are stored separately from the data.
- Request evidence of a failed-hash alert test — confirm the pipeline halts on integrity failure.
- For L3: ask for a demonstration of dataset watermarking and attribution retrieval.

**Expected Artifacts**
- Data inventory artifact (or screenshot/export)
- Integrity manifest file sample
- Pipeline run log showing integrity check
- Alert configuration for modification detection
- PASS criteria: All L1 controls met; L2+ controls met for systems in scope.
- Document findings in `templates/AISVS-assessment-report.md` under section C1.

**Pass/Fail Rule**
- All L1 controls met; L2+ controls met for systems in scope.

**Source Prompt**
```text
You are conducting an AISVS security assessment of an AI system's training data controls.
Scope: C1.1 — Training Data Origin & Data Security.

Assessment tasks:
1. Request the training data inventory. Verify it exists, is current, and covers all training sources.
2. Verify that integrity hashes exist for all training data files and are stored separately from the data.
3. Request evidence of a failed-hash alert test — confirm the pipeline halts on integrity failure.
4. For L3: ask for a demonstration of dataset watermarking and attribution retrieval.

Evidence to collect:
- Data inventory artifact (or screenshot/export)
- Integrity manifest file sample
- Pipeline run log showing integrity check
- Alert configuration for modification detection

PASS criteria: All L1 controls met; L2+ controls met for systems in scope.
Document findings in `templates/AISVS-assessment-report.md` under section C1.
```


### C1-ASSESS-02: Data Poisoning Defense Assessment

**Objective**
- You are conducting an AISVS assessment focused on poisoning defenses.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Request the pipeline configuration and identify where poisoning detection runs.
- Inject 5 synthetic outlier samples into a test dataset and run the detection step — verify they are flagged.
- Inject 3 samples containing disallowed content (benign test strings that match policy keywords) — verify removal.
- Review bias evaluation reports for the last 3 model releases.
- For L3: review clean-label poisoning test results if available.

**Expected Artifacts**
- Poisoning detection module configuration
- Test run output showing flagged samples
- Pre-training report from last production run
- Bias evaluation report
- PASS criteria: Poisoning detection flags synthetic outliers; disallowed content is removed; bias evaluation exists.

**Pass/Fail Rule**
- Poisoning detection flags synthetic outliers; disallowed content is removed; bias evaluation exists.

**Source Prompt**
```text
You are conducting an AISVS assessment focused on poisoning defenses.
Scope: C1.3 — Training Data Quality and Security Assurance.

Assessment tasks:
1. Request the pipeline configuration and identify where poisoning detection runs.
2. Inject 5 synthetic outlier samples into a test dataset and run the detection step — verify they are flagged.
3. Inject 3 samples containing disallowed content (benign test strings that match policy keywords) — verify removal.
4. Review bias evaluation reports for the last 3 model releases.
5. For L3: review clean-label poisoning test results if available.

Evidence to collect:
- Poisoning detection module configuration
- Test run output showing flagged samples
- Pre-training report from last production run
- Bias evaluation report

PASS criteria: Poisoning detection flags synthetic outliers; disallowed content is removed; bias evaluation exists.
```

