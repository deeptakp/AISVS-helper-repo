# C12 — Monitoring, Logging & Anomaly Detection: Prompts

> AISVS Reference: C12.1–C12.5 | Controls: 12.1.1–12.5.4

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C12-CODE-02: Implement AI-Specific Threat Detection Rules

**Objective**
- You are implementing detection rules for an AI security monitoring system.

**Required Controls**
- Apply AISVS C12.2.1, C12.2.2, C12.2.3, and C12.2.5.

**Execution Steps**
- Follow the source prompt body exactly and map each action to AISVS control IDs.

**Expected Artifacts**
- AI threat detection rule engine with configurable rules and structured alerting.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing detection rules for an AI security monitoring system.
Apply AISVS C12.2.1, C12.2.2, C12.2.3, and C12.2.5.

Requirements:
Implement detection rules for the following AI-specific threat patterns:
1. Prompt injection attempts: detect known injection patterns in inputs (C12.2.1).
2. Jailbreak patterns: detect known jailbreak signatures and multi-turn jailbreak sequences (C12.2.1).
3. System prompt extraction: detect outputs that contain system prompt content patterns (C12.2.3).
4. Behavioral anomalies: detect (C12.2.2):
   - Excessive retry attempts (>5 retries within 60s from same session)
   - Unusually long inputs (>3 standard deviations above mean for the endpoint)
   - High-frequency low-variance queries (extraction probing pattern)
5. Token usage anomalies: detect per-user, per-session, per-endpoint usage spikes (C12.2.5).
   - Alert when usage exceeds 2x the user's 7-day rolling average.

Each detection rule must:
- Produce a structured alert with: rule_id, severity, session_id, user_id_hash, evidence_summary, timestamp.
- Be individually configurable (enable/disable, threshold tuning).

Output: AI threat detection rule engine with configurable rules and structured alerting.
```


### C12-CODE-03: Implement Data Drift and Hallucination Monitoring

**Objective**
- You are implementing model performance and safety monitoring.

**Required Controls**
- Apply AISVS C12.3.1, C12.3.2, and C12.3.3.

**Execution Steps**
- Implement data drift detection on the input distribution:
- For text inputs: monitor embedding-distance metrics comparing current input distribution
- to the reference distribution from the last model training/evaluation period.
- Alert when drift exceeds a configurable threshold (PSI or embedding distance).
- Implement hallucination monitoring (C12.3.2 and C12.3.3):
- For RAG responses: track citation verification failure rate (claims not traceable to retrieved chunks).
- Track hallucination rate as a continuous time-series metric.
- Alert when the hallucination rate exceeds the defined threshold.
- Store metrics in a time-series database to enable trend analysis and regression detection.
- Implement model behavioral shift detection (C12.3.4):
- Run a reference probe set on the model daily and track response distribution.
- Alert when response distribution shifts significantly from the established baseline.
- Distinguish behavioral shifts from expected operational drift (use statistical significance testing).
- Output: ModelMonitor with input drift detection + hallucination rate tracking + behavioral shift detection.

**Expected Artifacts**
- ModelMonitor with input drift detection + hallucination rate tracking + behavioral shift detection.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing model performance and safety monitoring.
Apply AISVS C12.3.1, C12.3.2, and C12.3.3.

Requirements:
- Implement data drift detection on the input distribution:
  - For text inputs: monitor embedding-distance metrics comparing current input distribution
    to the reference distribution from the last model training/evaluation period.
  - Alert when drift exceeds a configurable threshold (PSI or embedding distance).
- Implement hallucination monitoring (C12.3.2 and C12.3.3):
  - For RAG responses: track citation verification failure rate (claims not traceable to retrieved chunks).
  - Track hallucination rate as a continuous time-series metric.
  - Alert when the hallucination rate exceeds the defined threshold.
  - Store metrics in a time-series database to enable trend analysis and regression detection.
- Implement model behavioral shift detection (C12.3.4):
  - Run a reference probe set on the model daily and track response distribution.
  - Alert when response distribution shifts significantly from the established baseline.
  - Distinguish behavioral shifts from expected operational drift (use statistical significance testing).

Output: ModelMonitor with input drift detection + hallucination rate tracking + behavioral shift detection.
```


### C12-CODE-04: Implement Training Data and Model Lifecycle Audit Logging

**Objective**
- You are implementing audit logging for an AI model training and deployment pipeline.

**Required Controls**
- Apply AISVS C12.5.1, C12.5.2, C12.5.3, and C12.5.4.

**Execution Steps**
- Dataset lineage logging (C12.5.1):
- Record every dataset used: name, version, source, transformations applied, merge operations, timestamps.
- Store lineage as a directed acyclic graph (DAG) linking raw data → processed data → training artifact.
- Labeling activity logging (C12.5.2):
- Log every labeling action: annotator identity, timestamp, document ID, label applied, change from previous.
- Model change audit records (C12.5.3):
- Every model change (new version, fine-tune, adapter update, config change) generates an immutable audit record.
- Audit record includes: change type, model hash before/after, operator identity, approver identity, timestamp.
- Records are append-only and cryptographically chained (each record includes the hash of the previous record).
- Document ingestion tagging (C12.5.4):
- Every document ingested into a knowledge base or training corpus is tagged at write time with:
- source, writer identity, and timestamp. These tags are immutable after write.
- Output: AIPipelineAuditLogger with dataset lineage DAG + labeling log + model change audit + document tagging.

**Expected Artifacts**
- AIPipelineAuditLogger with dataset lineage DAG + labeling log + model change audit + document tagging.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing audit logging for an AI model training and deployment pipeline.
Apply AISVS C12.5.1, C12.5.2, C12.5.3, and C12.5.4.

Requirements:
- Dataset lineage logging (C12.5.1):
  - Record every dataset used: name, version, source, transformations applied, merge operations, timestamps.
  - Store lineage as a directed acyclic graph (DAG) linking raw data → processed data → training artifact.
- Labeling activity logging (C12.5.2):
  - Log every labeling action: annotator identity, timestamp, document ID, label applied, change from previous.
- Model change audit records (C12.5.3):
  - Every model change (new version, fine-tune, adapter update, config change) generates an immutable audit record.
  - Audit record includes: change type, model hash before/after, operator identity, approver identity, timestamp.
  - Records are append-only and cryptographically chained (each record includes the hash of the previous record).
- Document ingestion tagging (C12.5.4):
  - Every document ingested into a knowledge base or training corpus is tagged at write time with:
    source, writer identity, and timestamp. These tags are immutable after write.

Output: AIPipelineAuditLogger with dataset lineage DAG + labeling log + model change audit + document tagging.
```


---
