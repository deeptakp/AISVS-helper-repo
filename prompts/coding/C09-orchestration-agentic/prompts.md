# C9 — Orchestration & Agentic Security: Prompts

> AISVS Reference: C9.1–C9.6 | Controls: 9.1.1–9.6.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C9-CODE-02: Implement Human-in-the-Loop Approval Gate

**Objective**
- You are implementing the action approval system for an autonomous AI agent.

**Required Controls**
- Apply AISVS C9.2.1, C9.2.2, C9.2.3, and C9.2.4.

**Execution Steps**
- Define a reversibility classification for every action type:
- READ_ONLY: file reads, API GETs — no approval required
- REVERSIBLE: file writes, database updates — log but proceed
- EXTERNALLY_REVERSIBLE: email sends, API POSTs — require approval
- IRREVERSIBLE: deletions, financial transactions, public posts — require approval + secondary confirmation
- Before executing any EXTERNALLY_REVERSIBLE or IRREVERSIBLE action:
- Pause execution.
- Present the complete, canonicalized action parameters to the human approver
- (exact diff, full command, complete recipient list, precise amount, full resource path).
- Wait for explicit approval within a configurable timeout (default: 300s).
- If approval is not received within the timeout, block the action.
- Reject any self-modification requests: the agent cannot rewrite its own system prompt, tool list,
- or configuration parameters (C9.2.5).
- Log every approval request, approval decision, approver identity, and action outcome.
- Output: ActionApprovalGate with reversibility classification + human approval UI + timeout enforcement.

**Expected Artifacts**
- ActionApprovalGate with reversibility classification + human approval UI + timeout enforcement.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing the action approval system for an autonomous AI agent.
Apply AISVS C9.2.1, C9.2.2, C9.2.3, and C9.2.4.

Requirements:
- Define a reversibility classification for every action type:
  - READ_ONLY: file reads, API GETs — no approval required
  - REVERSIBLE: file writes, database updates — log but proceed
  - EXTERNALLY_REVERSIBLE: email sends, API POSTs — require approval
  - IRREVERSIBLE: deletions, financial transactions, public posts — require approval + secondary confirmation
- Before executing any EXTERNALLY_REVERSIBLE or IRREVERSIBLE action:
  1. Pause execution.
  2. Present the complete, canonicalized action parameters to the human approver
     (exact diff, full command, complete recipient list, precise amount, full resource path).
  3. Wait for explicit approval within a configurable timeout (default: 300s).
  4. If approval is not received within the timeout, block the action.
- Reject any self-modification requests: the agent cannot rewrite its own system prompt, tool list,
  or configuration parameters (C9.2.5).
- Log every approval request, approval decision, approver identity, and action outcome.

Output: ActionApprovalGate with reversibility classification + human approval UI + timeout enforcement.
```


### C9-CODE-03: Implement Tool Sandboxing and Manifest Enforcement

**Objective**
- You are implementing the tool execution layer for an AI agent framework.

**Required Controls**
- Apply AISVS C9.3.1, C9.3.2, C9.3.3, and C9.3.4.

**Execution Steps**
- Each tool/plugin must execute in a least-privilege sandbox:
- Containerized execution with seccomp profile.
- Read-only filesystem except for explicitly declared output paths.
- No network access except explicitly declared allowed endpoints.
- No access to agent's model context, credentials, or other tool outputs.
- Require a tool manifest for every tool that declares:
- Required privileges (filesystem paths, network endpoints, syscalls)
- Resource limits (CPU, memory, execution time)
- Output schema (JSON schema of expected output format)
- Reversibility classification (read-only, reversible, irreversible)
- Validate every tool output against the declared output schema before passing to the agent.
- Reject any tool output that does not conform to the schema.
- Implement an external resource allow-list: verify any URL or resource name from model output
- against the allow-list before the agent installs or invokes it (C9.3.7).
- Output: ToolExecutionSandbox with manifest enforcement + output validation + resource allowlist.

**Expected Artifacts**
- ToolExecutionSandbox with manifest enforcement + output validation + resource allowlist.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing the tool execution layer for an AI agent framework.
Apply AISVS C9.3.1, C9.3.2, C9.3.3, and C9.3.4.

Requirements:
- Each tool/plugin must execute in a least-privilege sandbox:
  - Containerized execution with seccomp profile.
  - Read-only filesystem except for explicitly declared output paths.
  - No network access except explicitly declared allowed endpoints.
  - No access to agent's model context, credentials, or other tool outputs.
- Require a tool manifest for every tool that declares:
  - Required privileges (filesystem paths, network endpoints, syscalls)
  - Resource limits (CPU, memory, execution time)
  - Output schema (JSON schema of expected output format)
  - Reversibility classification (read-only, reversible, irreversible)
- Validate every tool output against the declared output schema before passing to the agent.
- Reject any tool output that does not conform to the schema.
- Implement an external resource allow-list: verify any URL or resource name from model output
  against the allow-list before the agent installs or invokes it (C9.3.7).

Output: ToolExecutionSandbox with manifest enforcement + output validation + resource allowlist.
```


### C9-CODE-04: Implement Agent Identity and Credential Isolation

**Objective**
- You are implementing identity management for a multi-agent system.

**Required Controls**
- Apply AISVS C9.4.1, C9.4.2, C9.5.4, and C9.5.5.

**Execution Steps**
- Assign a unique cryptographic identity to each agent instance:
- Generate a key pair per agent instance at startup.
- Register the agent's public key with the identity provider.
- Authenticate agent-to-downstream-service calls using the agent's identity (not a shared service account).
- Cryptographically sign every agent action in the execution chain:
- Each action record includes: action type, parameters, agent identity, parent action ID, timestamp, signature.
- This creates a tamper-evident action chain for non-repudiation.
- Isolate credentials from the model's context:
- Secrets and API keys used by tools must be injected at execution time by the runtime, NOT stored
- in the agent's context window, system prompt, or tool call parameters.
- Use a secrets manager integration; never pass secrets through the model.
- Restrict inter-agent delegation:
- An agent can only delegate to agents explicitly listed in its delegation policy.
- Delegation tokens are scoped and short-lived.
- Output: AgentIdentityManager with per-instance key pairs + signed action chain + credential isolation.

**Expected Artifacts**
- AgentIdentityManager with per-instance key pairs + signed action chain + credential isolation.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing identity management for a multi-agent system.
Apply AISVS C9.4.1, C9.4.2, C9.5.4, and C9.5.5.

Requirements:
- Assign a unique cryptographic identity to each agent instance:
  - Generate a key pair per agent instance at startup.
  - Register the agent's public key with the identity provider.
  - Authenticate agent-to-downstream-service calls using the agent's identity (not a shared service account).
- Cryptographically sign every agent action in the execution chain:
  - Each action record includes: action type, parameters, agent identity, parent action ID, timestamp, signature.
  - This creates a tamper-evident action chain for non-repudiation.
- Isolate credentials from the model's context:
  - Secrets and API keys used by tools must be injected at execution time by the runtime, NOT stored
    in the agent's context window, system prompt, or tool call parameters.
  - Use a secrets manager integration; never pass secrets through the model.
- Restrict inter-agent delegation:
  - An agent can only delegate to agents explicitly listed in its delegation policy.
  - Delegation tokens are scoped and short-lived.

Output: AgentIdentityManager with per-instance key pairs + signed action chain + credential isolation.
```


---
