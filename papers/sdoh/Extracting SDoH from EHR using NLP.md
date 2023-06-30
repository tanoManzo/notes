JAMIA - doi: 10.1093/jamia/ocab170

## Intro 
The annual County Health Rankings ([County Health Rankings & Roadmaps](https://www.countyhealthrankings.org/)) gauge the impact of a wide range of health factors by ranking the health outcomes of the over 3000 counties across the United States.

Social, economic, and physical environment factors contribute the most to health outcomes (50%), followed by health behaviors (30%). 

![[Pasted image 20230630132334.png]]

Attempts to improve standardization at the national level have been made by the Protocol for Responding to and Assessing Patients’ Assets, Risks, and Experiences (PRAPARE) (https://www.cdc.gov/media/releases/2014/ p0501-preventable-deaths.html) and the National Academy of Medicine (https://nam.edu/social-determinants-of-health-101-for-healthcare-five-plus-five/).


A final total of 82 publications were included in this study at the end of the full text review process. We also searched references of all82 articles, and most of these publications overlap with our search results. The included articles were published between 2005 and 2021

SDoH categories that were not evaluated in the County Health Rankings (such as race, ethnicity, mental health conditions, or stress) were not included in our study.

## SDoH Categories

![[Pasted image 20230630170602.png]]

## Supervised methods
Furthermore, we observed 7 studies that investigated deep learning algorithms for SDoH extraction Convolutional neural network (CNN) and feedforward neural network (FNN) performed poorly compared to traditional ML algorithms, such asSVM, random forests, Classification and Regression Tree (CaRT), and AdaBoost due to scarcity of annotated data for identifying SDoH such as alcohol abuse, substance abuse, homelessness, and sexual orientation.33 In more recent work, Lybarger et al42 used Bidirectional Encoder Representations from Transformers (BERT) for embedding, Bidirectional Long Short-Term Memory (BiLSTM) for trigger and label identification, and Conditional Random Field (CRF) for SDoH span identification.

![[Pasted image 20230630174751.png]]

## SDoH outcome analysis
![[Pasted image 20230630175702.png]]

## Future work
Several studies were performed on identifying smoking, substance abuse, housing, and alcohol status in the EHR systems using NLP techniques. In the future, the NLP research community might focus on lessstudied SDoH such as child and sexual abuse, financial issues, transportation, neighborhood, social isolation, family problems, employment, education, food insecurity, and healthcare access. Another interesting study would be to compare different aspects of NLP algorithms, such as system performance, amount of annotated data, type of NLP systems, and so forth with the difficulty of SDoH extraction. 

Analyzing longitudinal aspects of the data may be helpful for developing outcome-based systems. Bejan et al. analyzed longitudinal data on homelessness and found that homelessness status changes with time. Temporal information (temporal information (current and past, amount/quantity/frequency, and type) extraction systems were developed for alcohol abuse, smoking status, and substance use/abuse. However, temporal extraction was rare in homelessness (temporal)16 and employment (status, duration, history, and type).

Fewer experiments have identified the span of SDoH keywords in clinical texts. Furthermore, relation extraction/identifying relationships between medical concepts are semantic tasks that have been popular among the NLP community. Thus, developing comprehensive systems for 1) capturing longitudinal information; 2) extracting temporal information; 3) extracting [[SDoH]] concepts; and 4) extracting relations among SDoH concepts will be valuable future goals in this area of interest.

Surprisingly, DL algorithms were rare for identifying SDoH. This may be attributed to insufficient amounts of annotated data whereas DL models necessitate large volumes of annotated data. More experiments implementing DL algorithms for SDoH identification and relation extraction can be performed in future. 

Finally, NLP algorithms developed for SDoH extraction heavily rely on structural and linguistic information available in the data. Significant progress has been made in terms of enhancing portability of NLP systems across clinical specialties. In the future, developing a cross-site NLP algorithm will be helpful to delineate individual noting styles of providers and to generalize NLP systems for SDoH.


#research
#nlp
#sdoh
#paper
#nih
