# AISVS AI System Threat Model

> **Standard:** OWASP AISVS v1.0 | Template Version: 1.0

---

## System Identification

| Field | Value |
|-------|-------|
| **System Name** | |
| **Version** | |
| **Threat Model Date** | |
| **Threat Modeller** | |
| **Review Cycle** | ☐ Initial  ☐ Annual Refresh  ☐ Change-triggered |

---

## 1. System Description

### 1.1 AI System Overview

Describe the AI system:
- Business purpose and user base
- AI model type(s) used (LLM, classifier, embedding model, multimodal)
- Training modality (pre-trained + fine-tuned, trained from scratch, API-only)
- Deployment context (cloud SaaS, on-premise, edge, hybrid)

_[Write here]_

### 1.2 AI Component Inventory

| Component | Type | Provider | Trust Level | Description |
|-----------|------|----------|-------------|-------------|
| Base model | LLM / classifier / embedding | | High / Medium / Low | |
| Fine-tuning dataset | Training data | | | |
| Safety/policy model | Classifier | | | |
| Vector store | Database | | | |
| Embedding model | Embedding | | | |
| Tool integrations | MCP / API | | | |
| Agent orchestrator | Framework | | | |

### 1.3 Data Flows

Describe or diagram key data flows:

```
[User] → [Input Validation] → [Model Inference] → [Output Safety] → [User Response]
                                      ↑
                              [RAG Retrieval] ← [Vector Store]
                                      ↑
                             [Knowledge Base / Documents]
```

_[Adapt this diagram or replace with a Mermaid diagram]_

---

## 2. Trust Boundaries

| Boundary | Components Inside | Components Outside | Crossing Controls |
|----------|------------------|--------------------|-------------------|
| User input boundary | Input validator, prompt builder | User/client | Authentication, input screening |
| Model execution boundary | Model runtime, inference engine | Tools, plugins, external APIs | Sandboxing, output validation |
| Data storage boundary | Vector store, training data store | External data sources | Access control, integrity verification |
| Agent action boundary | Agent runtime | External systems (email, APIs, filesystems) | Approval gates, least-privilege tools |
| Infrastructure boundary | AI workloads | Shared cloud infrastructure | Isolation, network policies |

---

## 3. Threat Catalogue

For each threat, identify:
- **AISVS Controls** that mitigate it
- **Current Status**: ✅ Mitigated | ⚠️ Partially Mitigated | ❌ Not Mitigated | N/A

### 3.1 Training Phase Threats

| ID | Threat | MITRE ATLAS | AISVS Controls | Status | Notes |
|----|--------|-------------|----------------|--------|-------|
| T01 | Training data poisoning | AML.T0020 | C1.3.1, C1.3.4 | | |
| T02 | Clean-label poisoning | AML.T0020 | C1.3.5 | | |
| T03 | Data supply chain compromise | AML.T0010 | C1.1.2, C6.1.1, C6.1.2 | | |
| T04 | Labeling platform compromise | — | C1.2.1, C1.2.2 | | |
| T05 | Model artifact tampering | AML.T0018 | C3.1.2, C3.1.3, C6.1.3 | | |
| T06 | Fine-tuning backdoor injection | AML.T0018 | C3.5.1, C3.5.3 | | |

### 3.2 Inference Phase Threats

| ID | Threat | MITRE ATLAS | AISVS Controls | Status | Notes |
|----|--------|-------------|----------------|--------|-------|
| T07 | Direct prompt injection | AML.T0051 | C2.1.3, C2.1.6, C12.2.1 | | |
| T08 | Indirect prompt injection (RAG) | AML.T0051 | C8.2.3, C8.2.4, C10.4.2 | | |
| T09 | Jailbreak / policy bypass | — | C2.1.8, C11.1.1, C11.1.2 | | |
| T10 | System prompt extraction | — | C7.3.2, C12.2.3 | | |
| T11 | Sensitive data disclosure in output | — | C7.3.2, C5.2.4, C11.2.1 | | |
| T12 | Hallucination exploitation | — | C7.2.1, C7.4.3 | | |
| T13 | Multi-modal adversarial attack | AML.T0015 | C2.2.3, C2.2.4, C11.1.3 | | |

### 3.3 Model Extraction and Inversion Threats

| ID | Threat | MITRE ATLAS | AISVS Controls | Status | Notes |
|----|--------|-------------|----------------|--------|-------|
| T14 | Model extraction via API queries | AML.T0024 | C11.2.2, C11.3.1, C11.3.2 | | |
| T15 | Membership inference attack | AML.T0024 | C11.2.2, C11.2.4, C11.2.5 | | |
| T16 | Model inversion / attribute inference | — | C11.2.1, C11.2.3 | | |

### 3.4 Agentic Threats

| ID | Threat | MITRE ATLAS | AISVS Controls | Status | Notes |
|----|--------|-------------|----------------|--------|-------|
| T17 | Excessive agent autonomy / over-reach | — | C9.1.1, C9.1.2, C9.2.1 | | |
| T18 | Agent taking irreversible actions | — | C9.2.1, C9.2.3, C9.2.4 | | |
| T19 | Agent credential exposure | — | C9.5.4 | | |
| T20 | Inter-agent privilege escalation | — | C9.5.5, C9.4.1 | | |
| T21 | Tool sandbox escape | — | C9.3.1, C9.3.4 | | |
| T22 | Agent self-modification | — | C9.2.5 | | |

### 3.5 Infrastructure and Supply Chain Threats

| ID | Threat | MITRE ATLAS | AISVS Controls | Status | Notes |
|----|--------|-------------|----------------|--------|-------|
| T23 | Model artifact supply chain compromise | AML.T0010 | C6.1.1, C6.1.2, C6.1.3 | | |
| T24 | Cross-tenant inference cache leakage | — | C5.3.1, C5.3.2, C8.1.1 | | |
| T25 | RAG vector store poisoning | AML.T0070 | C8.2.2, C8.2.4 | | |
| T26 | MCP tool injection | — | C10.4.2, C10.2.5 | | |
| T27 | GPU side-channel / memory leakage | — | C4.2.4, C5.3.2 | | |
| T28 | Edge model extraction from device | — | C4.3.4, C4.3.5 | | |

---

## 4. Risk Register

| Threat ID | Likelihood (1-5) | Impact (1-5) | Risk Score | Accepted? | Mitigation Owner | Due Date |
|-----------|-----------------|--------------|------------|-----------|-----------------|----------|
| T07 | | | | | | |
| T09 | | | | | | |
| T14 | | | | | | |
| _[continue]_ | | | | | | |

**Risk scoring:** Risk Score = Likelihood × Impact  
**Thresholds:** Critical ≥ 20 | High 12–19 | Medium 6–11 | Low 1–5

---

## 5. Residual Risk

List threats that are accepted or partially mitigated with known residual risk:

| Threat | Residual Risk | Justification | Risk Owner |
|--------|--------------|---------------|------------|
| | | | |

---

## 6. Threat Model Review History

| Date | Change | Trigger | Reviewer |
|------|--------|---------|----------|
| | Initial threat model | New system | |
| | | | |
