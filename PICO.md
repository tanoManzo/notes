Patient Intervention Comparison Outcome

1) move part of the related work to explain the limitation of the  EBM-NLP dataset to the related work section to enhance readability and highlight authors' contribution. 
To improve on these areas, we proposed FinePICO, a semi-supervised learning (SSL) algorithm to enhance the extraction of fine-grained PICO entities. Our main objective was to demonstrate that combining limited labeled data and a substantial volume of unlabeled data can achieve performance comparable to that of models trained using fully annotated data.

Once the initial model is trained, it is deployed to make inferences on the unlabeled data, referred to as pseudo-labels. We enrich the original labeled data with the high-confidence pseudo-labeled data for fine-tuning the model. We iteratively repeat the cycle of generating pseudo-labels and updating model weights until the model’s performance converges on the validation dataset or a predefined maximum number of iterations has been reached
2) generate pseudo labels
3) Class-wise typo
4) How from raw-pseudo data, we have high-quality data labels. Why not to use an LLM from the begging. .
