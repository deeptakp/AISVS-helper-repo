# C8 — Memory, Embeddings & Vector Database Security: Prompts

> AISVS Reference: C8.1–C8.3 | Controls: 8.1.1–8.3.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C8-REVIEW-01: Review Vector Store Access Controls

**Objective**
- You are reviewing a RAG vector store implementation for AISVS C8.1 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C8.1.1 — Are vector identifiers and namespaces scoped per tenant? Are cross-tenant collisions prevented?
- C8.1.2 — Are document metadata tags immutable after initial write? Is there a tamper check?
- C8.1.3 — Do all retrieval operations enforce scope constraints (tenant_id filter required)?

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing a RAG vector store implementation for AISVS C8.1 compliance.

Check each item:
[ ] C8.1.1 — Are vector identifiers and namespaces scoped per tenant? Are cross-tenant collisions prevented?
[ ] C8.1.2 — Are document metadata tags immutable after initial write? Is there a tamper check?
[ ] C8.1.3 — Do all retrieval operations enforce scope constraints (tenant_id filter required)?

Look for:
- Vector queries that do not include a tenant_id or user_id filter.
- Metadata fields that can be updated after creation.
- Shared vector namespaces used across tenants.

For each FAIL: state gap, control ID, and remediation.
```


### C8-REVIEW-02: Review Embedding Sanitization and Memory Security

**Objective**
- You are reviewing a document ingestion and vector memory pipeline for AISVS C8.2 and C8.3 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C8.2.1 — Are sensitive fields detected and masked/tokenized/dropped before embedding?
- C8.2.2 — Are outlier vectors flagged and quarantined before entering production indices?
- C8.2.3 — Are agent and tool outputs subject to validation before being written to vector memory?
- C8.2.4 (L3) — Is content crafted to manipulate retrieval results detected before vectorization?
- C8.2.5 (L3) — Is new memory content checked for contradictions with existing memory?
- C8.3.1 — Are expired vectors excluded from retrieval results?
- C8.3.2 — Is there a memory reset capability?
- C8.3.3 (L3) — Is quarantined content retained but excluded from all retrieval?
- For each FAIL: state gap, control ID, and remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing a document ingestion and vector memory pipeline for AISVS C8.2 and C8.3 compliance.

Check each item:
[ ] C8.2.1 — Are sensitive fields detected and masked/tokenized/dropped before embedding?
[ ] C8.2.2 — Are outlier vectors flagged and quarantined before entering production indices?
[ ] C8.2.3 — Are agent and tool outputs subject to validation before being written to vector memory?
[ ] C8.2.4 (L3) — Is content crafted to manipulate retrieval results detected before vectorization?
[ ] C8.2.5 (L3) — Is new memory content checked for contradictions with existing memory?
[ ] C8.3.1 — Are expired vectors excluded from retrieval results?
[ ] C8.3.2 — Is there a memory reset capability?
[ ] C8.3.3 (L3) — Is quarantined content retained but excluded from all retrieval?

For each FAIL: state gap, control ID, and remediation.
```


---
