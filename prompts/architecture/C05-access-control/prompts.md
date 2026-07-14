# C5 — Access Control & Identity for AI Components & Users: Architecture Prompts

> AISVS Reference: C5.1–C5.3 | Controls: 5.1.1–5.3.2

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C5-ARCH-01: Implement Default-Deny AI Resource Authorization

**Objective**
- You are designing access control for AI system resources (datasets, inference endpoints, vector collections).

**Required Controls**
- Apply AISVS C5.2.1.

**Execution Steps**
- Implement a resource authorization middleware that applies to all AI resource endpoints.
- Default deny: any request without an explicit ALLOW decision is rejected with HTTP 403.
- Maintain an explicit allow-list per resource (dataset, endpoint, vector collection) specifying:
- Allowed principals (users, service accounts, agent identities)
- Allowed operations (read, write, query, infer, manage)
- Apply this authorization check at every access point — not just at the API gateway.
- Log every authorization decision (allow and deny) with: principal, resource, operation, timestamp, decision.
- Output: authorization middleware with allow-list enforcement + audit logging.

**Expected Artifacts**
- authorization middleware with allow-list enforcement + audit logging.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are designing access control for AI system resources (datasets, inference endpoints, vector collections).
Apply AISVS C5.2.1.

Requirements:
- Implement a resource authorization middleware that applies to all AI resource endpoints.
- Default deny: any request without an explicit ALLOW decision is rejected with HTTP 403.
- Maintain an explicit allow-list per resource (dataset, endpoint, vector collection) specifying:
  - Allowed principals (users, service accounts, agent identities)
  - Allowed operations (read, write, query, infer, manage)
- Apply this authorization check at every access point — not just at the API gateway.
- Log every authorization decision (allow and deny) with: principal, resource, operation, timestamp, decision.

Output: authorization middleware with allow-list enforcement + audit logging.
```

