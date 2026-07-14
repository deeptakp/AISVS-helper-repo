# REQUIREMENTS.md — AISVS Control Reference

> Source: [OWASP AI Security Verification Standard v1.0](https://github.com/OWASP/AISVS/tree/main/1.0/en)
> Levels: **L1** = Baseline · **L2** = Standard · **L3** = Advanced

---

## C1 — Training Data Integrity & Traceability

### C1.1 Training Data Origin & Data Security

| ID | Requirement | Level |
|----|-------------|-------|
| 1.1.1 | Training data includes only features, attributes, and fields required for the model's stated purpose. | L1 |
| 1.1.2 | An up-to-date inventory is kept of every training-data source, including origin, responsible party, license, collection method, intended use constraints, and processing history. | L2 |
| 1.1.3 | Data integrity is provided when training data is stored and transferred. | L2 |
| 1.1.4 | Integrity monitoring is applied to guard against unauthorized modifications or corruption of training data. | L2 |
| 1.1.5 | Datasets are watermarked so their use can be attributed and any unauthorized use detected. | L3 |

### C1.2 Data Labeling and Annotation Security

| ID | Requirement | Level |
|----|-------------|-------|
| 1.2.1 | Labeling platforms enforce access controls that restrict who can create, modify, or approve annotations. | L1 |
| 1.2.2 | Cryptographic integrity is applied to labeling artifacts. | L2 |
| 1.2.3 | Sensitive information in labels is redacted, anonymized, or encrypted before being used in any labeling artifact. | L2 |

### C1.3 Training Data Quality and Security Assurance

| ID | Requirement | Level |
|----|-------------|-------|
| 1.3.1 | Training and fine-tuning pipelines implement poisoning detection techniques. | L2 |
| 1.3.2 | Automatically generated labels are subject to confidence thresholds and consistency checks. | L2 |
| 1.3.3 | Models used in security-relevant decisions are evaluated for bias patterns. | L2 |
| 1.3.4 | Disallowed content is detected and removed before training. | L2 |
| 1.3.5 | Defenses against clean-label poisoning attacks are implemented. | L3 |

---

## C2 — Input Validation

### C2.1 Prompt Injection Defenses

| ID | Requirement | Level |
|----|-------------|-------|
| 2.1.1 | Input normalization is applied before tokenization or embedding. | L1 |
| 2.1.2 | Encoding and representation smuggling in inputs is detected and mitigated. | L1 |
| 2.1.3 | All inputs that could steer model behavior are treated as untrusted and screened by a prompt injection detection ruleset or classifier, with flagged inputs blocked. | L1 |
| 2.1.4 | Input length controls prevent content from exceeding the context window; inputs exceeding token limits are rejected, not truncated. | L1 |
| 2.1.5 | A character set restriction uses an allow-list approach that permits only characters explicitly required. | L1 |
| 2.1.6 | The system enforces an instruction hierarchy where system and developer messages override user instructions. | L2 |
| 2.1.7 | Reserved special tokens are encoded as literal characters and cannot be injected into the model context. | L2 |
| 2.1.8 | The system can detect many-shot jailbreaking patterns. | L3 |

### C2.2 Content & Policy Screening

| ID | Requirement | Level |
|----|-------------|-------|
| 2.2.1 | Every prompt is scored by a content classifier for violence, self-harm, hate, and sexual content. | L1 |
| 2.2.2 | Prompt content classification is evaluated for unsupported languages. | L1 |
| 2.2.3 | Non-text inputs (image/video/audio) are checked for adversarial perturbations, steganographic payloads, or hidden content. | L2 |
| 2.2.4 | Coordinated attacks spanning multiple input types are detected and blocked. | L3 |

---

## C3 — Model Lifecycle Management & Change Control

### C3.1 Model Authorization & Integrity

| ID | Requirement | Level |
|----|-------------|-------|
| 3.1.1 | A model registry maintains an inventory of all deployed model artifacts and their origin. | L1 |
| 3.1.2 | All model artifacts are cryptographically signed by authorized entities. | L2 |
| 3.1.3 | Model cryptographic signatures are verified at deployment admission and on load. | L2 |

### C3.2 Model Validation & Testing

| ID | Requirement | Level |
|----|-------------|-------|
| 3.2.1 | Models undergo automated input validation testing, safety evaluation testing, and output sanitization testing before deployment. | L1 |
| 3.2.2 | Models subjected to post-training quantization are re-evaluated against the same safety and alignment test suite. | L2 |
| 3.2.3 | Provider model, version, or routing changes trigger security re-evaluation before continued use. | L3 |

### C3.3 Controlled Deployment & Rollback

| ID | Requirement | Level |
|----|-------------|-------|
| 3.3.1 | Production deployments implement rollout mechanisms with automated rollback triggers. | L2 |
| 3.3.2 | Rollback capabilities restore the complete model state. | L2 |
| 3.3.3 | Model versions running in parallel use isolated runtime state. | L2 |

### C3.4 Secure Development Practices

| ID | Requirement | Level |
|----|-------------|-------|
| 3.4.1 | AI-specific runtime components are not shared across environment boundaries (dev, staging, prod). | L1 |
| 3.4.2 | Model training and fine-tuning environments are isolated from production environments. | L2 |

### C3.5 Pipeline Fine-Tuning

| ID | Requirement | Level |
|----|-------------|-------|
| 3.5.1 | Models used in RLHF fine-tuning are versioned and integrity-verified before use. | L2 |
| 3.5.2 | RLHF training stages include automated detection of reward hacking or reward model over-optimization. | L3 |
| 3.5.3 | In multi-stage fine-tuning pipelines, each stage's output is integrity-verified before being consumed by the next stage. | L3 |
| 3.5.4 | Fine-tuning checkpoints are registered as distinct artifacts. | L3 |

---

## C4 — Infrastructure, Configuration & Deployment Security

### C4.1 AI Workload Sandboxing & Validation

| ID | Requirement | Level |
|----|-------------|-------|
| 4.1.1 | AI models execute in isolated sandboxes. | L1 |
| 4.1.2 | Model artifact loading enforces an explicit allow-list of serialization formats that do not permit arbitrary code execution during deserialization. | L1 |
| 4.1.3 | Workload attestation is performed before model loading. | L3 |
| 4.1.4 | Confidential inference services protect model weights during runtime through isolated execution environments. | L3 |

### C4.2 AI Hardware Security

| ID | Requirement | Level |
|----|-------------|-------|
| 4.2.1 | AI accelerator (GPU) firmware is version-pinned, signed, and attested at boot. | L2 |
| 4.2.2 | Execution within a TEE provides hardware-enforced isolation, memory encryption, and integrity protection. | L3 |
| 4.2.3 | AI accelerator (GPU) integrity is validated using hardware-based attestation mechanisms before each workload. | L3 |
| 4.2.4 | Accelerator (GPU) memory is isolated between workloads through partitioning with memory sanitization. | L3 |
| 4.2.5 | Accelerator interconnects are restricted to approved topologies and authenticated endpoints. | L3 |

### C4.3 Edge & Distributed AI Security

| ID | Requirement | Level |
|----|-------------|-------|
| 4.3.1 | Edge AI devices authenticate to central infrastructure using strong authentication mechanisms. | L1 |
| 4.3.2 | Models deployed to edge or mobile devices are cryptographically signed during packaging, and on-device runtime validates signatures before loading. | L2 |
| 4.3.3 | Inference runtimes enforce process, memory, and file access isolation. | L3 |
| 4.3.4 | Model weights and sensitive parameters stored locally are encrypted using hardware-backed key stores or secure enclaves. | L3 |
| 4.3.5 | Models packaged within mobile, IoT, or embedded applications are encrypted at rest, decrypted only inside a trusted runtime or secure enclave. | L3 |

---

## C5 — Access Control & Identity for AI Components & Users

### C5.1 Authentication

| ID | Requirement | Level |
|----|-------------|-------|
| 5.1.1 | High-risk AI operations require step-up authentication. | L3 |
| 5.1.2 | AI agents in federated or multi-system deployments authenticate using short-lived, minimal-scoped, cryptographically signed tokens. | L3 |

### C5.2 AI Resource Authorization & Classification

| ID | Requirement | Level |
|----|-------------|-------|
| 5.2.1 | Every AI resource enforces access controls with explicit allow-lists and default-deny policies. | L2 |
| 5.2.2 | Retrieval pipelines (RAG, embedding lookups) enforce the end-user's authorization context at each retrieval and assembly stage. | L2 |
| 5.2.3 | Sensitive data is retrieved via retrieval pipelines to prevent permanent storage in models. | L2 |
| 5.2.4 | Post-inference filtering mechanisms prevent responses from including data the requester is not authorized to receive. | L2 |
| 5.2.5 | The policy decision point for agent authorization is isolated from the agent's execution environment. | L2 |
| 5.2.6 | Privileged access to model weights, training pipelines, and production AI configuration is granted just-in-time with automatic expiry. | L3 |
| 5.2.7 | Data classification labels propagate to downstream resources (embeddings, prompt caches, model outputs). | L3 |

### C5.3 Multi-Tenant Isolation

| ID | Requirement | Level |
|----|-------------|-------|
| 5.3.1 | Shared model serving infrastructure prevents one tenant's operations from influencing or observing another tenant's operations. | L2 |
| 5.3.2 | One tenant cannot influence or observe another tenant's operations through shared compute resources. | L3 |

---

## C6 — Supply Chain Security for Models

### C6.1 Model Artifact Integrity

| ID | Requirement | Level |
|----|-------------|-------|
| 6.1.1 | Models are scanned for malicious code before import. | L1 |
| 6.1.2 | Model weights, datasets, and fine-tuning adapters are downloaded only from approved sources. | L1 |
| 6.1.3 | Every third-party model artifact can be integrity-verified. | L2 |
| 6.1.4 | Models pass a behavioral acceptance test suite before being promoted to any non-development environment. | L2 |

### C6.2 AI BOM & Supply Chain Monitoring

| ID | Requirement | Level |
|----|-------------|-------|
| 6.2.1 | Every model artifact publishes a version-controlled, machine-readable AI BOM listing datasets, weights, licenses, and data-origin statements. | L1 |
| 6.2.2 | AI BOMs are cryptographically signed before deployment. | L2 |
| 6.2.3 | AI BOM completeness checks fail the build if any component metadata is missing. | L2 |

---

## C7 — Model Behavior, Output Control & Safety Assurance

### C7.1 Output Format Enforcement

| ID | Requirement | Level |
|----|-------------|-------|
| 7.1.1 | The application validates all model outputs against a defined schema and rejects any output that does not match. | L1 |
| 7.1.2 | Model-generated output is bounded by length limits and termination controls. | L1 |

### C7.2 Hallucination Detection & Mitigation

| ID | Requirement | Level |
|----|-------------|-------|
| 7.2.1 | The system assesses the reliability of generated answers using a confidence estimation method. | L2 |
| 7.2.2 | The application automatically blocks answers or switches to a fallback message if the confidence score drops below a defined threshold. | L2 |
| 7.2.3 | For responses classified as high-risk by policy, the system performs an additional verification step. | L3 |

### C7.3 Output Safety

| ID | Requirement | Level |
|----|-------------|-------|
| 7.3.1 | Automated classifiers scan every response and block content matching defined harmful content categories. | L1 |
| 7.3.2 | Output filters detect and block responses that disclose system prompt content or backend data. | L2 |
| 7.3.3 | Model-generated output is prevented from triggering outbound requests. | L2 |
| 7.3.4 | Model outputs are checked for hidden, encoded, or misleading content (homoglyphs, formatting, metadata, structured fields). | L3 |

### C7.4 Source Attribution & Citation Integrity

| ID | Requirement | Level |
|----|-------------|-------|
| 7.4.1 | Responses generated using RAG include attribution to the source documents. | L1 |
| 7.4.2 | RAG attributions are derived from retrieval metadata and are not model-generated. | L1 |
| 7.4.3 | Claims in a RAG response can be traced to the retrieved chunk. | L2 |
| 7.4.4 | Generated media is watermarked to prove it was AI-generated. | L3 |

---

## C8 — Memory, Embeddings & Vector Database Security

### C8.1 Access Controls on Memory & RAG Indices

| ID | Requirement | Level |
|----|-------------|-------|
| 8.1.1 | Vector identifiers and namespaces enforce uniqueness per tenant and prevent cross-tenant collisions. | L1 |
| 8.1.2 | Document metadata tags are immutable after the initial write. | L2 |
| 8.1.3 | Retrieval operations enforce scope constraints. | L2 |

### C8.2 Embedding Sanitization & Validation

| ID | Requirement | Level |
|----|-------------|-------|
| 8.2.1 | Sensitive fields are detected before embedding and are masked, tokenized, or dropped. | L1 |
| 8.2.2 | Vectors that fall outside normal clustering patterns are flagged and quarantined before entering production indices. | L2 |
| 8.2.3 | Agent outputs and tool outputs are not automatically written to trusted agent memory without explicit source validation. | L2 |
| 8.2.4 | Content crafted to manipulate retrieval results is detected and rejected or quarantined before vectorization. | L3 |
| 8.2.5 | New content written to memory is checked for contradictions with what is already stored, and conflicts trigger alerts. | L3 |

### C8.3 Memory Expiry & Revocation

| ID | Requirement | Level |
|----|-------------|-------|
| 8.3.1 | Expired vectors are excluded from retrieval results. | L2 |
| 8.3.2 | Memory can be reset. | L2 |
| 8.3.3 | Quarantined content is retained but excluded from all retrieval results. | L3 |

---

## C9 — Orchestration & Agentic Security

### C9.1 Execution Budgets, Loop Control, and Circuit Breakers

| ID | Requirement | Level |
|----|-------------|-------|
| 9.1.1 | Per-tool quotas and timeouts (CPU, memory, disk, egress, execution time) are enforced. | L1 |
| 9.1.2 | Per-execution budgets (max recursion depth, token use, monetary spend) are configured and enforced by the runtime. | L1 |
| 9.1.3 | A swarm-level kill-switch exists that can halt all active agent instances. | L2 |

### C9.2 High-Impact Action Approval and Irreversibility Controls

| ID | Requirement | Level |
|----|-------------|-------|
| 9.2.1 | The agent runtime blocks execution of privileged, high-impact, or irreversible actions until explicit human approval is received and verified. | L1 |
| 9.2.2 | Approval requests display canonicalized and complete action parameters without truncation. | L2 |
| 9.2.3 | Each high-impact action has a trusted reversibility classification (read-only, reversible, externally reversible, irreversible). | L2 |
| 9.2.4 | The agent runtime enforces reversibility classifications. | L2 |
| 9.2.5 | Any self-modification capability is restricted by enforceable boundaries. | L2 |
| 9.2.6 | Agentic systems include an AI-augmented review of planned high-risk actions before execution. | L2 |
| 9.2.7 | The AI-augmented review mechanism is protected against manipulation by adversarial inputs. | L2 |
| 9.2.8 | Approvals are cryptographically bound to action parameters, requester identity, execution context, and a unique single-use nonce. | L3 |
| 9.2.9 | Cryptographic key material or credentials used to issue approvals are isolated from the agent runtime. | L3 |
| 9.2.10 | Approval gates for multi-step or multi-agent action chains enforce the highest-impact reversibility classification present anywhere in the chain. | L3 |

### C9.3 Component Isolation and Tool Authorization

| ID | Requirement | Level |
|----|-------------|-------|
| 9.3.1 | Each tool/plugin executes in a least-privilege sandbox or is otherwise isolated from model operations. | L1 |
| 9.3.2 | Tool outputs are validated against schemas. | L1 |
| 9.3.3 | Tool manifests declare required privileges, resource limits, and output validation requirements. | L2 |
| 9.3.4 | The runtime enforces the privileges, resource limits, and output-validation requirements declared in tool manifests. | L2 |
| 9.3.5 | Components processing untrusted data are isolated from tool-calling capabilities. | L2 |
| 9.3.6 | There is architectural separation between processing of untrusted tool outputs and agent operations. | L2 |
| 9.3.7 | External resources named in model output are verified against an approved allow-list or registry before the agent installs or invokes them. | L2 |
| 9.3.8 | Policy violations trigger automated tool containment. | L3 |

### C9.4 Agent and Orchestrator Identity

| ID | Requirement | Level |
|----|-------------|-------|
| 9.4.1 | Each agent instance has a unique cryptographic identity and authenticates as a first-class principal to downstream systems. | L2 |
| 9.4.2 | Agent-initiated actions are cryptographically bound to each step of the execution chain for non-repudiation. | L2 |
| 9.4.3 | Agent identity credentials rotate on a defined schedule. | L3 |
| 9.4.4 | Agent state persisted between invocations is integrity-protected. | L3 |

### C9.5 Agent Authorization, Delegation, and Continuous Enforcement

| ID | Requirement | Level |
|----|-------------|-------|
| 9.5.1 | Agent actions are authorized against fine-grained policies enforced by the runtime. | L2 |
| 9.5.2 | When an agent acts on a user's behalf, the runtime propagates an integrity-protected, scope-limited token. | L2 |
| 9.5.3 | All access control decisions are enforced by application logic or a policy engine, never by the AI model itself. | L2 |
| 9.5.4 | Secrets and credentials required by an agent at runtime are not exposed within the model's observable context. | L2 |
| 9.5.5 | Inter-agent task delegation is restricted by an explicit authorization policy. | L2 |
| 9.5.6 | Long-running agent sessions re-evaluate current backend authorization policy on every privileged action. | L3 |

### C9.6 Shutdown and Graceful Degradation

| ID | Requirement | Level |
|----|-------------|-------|
| 9.6.1 | A manual kill-switch mechanism exists to immediately halt AI model inference and outputs. | L1 |
| 9.6.2 | When a human-approval gate is not satisfied within the defined approval time, the system blocks the pending action. | L2 |
| 9.6.3 | Kill-switch commands are implemented through an out-of-band channel isolated from the agent runtime. | L3 |

---

## C10 — Model Context Protocol (MCP) Security

### C10.1 Component Integrity

| ID | Requirement | Level |
|----|-------------|-------|
| 10.1.1 | MCP components are obtained only from trusted sources and cryptographically verified. | L1 |
| 10.1.2 | Only allow-listed MCP servers are permitted. | L2 |
| 10.1.3 | Locally launched MCP servers run in a least-privilege sandbox. | L2 |

### C10.2 Authentication & Authorization

| ID | Requirement | Level |
|----|-------------|-------|
| 10.2.1 | MCP servers validate access tokens for each request and do not rely on transport security alone. | L1 |
| 10.2.2 | MCP servers validate the presented access token's issuer, audience, expiration, and scope claims (OAuth 2.1). | L1 |
| 10.2.3 | MCP servers acting as OAuth 2.1 resource servers do not store or persist access tokens or user credentials. | L1 |
| 10.2.4 | MCP tools/list returns only tools permitted by resource owners' authorized scopes. | L2 |
| 10.2.5 | MCP servers enforce access control on every tool invocation. | L2 |
| 10.2.6 | MCP servers ensure all session artifacts are removed when a session terminates. | L2 |
| 10.2.7 | MCP servers do not pass through access tokens received from clients to downstream APIs. | L2 |

### C10.3 Secure Transport

| ID | Requirement | Level |
|----|-------------|-------|
| 10.3.1 | Authenticated, encrypted streamable HTTP is used for MCP transport for remote services. | L1 |
| 10.3.2 | stdio transport is permitted only in controlled local environments. | L1 |
| 10.3.3 | MCP servers validate both the Origin header and the Host header independently on all HTTP-based transports. | L2 |
| 10.3.4 | MCP clients enforce a minimum acceptable protocol version. | L2 |
| 10.3.5 | Access tokens between the MCP client and server are sender-constrained using mTLS or DPoP. | L3 |

### C10.4 Schema, Message, and Input Validation

| ID | Requirement | Level |
|----|-------------|-------|
| 10.4.1 | MCP tools/list and tools/call responses are validated against their declared schemas before being injected into the model context. | L1 |
| 10.4.2 | MCP tools/list and tools/call responses are screened for indirect prompt injection. | L1 |
| 10.4.3 | MCP servers reject unrecognized or oversized parameters in function calls. | L1 |
| 10.4.4 | All MCP servers enforce strict schema validation. | L2 |
| 10.4.5 | All MCP transports enforce maximum payload size limits. | L2 |
| 10.4.6 | MCP servers sign tool responses with a unique nonce and timestamp. | L2 |
| 10.4.7 | MCP clients present users with explicit consent dialogue upon installation of a local MCP server. | L2 |
| 10.4.8 | MCP clients maintain a snapshot of tool definitions and re-approve changes before the modified tool can be invoked. | L3 |

---

## C11 — Adversarial Robustness

### C11.1 Model Alignment, Safety, and Robustness Testing

| ID | Requirement | Level |
|----|-------------|-------|
| 11.1.1 | The model has undergone alignment and safety training to prevent generation of disallowed content categories. | L1 |
| 11.1.2 | A version-controlled alignment test suite is run on every model update or release. | L1 |
| 11.1.3 | Models are evaluated against known adversarial attack techniques relevant to their modality. | L1 |
| 11.1.4 | Models are hardened against adversarial inputs. | L2 |
| 11.1.5 | An automated evaluator measures harmful-content rate and flags regressions beyond a defined threshold. | L3 |

### C11.2 Membership-Inference and Model-Inversion Mitigation

| ID | Requirement | Level |
|----|-------------|-------|
| 11.2.1 | Model-inferred sensitive attributes are not directly returned in outputs. | L1 |
| 11.2.2 | Inference endpoints enforce per-principal and global rate limits sized to the extraction threat model. | L1 |
| 11.2.3 | Model outputs are calibrated to reduce overconfident predictions. | L2 |
| 11.2.4 | Training on sensitive datasets employs differentially-private optimization. | L2 |
| 11.2.5 | Membership-inference attack simulations demonstrate attack accuracy does not exceed random guessing. | L3 |

### C11.3 Model-Extraction Defense

| ID | Requirement | Level |
|----|-------------|-------|
| 11.3.1 | Query-pattern analysis feeds an extraction-attempt detector. | L1 |
| 11.3.2 | Raw model outputs are not directly exposed beyond the application backend. | L2 |
| 11.3.3 | Model watermarking or fingerprinting techniques are applied so unauthorized copies can be identified. | L3 |
| 11.3.4 | Detection of suspected extraction triggers response measures. | L3 |

### C11.4 Model Runtime Anomaly Detection

| ID | Requirement | Level |
|----|-------------|-------|
| 11.4.1 | Inputs from external or untrusted sources pass through anomaly detection before model inference. | L2 |
| 11.4.2 | Inputs flagged as anomalous trigger gating actions. | L2 |
| 11.4.3 | The safety violation feedback pipeline includes poisoning detection and human review gates. | L3 |

---

## C12 — Monitoring, Logging & Anomaly Detection

### C12.1 Request & Response Logging

| ID | Requirement | Level |
|----|-------------|-------|
| 12.1.1 | AI interactions are logged with session context and AI-specific telemetry. | L1 |
| 12.1.2 | Safety filtering and policy decisions are logged with sufficient detail to support audit, debugging, and forensic analysis. | L2 |
| 12.1.3 | Log entries for AI inference events follow a structured, interoperable schema (model ID, token usage, provider name, operation type). | L2 |
| 12.1.4 | RAG pipeline retrieval events are logged, including the query, documents retrieved, and knowledge source. | L2 |

### C12.2 Detection and Alerting

| ID | Requirement | Level |
|----|-------------|-------|
| 12.2.1 | The system detects and alerts on known jailbreak patterns, prompt injection attempts, and adversarial inputs. | L1 |
| 12.2.2 | Behavioral anomaly detection identifies unusual conversation patterns, excessive retry attempts, or probing behaviors. | L2 |
| 12.2.3 | Custom rules detect AI-specific threat patterns for coordinated jailbreak attempts, prompt injection, and system prompt extraction. | L2 |
| 12.2.4 | Extraction-alert events include offending query metadata to support investigation. | L2 |
| 12.2.5 | Token usage is tracked at granular attribution levels (per user, per session, per feature endpoint, per team). | L2 |
| 12.2.6 | LLM API traffic is monitored for covert-channel indicators and C2 activity signatures. | L3 |

### C12.3 Model, Data, and Performance Drift Detection

| ID | Requirement | Level |
|----|-------------|-------|
| 12.3.1 | Data drift detection monitors input distribution changes using statistically validated methods. | L1 |
| 12.3.2 | Hallucination detection monitors identify and flag model outputs that contain factually incorrect or fabricated information. | L2 |
| 12.3.3 | Hallucination rates are tracked as continuous time-series metrics. | L2 |
| 12.3.4 | Unexplained behavioral shifts are distinguished from gradual, expected operational drift. | L3 |

### C12.4 Proactive Security Behavior Monitoring

| ID | Requirement | Level |
|----|-------------|-------|
| 12.4.1 | Autonomous action triggers include proactive behavior-pattern analysis, security evaluation, and threat-landscape assessment. | L2 |
| 12.4.2 | Audit logs capture security-critical proactive actions, including approver identity, timestamp, action parameters, and decision outcomes. | L2 |
| 12.4.3 | Kill-switch activations and override commands are logged. | L2 |

### C12.5 Training Data & Model Lifecycle Audit

| ID | Requirement | Level |
|----|-------------|-------|
| 12.5.1 | Dataset lineage records each dataset and its components, including all transformations, augmentations, and merges. | L1 |
| 12.5.2 | All labeling activities are recorded in logs. | L1 |
| 12.5.3 | All model changes generate immutable audit records. | L2 |
| 12.5.4 | Every ingested document is tagged at write time with source, writer identity, and timestamp. | L2 |
