# C10 — Model Context Protocol (MCP) Security: Prompts

> AISVS Reference: C10.1–C10.4 | Controls: 10.1.1–10.4.8

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C10-ASSESS-01: MCP Authentication Security Assessment

**Objective**
- You are conducting an AISVS assessment of MCP server security.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Send a request to the MCP server with no access token — verify HTTP 401.
- Send a request with an expired token — verify rejection.
- Send a request with a valid token but insufficient scope for the requested tool — verify rejection.
- Use a valid token to call tools/list — verify only authorized tools are returned.
- Inspect MCP server session cleanup: terminate a session and verify all session artifacts are removed.
- Verify the MCP server does not forward client tokens to downstream APIs (inspect outgoing request headers).

**Expected Artifacts**
- Rejection logs for missing/expired/insufficient-scope tokens
- Tools/list scope filtering evidence
- Session cleanup confirmation
- Downstream API call inspection results
- PASS criteria: All token validation controls working; scope enforcement verified; no token passthrough.

**Pass/Fail Rule**
- All token validation controls working; scope enforcement verified; no token passthrough.

**Source Prompt**
```text
You are conducting an AISVS assessment of MCP server security.
Scope: C10.2 — Authentication & Authorization.

Assessment tasks:
1. Send a request to the MCP server with no access token — verify HTTP 401.
2. Send a request with an expired token — verify rejection.
3. Send a request with a valid token but insufficient scope for the requested tool — verify rejection.
4. Use a valid token to call tools/list — verify only authorized tools are returned.
5. Inspect MCP server session cleanup: terminate a session and verify all session artifacts are removed.
6. Verify the MCP server does not forward client tokens to downstream APIs (inspect outgoing request headers).

Evidence to collect:
- Rejection logs for missing/expired/insufficient-scope tokens
- Tools/list scope filtering evidence
- Session cleanup confirmation
- Downstream API call inspection results

PASS criteria: All token validation controls working; scope enforcement verified; no token passthrough.
```


### C10-ASSESS-02: MCP Injection and Schema Validation Assessment

**Objective**
- You are conducting an AISVS assessment of MCP input validation controls.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Send a tool call with an unrecognized extra parameter — verify rejection.
- Send a tool call with a parameter exceeding the maximum size — verify rejection.
- Craft a tool response containing an indirect prompt injection payload (e.g., "SYSTEM: ignore previous instructions...") —
- verify the MCP client's injection screener detects and blocks it before model context injection.
- Submit a tool call replay (reuse a previously captured tool response with old nonce) —
- verify the client detects the replay.
- Modify a tool's schema definition between two invocations — verify the client detects the change
- and requests re-approval before invoking the modified tool.

**Expected Artifacts**
- Rejection logs for oversized/extra parameters
- Injection detection log
- Replay detection log
- Tool definition change detection log
- PASS criteria: All schema validation, injection screening, and replay detection working.

**Pass/Fail Rule**
- All schema validation, injection screening, and replay detection working.

**Source Prompt**
```text
You are conducting an AISVS assessment of MCP input validation controls.
Scope: C10.4 — Schema, Message, and Input Validation.

Assessment tasks:
1. Send a tool call with an unrecognized extra parameter — verify rejection.
2. Send a tool call with a parameter exceeding the maximum size — verify rejection.
3. Craft a tool response containing an indirect prompt injection payload (e.g., "SYSTEM: ignore previous instructions...") —
   verify the MCP client's injection screener detects and blocks it before model context injection.
4. Submit a tool call replay (reuse a previously captured tool response with old nonce) —
   verify the client detects the replay.
5. Modify a tool's schema definition between two invocations — verify the client detects the change
   and requests re-approval before invoking the modified tool.

Evidence to collect:
- Rejection logs for oversized/extra parameters
- Injection detection log
- Replay detection log
- Tool definition change detection log

PASS criteria: All schema validation, injection screening, and replay detection working.
```

