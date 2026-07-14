# C10 — Model Context Protocol (MCP) Security: Architecture Prompts

> AISVS Reference: C10.1–C10.4 | Controls: 10.1.1–10.4.8

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C10-ARCH-01: Implement Secure MCP Server Authentication

**Objective**
- You are designing an MCP server that exposes tools to AI agents.

**Required Controls**
- Apply AISVS C10.2.1, C10.2.2, C10.2.3, and C10.2.7.

**Execution Steps**
- Validate access tokens on EVERY request — do not rely on transport-level security alone.
- Validate token claims per OAuth 2.1:
- Issuer (iss): must match configured trusted issuer
- Audience (aud): must include this server's identifier
- Expiration (exp): must not be expired
- Scope (scope): must include the required scope for the requested tool
- Reject any request with a missing, invalid, or expired token with HTTP 401.
- Do NOT store or cache access tokens or user credentials server-side.
- Do NOT pass through access tokens received from MCP clients to downstream APIs —
- use the MCP server's own service credentials for downstream calls.
- Clean up all session artifacts (tokens, cached state, tool invocation records)
- when the MCP session terminates.
- Output: MCP server authentication middleware with OAuth 2.1 token validation + session cleanup.

**Expected Artifacts**
- MCP server authentication middleware with OAuth 2.1 token validation + session cleanup.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are designing an MCP server that exposes tools to AI agents.
Apply AISVS C10.2.1, C10.2.2, C10.2.3, and C10.2.7.

Requirements:
- Validate access tokens on EVERY request — do not rely on transport-level security alone.
- Validate token claims per OAuth 2.1:
  - Issuer (iss): must match configured trusted issuer
  - Audience (aud): must include this server's identifier
  - Expiration (exp): must not be expired
  - Scope (scope): must include the required scope for the requested tool
- Reject any request with a missing, invalid, or expired token with HTTP 401.
- Do NOT store or cache access tokens or user credentials server-side.
- Do NOT pass through access tokens received from MCP clients to downstream APIs —
  use the MCP server's own service credentials for downstream calls.
- Clean up all session artifacts (tokens, cached state, tool invocation records)
  when the MCP session terminates.

Output: MCP server authentication middleware with OAuth 2.1 token validation + session cleanup.
```

