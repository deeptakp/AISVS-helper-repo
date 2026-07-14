# C5 — Access Control & Identity for AI Components & Users: Prompts

> AISVS Reference: C5.1–C5.3 | Controls: 5.1.1–5.3.2

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C5-REVIEW-01: Review AI Resource Access Control

**Objective**
- You are reviewing an AI system's access control implementation for AISVS C5.2 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C5.2.1 — Do all AI resources (datasets, endpoints, vector collections) enforce explicit allow-lists with default-deny?
- C5.2.2 — Does the RAG pipeline enforce per-user authorization at each retrieval and assembly stage?
- C5.2.3 — Is sensitive data retrieved via pipeline (not permanently stored in model weights)?
- C5.2.4 — Is there a post-inference output filter that prevents unauthorized data from appearing in responses?
- C5.2.5 — Is the policy decision point (PDP) isolated from the agent's execution environment?
- C5.2.6 (L3) — Is privileged access to model weights and training pipelines granted JIT with automatic expiry?
- C5.2.7 (L3) — Do data classification labels propagate to downstream resources (embeddings, caches, outputs)?

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an AI system's access control implementation for AISVS C5.2 compliance.

Check each item:
[ ] C5.2.1 — Do all AI resources (datasets, endpoints, vector collections) enforce explicit allow-lists with default-deny?
[ ] C5.2.2 — Does the RAG pipeline enforce per-user authorization at each retrieval and assembly stage?
[ ] C5.2.3 — Is sensitive data retrieved via pipeline (not permanently stored in model weights)?
[ ] C5.2.4 — Is there a post-inference output filter that prevents unauthorized data from appearing in responses?
[ ] C5.2.5 — Is the policy decision point (PDP) isolated from the agent's execution environment?
[ ] C5.2.6 (L3) — Is privileged access to model weights and training pipelines granted JIT with automatic expiry?
[ ] C5.2.7 (L3) — Do data classification labels propagate to downstream resources (embeddings, caches, outputs)?

Look for:
- Service account over-permissions used for retrieval instead of per-user scoping.
- AI endpoints with no explicit authorization check (relying solely on network controls).
- Sensitive data hard-coded in system prompts or model configurations.

For each FAIL: state gap, control ID, and remediation.
```


### C5-REVIEW-02: Review Multi-Tenant Isolation

**Objective**
- You are reviewing a shared AI serving infrastructure for AISVS C5.3 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C5.3.1 — Is there demonstrable isolation between tenant inference, fine-tuning, and embedding operations?
- C5.3.1 — Are KV caches and shared model state namespaced and flushed between tenant sessions?
- C5.3.2 (L3) — Is there hardware-level partitioning or dedicated compute per tenant for high-sensitivity workloads?

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing a shared AI serving infrastructure for AISVS C5.3 compliance.

Check each item:
[ ] C5.3.1 — Is there demonstrable isolation between tenant inference, fine-tuning, and embedding operations?
[ ] C5.3.1 — Are KV caches and shared model state namespaced and flushed between tenant sessions?
[ ] C5.3.2 (L3) — Is there hardware-level partitioning or dedicated compute per tenant for high-sensitivity workloads?

Look for:
- Shared inference caches without tenant namespacing.
- Vector collections without tenant_id scoping enforcement.
- Fine-tuning adapters loaded into shared model state.

For each FAIL: state gap, control ID, and remediation.
```


---
