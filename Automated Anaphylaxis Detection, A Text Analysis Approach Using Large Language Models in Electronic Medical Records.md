
**Goal:** Detect potential anaphylaxis cases from Electronic Medical Records (EMRs) texts.

**Material and Methods:** GPT 3.5, 4, and 4-turbo, anaphylaxis-positive (48) or -negative (921). Two prompts:  to simulate a general practitioner’s role in reviewing medical narratives for anaphylaxis detection and to incorporate the World Allergy Organization (WAO) criteria into its instructions.

**Conclusion:** The results underscore the great potential of LLMs to support healthcare professionals by automating the identification of anaphylaxis diagnoses to improve patient safety and care.

## Intro

The World Allergy Organization (WAO) diagnostic criteria detail two primary clinical indicators: (1) the presence of typical skin symptoms accompanied by significant symptoms from at least one other organ system, and (2) the patient’s exposure to a known or probable allergen, leading to respiratory and/or cardiovascular impairment [4]. It often leads to symptoms being recorded in medical reports. Still, the diagnoses not being registered correctly, or not being registered at all, in structured form in Electronic Medical Records (EMRs).

This potential lack of structured documentation unveils a significant gap and an opportunity for leveraging automated systems, such as Large Language Models (LLMs), to bolster the timely identification and documentation of anaphylaxis, thereby contributing to enhanced patient safety and optimized care delivery [8].

The primary aim of this study is to explore and validate the efficacy of LLMs in autonomously identifying and recommending diagnoses of anaphylaxis from the textual data encapsulated within EMRs. We specifically target those instances where the diagnosis of anaphylaxis may be evident or inferable from the narrative text but remains undocumented in the EMR’s structured data. By addressing this gap, our research seeks to mitigate the risk of overlooking anaphylaxis, thereby reducing the potential for severe complications or fatalities associated with delayed or missed diagnoses.

## MATERIALS AND METHODS

The texts were categorized into distinct groups to facilitate a structured analysis:

• Anonymized Anaphylaxis Cases (35 texts): Texts known to have a confirmed diagnosis of anaphylaxis derived from anonymized patient data. 

• Literature Cases (29 texts): Texts from the literature (13 with a confirmed diagnosis of anaphylaxis and 16 that are not anaphylaxis). 

• Differential Diagnosis Cases (35 texts): These are cases particularly challenging to diagnose as they could present clinically with symptoms similar to anaphylaxis. Ten cases were adapted from the literature, and 25 were from patient data, all with final diagnoses other than anaphylaxis. 

• SemClinBR Cases (870 texts): Medical texts from SemClinBR, a corpus of annotated clinical narratives about various clinical conditions. None of them were suspicious of anaphylaxis. For a better understanding, we consider the texts where anaphylaxis diagnoses were confirmed as “positive” and texts with other diagnoses as “negative.”


The decision to opt for a 5% rate of positive cases was made to mimic real-world prevalence estimates, which can reach up to 5% [4]. It aims to ensure that the method maintains a low false positive rate if applied to actual medical texts, thereby preventing users from being overwhelmed with incorrect cases.


### LLM Selection and Configuration

The LLMs selected for this study were OpenAi’s GPT 3.5, 4, and 4 Turbo, chosen due to their novelty, widespread use, and demonstrated ability to generate coherent and contextually relevant text.