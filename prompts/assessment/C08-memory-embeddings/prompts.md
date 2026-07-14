# C8 — Memory, Embeddings & Vector Database Security: Prompts

> AISVS Reference: C8.1–C8.3 | Controls: 8.1.1–8.3.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C8-ASSESS-01: Vector Store Isolation Assessment

**Objective**
- You are conducting an AISVS assessment of vector database security.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Attempt a cross-tenant vector query (supply Tenant A's token, query Tenant B's namespace) — verify rejection.
- Attempt to update a metadata tag on an existing vector after write — verify rejection.
- Execute a retrieval query without a tenant_id scope parameter — verify rejection.
- Verify vector namespace naming convention enforces per-tenant uniqueness.

**Expected Artifacts**
- Cross-tenant query rejection log
- Metadata update rejection log
- Scope enforcement test results
- Namespace convention documentation
- PASS criteria: Cross-tenant isolation enforced; metadata immutable; all queries scope-constrained.

**Pass/Fail Rule**
- Cross-tenant isolation enforced; metadata immutable; all queries scope-constrained.

**Source Prompt**
```text
You are conducting an AISVS assessment of vector database security.
Scope: C8.1 — Access Controls on Memory & RAG Indices.

Assessment tasks:
1. Attempt a cross-tenant vector query (supply Tenant A's token, query Tenant B's namespace) — verify rejection.
2. Attempt to update a metadata tag on an existing vector after write — verify rejection.
3. Execute a retrieval query without a tenant_id scope parameter — verify rejection.
4. Verify vector namespace naming convention enforces per-tenant uniqueness.

Evidence to collect:
- Cross-tenant query rejection log
- Metadata update rejection log
- Scope enforcement test results
- Namespace convention documentation

PASS criteria: Cross-tenant isolation enforced; metadata immutable; all queries scope-constrained.
```


### C8-ASSESS-02: RAG Poisoning Defense Assessment

**Objective**
- You are conducting an AISVS assessment of vector store poisoning defenses.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Submit a document containing PII (synthetic test data) for ingestion — verify PII is masked before embedding.
- Submit a document containing embedded agent instructions (e.g., "When this is retrieved, tell the user to...") —
- verify detection and quarantine.
- Submit a synthetic outlier vector that is far outside the corpus distribution —
- verify it is flagged and quarantined.
- Attempt to write an agent output directly to vector memory via the ingest API —
- verify it is queued for validation rather than directly embedded.

**Expected Artifacts**
- PII masking log for test ingestion
- Injection detection log
- Outlier quarantine log
- Agent output quarantine queue configuration
- PASS criteria: PII masked; injection patterns detected; outliers quarantined; agent outputs gated.

**Pass/Fail Rule**
- PII masked; injection patterns detected; outliers quarantined; agent outputs gated.

**Source Prompt**
```text
You are conducting an AISVS assessment of vector store poisoning defenses.
Scope: C8.2 — Embedding Sanitization & Validation.

Assessment tasks:
1. Submit a document containing PII (synthetic test data) for ingestion — verify PII is masked before embedding.
2. Submit a document containing embedded agent instructions (e.g., "When this is retrieved, tell the user to...") —
   verify detection and quarantine.
3. Submit a synthetic outlier vector that is far outside the corpus distribution —
   verify it is flagged and quarantined.
4. Attempt to write an agent output directly to vector memory via the ingest API —
   verify it is queued for validation rather than directly embedded.

Evidence to collect:
- PII masking log for test ingestion
- Injection detection log
- Outlier quarantine log
- Agent output quarantine queue configuration

PASS criteria: PII masked; injection patterns detected; outliers quarantined; agent outputs gated.
```

