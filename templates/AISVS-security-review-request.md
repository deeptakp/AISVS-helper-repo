# AISVS Security Review Request

> Use this template to request a security review of an AI system or AI-related feature.

---

## Request Metadata

| Field | Value |
|-------|-------|
| **Request ID** | SR-[YYYY]-[NNNN] |
| **Requested By** | |
| **Team / Product** | |
| **Date Submitted** | |
| **Target Review Date** | |
| **Priority** | ☐ Critical (blocking release)  ☐ High  ☐ Medium  ☐ Low |

---

## 1. System / Feature Description

### 1.1 What Is Being Reviewed?

_Describe the AI system, feature, or change that requires a security review:_

_[Write here]_

### 1.2 Review Trigger

☐ New AI system or feature being built  
☐ Significant change to an existing AI system  
☐ New AI model, provider, or version being adopted  
☐ New MCP server or tool integration  
☐ Regulatory or compliance requirement  
☐ Incident response or post-incident review  
☐ Periodic scheduled review  
☐ Other: _________________________

### 1.3 Desired AISVS Level

☐ L1 (Baseline — minimal viable security)  
☐ L1 + L2 (Standard — production system with sensitive data)  
☐ L1 + L2 + L3 (Advanced — high-assurance or regulated system)

---

## 2. System Information

### 2.1 AI Components

| Component | Type | Provider / Source | Version | In Scope? |
|-----------|------|-------------------|---------|-----------|
| | | | | ☐ |
| | | | | ☐ |
| | | | | ☐ |

### 2.2 Data Classification

What is the most sensitive data processed by this AI system?

☐ Public data only  
☐ Internal / confidential data  
☐ Personal data (PII)  
☐ Special category personal data (health, financial, etc.)  
☐ Regulated data (HIPAA, GDPR, PCI, etc.)  
☐ Classified / government data  

### 2.3 Deployment Context

☐ Cloud (SaaS / hosted)  
☐ On-premise  
☐ Edge / embedded  
☐ Mobile  
☐ Hybrid  

Deployment regions: _____________________

### 2.4 User Base

Who are the users / callers of this AI system?

☐ Internal employees only  
☐ Authenticated external users  
☐ Unauthenticated public users  
☐ Other AI agents / automated systems  
☐ Mixed: _____________________

---

## 3. AISVS Focus Areas

Check the control families most relevant to this review:

☐ **C1** — Training Data Integrity (new training pipeline, new dataset, new fine-tune)  
☐ **C2** — Input Validation (new model interface, new input type, new prompt construction)  
☐ **C3** — Model Lifecycle (new model version, new deployment pipeline, rollback capability)  
☐ **C4** — Infrastructure (new compute environment, edge deployment, TEE)  
☐ **C5** — Access Control (new RAG system, new data classification, multi-tenant)  
☐ **C6** — Supply Chain (new third-party model, new adapter, new framework)  
☐ **C7** — Model Behavior (new output types, new RAG integration, hallucination risk)  
☐ **C8** — Memory/Embeddings (new vector store, new memory architecture)  
☐ **C9** — Agentic Security (new autonomous agent, new tool integration, multi-agent)  
☐ **C10** — MCP Security (new MCP server or client integration)  
☐ **C11** — Adversarial Robustness (new attack surface, adversarial input risk)  
☐ **C12** — Monitoring/Logging (new AI component requiring observability)  

---

## 4. Supporting Materials

Please attach or link:

| Material | Location / Link | Available? |
|----------|----------------|-----------|
| Architecture diagram | | ☐ |
| Threat model | | ☐ |
| Data flow diagram | | ☐ |
| API specification | | ☐ |
| Source code repository | | ☐ |
| Infrastructure configuration (IaC) | | ☐ |
| Previous security review (if any) | | ☐ |
| AI BOM | | ☐ |

---

## 5. Known Risks / Open Questions

Describe any risks you are already aware of, or security questions you want the review to answer:

_[Write here]_

---

## 6. Review Constraints

| Constraint | Detail |
|-----------|--------|
| **Release deadline** | |
| **Access restrictions** | (e.g., no access to production data) |
| **Compliance deadlines** | |
| **Other constraints** | |

---

## 7. Sign-Off

| Role | Name | Date |
|------|------|------|
| Requesting Engineer / Architect | | |
| Product / Engineering Manager | | |

---

## For Security Team Use Only

| Field | Value |
|-------|-------|
| **Assigned Reviewer** | |
| **Accepted Date** | |
| **Estimated Effort** | |
| **Review Report Link** | |
| **Final Status** | ☐ PASS  ☐ CONDITIONAL PASS  ☐ FAIL  ☐ WITHDRAWN |
