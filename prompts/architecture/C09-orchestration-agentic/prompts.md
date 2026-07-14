# C9 — Orchestration & Agentic Security: Architecture Prompts

> AISVS Reference: C9.1–C9.6 | Controls: 9.1.1–9.6.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C9-ARCH-01: Implement Agent Execution Budgets and Circuit Breakers

**Objective**
- You are designing the runtime execution layer for an autonomous AI agent.

**Required Controls**
- Apply AISVS C9.1.1, C9.1.2, and C9.1.3.

**Execution Steps**
- Implement per-tool quotas and timeouts enforced at runtime:
- CPU time limit per tool invocation (configurable, default: 30s)
- Memory limit per tool invocation (configurable, default: 512MB)
- Disk I/O limit per tool invocation
- Network egress limit per tool invocation
- Timeout: terminate tool after configured maximum execution time
- Implement per-execution budgets:
- Maximum recursion depth (configurable, default: 10)
- Maximum total token usage across the execution chain
- Maximum monetary spend per execution (for API-cost-bearing tools)
- When any budget is exceeded: immediately halt the agent execution, log the budget breach,
- and return a safe error to the caller.
- Implement a swarm-level kill-switch (C9.1.3):
- A single API call or CLI command can halt ALL running agent instances immediately.
- Kill-switch state is checked at the start of every agent step.
- Output: AgentRuntime with per-tool quotas, execution budgets, and swarm kill-switch.

**Expected Artifacts**
- AgentRuntime with per-tool quotas, execution budgets, and swarm kill-switch.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are designing the runtime execution layer for an autonomous AI agent.
Apply AISVS C9.1.1, C9.1.2, and C9.1.3.

Requirements:
- Implement per-tool quotas and timeouts enforced at runtime:
  - CPU time limit per tool invocation (configurable, default: 30s)
  - Memory limit per tool invocation (configurable, default: 512MB)
  - Disk I/O limit per tool invocation
  - Network egress limit per tool invocation
  - Timeout: terminate tool after configured maximum execution time
- Implement per-execution budgets:
  - Maximum recursion depth (configurable, default: 10)
  - Maximum total token usage across the execution chain
  - Maximum monetary spend per execution (for API-cost-bearing tools)
- When any budget is exceeded: immediately halt the agent execution, log the budget breach,
  and return a safe error to the caller.
- Implement a swarm-level kill-switch (C9.1.3):
  - A single API call or CLI command can halt ALL running agent instances immediately.
  - Kill-switch state is checked at the start of every agent step.

Output: AgentRuntime with per-tool quotas, execution budgets, and swarm kill-switch.
```

