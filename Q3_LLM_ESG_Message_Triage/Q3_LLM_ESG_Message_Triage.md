# Q3 LLM ESG Message Triage Experiment Log

## Scenario

The organisation receives ESG-related operational messages through email, service portals and internal chat channels. The prototype uses an LLM to classify each message by category, urgency, sentiment, follow-up need, recommended team, escalation reason, sensitivity risk and human review requirement.

## Revised Prompt Template

```text
You are supporting an ESG operations desk. Classify the employee message using only the details provided. Do not assume missing facts. Return valid JSON only.

Allowed issue_category values:
ENERGY_USE, WATER_LEAK, WASTE_RECYCLING, SUPPLIER_RISK, ACCESSIBILITY, GOVERNANCE_CONDUCT, GENERAL_QUERY.

Urgency rules:
CRITICAL = immediate danger, blocked access, legal/compliance emergency or major disruption.
HIGH = issue has continued for several hours/days or requires urgent operational action.
MEDIUM = requires follow-up but no immediate danger is stated.
LOW = advice request or minor non-urgent issue.

Return this JSON structure:
{
  "issue_category": "",
  "urgency": "",
  "sentiment": "",
  "followup_required": "",
  "recommended_team": "",
  "escalation_reason": "",
  "data_sensitivity_risk": "",
  "brief_summary": "",
  "confidence_score": "",
  "missing_information": [],
  "human_review_required": ""
}

Message: <insert employee message>
```

## Prompt Enhancement Rationale

| Enhancement | Reason introduced |
|---|---|
| Controlled category list | Reduces inconsistent labels and improves workflow routing. |
| Urgency definitions | Makes triage decisions more consistent and auditable. |
| JSON-only instruction | Allows automated validation and downstream processing. |
| Missing information field | Reduces hallucination by requiring the model to identify absent facts. |
| Confidence score | Supports human review thresholds. |
| Human review flag | Ensures sensitive or high-risk cases are not fully automated. |
| Data sensitivity risk | Helps identify privacy, governance and compliance concerns. |

## Structured Output Validation

The output should be checked before any ticket is created. Validation rules:

- JSON must parse successfully.
- All required fields must be present.
- `issue_category` must match the approved category list.
- `urgency` must be LOW, MEDIUM, HIGH or CRITICAL.
- `followup_required` must be Y or N.
- `confidence_score` must be between 0 and 1.
- HIGH, CRITICAL, ACCESSIBILITY, SUPPLIER_RISK and GOVERNANCE_CONDUCT cases should trigger human review.

## LLM Test Outputs

### Test 1: Energy use message

**Message:** The air conditioning is running overnight in an empty office.

```json
{
  "issue_category": "ENERGY_USE",
  "urgency": "MEDIUM",
  "sentiment": "NEGATIVE",
  "followup_required": "Y",
  "recommended_team": "Facilities Management",
  "escalation_reason": "The message reports after-hours air conditioning use in an empty office, which indicates avoidable energy waste and requires operational follow-up.",
  "data_sensitivity_risk": "LOW",
  "brief_summary": "Air conditioning is running overnight in an empty office.",
  "confidence_score": "0.93",
  "missing_information": [
    "building name",
    "floor or room number",
    "how many nights this has occurred"
  ],
  "human_review_required": "N"
}
```

### Test 2: Accessibility message

**Message:** The accessible entrance near the main building has been blocked for two days.

```json
{
  "issue_category": "ACCESSIBILITY",
  "urgency": "HIGH",
  "sentiment": "NEGATIVE",
  "followup_required": "Y",
  "recommended_team": "Facilities Management and Accessibility Support",
  "escalation_reason": "The message reports a blocked accessible entrance for two days, creating an inclusion, access and potential compliance issue that requires urgent follow-up.",
  "data_sensitivity_risk": "MEDIUM",
  "brief_summary": "Accessible entrance near the main building has been blocked for two days.",
  "confidence_score": "0.97",
  "missing_information": [
    "exact entrance location",
    "cause of the blockage",
    "whether an alternative accessible route is available"
  ],
  "human_review_required": "Y"
}
```

### Test 3: Supplier risk message

**Message:** I think one of our suppliers may not meet our sustainability policy.

```json
{
  "issue_category": "SUPPLIER_RISK",
  "urgency": "MEDIUM",
  "sentiment": "NEUTRAL",
  "followup_required": "Y",
  "recommended_team": "Procurement and Sustainability Governance",
  "escalation_reason": "The message raises a possible supplier sustainability policy concern that requires review, but no immediate danger or confirmed compliance breach is stated.",
  "data_sensitivity_risk": "MEDIUM",
  "brief_summary": "Employee reports a possible supplier sustainability policy concern.",
  "confidence_score": "0.86",
  "missing_information": [
    "supplier name",
    "specific sustainability policy requirement",
    "evidence or reason for concern",
    "whether procurement activity is currently pending"
  ],
  "human_review_required": "Y"
}
```

## Rule-Based Baseline

The baseline uses keyword matching.

| Keywords | Category | Urgency |
|---|---|---|
| air conditioning, overnight, empty office | ENERGY_USE | MEDIUM |
| accessible entrance, blocked, two days | ACCESSIBILITY | HIGH |
| supplier, sustainability policy | SUPPLIER_RISK | LOW or MEDIUM |
| leak, water, all morning | WATER_LEAK | HIGH |
| recycling, bins, contaminated | WASTE_RECYCLING | MEDIUM |

## Baseline Comparison

| Message | LLM result | Rule-based baseline | Evaluation |
|---|---|---|---|
| Air conditioning running overnight | ENERGY_USE / MEDIUM | ENERGY_USE / MEDIUM | Consistent result. |
| Accessible entrance blocked two days | ACCESSIBILITY / HIGH | ACCESSIBILITY / HIGH | Consistent and appropriate escalation. |
| Supplier may not meet sustainability policy | SUPPLIER_RISK / MEDIUM | SUPPLIER_RISK / LOW | LLM better recognised governance risk. |

## Error and Bias Analysis

The LLM produced richer explanations than the baseline because it identified escalation reasons, missing information and sensitivity risk. However, it may over-escalate emotionally worded messages. For example, the message "the office is freezing again" might be classified as HIGH by the LLM if it interprets the wording as serious, while a rule-based baseline may classify it as ENERGY_USE / MEDIUM unless danger or duration is stated.

Bias may occur because messages written in urgent or emotional language may receive higher priority than short but serious messages. Accessibility and supplier-risk cases also require care because under-classification can affect inclusion, compliance and governance outcomes. For this reason, ACCESSIBILITY, SUPPLIER_RISK and GOVERNANCE_CONDUCT outputs should always be reviewed by a human.

## Readiness Recommendation

The approach is suitable for a controlled pilot, not immediate production. Required improvements:

- Confidence thresholds, with results below 0.80 sent to human review.
- JSON schema validation before ticket creation.
- Human-in-the-loop workflow for high-risk categories.
- Monitoring of false positives, false negatives and category drift.
- Audit logs for prompt version, model output and final human decision.
- Privacy filtering to avoid unnecessary personal data retention.
