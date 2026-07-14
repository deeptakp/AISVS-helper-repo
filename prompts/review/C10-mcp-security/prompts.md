# C10 — Model Context Protocol (MCP) Security: Prompts

> AISVS Reference: C10.1–C10.4 | Controls: 10.1.1–10.4.8

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C10-REVIEW-01: Review MCP Authentication and Transport Security

**Objective**
- You are reviewing an MCP integration for AISVS C10.2 and C10.3 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C10.2.1 — Does the MCP server validate access tokens on every request (not just at connection)?
- C10.2.2 — Are all OAuth 2.1 token claims validated (iss, aud, exp, scope)?
- C10.2.3 — Does the MCP server avoid storing or caching access tokens or credentials?
- C10.2.4 — Does tools/list return only tools permitted by the caller's authorized scopes?
- C10.2.5 — Is access control enforced on every individual tool invocation?
- C10.2.6 — Are all session artifacts cleaned up when sessions terminate?
- C10.2.7 — Does the MCP server avoid passing client tokens to downstream APIs?
- C10.3.1 — Is authenticated HTTPS used for all remote MCP transport?
- C10.3.2 — Is stdio restricted to controlled local environments only?
- C10.3.3 — Are both Origin and Host headers independently validated to prevent DNS rebinding?
- C10.3.4 — Is a minimum MCP protocol version enforced?
- For each FAIL: state gap, control ID, and remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an MCP integration for AISVS C10.2 and C10.3 compliance.

Check each item:
[ ] C10.2.1 — Does the MCP server validate access tokens on every request (not just at connection)?
[ ] C10.2.2 — Are all OAuth 2.1 token claims validated (iss, aud, exp, scope)?
[ ] C10.2.3 — Does the MCP server avoid storing or caching access tokens or credentials?
[ ] C10.2.4 — Does tools/list return only tools permitted by the caller's authorized scopes?
[ ] C10.2.5 — Is access control enforced on every individual tool invocation?
[ ] C10.2.6 — Are all session artifacts cleaned up when sessions terminate?
[ ] C10.2.7 — Does the MCP server avoid passing client tokens to downstream APIs?
[ ] C10.3.1 — Is authenticated HTTPS used for all remote MCP transport?
[ ] C10.3.2 — Is stdio restricted to controlled local environments only?
[ ] C10.3.3 — Are both Origin and Host headers independently validated to prevent DNS rebinding?
[ ] C10.3.4 — Is a minimum MCP protocol version enforced?

For each FAIL: state gap, control ID, and remediation.
```


### C10-REVIEW-02: Review MCP Input Validation

**Objective**
- You are reviewing MCP server and client input validation for AISVS C10.4 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C10.4.1 — Are tools/list and tools/call responses validated against declared schemas before model context injection?
- C10.4.2 — Are tool responses screened for indirect prompt injection before model context injection?
- C10.4.3 — Does the MCP server reject unrecognized or oversized parameters?
- C10.4.4 — Is strict schema validation enforced on all MCP servers?
- C10.4.5 — Are maximum payload size limits enforced on all transports?
- C10.4.6 — Are tool responses signed with nonce+timestamp for replay detection?
- C10.4.7 — Is an explicit user consent dialogue shown when installing a local MCP server?
- C10.4.8 (L3) — Does the MCP client detect tool definition changes and require re-approval?
- For each FAIL: state gap, control ID, and remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing MCP server and client input validation for AISVS C10.4 compliance.

Check each item:
[ ] C10.4.1 — Are tools/list and tools/call responses validated against declared schemas before model context injection?
[ ] C10.4.2 — Are tool responses screened for indirect prompt injection before model context injection?
[ ] C10.4.3 — Does the MCP server reject unrecognized or oversized parameters?
[ ] C10.4.4 — Is strict schema validation enforced on all MCP servers?
[ ] C10.4.5 — Are maximum payload size limits enforced on all transports?
[ ] C10.4.6 — Are tool responses signed with nonce+timestamp for replay detection?
[ ] C10.4.7 — Is an explicit user consent dialogue shown when installing a local MCP server?
[ ] C10.4.8 (L3) — Does the MCP client detect tool definition changes and require re-approval?

For each FAIL: state gap, control ID, and remediation.
```


---
