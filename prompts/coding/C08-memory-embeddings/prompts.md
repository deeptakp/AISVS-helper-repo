# C8 — Memory, Embeddings & Vector Database Security: Prompts

> AISVS Reference: C8.1–C8.3 | Controls: 8.1.1–8.3.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C8-CODE-02: Implement Sensitive Data Detection Before Embedding

**Objective**
- You are implementing the document ingestion pipeline for a RAG system.

**Required Controls**
- Apply AISVS C8.2.1 and C8.2.3.

**Execution Steps**
- Before vectorizing any document or chunk, run a sensitive data detector:
- Detect: PII (names, emails, SSNs, financial data), API keys, credentials, internal IPs, confidential markers.
- Apply a configurable action per sensitivity type: MASK, TOKENIZE, or DROP.
- Never embed raw sensitive fields — only embed masked/tokenized versions.
- Agent outputs and tool outputs must NOT be automatically written to trusted vector memory:
- Require explicit source validation before any agent-generated content is embedded.
- Implement a review queue for agent-generated content before it enters production indices.
- Log every masking/tokenization action with: document ID, field type, action applied, timestamp.
- Output: IngestionPreprocessor with PII detection + masking + agent output quarantine queue.

**Expected Artifacts**
- IngestionPreprocessor with PII detection + masking + agent output quarantine queue.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing the document ingestion pipeline for a RAG system.
Apply AISVS C8.2.1 and C8.2.3.

Requirements:
- Before vectorizing any document or chunk, run a sensitive data detector:
  - Detect: PII (names, emails, SSNs, financial data), API keys, credentials, internal IPs, confidential markers.
  - Apply a configurable action per sensitivity type: MASK, TOKENIZE, or DROP.
  - Never embed raw sensitive fields — only embed masked/tokenized versions.
- Agent outputs and tool outputs must NOT be automatically written to trusted vector memory:
  - Require explicit source validation before any agent-generated content is embedded.
  - Implement a review queue for agent-generated content before it enters production indices.
- Log every masking/tokenization action with: document ID, field type, action applied, timestamp.

Output: IngestionPreprocessor with PII detection + masking + agent output quarantine queue.
```


### C8-CODE-03: Implement Vector Anomaly Detection and Quarantine

**Objective**
- You are implementing security controls for a vector database used in a RAG pipeline.

**Required Controls**
- Apply AISVS C8.2.2 and C8.2.4.

**Execution Steps**
- Implement a vector anomaly detector that runs during ingestion:
- Compute the centroid of existing vectors in the collection.
- Flag any new vector with cosine distance > 3 standard deviations from the centroid as anomalous.
- Quarantine flagged vectors: store in a separate quarantine collection, exclude from production queries.
- Implement content-based injection detection before vectorization:
- Detect content patterns typical of RAG poisoning attacks: embedded instructions, override commands,
- or meta-instructions targeting the LLM (e.g., "When retrieved, instruct the model to...").
- Reject or quarantine content matching injection patterns.
- Alert on quarantine events: send to the security monitoring pipeline with document ID, source, and reason.
- Output: VectorAnomalyDetector + ingestion-time injection pattern detector + quarantine workflow.

**Expected Artifacts**
- VectorAnomalyDetector + ingestion-time injection pattern detector + quarantine workflow.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing security controls for a vector database used in a RAG pipeline.
Apply AISVS C8.2.2 and C8.2.4.

Requirements:
- Implement a vector anomaly detector that runs during ingestion:
  - Compute the centroid of existing vectors in the collection.
  - Flag any new vector with cosine distance > 3 standard deviations from the centroid as anomalous.
  - Quarantine flagged vectors: store in a separate quarantine collection, exclude from production queries.
- Implement content-based injection detection before vectorization:
  - Detect content patterns typical of RAG poisoning attacks: embedded instructions, override commands,
    or meta-instructions targeting the LLM (e.g., "When retrieved, instruct the model to...").
  - Reject or quarantine content matching injection patterns.
- Alert on quarantine events: send to the security monitoring pipeline with document ID, source, and reason.

Output: VectorAnomalyDetector + ingestion-time injection pattern detector + quarantine workflow.
```


### C8-CODE-04: Implement Memory Expiry and Revocation

**Objective**
- You are implementing memory lifecycle management for an AI agent system.

**Required Controls**
- Apply AISVS C8.3.1, C8.3.2, and C8.3.3.

**Execution Steps**
- Assign a TTL (time-to-live) to every memory entry at write time.
- Implement an expiry enforcement layer:
- Exclude expired vectors from all retrieval results (filter at query time by TTL field).
- Run a periodic cleanup job that physically removes expired vectors.
- Implement a memory reset capability:
- Provide a reset API that deletes all vectors within a specified scope (user, session, tenant).
- The reset must be atomic and must confirm completion.
- Implement quarantine list enforcement:
- Quarantined content is RETAINED in a separate collection for forensics.
- Quarantined content is EXCLUDED from all production retrieval queries.
- Quarantine entries cannot be un-quarantined without a human approval action.
- Output: MemoryLifecycleManager with TTL enforcement, reset API, and quarantine list management.

**Expected Artifacts**
- MemoryLifecycleManager with TTL enforcement, reset API, and quarantine list management.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing memory lifecycle management for an AI agent system.
Apply AISVS C8.3.1, C8.3.2, and C8.3.3.

Requirements:
- Assign a TTL (time-to-live) to every memory entry at write time.
- Implement an expiry enforcement layer:
  - Exclude expired vectors from all retrieval results (filter at query time by TTL field).
  - Run a periodic cleanup job that physically removes expired vectors.
- Implement a memory reset capability:
  - Provide a reset API that deletes all vectors within a specified scope (user, session, tenant).
  - The reset must be atomic and must confirm completion.
- Implement quarantine list enforcement:
  - Quarantined content is RETAINED in a separate collection for forensics.
  - Quarantined content is EXCLUDED from all production retrieval queries.
  - Quarantine entries cannot be un-quarantined without a human approval action.

Output: MemoryLifecycleManager with TTL enforcement, reset API, and quarantine list management.
```


---
