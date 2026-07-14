# C2 — Input Validation: Prompts

> AISVS Reference: C2.1–C2.2 | Controls: 2.1.1–2.2.4

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C2-CODE-02: Implement Instruction Hierarchy Enforcement

**Objective**
- You are implementing the prompt construction system for an LLM application.

**Required Controls**
- Apply AISVS C2.1.6 and C2.1.7.

**Execution Steps**
- Build a PromptBuilder that enforces a strict instruction hierarchy:
- System prompt (highest authority — developer-controlled)
- Tool/context injections (developer-controlled)
- User message (lowest authority — untrusted)
- The system prompt must be inserted in a tamper-resistant position that survives multi-turn conversations.
- Reserve special tokens (e.g., <|im_start|>, <|system|>, [INST], ###) — detect and reject any attempt
- to inject these tokens in user input.
- Include a validation step that checks the final assembled prompt for injection of control tokens before
- sending to the model.
- Output: PromptBuilder with hierarchy enforcement + special-token injection detection.

**Expected Artifacts**
- PromptBuilder with hierarchy enforcement + special-token injection detection.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing the prompt construction system for an LLM application.
Apply AISVS C2.1.6 and C2.1.7.

Requirements:
- Build a PromptBuilder that enforces a strict instruction hierarchy:
    1. System prompt (highest authority — developer-controlled)
    2. Tool/context injections (developer-controlled)
    3. User message (lowest authority — untrusted)
- The system prompt must be inserted in a tamper-resistant position that survives multi-turn conversations.
- Reserve special tokens (e.g., <|im_start|>, <|system|>, [INST], ###) — detect and reject any attempt
  to inject these tokens in user input.
- Include a validation step that checks the final assembled prompt for injection of control tokens before
  sending to the model.

Output: PromptBuilder with hierarchy enforcement + special-token injection detection.
```


### C2-CODE-03: Implement Content Policy Screening

**Objective**
- You are implementing pre-inference content screening for an LLM application.

**Required Controls**
- Apply AISVS C2.2.1 and C2.2.2.

**Execution Steps**
- Score every incoming prompt against a content policy classifier that detects:
- Violence and graphic content
- Self-harm and suicide
- Hate speech and discrimination
- Sexual content (including CSAM detection)
- Use configurable per-category thresholds. Block prompts that exceed any threshold.
- For prompts in languages not supported by the classifier, apply a conservative default policy
- (block or route to human review). Log the language detection result.
- Return a policy-violation response to the user that does not reveal classifier details.
- Log every block event with: input hash, classifier scores, category triggered, timestamp.
- Output: ContentPolicyScreener with classifier integration + language detection + logging.

**Expected Artifacts**
- ContentPolicyScreener with classifier integration + language detection + logging.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are implementing pre-inference content screening for an LLM application.
Apply AISVS C2.2.1 and C2.2.2.

Requirements:
- Score every incoming prompt against a content policy classifier that detects:
  - Violence and graphic content
  - Self-harm and suicide
  - Hate speech and discrimination
  - Sexual content (including CSAM detection)
- Use configurable per-category thresholds. Block prompts that exceed any threshold.
- For prompts in languages not supported by the classifier, apply a conservative default policy
  (block or route to human review). Log the language detection result.
- Return a policy-violation response to the user that does not reveal classifier details.
- Log every block event with: input hash, classifier scores, category triggered, timestamp.

Output: ContentPolicyScreener with classifier integration + language detection + logging.
```


---
