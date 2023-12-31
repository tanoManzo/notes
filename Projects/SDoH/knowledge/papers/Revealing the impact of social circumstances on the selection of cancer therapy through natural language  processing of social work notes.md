
Goal: the impact of social circumstances on cancer therapy
How: predict the prescription of targeted cancer therapy to patients based solely on documentation by clinical social workers.
What: a feature importance analysis to pinpoint the specific social circumstances that impact cancer therapy

Results: Using only social work notes, we consistently predicted the administration of targeted therapies, suggesting systematic differences in treatment selection exist due to non-clinical factors.

UCSF-BERT model, pretrained on clinical text at UCSF, outperformed other publicly available language models with an AUROC of 0.675 and a Macro F1 score of 0.599.

Our feature importance analysis identified several clinically intuitive social determinants of health (SDOH) that potentially contribute to disparities in treatment. Our findings indicate that significant disparities exist among breast cancer patients receiving different types of therapies based on social determinants of health. Social work reports play a crucial role in understanding these disparities in clinical decision-making.

## Objective

Clinical decisions are influenced not only by clinical criteria but also by non-clinical factors such as race, gender, perceived financial stability, and more, which are collectively referred to as social determinants of health (SDOH). Financial constraints are but one example of factors that can potentially influence the treatment decision[8].

In this work, we demonstrated a strong association between specific features within social work (SW) clinical documentation and the choice of expensive, targeted therapy prescription for patients with breast cancer.

We developed a hierarchical language model for prediction over long sequences of clinical notes and successfully increased the predictability of the outcome. To understand which SDOH factors are used by the model for prediction, we measured the importance of SDOH factors by deleting words belonging to specific SDOH topics. Several critical contributors emerged, including socio-economic factors, abuse history, and risk of death. Our findings demonstrate that SW notes can reveal the impact of a patient's social environment on medical treatment prescription without requiring expensive and time-consuming manual annotation. Our hierarchical modeling approach will inform the development of models capable of leveraging multiple clinical notes for prediction.

Previous research showed that clinical management decisions can be influenced by socioeconomic status[8], race[15], gender[16], adherence to treatment[17], patient behavior[18], attitude[19], and even physician personal characteristics[20].


## Deep learning 
We ran our algorithm 5 times for each model and evaluated the model performance using the validation set. We reported the median scores in the five models on the test set to reduce the training variation. The cross-entropy loss function was used for optimization. After training and hyperparameter tuning, the model was tested on the held-out test set to compute model performance. 

We used an internal UCSF-BERT model, which is a cased BERT model pretrained on the UCSF clinical notes using the masked language modeling (MLM) and next sentence prediction (NSP) objectives from scratch, developed by Sushil et al [26].

We selected this model with the hypothesis that pretraining on the same domain will improve the model's performance. We also implemented publicly available pretrained BERT-base models: SciBERT[28], ClinicalBERT[29], BioLM[30], and Biomed-Roberta[35]. We fine-tuned these models for the classification task.


To rule out the possibility of finding results by randomness, we implemented three distinct dummy classifiers as a control. Dummy (Prior): This strategy always predicts the most frequent class in the training set. Dummy (Stratified): This strategy generates predictions by respecting the class distribution of the training set. It randomly predicts class labels based on the distribution of the training set. Dummy (Uniform): This strategy generates predictions uniformly at random.

Evaluation metrics Model evaluation results were reported for the testing dataset only. For the classification task, Area Under the Receiver Operating Characteristic curve (AUROC), F1 score, precision, and recall metrics are reported. In order to address the issue of data imbalance, which can impede the interpretation of model performance, we used macro-averaged format for F1, precision, and recall score. F1 score is the harmonic mean of precision and recall.

Notably, macro-averaged computation uses the arithmetic mean of all the per-class scores, which provides equal weight to all the classes. We used sklearn.metrics from the scikit-learn python package for programming[32].


To use long sequences of clinical notes for prediction, we built a hierarchical BERT model (BERT-MS), where the first step divides a long sequence of notes into multiple independent instances and then trains the single BERT classifier on the individual chunks in the training set. In the second step, we concatenate the BERT representations of all notes of the same patient and further fit them into a multilayer perceptron for the training.

The UCSF BERT-MS-n model was trained in two steps. First, we used multiple notes for a single patient as multiple independent instances for classification. We then trained the UCSF-BERT classification model on this set. Second, we retained only the lower-dimensional hidden representations of each note from the final layer of the trained classification model obtained in the previous step. These low-dimensional representations of multiple reports of the same patient were thereby concatenated into a single representation. We then trained a second multilayer perceptron for the same classification task (Figure 3). In this manner, we were able to train a hierarchical language model that can integrate n-fold information without expending the model parameter nfolds. We built several UCSF BERT-MS-n models including UCSF BERT-MS-3, UCSF BERTMS-5, UCSF BERT-MS-8, UCSF BERT-MS-10, that corresponds to the use of at most 3, 5, 8 and 10 notes.


## Feature importance analysis 
To understand which SDOH factors are used by the model for prediction, we used feature ablation methods to measure the importance of different SDOH factors. We examined the effect on model performance of removing keywords associated with the following topics: Mental health, Family, Consultation/Appointment, Group session, Risk of death, Clinician/Hospital/Medication, Living condition/Lifestyle/Social support, Telephone encounter/Online communication, Abuse history (all forms), and Insurance/Income. These categories, and keywords associated with each category, were selected following the LDA topic modelling analysis as described by Sun et al[33] (Supplementary Table 5)


## Results

First, we explored whether SDOH information within structured data alone could stratify these patients. For the 2496 patients identified, we found information regarding demographics, marriage status and smoking history was present, but data on patient financial status, education level and other important SDOH were absent from the structured data. Machine learning-based approaches leveraging the SDOH coded within structured data failed to predict the administration of targeted therapy in patients (S. Table 3), demonstrating the limitations of structured data in predicting this task. In contrast, our prior research has demonstrated that social work notes possess a wealth of information relating to SDOH, including details on frequently discussed topics such as mental health, insurance status and family support (Figure 2C, D)[33]. This qualitative observation suggested that social work notes encompass a wealth of SDOH factors, which may be captured by pre-trained language models when predicting the administration of therapy regimens to patients.



Table 1 shows the prediction performance of different deeplearning classification models. UCSF-BERT achieved the best result with a Macro F1 of 0.599 and AUROC score of 0.675. RoBERTa models (BioLM and Biomed-Roberta) performed generally better than BERT-base models (SciBERT, ClinicalBERT) potentially because of their dynamic masking strategy during pretraining such that the masked token changes during each training epoch[31]. Yet, none of them outperformed the UCSF-BERT model. This suggests that pretraining BERT-based models with clinical data can be helpful for achieving superior performance on domain-specific tasks. We also ran our tasks on three random baseline models, each of which ruled out the random performance from different perspectives (See methods). Our model significantly outperformed the random baselines (Table 1). Overall, the predictive performance of the UCSFBERT model suggested that the social circumstance of patients is associated with the type of therapies administered to them.


To explore the role different SDOH factors may have in predicting utilization of targeted therapy, we assessed the importance of SDOH factors by feature ablation methods (See Methods). The 11 topics that we tested were mentioned with varying frequency in the social work notes (Supplementary Figure 1). Notably, our findings did not reveal any topic specific class imbalance among the extracted topics in patients who were not administered targeted therapy. The notes belong in each topics have the similar class proportion: 70% “TT-Yes” group and 30% “TT-No” group.

We found several SDOH topics, including Abuse History, Risk of Death, Social Support as the most significant influencers that the model leveraged in the prediction task (Figure 4). Other SDOH topics such as Family, Living Condition also had obvious impact in model decision making. However, besides the broad topic area “medical factors”, the common topics related to medical aspects, Mental Health and Group Session, had a lower influence on the model prediction. As the neutral control, topic Consultation and TelephoneEncounter played a less important role in the prediction task. Interestingly, Finance, which represents the socioeconomic factor that likely influences patients’ decisions in therapy regimen, did not come up as an important regulator in the process. Overall, we successfully used model interpretability methods to analyze the trained language model to discover the SDOH factors that are not frequently considered to be influencers of the prescription of more financially toxic oncology medications.

We found that pretraining a language model on the same data source is important for better prediction performance in specialized domains, particularly from small datasets that are common in clinical studies. Among all the transformer-based models we explored (Table 1), UCSF-BERT achieved the best prediction performance on our task. Moreover, with our hierarchical BERT model, we showed that integrating multiple notes, and consequently more information about a patient, improves model performance. I