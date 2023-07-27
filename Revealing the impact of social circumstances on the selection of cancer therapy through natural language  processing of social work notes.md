
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