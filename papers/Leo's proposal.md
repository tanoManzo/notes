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

The overall objective of Aim 2 is to utilize LLM to extract patient-level SDoH from clinical notes in the MIMIC database. By leveraging natural language processing (NLP) techniques, integrating diverse data sources, and debiasing LLMs, healthcare systems can improve their ability to tailor interventions, understand individual patient needs, and extract accurate and contextually appropriate recommendations and insights.

**Aim 2a. Leverage an open multilingual LLM (BLOOM) to extract patient-level SDoH features from clinical notes.** 

2a (ii) Train a tailored BLOOM model to extract information from clinical notes in the MIMIC database.

As a first step, Named Entity Recognition (NER) models can be trained to identify and categorize SDoH factors within medical reports, discharge summaries, and nursing notes. By learning patterns and features from annotated data, NER models can accurately recognize SDoH factors within the text, enabling the analysis of large volumes of clinical data and enhancing understanding of the impact of social determinants on patient health outcomes. Advanced techniques such as word embeddings or contextualized word representations —BERT (Bidirectional Encoder Representations from Transformers) or GPT (Generative Pre-trained Transformer) — can be employed to enhance the semantic understanding of the text, resulting in improved accuracy when identifying SDoH factors.70,71 Finally, medical ontologies such as SNOMED CT, UMLS, or disease-specific ontologies can be linked to corresponding SDoH factors. These techniques enable the models to grasp the nuanced relationships and context-specific implications of SDoH factors within the clinical notes.

2a (iii) Debias pretrained Large Language Models

A comprehensive bias detection analysis will be performed to identify and comprehend the biases associated with traditional patient demographic features. This analysis seeks to gain insights into the underlying biases present in the LLMs' responses and outputs. To mitigate these biases, a range of techniques will be applied:

1. Fine-tune the LLMs using additional training data explicitly addressing bias.

2. Modify the loss functions to penalize biased behavior within the LLMs.

3. Integrate SDoH features into the pre-trained LLMs. This integration allows the models to consider the broader context of SDoH during inference and guide the model's attention, ensuring that the LLMs attend to relevant contextual information related to SDoH.

**Aim 2b. Investigate the task-dependent value of SDoH indicators in clinical prediction and optimization models.**

1. Compare extracted features from the clinical notes using LLM with patient outcomes:
   
   Comparisons of patient severity and clinical severity scores and associations between patient clinical features, or phenotype, and SDoH will be made.

2. Analyze patient-level SDoH data at the population level:

	Analyzing patient-level SDoH factors extracted from the clinical notes against health outcomes, can identify population-level impact. One example of this is “What is the effect of being a caretaker for an ill family member on the presentation of chronic kidney disease in the ICU?” Data mining techniques, such as clustering, classification, and regression, can be applied to patient-level SDoH from the clinical notes to identify population segments based on shared SDoH characteristics. Classification predicts health outcomes based on SDoH factors, while regression models quantify the relationship between SDoH factors and health outcomes. These techniques enable targeted interventions and evidence-based decision-making in addressing health disparities associated with social and environmental factors. 

3. Evaluate extracted patient-level SDoH against care variation that is not explained by clinical features:

	Topic to vector or Topic2vec analysis will be conducted on extracted features alongside sentiment analysis as we have done previously with nursing notes in the neonatal intensive care unit described above. Topic2vec leverages an embedding methodology to learn topic representations in the same semantic vector space with words within the clinical notes. The resultant embedding will be explored for relationship with community-level SDoH, disparity proxies and clinical outcomes.

**Evaluation Plan**

Outcomes

Our evaluation plan will entail a thorough evaluation of all interventions using the existing "Fair Use" audit framework. This framework provides a systematic approach to assessing the utility and fairness of AI models. Our specific goal is to determine which interventions, denoted as "y," gain from the inclusion of demographic data, denoted as "x," as model inputs. As highlighted in our paper 19, the inclusion of such data does not guarantee model performance of clinical algorithms. Therefore, understanding which risk scores are advantaged by specific variables is crucial to enhance the fairness and effectiveness of our models.

The successful completion of this project will represent a significant step forward in using LLMs in healthcare and their application in improving patient outcomes through extracting SDoH from clinical notes. It will open new avenues for precision healthcare, enabling clinicians to tailor care based on individual patients' circumstances and needs. Furthermore, the availability of our models for reuse by other researchers will help promote further research in the field.

Deliverables
1. A fine-tuned BLOOM model that other researchers can reuse to extract information from MIMIC clinical notes.
2. Patient-level SDoH from the clinical notes.Comprehensive report detailing our findings, methodologies, and potential applications.
3. Peer-reviewed publications and conference presentations to disseminate our findings to the broader scientific and healthcare community.
4. International Datathons to fine tune further models pre-trained on MIMIC notes on unstructured data from other health datasets.

**Aim 3: Build a framework for mapping care disparities in health data using knowledge graphs and network analysis.**

The proxies of care disparity will serve as nodes and the “edges” between the “nodes” will indicate the homophily (relative to SDoH and traditional labels) in terms of affected patients by the disparity that the node represents.
![[Pasted image 20230703155230.png]]

**Aim 3a. Build a knowledge graph of disparity proxies (nodes, e.g., SaO2-SpO2 gap) that are linked by the traditional labels and SDoH to systematically map disparities across MIMIC-IV.**

![[Pasted image 20230703155416.png]]

Design and build a weighted multigraph of clinical disparities (Fig. 8). The **nodes** will be the previously identified disparity proxies, e.g.  degree of hidden hypoxemia or differences in the “volume” of ICU care, and new ones, detected in Aim 1. **Edges** will represent disparities that simultaneously affect the same patients (above a threshold of recurrence, to be learnt from the data). Different **Edge Types** will reflect different subgroups of patients in terms of traditional demographic labels and SDoH (e.g., for the same pair of nodes: one edge will tell how many Black patients share that disparity; another edge will tell how many Medicare patients share the disparity; etc.). **Weights** will be calibrated to represent the percentage of patients that share the disparity above different quartiles that will represent the impact of the disparity. The creation of such a tool will be incremental and we plan to add to it as new disparities are found.

**Aim 3b. Conduct network analysis studies to find clusters of related disparity proxies, understand underlying drivers, and assess the impact of individual proxies in the whole network and through time.**

1. Perform network analysis to identify clusters of related disparity proxies and quantify propensity to clustering.

2. Analyze disparity proxy clusters for underlying sources and drivers of health data bias.

3. Conduct centrality analysis.

4. Assess the impact of individual proxies on the whole network over time.




#research
#nlp
#sdoh
#paper
#nih
#good4pub 