# AISVS Security Assessment Report

> **Standard:** OWASP AI Security Verification Standard (AISVS) v1.0
> **Report Template Version:** 1.0

---

## Report Metadata

| Field | Value |
|-------|-------|
| **System Name** | |
| **System Version** | |
| **Assessment Date** | |
| **Assessment Type** | ☐ Self-Assessment  ☐ Internal Review  ☐ Third-Party Assessment |
| **AISVS Level Assessed** | ☐ L1  ☐ L1+L2  ☐ L1+L2+L3 |
| **Lead Assessor** | |
| **Review Status** | ☐ Draft  ☐ Final |
| **Classification** | ☐ Public  ☐ Internal  ☐ Confidential |

---

## 1. Executive Summary

### 1.1 Assessment Scope

Describe the AI system assessed, including:
- System description and business purpose
- AI components in scope (inference APIs, training pipelines, RAG system, agentic workflows, MCP integrations)
- AI components out of scope and rationale
- Assessment method (automated testing, code review, configuration review, interview)

_[Write here]_

### 1.2 Overall Result

| Level | Controls Assessed | Pass | Fail | Partial | N/A |
|-------|------------------|------|------|---------|-----|
| L1 | | | | | |
| L2 | | | | | |
| L3 | | | | | |

**Overall Verdict:** ☐ PASS  ☐ CONDITIONAL PASS (remediation required)  ☐ FAIL

### 1.3 Key Findings Summary

| Severity | Count | Most Critical Finding |
|----------|-------|-----------------------|
| Critical | | |
| High | | |
| Medium | | |
| Low | | |
| Informational | | |

### 1.4 Critical Gaps

List the most important gaps requiring immediate remediation:

1. _[Gap 1]_
2. _[Gap 2]_
3. _[Gap 3]_

---

## 2. Findings by Control Family

For each finding, use the format below.

**Finding template:**

```
### Finding ID: [CONTROL_ID]-[NNNN]

**Control:** [AISVS control ID, e.g., C2.1.3]
**Title:** [Short description]
**Severity:** Critical | High | Medium | Low | Informational
**Status:** FAIL | PARTIAL

**Description:**
[Detailed description of the gap or weakness found]

**Evidence:**
[Evidence collected: log samples, configuration excerpts, test results, screenshots]

**Risk:**
[What can an attacker or adversary do by exploiting this gap?]

**Remediation:**
[Specific, actionable steps to remediate]

**Remediation Priority:** Immediate | Short-term (30 days) | Medium-term (90 days)
```

---

### C1 — Training Data Integrity & Traceability

_[Insert findings or "No findings" if all controls passed]_

---

### C2 — Input Validation

_[Insert findings or "No findings"]_

---

### C3 — Model Lifecycle Management

_[Insert findings or "No findings"]_

---

### C4 — Infrastructure & Deployment Security

_[Insert findings or "No findings"]_

---

### C5 — Access Control & Identity

_[Insert findings or "No findings"]_

---

### C6 — Supply Chain Security

_[Insert findings or "No findings"]_

---

### C7 — Model Behavior & Output Control

_[Insert findings or "No findings"]_

---

### C8 — Memory, Embeddings & Vector Database

_[Insert findings or "No findings"]_

---

### C9 — Orchestration & Agentic Security

_[Insert findings or "No findings"]_

---

### C10 — MCP Security

_[Insert findings or "No findings"]_

---

### C11 — Adversarial Robustness

_[Insert findings or "No findings"]_

---

### C12 — Monitoring, Logging & Anomaly Detection

_[Insert findings or "No findings"]_

---

## 3. Remediation Roadmap

| Priority | Finding ID | Control | Title | Owner | Target Date | Status |
|----------|-----------|---------|-------|-------|-------------|--------|
| Immediate | | | | | | |
| Short-term | | | | | | |
| Medium-term | | | | | | |

---

## 4. Detailed Control Results

_Link to or embed the completed `AISVS-checklist.md` for this assessment._

---

## 5. Methodology

### 5.1 Test Approach
- **Code Review:** Static analysis of AI pipeline code, configuration, and infrastructure definitions.
- **Dynamic Testing:** Live testing of the AI system's inputs, outputs, and behavioral controls.
- **Configuration Review:** Review of deployment configuration, IAM policies, and security controls.
- **Interview:** Structured interviews with development and operations teams.

### 5.2 Tools Used

| Tool | Purpose | Version |
|------|---------|---------|
| | | |

### 5.3 Limitations
- _[List any limitations that affected the completeness of the assessment]_

---

## 6. Attestation

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Lead Assessor | | | |
| System Owner | | | |
| Security Lead | | | |

---

## Appendix A: AISVS Reference

Full control inventory: [`REQUIREMENTS.md`](../REQUIREMENTS.md)

## Appendix B: Evidence Index

| Evidence ID | Description | Location | Collected By | Date |
|-------------|-------------|----------|--------------|------|
| | | | | |
