# C5 — Access Control & Identity for AI Components & Users: Prompts

> AISVS Reference: C5.1–C5.3 | Controls: 5.1.1–5.3.2

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C5-CODE-02: Implement Per-User Authorization in RAG Pipeline

**Objective**
- You are implementing a Retrieval-Augmented Generation (RAG) pipeline.

**Required Controls**
- Apply AISVS C5.2.2, C5.2.3, and C5.2.4.

**Execution Steps**
- At every retrieval step in the RAG pipeline, enforce the end-user's authorization context:
- Filter retrieved documents/chunks to those the user is authorized to access.
- Do NOT rely solely on the service account's permissions for retrieval.
- Sensitive data must flow through the RAG retrieval pipeline — it must NOT be baked into model weights or prompts.
- Implement post-inference filtering: before returning a response, verify no content is present that
- the user is not authorized to receive.
- The policy decision point (PDP) must be external to the agent/model — never make authorization decisions
- inside the model context.
- Output: RAG pipeline with per-user retrieval authorization + post-inference output filter.

**Expected Artifacts**
- RAG pipeline with per-user retrieval authorization + post-inference output filter.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing a Retrieval-Augmented Generation (RAG) pipeline.
Apply AISVS C5.2.2, C5.2.3, and C5.2.4.

Requirements:
- At every retrieval step in the RAG pipeline, enforce the end-user's authorization context:
  - Filter retrieved documents/chunks to those the user is authorized to access.
  - Do NOT rely solely on the service account's permissions for retrieval.
- Sensitive data must flow through the RAG retrieval pipeline — it must NOT be baked into model weights or prompts.
- Implement post-inference filtering: before returning a response, verify no content is present that
  the user is not authorized to receive.
- The policy decision point (PDP) must be external to the agent/model — never make authorization decisions
  inside the model context.

Output: RAG pipeline with per-user retrieval authorization + post-inference output filter.
```


### C5-CODE-03: Implement Multi-Tenant Inference Isolation

**Objective**
- You are implementing a shared model serving infrastructure used by multiple tenants.

**Required Controls**
- Apply AISVS C5.3.1.

**Execution Steps**
- Implement tenant isolation in the inference service:
- Each tenant's requests must be processed in isolated contexts (separate queue, separate cache namespace).
- One tenant's fine-tuning, inference, or embedding operations must not be observable by another tenant.
- Shared KV caches must be namespaced and invalidated between tenant sessions.
- Implement cache poisoning detection: monitor for cross-tenant cache collisions.
- Implement strict namespace enforcement for vector collections: tenant_id must be included in all
- vector operation scoping — reject operations that do not supply a valid tenant_id.
- Log cross-tenant collision attempts as security events.
- Output: multi-tenant isolation layer with cache namespacing + collision detection.

**Expected Artifacts**
- multi-tenant isolation layer with cache namespacing + collision detection.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing a shared model serving infrastructure used by multiple tenants.
Apply AISVS C5.3.1.

Requirements:
- Implement tenant isolation in the inference service:
  - Each tenant's requests must be processed in isolated contexts (separate queue, separate cache namespace).
  - One tenant's fine-tuning, inference, or embedding operations must not be observable by another tenant.
  - Shared KV caches must be namespaced and invalidated between tenant sessions.
  - Implement cache poisoning detection: monitor for cross-tenant cache collisions.
- Implement strict namespace enforcement for vector collections: tenant_id must be included in all
  vector operation scoping — reject operations that do not supply a valid tenant_id.
- Log cross-tenant collision attempts as security events.

Output: multi-tenant isolation layer with cache namespacing + collision detection.
```


### C5-CODE-04: Implement Just-In-Time Privileged Access

**Objective**
- You are implementing access control for high-privilege AI operations (model deployment, weight export,

**Required Controls**
- Apply AISVS C5.1.1 (L3) and C5.2.6 (L3).

**Execution Steps**
- Implement a just-in-time (JIT) access request workflow for privileged AI operations:
- Operator requests access, specifying operation type, resource, and justification.
- A second approver must authorize the request.
- Access is granted as a time-limited credential (max session duration configurable, default 4h).
- Access automatically expires — no standing privilege.
- Step-up authentication required: MFA re-authentication at request time.
- All privileged access grants, operations performed, and expirations are audit-logged.
- Implement automatic credential revocation on session expiry or anomaly detection.
- Output: JIT access workflow with step-up auth + time-limited credential issuance + audit log.

**Expected Artifacts**
- JIT access workflow with step-up auth + time-limited credential issuance + audit log.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing access control for high-privilege AI operations (model deployment, weight export,
training data access, production configuration changes).
Apply AISVS C5.1.1 (L3) and C5.2.6 (L3).

Requirements:
- Implement a just-in-time (JIT) access request workflow for privileged AI operations:
  - Operator requests access, specifying operation type, resource, and justification.
  - A second approver must authorize the request.
  - Access is granted as a time-limited credential (max session duration configurable, default 4h).
  - Access automatically expires — no standing privilege.
- Step-up authentication required: MFA re-authentication at request time.
- All privileged access grants, operations performed, and expirations are audit-logged.
- Implement automatic credential revocation on session expiry or anomaly detection.

Output: JIT access workflow with step-up auth + time-limited credential issuance + audit log.
```


---
