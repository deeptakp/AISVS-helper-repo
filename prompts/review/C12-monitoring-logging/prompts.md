# C12 — Monitoring, Logging & Anomaly Detection: Prompts

> AISVS Reference: C12.1–C12.5 | Controls: 12.1.1–12.5.4

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C12-REVIEW-01: Review AI Logging and Monitoring Controls

**Objective**
- You are reviewing an AI system's logging and monitoring implementation for AISVS C12.1 and C12.2 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C12.1.1 — Are AI interactions logged with session context and AI-specific telemetry?
- C12.1.2 — Are safety filtering and policy decisions logged with detail for forensic analysis?
- C12.1.3 — Do log entries follow a structured, interoperable schema with required fields?
- C12.1.4 — Are RAG pipeline retrieval events logged (query, documents retrieved, knowledge source)?
- C12.2.1 — Does the system detect and alert on known jailbreak patterns and prompt injection?
- C12.2.2 — Is behavioral anomaly detection implemented (unusual patterns, excessive retries, probing)?
- C12.2.3 — Are custom rules in place for AI-specific threat patterns?
- C12.2.5 — Is token usage tracked at granular levels (per user, session, feature, team)?
- C12.2.6 (L3) — Is LLM API traffic monitored for covert-channel and C2 indicators?

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an AI system's logging and monitoring implementation for AISVS C12.1 and C12.2 compliance.

Check each item:
[ ] C12.1.1 — Are AI interactions logged with session context and AI-specific telemetry?
[ ] C12.1.2 — Are safety filtering and policy decisions logged with detail for forensic analysis?
[ ] C12.1.3 — Do log entries follow a structured, interoperable schema with required fields?
[ ] C12.1.4 — Are RAG pipeline retrieval events logged (query, documents retrieved, knowledge source)?
[ ] C12.2.1 — Does the system detect and alert on known jailbreak patterns and prompt injection?
[ ] C12.2.2 — Is behavioral anomaly detection implemented (unusual patterns, excessive retries, probing)?
[ ] C12.2.3 — Are custom rules in place for AI-specific threat patterns?
[ ] C12.2.5 — Is token usage tracked at granular levels (per user, session, feature, team)?
[ ] C12.2.6 (L3) — Is LLM API traffic monitored for covert-channel and C2 indicators?

Look for:
- Logging that captures raw prompts in plaintext without redaction.
- Missing model identifier or token usage in log entries.
- No alerting on jailbreak or injection patterns.
- Logs stored in mutable storage.

For each FAIL: state gap, control ID, and remediation.
```


### C12-REVIEW-02: Review Drift Detection and Lifecycle Audit

**Objective**
- You are reviewing an AI system's drift monitoring and audit trail for AISVS C12.3 and C12.5 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C12.3.1 — Is data drift detection implemented using statistically validated methods for the input type?
- C12.3.2 — Is hallucination detection monitoring implemented?
- C12.3.3 — Are hallucination rates tracked as continuous time-series metrics?
- C12.5.1 — Does dataset lineage record all transformations, augmentations, and merges?
- C12.5.2 — Are all labeling activities recorded in logs?
- C12.5.3 — Do all model changes generate immutable audit records?
- C12.5.4 — Is every ingested document tagged with source, writer identity, and timestamp at write time?
- C12.4.2 — Are audit logs capturing agent proactive actions (approver, timestamp, parameters, outcome)?
- C12.4.3 — Are kill-switch activations and override commands logged?
- For each FAIL: state gap, control ID, and remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an AI system's drift monitoring and audit trail for AISVS C12.3 and C12.5 compliance.

Check each item:
[ ] C12.3.1 — Is data drift detection implemented using statistically validated methods for the input type?
[ ] C12.3.2 — Is hallucination detection monitoring implemented?
[ ] C12.3.3 — Are hallucination rates tracked as continuous time-series metrics?
[ ] C12.5.1 — Does dataset lineage record all transformations, augmentations, and merges?
[ ] C12.5.2 — Are all labeling activities recorded in logs?
[ ] C12.5.3 — Do all model changes generate immutable audit records?
[ ] C12.5.4 — Is every ingested document tagged with source, writer identity, and timestamp at write time?
[ ] C12.4.2 — Are audit logs capturing agent proactive actions (approver, timestamp, parameters, outcome)?
[ ] C12.4.3 — Are kill-switch activations and override commands logged?

For each FAIL: state gap, control ID, and remediation.
```


---
