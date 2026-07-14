# AISVS Security Checklist

> **Project:** _________________________________
> **Version:** _________________________________
> **Assessment Date:** _________________________________
> **Assessor:** _________________________________
> **AISVS Level in Scope:** ☐ L1 only  ☐ L1 + L2  ☐ L1 + L2 + L3

---

## How to Use

- **Status values:** ✅ PASS | ❌ FAIL | ⚠️ PARTIAL | N/A | ⬜ NOT TESTED
- Complete all L1 items for every AI system. Add L2/L3 based on risk profile.
- Link evidence (log samples, config files, test results) in the Evidence column.

---

## C1 — Training Data Integrity & Traceability

| ID | Requirement Summary | L | Status | Evidence |
|----|---------------------|---|--------|----------|
| 1.1.1 | Training data limited to fields required for stated purpose | L1 | ⬜ | |
| 1.1.2 | Data source inventory with origin, license, responsible party | L2 | ⬜ | |
| 1.1.3 | Integrity protection during storage and transfer | L2 | ⬜ | |
| 1.1.4 | Integrity monitoring for unauthorized modification | L2 | ⬜ | |
| 1.1.5 | Dataset watermarking for attribution | L3 | ⬜ | |
| 1.2.1 | Labeling platform RBAC (create/modify/approve) | L1 | ⬜ | |
| 1.2.2 | Cryptographic integrity of labeling artifacts | L2 | ⬜ | |
| 1.2.3 | PII/sensitive data redacted in labels | L2 | ⬜ | |
| 1.3.1 | Poisoning detection in training pipeline | L2 | ⬜ | |
| 1.3.2 | Auto-label confidence thresholds and consistency checks | L2 | ⬜ | |
| 1.3.3 | Bias evaluation for security-relevant models | L2 | ⬜ | |
| 1.3.4 | Disallowed content removed before training | L2 | ⬜ | |
| 1.3.5 | Clean-label poisoning defenses | L3 | ⬜ | |

---

## C2 — Input Validation

| ID | Requirement Summary | L | Status | Evidence |
|----|---------------------|---|--------|----------|
| 2.1.1 | Input normalization before tokenization | L1 | ⬜ | |
| 2.1.2 | Encoding/representation smuggling detection | L1 | ⬜ | |
| 2.1.3 | All inputs screened by prompt injection classifier | L1 | ⬜ | |
| 2.1.4 | Inputs exceeding token limit rejected (not truncated) | L1 | ⬜ | |
| 2.1.5 | Allow-list character set restriction | L1 | ⬜ | |
| 2.1.6 | Instruction hierarchy enforced (system > user) | L2 | ⬜ | |
| 2.1.7 | Reserved special tokens protected from injection | L2 | ⬜ | |
| 2.1.8 | Many-shot jailbreak pattern detection | L3 | ⬜ | |
| 2.2.1 | Content classifier for all prompts (violence/self-harm/hate/sexual) | L1 | ⬜ | |
| 2.2.2 | Unsupported language handling policy | L1 | ⬜ | |
| 2.2.3 | Non-text input adversarial perturbation detection | L2 | ⬜ | |
| 2.2.4 | Multi-modal coordinated attack detection | L3 | ⬜ | |

---

## C3 — Model Lifecycle Management

| ID | Requirement Summary | L | Status | Evidence |
|----|---------------------|---|--------|----------|
| 3.1.1 | Model registry with all deployed artifacts and origins | L1 | ⬜ | |
| 3.1.2 | All model artifacts cryptographically signed | L2 | ⬜ | |
| 3.1.3 | Signatures verified at deployment admission and load | L2 | ⬜ | |
| 3.2.1 | Automated safety/validation testing before deployment | L1 | ⬜ | |
| 3.2.2 | Quantized models re-evaluated against safety suite | L2 | ⬜ | |
| 3.2.3 | Provider/version changes trigger security re-evaluation | L3 | ⬜ | |
| 3.3.1 | Controlled rollout with automated rollback triggers | L2 | ⬜ | |
| 3.3.2 | Rollback restores complete model state | L2 | ⬜ | |
| 3.3.3 | Parallel model versions use isolated runtime state | L2 | ⬜ | |
| 3.4.1 | No shared AI runtime components across environment boundaries | L1 | ⬜ | |
| 3.4.2 | Training/fine-tuning environments isolated from production | L2 | ⬜ | |

---

## C4 — Infrastructure & Deployment Security

| ID | Requirement Summary | L | Status | Evidence |
|----|---------------------|---|--------|----------|
| 4.1.1 | AI models execute in isolated sandboxes | L1 | ⬜ | |
| 4.1.2 | Explicit allowlist of safe serialization formats; unsafe blocked | L1 | ⬜ | |
| 4.1.3 | Workload attestation before model loading | L3 | ⬜ | |
| 4.2.1 | GPU firmware version-pinned, signed, attested at boot | L2 | ⬜ | |
| 4.3.1 | Edge devices use strong authentication to central infra | L1 | ⬜ | |
| 4.3.2 | Edge/mobile model packages cryptographically signed and verified | L2 | ⬜ | |
| 4.3.4 | On-device model weights encrypted with hardware-backed key | L3 | ⬜ | |
| 4.3.5 | Mobile/IoT model packages encrypted at rest | L3 | ⬜ | |

---

## C5 — Access Control & Identity

| ID | Requirement Summary | L | Status | Evidence |
|----|---------------------|---|--------|----------|
| 5.2.1 | All AI resources enforce explicit allow-lists and default-deny | L2 | ⬜ | |
| 5.2.2 | RAG pipeline enforces per-user authorization at retrieval | L2 | ⬜ | |
| 5.2.3 | Sensitive data retrieved via pipeline, not stored in model | L2 | ⬜ | |
| 5.2.4 | Post-inference filtering prevents unauthorized data in responses | L2 | ⬜ | |
| 5.2.5 | Policy decision point isolated from agent execution environment | L2 | ⬜ | |
| 5.2.6 | Privileged AI access granted JIT with automatic expiry | L3 | ⬜ | |
| 5.3.1 | Shared serving infrastructure prevents cross-tenant leakage | L2 | ⬜ | |
| 5.3.2 | Hardware-level isolation for high-sensitivity tenant workloads | L3 | ⬜ | |
| 5.1.1 | Step-up authentication for high-risk AI operations | L3 | ⬜ | |

---

## C6 — Supply Chain Security

| ID | Requirement Summary | L | Status | Evidence |
|----|---------------------|---|--------|----------|
| 6.1.1 | Models scanned for malicious code before import | L1 | ⬜ | |
| 6.1.2 | Model artifacts downloaded only from approved sources | L1 | ⬜ | |
| 6.1.3 | All third-party model artifacts integrity-verifiable | L2 | ⬜ | |
| 6.1.4 | Behavioral acceptance test suite before non-dev promotion | L2 | ⬜ | |
| 6.2.1 | Machine-readable AI BOM for every model artifact | L1 | ⬜ | |
| 6.2.2 | AI BOMs cryptographically signed before deployment | L2 | ⬜ | |
| 6.2.3 | Build fails if BOM component metadata is missing | L2 | ⬜ | |

---

## C7 — Model Behavior & Output Control

| ID | Requirement Summary | L | Status | Evidence |
|----|---------------------|---|--------|----------|
| 7.1.1 | All model outputs validated against declared schema | L1 | ⬜ | |
| 7.1.2 | Output length limits and termination controls enforced | L1 | ⬜ | |
| 7.2.1 | Confidence estimation applied to model responses | L2 | ⬜ | |
| 7.2.2 | Low-confidence responses blocked or returned as fallback | L2 | ⬜ | |
| 7.2.3 | High-risk responses routed to additional verification | L3 | ⬜ | |
| 7.3.1 | Safety classifier applied to every response | L1 | ⬜ | |
| 7.3.2 | System prompt leak detector on outputs | L2 | ⬜ | |
| 7.3.3 | Model output prevented from triggering outbound requests | L2 | ⬜ | |
| 7.4.1 | RAG responses include source attribution | L1 | ⬜ | |
| 7.4.2 | RAG attributions derived from metadata, not model-generated | L1 | ⬜ | |
| 7.4.3 | Claims in RAG responses traceable to retrieved chunks | L2 | ⬜ | |

---

## C8 — Memory, Embeddings & Vector Database

| ID | Requirement Summary | L | Status | Evidence |
|----|---------------------|---|--------|----------|
| 8.1.1 | Vector identifiers/namespaces unique per tenant | L1 | ⬜ | |
| 8.1.2 | Document metadata tags immutable after initial write | L2 | ⬜ | |
| 8.1.3 | Retrieval operations enforce scope constraints | L2 | ⬜ | |
| 8.2.1 | Sensitive fields masked/tokenized/dropped before embedding | L1 | ⬜ | |
| 8.2.2 | Outlier vectors flagged and quarantined | L2 | ⬜ | |
| 8.2.3 | Agent/tool outputs not auto-written to vector memory without validation | L2 | ⬜ | |
| 8.3.1 | Expired vectors excluded from retrieval | L2 | ⬜ | |
| 8.3.2 | Memory reset capability exists | L2 | ⬜ | |
| 8.3.3 | Quarantined content excluded from all retrieval | L3 | ⬜ | |

---

## C9 — Orchestration & Agentic Security

| ID | Requirement Summary | L | Status | Evidence |
|----|---------------------|---|--------|----------|
| 9.1.1 | Per-tool quotas and timeouts enforced | L1 | ⬜ | |
| 9.1.2 | Per-execution budgets (recursion, tokens, spend) enforced | L1 | ⬜ | |
| 9.1.3 | Swarm-level kill-switch to halt all agent instances | L2 | ⬜ | |
| 9.2.1 | High-impact/irreversible actions require human approval | L1 | ⬜ | |
| 9.2.2 | Approval requests show complete canonicalized parameters | L2 | ⬜ | |
| 9.2.3 | Reversibility classification for each action type | L2 | ⬜ | |
| 9.2.5 | Agent self-modification blocked | L2 | ⬜ | |
| 9.3.1 | Each tool executes in least-privilege sandbox | L1 | ⬜ | |
| 9.3.2 | Tool outputs validated against schemas | L1 | ⬜ | |
| 9.4.1 | Each agent has unique cryptographic identity | L2 | ⬜ | |
| 9.5.3 | Access control decisions made by policy engine, not model | L2 | ⬜ | |
| 9.5.4 | Secrets absent from model's context window and prompts | L2 | ⬜ | |
| 9.5.5 | Inter-agent delegation restricted by explicit policy | L2 | ⬜ | |
| 9.6.1 | Manual kill-switch to halt model inference immediately | L1 | ⬜ | |

---

## C10 — MCP Security

| ID | Requirement Summary | L | Status | Evidence |
|----|---------------------|---|--------|----------|
| 10.1.1 | MCP components from trusted sources and cryptographically verified | L1 | ⬜ | |
| 10.2.1 | MCP server validates access tokens per request | L1 | ⬜ | |
| 10.2.2 | OAuth 2.1 token claims fully validated (iss, aud, exp, scope) | L1 | ⬜ | |
| 10.2.3 | MCP server does not store tokens or credentials | L1 | ⬜ | |
| 10.3.1 | Encrypted streamable HTTP for remote MCP transport | L1 | ⬜ | |
| 10.3.3 | Origin and Host headers independently validated | L2 | ⬜ | |
| 10.4.1 | Tool responses validated against schemas before model context injection | L1 | ⬜ | |
| 10.4.2 | Tool responses screened for indirect prompt injection | L1 | ⬜ | |
| 10.4.3 | Unrecognized/oversized parameters rejected | L1 | ⬜ | |
| 10.4.6 | Tool responses signed with nonce+timestamp | L2 | ⬜ | |

---

## C11 — Adversarial Robustness

| ID | Requirement Summary | L | Status | Evidence |
|----|---------------------|---|--------|----------|
| 11.1.1 | Model has undergone alignment/safety training | L1 | ⬜ | |
| 11.1.2 | Alignment test suite run on every model update | L1 | ⬜ | |
| 11.1.3 | Evaluated against known adversarial techniques for modality | L1 | ⬜ | |
| 11.2.1 | Model-inferred sensitive attributes not returned in outputs | L1 | ⬜ | |
| 11.2.2 | Per-principal and global rate limits sized to extraction threat model | L1 | ⬜ | |
| 11.3.1 | Query-pattern analysis feeds extraction-attempt detector | L1 | ⬜ | |
| 11.3.2 | Raw model outputs not exposed beyond application backend | L2 | ⬜ | |
| 11.4.1 | External/untrusted inputs pass through anomaly detection | L2 | ⬜ | |
| 11.4.2 | Anomalous inputs trigger gating actions | L2 | ⬜ | |

---

## C12 — Monitoring, Logging & Anomaly Detection

| ID | Requirement Summary | L | Status | Evidence |
|----|---------------------|---|--------|----------|
| 12.1.1 | AI interactions logged with session context and AI telemetry | L1 | ⬜ | |
| 12.1.3 | Structured log schema with model ID, token usage, provider, operation | L2 | ⬜ | |
| 12.1.4 | RAG retrieval events logged | L2 | ⬜ | |
| 12.2.1 | Detects and alerts on jailbreak/injection/adversarial inputs | L1 | ⬜ | |
| 12.2.2 | Behavioral anomaly detection for unusual patterns | L2 | ⬜ | |
| 12.3.1 | Data drift detection with statistically validated methods | L1 | ⬜ | |
| 12.3.2 | Hallucination detection monitoring | L2 | ⬜ | |
| 12.5.1 | Dataset lineage records transformations and merges | L1 | ⬜ | |
| 12.5.2 | All labeling activities logged | L1 | ⬜ | |
| 12.5.3 | All model changes generate immutable audit records | L2 | ⬜ | |
| 12.5.4 | Ingested documents tagged with source, identity, and timestamp | L2 | ⬜ | |

---

## Summary

| Control Family | L1 Pass | L1 Fail | L2 Pass | L2 Fail | L3 Pass | L3 Fail |
|----------------|---------|---------|---------|---------|---------|---------|
| C1 | | | | | | |
| C2 | | | | | | |
| C3 | | | | | | |
| C4 | | | | | | |
| C5 | | | | | | |
| C6 | | | | | | |
| C7 | | | | | | |
| C8 | | | | | | |
| C9 | | | | | | |
| C10 | | | | | | |
| C11 | | | | | | |
| C12 | | | | | | |
| **TOTAL** | | | | | | |

**Overall Assessment:** ☐ PASS  ☐ CONDITIONAL PASS  ☐ FAIL

**Conditions / Notes:**
_________________________________________________________________
