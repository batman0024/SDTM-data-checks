# Clinical Integrity Suite v8.1 – Regulatory-Grade Improvement Roadmap

This updated document incorporates **additional enhancements identified through FDA/PMDA-style reviewer critique**, extending the v8.0 roadmap toward a **regulatory-transparent, review-defensible clinical integrity platform**.

---

## 1. Explicit Protocol Linkage & Traceability (NEW)

### Improvement
Every configurable or assumption-based rule must be **explicitly traceable** to:
- Study Protocol
- SAP
- CDISC SDTMIG
- ICH E6 / E3 / E2A guidance

Introduce a **rule metadata block** per check:

```yaml
rule_id: AE015
rule_basis:
  type: ICH_E2A
  reference: "Safety reporting completeness"
  protocol_section: "6.2 Adverse Event Collection"
assumption_level: signal_only
```

### Regulatory Value
- Enables reviewer trust
- Supports inspection readiness
- Prevents perception of undocumented sponsor assumptions

---

## 2. Signal vs Violation Classification (NEW)

### Improvement
Introduce **regulatory-safe outcome classes**:

- _Violation_: Direct SDTM / protocol non-compliance
- _Signal_: Pattern requiring medical review
- _Inquiry_: Ambiguity due to partial/missing data

Example:
> Silent Grade 3 lab + no AE → **Safety Signal**, not Violation

### Regulatory Value
- Avoids over-interpretation of automated outputs
- Aligns with FDA/PMDA review philosophy

---

## 3. Severity Governance & Override Workflow (NEW)

### Improvement
Add controlled override capability:

- Sponsor justification field
- Medical monitor sign-off indicator
- Immutable audit trail

```yaml
override:
  approved_by: Medical Monitor
  date: 2026-03-30
  rationale: "Per protocol, AE collection not required for this lab"
```

### Regulatory Value
- Demonstrates human oversight
- Essential for inspection defense

---

## 4. Context-Aware Partial Date Framework (REFINED)

Differentiate **permitted uncertainty vs integrity risk**.

| Date Context | Regulatory Interpretation |
|-------------|---------------------------|
| AE dates | Acceptable uncertainty |
| RFICDTC | GCP-critical |
| RFSTDTC | GCP-critical |
| DTHDTC | High medical importance |

Partial dates should generate:
- Signal or Inquiry, not automatic violations

---

## 5. Subject-Level Narrative Reconstruction (ENHANCED)

### Improvement
Generate automated **subject narratives** summarizing:
- Consent → Treatment → Events → Disposition
- Highlight temporal inconsistencies inline

This narrative becomes:
- Inspectable artifact
- Reviewable by medical reviewers

---

## 6. Confidence & Dependency Disclosure (ENHANCED)

Every finding should disclose:

- Data completeness level
- Domains used
- Missing dependency impact

```yaml
confidence: Medium
missing_dependencies: [DS]
impact: "Disposition unavailable; interpretation limited"
```

---

## 7. Regulatory Mode Presets (NEW)

Introduce operational modes:

- FDA Safety Review Mode
- PMDA Compliance Mode
- Internal QC Mode

Each mode modifies:
- Severity threshold
- Signal vs violation labeling
- Output verbosity

---

## 8. Language Hardening for Regulatory Safety (NEW)

### Improvement
Standardize phrasing to avoid definitive claims:

Avoid:
- "Protocol violation detected"

Prefer:
- "Pattern inconsistent with protocol expectations; review recommended"

---

## 9. Validation & Governance Documentation (NEW)

### Improvement
Publish internal documentation covering:

- Rule development process
- Validation strategy
- Versioning and change control
- Intended use disclaimer

### Regulatory Value
- Required for inspection readiness
- Clarifies tool is decision-support, not decision-maker

---

## Summary

With these **v8.1 enhancements**, the Clinical Integrity Suite transitions from:

> _Advanced SDTM Validator_ → **Regulatory-Defensible Clinical Review Support System**

This positioning aligns with **FDA and PMDA expectations for transparency, explainability, and human oversight**, while preserving the system’s strong clinical insight.

---
