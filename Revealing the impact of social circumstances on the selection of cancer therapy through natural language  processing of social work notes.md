
Goal: the impact of social circumstances on cancer therapy
How: predict the prescription of targeted cancer therapy to patients based solely on documentation by clinical social workers.
What: a feature importance analysis to pinpoint the specific social circumstances that impact cancer therapy

Results: Using only social work notes, we consistently predicted the administration of targeted therapies, suggesting systematic differences in treatment selection exist due to non-clinical factors.

UCSF-BERT model, pretrained on clinical text at UCSF, outperformed other publicly available language models with an AUROC of 0.675 and a Macro F1 score of 0.599.

Our feature importance analysis identified several clinically intuitive social determinants of health (SDOH) that potentially contribute to disparities in treatment. Our findings indicate that significant disparities exist among breast cancer patients receiving different types of therapies based on social determinants of health. Social work reports play a crucial role in understanding these disparities in clinical decision-making.

## Objective

Clinical decisions are influenced not only by clinical criteria but also by non-clinical factors such as race, gender, perceived financial stability, and more, which are collectively referred to as social determinants of health (SDOH). Financial constraints are but one example of factors that can potentially influence the treatment decision[8].

In this work, we demonstrated a strong association between specific features within social work (SW) clinical documentation and the choice of expensive, targeted therapy prescription for patients with breast cancer.

We developed a hierarchical language model for prediction over long sequences of clinical notes and successfully increased the predictability of the outcome.