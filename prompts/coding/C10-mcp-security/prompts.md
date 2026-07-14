# C10 — Model Context Protocol (MCP) Security: Prompts

> AISVS Reference: C10.1–C10.4 | Controls: 10.1.1–10.4.8

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C10-CODE-02: Implement MCP Transport Security

**Objective**
- You are configuring transport security for an MCP-based tool integration.

**Required Controls**
- Apply AISVS C10.3.1, C10.3.2, and C10.3.3.

**Execution Steps**
- For remote MCP servers: require authenticated, encrypted streamable HTTP (HTTPS with TLS 1.2+).
- For local MCP servers: permit stdio transport ONLY if running in a controlled local environment;
- enforce a configuration check that prevents stdio from being enabled in production.
- On all HTTP-based MCP transports, independently validate BOTH:
- Origin header: must match the registered client origin
- Host header: must match the server's expected hostname
- Reject requests where either header does not match — this prevents DNS rebinding attacks.
- Enforce a minimum acceptable MCP protocol version on the server:
- Reject initialize requests that propose a version below the minimum.
- Document the minimum version in the server configuration.
- Output: MCP transport configuration + Origin/Host validation middleware + minimum version enforcement.

**Expected Artifacts**
- MCP transport configuration + Origin/Host validation middleware + minimum version enforcement.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are configuring transport security for an MCP-based tool integration.
Apply AISVS C10.3.1, C10.3.2, and C10.3.3.

Requirements:
- For remote MCP servers: require authenticated, encrypted streamable HTTP (HTTPS with TLS 1.2+).
- For local MCP servers: permit stdio transport ONLY if running in a controlled local environment;
  enforce a configuration check that prevents stdio from being enabled in production.
- On all HTTP-based MCP transports, independently validate BOTH:
  - Origin header: must match the registered client origin
  - Host header: must match the server's expected hostname
  Reject requests where either header does not match — this prevents DNS rebinding attacks.
- Enforce a minimum acceptable MCP protocol version on the server:
  - Reject initialize requests that propose a version below the minimum.
  - Document the minimum version in the server configuration.

Output: MCP transport configuration + Origin/Host validation middleware + minimum version enforcement.
```


### C10-CODE-03: Implement MCP Input Validation and Schema Enforcement

**Objective**
- You are implementing input validation for an MCP server and client.

**Required Controls**
- Apply AISVS C10.4.1, C10.4.2, C10.4.3, C10.4.4, and C10.4.5.

**Execution Steps**
- Follow the source prompt body exactly and map each action to AISVS control IDs.

**Expected Artifacts**
- MCP server strict schema validator + replay detection + MCP client injection screener + tool snapshot manager.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing input validation for an MCP server and client.
Apply AISVS C10.4.1, C10.4.2, C10.4.3, C10.4.4, and C10.4.5.

Requirements:
MCP SERVER side:
- Enforce strict JSON schema validation on ALL incoming function call parameters.
- Reject any function call with unrecognized parameters (strict mode — no extra properties).
- Reject any function call with oversized parameters (enforce max size per parameter and per request).
- Enforce maximum payload size limits on all transports.
- Sign tool responses with a unique nonce (UUID) and timestamp so clients can detect replay attacks (C10.4.6).

MCP CLIENT side:
- Before injecting tools/list and tools/call responses into the model context:
  1. Validate the response against the declared tool schema (C10.4.1).
  2. Screen the response for indirect prompt injection patterns (C10.4.2).
  Reject and quarantine any response that fails either check.
- Maintain a snapshot of each tool's declared schema (C10.4.8):
  - If a tool definition changes between invocations, trigger a re-approval request before the modified
    tool can be invoked.
- Present an explicit consent dialogue to users when installing a local MCP server (C10.4.7).

Output: MCP server strict schema validator + replay detection + MCP client injection screener + tool snapshot manager.
```


### C10-CODE-04: Implement MCP Component Allow-Listing

**Objective**
- You are implementing MCP server discovery and allow-listing controls.

**Required Controls**
- Apply AISVS C10.1.1, C10.1.2, and C10.1.3.

**Execution Steps**
- Maintain an allow-list of permitted MCP servers (name, URL, expected certificate fingerprint).
- Reject connections to any MCP server not in the allow-list.
- Before using any MCP component, cryptographically verify it:
- Check the component's signature against the publisher's public key.
- Verify the TLS certificate matches the expected fingerprint for the server.
- For locally launched MCP servers:
- Run in a least-privilege sandbox (containerized, restricted filesystem, restricted network).
- Restrict file system access to the declared working directory only.
- Restrict network access to the declared upstream services only.
- Output: MCP allowlist enforcer + signature verifier + local server sandbox launcher.

**Expected Artifacts**
- MCP allowlist enforcer + signature verifier + local server sandbox launcher.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing MCP server discovery and allow-listing controls.
Apply AISVS C10.1.1, C10.1.2, and C10.1.3.

Requirements:
- Maintain an allow-list of permitted MCP servers (name, URL, expected certificate fingerprint).
- Reject connections to any MCP server not in the allow-list.
- Before using any MCP component, cryptographically verify it:
  - Check the component's signature against the publisher's public key.
  - Verify the TLS certificate matches the expected fingerprint for the server.
- For locally launched MCP servers:
  - Run in a least-privilege sandbox (containerized, restricted filesystem, restricted network).
  - Restrict file system access to the declared working directory only.
  - Restrict network access to the declared upstream services only.

Output: MCP allowlist enforcer + signature verifier + local server sandbox launcher.
```


---
