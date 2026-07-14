# C1 — Training Data Integrity & Traceability: Architecture Prompts

> AISVS Reference: C1.1–C1.3 | Controls: 1.1.1–1.3.5

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C1-ARCH-01: Implement Training Data Inventory

**Objective**
- You are designing a training data management system for an AI/ML pipeline.

**Required Controls**
- Apply AISVS C1.1.2.

**Execution Steps**
- Create a data inventory that records for each training dataset:
- Source origin (URL, database, partner name)
- Responsible party (team or person)
- License type and constraints
- Collection method (scraped, licensed, synthetic, crowdsourced)
- Intended use constraints
- Processing history (transformations applied, dates, tooling)
- Ensure the inventory is version-controlled and queryable.
- Implement an API to register new datasets and query provenance.
- Store the inventory in a tamper-evident format.
- Output: schema definition + registration API implementation.

**Expected Artifacts**
- schema definition + registration API implementation.

**Pass/Fail Rule**
- Mark PASS only when all required controls in scope are satisfied with evidence; otherwise mark FAIL and provide remediation.

**Source Prompt**
```text
You are designing a training data management system for an AI/ML pipeline.
Apply AISVS C1.1.2.

Requirements:
- Create a data inventory that records for each training dataset:
  - Source origin (URL, database, partner name)
  - Responsible party (team or person)
  - License type and constraints
  - Collection method (scraped, licensed, synthetic, crowdsourced)
  - Intended use constraints
  - Processing history (transformations applied, dates, tooling)
- Ensure the inventory is version-controlled and queryable.
- Implement an API to register new datasets and query provenance.
- Store the inventory in a tamper-evident format.

Output: schema definition + registration API implementation.
```

