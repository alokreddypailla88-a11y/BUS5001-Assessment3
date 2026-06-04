# Hugging Face Baseline Results
## Model: facebook/bart-large-mnli
## Zero-Shot Classification

### Message 1
Text: The air conditioning is running overnight in an empty office.
Results:
- Wellbeing: 0.531
- Accessibility: 0.507
- Energy: 0.235
- Governance: 0.119
- Procurement: 0.045
- Waste: 0.024
- Water: 0.000
LLM Classification: ENERGY
Agreement: NO - baseline incorrectly classified as Wellbeing

### Message 2
Text: I want to report that one of our suppliers may not meet our sustainability policy.
Results:
- Procurement: 0.636
- Water: 0.349
- Energy: 0.346
- Waste: 0.199
- Governance: 0.188
- Wellbeing: 0.178
- Accessibility: 0.008
LLM Classification: PROCUREMENT
Agreement: YES

### Message 3
Text: The accessible entrance near the main building has been blocked for two days.
Results:
- Accessibility: 0.983
- Governance: 0.534
- Wellbeing: 0.526
- Energy: 0.471
- Procurement: 0.403
- Water: 0.160
- Waste: 0.080
LLM Classification: ACCESSIBILITY
Agreement: YES - strong agreement (0.983)
