Health disparities refer to differences in health outcomes, disease prevalence, and access to healthcare resources among different demographic groups defined by factors including but not limited to gender, race, ethnicity, education, income, disability, or sexual orientation. 

Non-patient-specific factors contributing to differences in health outcomes include Social Determinants of Health ([[SDoH]]) and systemic racism and discrimination. The National Institutes of Health declared this challenge a top priority and created The National Institute on Minority Health and Health Disparities to focus solely on investigating and mitigating health disparities.

**_Traditional demographic labels do not capture the complexity and nuances of health disparities._**
Traditional labels associated with disparities include race/ethnicity, sex, socioeconomic status, geographic location, and limited English proficiency, among others. However, other social, economic, and environmental factors have been shown to have significant impacts on health disparities.

The groups affected by specific health disparities often lie at the intersection of traditional demographic labels, such as age, race-ethnicity, or English proficiency. It is imperative to develop new and more accurate methods for identifying and tracking health disparities beyond traditional demographic labels as a prerequisite to building fair models (Fig 2).

![[Pasted image 20230703150442.png]]

Community-level SDoH measures broad socioeconomic, neighborhood, and environmental characteristics such as unemployment rate, access to public transportation, and air pollution levels. They serve as “vital community signs'' that reflect complex societal factors and health disparities that influence one’s health. On the other hand, less is known about individual-level SDoH as access has been limited due to the lack of standardized and validated SDoH screening questions and privacy concerns.

In preliminary work, we have found use of these community-level SDoH significantly reduced confounding over traditional demographic labels for prediction of clinical outcomes after discharge from the ICU.


**Large Language Models (LLM) can be used to extract patient-level features from clinical notes**

Clinical notes written by healthcare providers are a rich source of detailed information about the patient’s clinical condition as well as clinical reasoning behind test and treatment choices, and context about their **living situation**. This information can provide insight into potential disparities in the care provided to individual patients and potential biases influencing these decisions.

**_Knowledge graphs can define complex interactions between the drivers of health disparities_**

Features associated with a given care disparity can be mapped against other disparities and SDoH to characterize sources and drivers of health inequity (Fig 3).

Identifying which groups of patients are affected by which disparity proxies, and categorizing these patients according to traditional demographic labels, community-level and individual-level SDoH will provide a more complete picture of the biases that exist in health data.

![[Pasted image 20230703151510.png]]

The proposed research is innovative for the following reasons:

1. A methodology to identify care disparities using a causal inference framework on a large EHR dataset and transform them into disparity proxies for mapping to SDoH.
2. Use of LLMs, with assistance from leaders in the field, to extract patient-level SDoH.
3. Development of a network analysis framework for mapping disparities in clinical care with SDoH to understand the complex interplay of sources and drivers of health data bias.
4. Engagement of community stakeholders and multidisciplinary teams through international Datathons to assist communities in applying these frameworks and tools to understand biases in their local health datasets.

**Aim 1:** **Utilize causal inference to identify disparity proxies within the ICU across traditional demographic labels (e.g., sex, race/ethnicity) as well as those not explained by such labels.**

Explore hidden sources and drivers of bias by identifying disparity proxies using causal inference (Fig 4).

![[Pasted image 20230703152749.png]]

We will look at common ICU interventions and investigate the ways care is not uniform across patient subgroups and that cannot be explained by clinical reasoning (Table 1).

![[Pasted image 20230703152859.png]]

**Aim 1a. Apply causal inference to uncover biases in MIMIC health data such as discrepancies in testing frequency, treatment likelihood, and medical device performance across patient sub-populations.**

Table 1 lists examples of common interventions performed in the ICU, along with possible metrics for each intervention that can be evaluated for variation in care that is not explained by clinical factors.

**Aim 1b. Leverage Datathons with a diverse team of researchers and patients to crowdsource the identification of disparity proxies across medical specialties, geographic regions, and health systems.**

Outcomes

We expect the following key outcomes for Aim 1:

1. The identification of disparity proxies in common ICU interventions.
2. The development of a framework for applying causal inference to identify hidden proxies.

Deliverables

1. Creation of disparity proxies of care with detailed methodologies on how they were identified and quantified or categorized.
2. Development of an open-sourced repository for codes, queries, derived tables, and their respective data dictionaries.
3. Peer-reviewed publications and conference presentations to disseminate our findings to the broader scientific and healthcare community.
4. National and international Datathons to engage the community and apply the causal inference framework to find disparity proxies within local datasets.

**Aim 2: Investigate how best to incorporate SDoH to improve performance of clinical algorithms.**

Clinical notes in EHRs are a rich source of patient care information including details about diagnosis, treatment, and medical decision making. These notes also capture information about an individual patient’s lifestyle, socioeconomic conditions, and environmental influences which impact health outcomes. With the advent of large language models (LLMs) such as BLOOM and GPT-4, this data resource can be mined to extract vital patient level features, opening new pathways to understand the drivers of diversity and sources of bias (Fig 6).

![[Pasted image 20230703153744.png]]


#research
#nlp
#sdoh
#paper
#nih
