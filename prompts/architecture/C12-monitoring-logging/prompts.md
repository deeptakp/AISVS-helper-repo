# C12 — Monitoring, Logging & Anomaly Detection: Architecture Prompts

> AISVS Reference: C12.1–C12.5 | Controls: 12.1.1–12.5.4

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C12-ARCH-01: Implement Structured AI Interaction Logging

**Objective**
- You are designing the observability layer for an LLM-based application.

**Required Controls**
- Apply AISVS C12.1.1, C12.1.2, C12.1.3, and C12.1.4.

**Execution Steps**
- Log every AI inference interaction with the following structured schema (C12.1.3):
- {
- "event_type": "ai_inference",
- "timestamp": "<ISO8601>",
- "session_id": "<uuid>",
- "request_id": "<uuid>",
- "user_id": "<hashed>",
- "model_id": "<model_name>:<version>",
- "provider": "<provider_name>",
- "operation_type": "<completion|embedding|classification>",
- "input_token_count": <int>,
- "output_token_count": <int>,
- "latency_ms": <int>,
- "safety_filter_triggered": <bool>,
- "safety_filter_category": "<category_or_null>",
- "policy_decision": "<allow|block|review>"
- }
- Log RAG retrieval events separately with (C12.1.4):
- query_hash, retrieved_document_ids, knowledge_source_id, retrieval_latency_ms
- Log all safety filtering and policy decisions with sufficient detail for forensic analysis (C12.1.2).
- Store logs in an append-only, tamper-evident store (WORM storage or cryptographic chaining).
- Never log raw prompt/response content in plaintext — log hashes only, with a secure lookup for authorized investigators.
- Output: AIInteractionLogger with structured schema + RAG event logging + append-only log storage.

**Expected Artifacts**
- AIInteractionLogger with structured schema + RAG event logging + append-only log storage.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are designing the observability layer for an LLM-based application.
Apply AISVS C12.1.1, C12.1.2, C12.1.3, and C12.1.4.

Requirements:
- Log every AI inference interaction with the following structured schema (C12.1.3):
  {
    "event_type": "ai_inference",
    "timestamp": "<ISO8601>",
    "session_id": "<uuid>",
    "request_id": "<uuid>",
    "user_id": "<hashed>",
    "model_id": "<model_name>:<version>",
    "provider": "<provider_name>",
    "operation_type": "<completion|embedding|classification>",
    "input_token_count": <int>,
    "output_token_count": <int>,
    "latency_ms": <int>,
    "safety_filter_triggered": <bool>,
    "safety_filter_category": "<category_or_null>",
    "policy_decision": "<allow|block|review>"
  }
- Log RAG retrieval events separately with (C12.1.4):
  - query_hash, retrieved_document_ids, knowledge_source_id, retrieval_latency_ms
- Log all safety filtering and policy decisions with sufficient detail for forensic analysis (C12.1.2).
- Store logs in an append-only, tamper-evident store (WORM storage or cryptographic chaining).
- Never log raw prompt/response content in plaintext — log hashes only, with a secure lookup for authorized investigators.

Output: AIInteractionLogger with structured schema + RAG event logging + append-only log storage.
```

