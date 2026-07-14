# C9 — Orchestration & Agentic Security: Prompts

> AISVS Reference: C9.1–C9.6 | Controls: 9.1.1–9.6.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C9-REVIEW-01: Review Agentic Execution Controls

**Objective**
- You are reviewing an AI agent implementation for AISVS C9.1 and C9.2 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C9.1.1 — Are per-tool quotas and timeouts (CPU, memory, disk, egress, time) enforced?
- C9.1.2 — Are per-execution budgets (recursion depth, token use, spend) enforced by the runtime?
- C9.1.3 — Does a swarm-level kill-switch exist that can halt all agent instances?
- C9.2.1 — Does the runtime block irreversible/high-impact actions pending human approval?
- C9.2.2 — Do approval requests show complete, canonicalized action parameters (no truncation)?
- C9.2.3 — Is there a reversibility classification for each action type?
- C9.2.4 — Does the runtime enforce the reversibility classification?
- C9.2.5 — Is self-modification (prompt rewriting, tool-list changes) blocked?
- C9.6.1 — Is there a manual kill-switch to halt model inference immediately?

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an AI agent implementation for AISVS C9.1 and C9.2 compliance.

Check each item:
[ ] C9.1.1 — Are per-tool quotas and timeouts (CPU, memory, disk, egress, time) enforced?
[ ] C9.1.2 — Are per-execution budgets (recursion depth, token use, spend) enforced by the runtime?
[ ] C9.1.3 — Does a swarm-level kill-switch exist that can halt all agent instances?
[ ] C9.2.1 — Does the runtime block irreversible/high-impact actions pending human approval?
[ ] C9.2.2 — Do approval requests show complete, canonicalized action parameters (no truncation)?
[ ] C9.2.3 — Is there a reversibility classification for each action type?
[ ] C9.2.4 — Does the runtime enforce the reversibility classification?
[ ] C9.2.5 — Is self-modification (prompt rewriting, tool-list changes) blocked?
[ ] C9.6.1 — Is there a manual kill-switch to halt model inference immediately?

Look for:
- Agents with no token or spend limits (unbounded execution risk).
- Irreversible actions (deletions, financial transactions) with no approval gate.
- Agents that accept self-modification instructions from the model.

For each FAIL: state gap, control ID, and remediation.
```


### C9-REVIEW-02: Review Tool Isolation and Agent Identity

**Objective**
- You are reviewing an AI agent framework for AISVS C9.3, C9.4, and C9.5 compliance.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- C9.3.1 — Does each tool/plugin run in a least-privilege sandbox?
- C9.3.2 — Are tool outputs validated against schemas before being consumed by the agent?
- C9.3.3 — Do tool manifests declare privileges, resource limits, and output schemas?
- C9.3.5 — Are components processing untrusted data isolated from tool-calling capabilities?
- C9.3.6 — Is there architectural separation between untrusted tool output processing and agent operations?
- C9.4.1 — Does each agent instance have a unique cryptographic identity?
- C9.5.3 — Are access control decisions made by application logic/policy engine, never by the AI model?
- C9.5.4 — Are secrets absent from the model's context window, system prompt, and tool call parameters?
- C9.5.5 — Is inter-agent delegation restricted by an explicit policy?
- For each FAIL: state gap, control ID, and remediation.

**Expected Artifacts**
- Evidence logs, control mapping, and remediation notes for each finding/gap.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are reviewing an AI agent framework for AISVS C9.3, C9.4, and C9.5 compliance.

Check each item:
[ ] C9.3.1 — Does each tool/plugin run in a least-privilege sandbox?
[ ] C9.3.2 — Are tool outputs validated against schemas before being consumed by the agent?
[ ] C9.3.3 — Do tool manifests declare privileges, resource limits, and output schemas?
[ ] C9.3.5 — Are components processing untrusted data isolated from tool-calling capabilities?
[ ] C9.3.6 — Is there architectural separation between untrusted tool output processing and agent operations?
[ ] C9.4.1 — Does each agent instance have a unique cryptographic identity?
[ ] C9.5.3 — Are access control decisions made by application logic/policy engine, never by the AI model?
[ ] C9.5.4 — Are secrets absent from the model's context window, system prompt, and tool call parameters?
[ ] C9.5.5 — Is inter-agent delegation restricted by an explicit policy?

For each FAIL: state gap, control ID, and remediation.
```


---
