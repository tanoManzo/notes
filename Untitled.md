### **Review of the Manuscript**

---

### **Summary of the Manuscript**
The paper proposes a novel machine learning framework, Speaker-Agnostic Latent Regularisation (SALR), to classify dysarthria severity in a speaker-independent manner. Authors fine-tuned the wav2vec 2.0 transformer model for multi-task learning objectives, combining cross-entropy loss and triplet margin loss to reduce speaker-specific clustering in the latent space. The authors report a classification accuracy of 70.5% and an F1 score of 59.2% on the UA-Speech dataset, claiming significant improvement over previous benchmarks.

---

**Major Concerns**
- The authors acknowledge that data scarcity is a critical issue in dysarthria research and attempt to address it by using wav2vec 2.0's pretraining on healthy speech to generate embeddings. However, the generated embeddings were not incorporated into state-of-the-art baseline models for a fair comparison. This omission undermines the validity of their claim that the SALR framework outperforms prior approaches.

- Beyond proposing a framework, the main contribution of the authors lies in ad-hoc regularization of the fine-tuned wav2vec 2.0 model to reduce patient-centric clustering in the latent space. While their regularization approach mitigates speaker-specific clustering, it does not entirely eliminate it, as evidenced by t-SNE visualizations and qualitative analysis. Furthermore, the authors do not sufficiently prove that patient-centric clustering in the embedding space is inherently detrimental to severity classification performance. Quantitative evidence linking this clustering to reduced generalizability is absent.

- The UA-Speech dataset includes only 15 dysarthric speakers, which severely limits the diversity and generalizability of the findings. The small sample size per severity class (e.g., only two patients in low and medium severity categories) further exacerbates this issue. While leave-one-subject-out cross-validation is appropriate for speaker-independent evaluation, it does not address real-world variability such as noise or accents, which are critical for clinical deployment.Furthermore, despite introducing regularization, overfitting remains a concern given the limited dataset size and lack of validation on external datasets.

- The reported accuracy (70.5%) and F1 score (59.2%) are insufficient for clinical use, where reliability must be significantly higher. Misclassifications between adjacent severity levels (e.g., low vs. medium) highlight challenges in distinguishing subtle differences in dysarthria severity, reducing its practical applicability.

5. **Explainability Deficit**:
   - The study lacks sufficient exploration of explainability tools (e.g., attention heatmaps) to ensure transparency in decision-making—a critical requirement for clinical AI systems.
   - The latent space analysis remains qualitative without quantitative metrics to validate improvements in speaker-independence or alignment with clinical features.

6. **Ethical and Practical Considerations**:
   - The authors do not discuss biases introduced by pretraining on healthy speech data or ethical implications of deploying AI-based assessments without human oversight.
   - The computational requirements for pretraining wav2vec 2.0 (64 GPUs over 1.6 days) make this approach resource-intensive and impractical for many researchers or clinicians.

---

### **Minor Concerns**
- Some figures (e.g., confusion matrices) are underexplained, leaving readers to interpret their significance independently.
- Writing could be streamlined for clarity and conciseness.

---

### **Recommendation**
In its current form, I recommend rejecting this manuscript due to significant methodological weaknesses, lack of fair comparisons, insufficient clinical relevance, and inadequate validation of key claims. To improve, the authors should:

1. Inject generated embeddings into state-of-the-art baseline models for fair comparison.
2. Provide quantitative evidence demonstrating that patient-centric clustering negatively impacts performance.
3. Validate their approach on larger, more diverse datasets or external benchmarks.
4. Enhance explainability through additional analyses (e.g., attention heatmaps).
5. Address ethical considerations and computational feasibility.

While the proposed SALR framework shows promise, addressing these issues would require substantial revisions beyond minor adjustments.

--- 

This review aims to provide constructive feedback while justifying rejection based on critical shortcomings in methodology and validation.

Citations:
[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/4223406/c3a740a8-6f10-4876-b095-1d7a170bc0c3/PDIG-D-24-00243_reviewer.pdf