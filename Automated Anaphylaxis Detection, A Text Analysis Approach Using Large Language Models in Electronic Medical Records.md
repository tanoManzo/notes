
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

Prompts are textual inputs or queries users provide to guide the responses or outputs of an LLM. They act as the initial command based on which the LLM generates its response. The design of the prompt is crucial, as it sets the context and direction for the model’s output. Effective prompting involves clearly and specifically articulating what is being asked or required so the model can accurately interpret and respond to the request.

This approach involves crafting precise, domain-specific instructions that guide the LLM in its task, ensuring that it remains focused on the relevant aspects of the medical text.

In our study, that involves several steps: 
• Initial Prompt Drafting: Preliminary prompts were formulated to encapsulate the criteria. These prompts were structured to guide the LLMs in analyzing medical texts and determining the presence or absence of indicators suggestive of anaphylaxis. 
• Iterative Refinement: The initial prompts were tested on a subset of the medical texts. Based on the LLMs’ responses and feedback from the experts in anaphylaxis, the prompts underwent iterations of refinement to enhance clarity and specificity (aligned with the WAO criteria). 
• Finalization: The finalized prompts were then employed to guide the LLMs in analyzing the entire dataset of medical texts.


In the finalized prompt, we explicitly instructed the LLM to: 
1. Suggest an anaphylaxis diagnosis (true or false); 
2. Name a probable allergen; 
3. Describe the reasons for their recommendation (citing passages from the medical texts); 
4. Provide a probability that the case was anaphylaxis (as a measure of their confidence); 
5. Explain their reasoning process step-by-step, indicating which criteria it used and why.

Issue: example of prompt missing, same prompt different results. 

One known drawback of LLMs is hallucinations. They refer to instances where the model generates incorrect, misleading, or nonsensical information presented as factual or logical [22]. Our experiments only consider whether or not the LLM recognizes an anaphylaxis case. 

Issue: 
If the LLM hallucinates and returns a wrong answer, it will be counted as a false positive or negative.
Issue:
Configuration??

## Experiments Setup
Besides allowing experiment automation, which is indispensable as we have almost 1000 texts, it also gives us much better control of the LLM parameters.


Issue:
In all experiments, we used the temperature equal to zero.


Issue: 
Configuration two uses the results from configuration one and confirms the positive cases using GPT 4. This choice was due to the high price of using GPT 4 in all texts.


Issue: 
In addition to these values, Cohen’s Kappa was used to evaluate the agreement between the program’s predictions and medical diagnostic evaluations [24]


## Results

Issue: which configuration
• For GPT 3.5 + 4 configuration, precision went from 81.0% to 84.2% and Kappa from 0.88


. Most of these texts should be easier to classify as they do not discuss anything related to anaphylaxis and could introduce a bias (some did have allergy cases but not anaphylaxis ones). In the best configuration results, using GPT 4 Turbo, precision and sensibility remained the same. Specificity went from 99.5% to 90.2%, and accuracy from 99.5% to 95% — still outstanding results. Kappa went down from 0.95 to 0.90, which still is an almost perfect agreement. The SinClimBr texts had a small effect on the overall results.

Issue: Missing analysis section


Issue: Results for two program runs for four model configurations on different days. There were not many changes.