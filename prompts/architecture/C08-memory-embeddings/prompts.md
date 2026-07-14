# C8 — Memory, Embeddings & Vector Database Security: Architecture Prompts

> AISVS Reference: C8.1–C8.3 | Controls: 8.1.1–8.3.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C8-ARCH-01: Implement Tenant-Scoped Vector Store Access

**Objective**
- You are designing a vector database integration for a multi-tenant RAG system.

**Required Controls**
- Apply AISVS C8.1.1, C8.1.2, and C8.1.3.

**Execution Steps**
- Enforce tenant isolation in all vector operations:
- Every vector namespace/collection must be scoped to a single tenant.
- Vector identifiers must be globally unique: use {tenant_id}::{document_id}::{chunk_id} scheme.
- Prevent cross-tenant namespace collisions by validating tenant_id on every read and write.
- Make document metadata tags immutable after the initial write:
- Reject any update request that attempts to modify metadata fields after creation.
- Store metadata with a creation timestamp and hash; verify on every retrieval.
- Enforce scope constraints on all retrieval operations:
- Every similarity search must include a tenant_id filter; reject queries without it.
- Return only vectors within the requesting user's authorized scope.
- Output: VectorStoreClient wrapper with tenant scoping, immutable metadata, and scope enforcement.

**Expected Artifacts**
- VectorStoreClient wrapper with tenant scoping, immutable metadata, and scope enforcement.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are designing a vector database integration for a multi-tenant RAG system.
Apply AISVS C8.1.1, C8.1.2, and C8.1.3.

Requirements:
- Enforce tenant isolation in all vector operations:
  - Every vector namespace/collection must be scoped to a single tenant.
  - Vector identifiers must be globally unique: use {tenant_id}::{document_id}::{chunk_id} scheme.
  - Prevent cross-tenant namespace collisions by validating tenant_id on every read and write.
- Make document metadata tags immutable after the initial write:
  - Reject any update request that attempts to modify metadata fields after creation.
  - Store metadata with a creation timestamp and hash; verify on every retrieval.
- Enforce scope constraints on all retrieval operations:
  - Every similarity search must include a tenant_id filter; reject queries without it.
  - Return only vectors within the requesting user's authorized scope.

Output: VectorStoreClient wrapper with tenant scoping, immutable metadata, and scope enforcement.
```

