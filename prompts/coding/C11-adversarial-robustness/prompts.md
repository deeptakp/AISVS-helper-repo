# C11 — Adversarial Robustness: Prompts

> AISVS Reference: C11.1–C11.4 | Controls: 11.1.1–11.4.3

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C11-CODE-02: Implement Rate Limiting and Output Calibration for Extraction Defense

**Objective**
- You are implementing extraction defense controls for an AI inference API.

**Required Controls**
- Apply AISVS C11.2.1, C11.2.2, C11.3.1, and C11.3.2.

**Execution Steps**
- Enforce per-principal rate limits sized to the extraction threat model:
- Rate limits must be based on the sensitivity of information accessible to the model,
- not just generic API throttling.
- Implement: per-user rate limit, per-IP rate limit, global rate limit (configurable per endpoint).
- Return HTTP 429 with Retry-After when limits are exceeded.
- Calibrate model outputs to prevent over-confidence:
- Do not return raw logits or probability scores to external callers.
- Quantize or bin confidence scores before exposing them in the API response.
- Where possible, use top-k filtering to avoid revealing the full probability distribution.
- Implement query-pattern analysis feeding an extraction-attempt detector:
- Flag: high-volume low-variance queries, systematic probing of token probabilities, membership inference patterns.
- Alert security monitoring on extraction attempt detection.
- (L3) Trigger response measures on confirmed extraction attempt (rate-limit escalation, session block).
- Output: ExtractionDefenseMiddleware with per-principal rate limits + output calibration + query-pattern analysis.

**Expected Artifacts**
- ExtractionDefenseMiddleware with per-principal rate limits + output calibration + query-pattern analysis.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing extraction defense controls for an AI inference API.
Apply AISVS C11.2.1, C11.2.2, C11.3.1, and C11.3.2.

Requirements:
- Enforce per-principal rate limits sized to the extraction threat model:
  - Rate limits must be based on the sensitivity of information accessible to the model,
    not just generic API throttling.
  - Implement: per-user rate limit, per-IP rate limit, global rate limit (configurable per endpoint).
  - Return HTTP 429 with Retry-After when limits are exceeded.
- Calibrate model outputs to prevent over-confidence:
  - Do not return raw logits or probability scores to external callers.
  - Quantize or bin confidence scores before exposing them in the API response.
  - Where possible, use top-k filtering to avoid revealing the full probability distribution.
- Implement query-pattern analysis feeding an extraction-attempt detector:
  - Flag: high-volume low-variance queries, systematic probing of token probabilities, membership inference patterns.
  - Alert security monitoring on extraction attempt detection.
  - (L3) Trigger response measures on confirmed extraction attempt (rate-limit escalation, session block).

Output: ExtractionDefenseMiddleware with per-principal rate limits + output calibration + query-pattern analysis.
```


### C11-CODE-03: Implement Adversarial Input Anomaly Detection

**Objective**
- You are implementing runtime anomaly detection for an AI inference endpoint.

**Required Controls**
- Apply AISVS C11.4.1 and C11.4.2.

**Execution Steps**
- Before model inference, run all inputs from external or untrusted sources through an anomaly detector:
- Statistical anomaly: detect inputs that are significantly out-of-distribution relative to the training corpus.
- Adversarial perturbation detection: detect inputs with adversarial noise patterns (L-infinity bounded perturbations).
- Semantic anomaly: detect inputs that are semantically inconsistent with the application's purpose.
- Inputs flagged as anomalous must trigger gating actions:
- Default: block the input and return a safe error response.
- Configurable: route to human review queue with input context.
- Log all anomaly detections with: input hash, anomaly type, confidence score, action taken, timestamp.
- (L3) Feed anomaly events to the safety violation feedback pipeline with human review gates to prevent
- adversarial manipulation of the feedback mechanism.
- Output: AdversarialInputDetector with out-of-distribution detection + perturbation detection + gating logic.

**Expected Artifacts**
- AdversarialInputDetector with out-of-distribution detection + perturbation detection + gating logic.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing runtime anomaly detection for an AI inference endpoint.
Apply AISVS C11.4.1 and C11.4.2.

Requirements:
- Before model inference, run all inputs from external or untrusted sources through an anomaly detector:
  - Statistical anomaly: detect inputs that are significantly out-of-distribution relative to the training corpus.
  - Adversarial perturbation detection: detect inputs with adversarial noise patterns (L-infinity bounded perturbations).
  - Semantic anomaly: detect inputs that are semantically inconsistent with the application's purpose.
- Inputs flagged as anomalous must trigger gating actions:
  - Default: block the input and return a safe error response.
  - Configurable: route to human review queue with input context.
- Log all anomaly detections with: input hash, anomaly type, confidence score, action taken, timestamp.
- (L3) Feed anomaly events to the safety violation feedback pipeline with human review gates to prevent
  adversarial manipulation of the feedback mechanism.

Output: AdversarialInputDetector with out-of-distribution detection + perturbation detection + gating logic.
```


---
