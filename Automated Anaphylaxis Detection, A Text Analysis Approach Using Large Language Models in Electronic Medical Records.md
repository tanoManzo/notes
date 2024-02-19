
**Goal:** Detect potential anaphylaxis cases from Electronic Medical Records (EMRs) texts.

**Material and Methods:** GPT 3.5, 4, and 4-turbo, anaphylaxis-positive (48) or -negative (921). Two prompts:  to simulate a general practitioner’s role in reviewing medical narratives for anaphylaxis detection and to incorporate the World Allergy Organization (WAO) criteria into its instructions.

**Conclusion:** The results underscore the great potential of LLMs to support healthcare professionals by automating the identification of anaphylaxis diagnoses to improve patient safety and care.

## Intro

The World Allergy Organization (WAO) diagnostic criteria detail two primary clinical indicators: (1) the presence of typical skin symptoms accompanied by significant symptoms from at least one other organ system, and (2) the patient’s exposure to a known or probable allergen, leading to respiratory and/or cardiovascular impairment [4]. It often leads to symptoms being recorded in medical reports. Still, the diagnoses not being registered correctly, or not being registered at all, in structured form in Electronic Medical Records (EMRs).

This potential lack of structured documentation unveils a significant gap and an opportunity for leveraging automated systems, such as Large Language Models (LLMs), to bolster the timely identification and documentation of anaphylaxis, thereby contributing to enhanced patient safety and optimized care delivery [8].