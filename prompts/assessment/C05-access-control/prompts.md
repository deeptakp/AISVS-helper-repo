# C5 — Access Control & Identity for AI Components & Users: Prompts

> AISVS Reference: C5.1–C5.3 | Controls: 5.1.1–5.3.2

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C5-ASSESS-01: RAG Authorization Assessment

**Objective**
- You are conducting an AISVS assessment of RAG pipeline access control.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Create two test users with different data access levels (User A: access to docs 1-10, User B: docs 1-5).
- As User B, query the RAG system with a question whose answer is only in docs 6-10 — verify no leak.
- Inspect the retrieval pipeline code: confirm authorization is checked at retrieval stage, not only at API gateway.
- Test post-inference filter: inject a response containing data User B is not authorized to see —
- verify the filter blocks it before returning to user.
- Verify that sensitive data is NOT present in any system prompt, model configuration, or embedding cache
- in plaintext.

**Expected Artifacts**
- Test results (User A vs User B query outcomes)
- Retrieval pipeline code showing per-user scoping
- Post-inference filter configuration
- PASS criteria: No cross-user data leakage detected; authorization enforced at retrieval stage.

**Pass/Fail Rule**
- No cross-user data leakage detected; authorization enforced at retrieval stage.

**Source Prompt**
```text
You are conducting an AISVS assessment of RAG pipeline access control.
Scope: C5.2 — AI Resource Authorization.

Assessment tasks:
1. Create two test users with different data access levels (User A: access to docs 1-10, User B: docs 1-5).
2. As User B, query the RAG system with a question whose answer is only in docs 6-10 — verify no leak.
3. Inspect the retrieval pipeline code: confirm authorization is checked at retrieval stage, not only at API gateway.
4. Test post-inference filter: inject a response containing data User B is not authorized to see —
   verify the filter blocks it before returning to user.
5. Verify that sensitive data is NOT present in any system prompt, model configuration, or embedding cache
   in plaintext.

Evidence to collect:
- Test results (User A vs User B query outcomes)
- Retrieval pipeline code showing per-user scoping
- Post-inference filter configuration

PASS criteria: No cross-user data leakage detected; authorization enforced at retrieval stage.
```


### C5-ASSESS-02: Multi-Tenant Isolation Assessment

**Objective**
- You are conducting an AISVS assessment of multi-tenant AI serving isolation.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Run inference for Tenant A with a distinctive system prompt. Immediately run inference for Tenant B.
- Verify Tenant B cannot retrieve Tenant A's context via cache probing.
- Inspect KV cache namespace configuration — verify tenant_id is part of the cache key.
- Verify vector collection queries always require and enforce a tenant_id scope parameter.
- (L3) Review hardware partitioning configuration for high-sensitivity tenants.

**Expected Artifacts**
- Cache probing test results
- Cache key schema documentation
- Vector collection scoping configuration
- PASS criteria: No cross-tenant context leakage; namespacing enforced for all shared resources.

**Pass/Fail Rule**
- No cross-tenant context leakage; namespacing enforced for all shared resources.

**Source Prompt**
```text
You are conducting an AISVS assessment of multi-tenant AI serving isolation.
Scope: C5.3 — Multi-Tenant Isolation.

Assessment tasks:
1. Run inference for Tenant A with a distinctive system prompt. Immediately run inference for Tenant B.
   Verify Tenant B cannot retrieve Tenant A's context via cache probing.
2. Inspect KV cache namespace configuration — verify tenant_id is part of the cache key.
3. Verify vector collection queries always require and enforce a tenant_id scope parameter.
4. (L3) Review hardware partitioning configuration for high-sensitivity tenants.

Evidence to collect:
- Cache probing test results
- Cache key schema documentation
- Vector collection scoping configuration

PASS criteria: No cross-tenant context leakage; namespacing enforced for all shared resources.
```

