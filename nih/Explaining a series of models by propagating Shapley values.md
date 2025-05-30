## abstract 
Local feature attribution methods are increasingly used to explain complex machine learning models. 

Current methods expensive to compute and not capable of explaining a distributed series of models.

Generalized DeepSHAP (GDeepSHAP), a tractable method to propagate local feature attributions through complex series of models based on a connection to the Shapley value. 

We evaluate G-DeepSHAP across biological, health, and financial datasets. 


## General 

Explaining a series of models is crucial for debugging and building trust, even more so because a series of models is inherently harder to explain compared to a single model.

Local feature attribution approaches explain why a model makes a prediction for a single sample (known as the [[explicand]]). Existing model-agnostic local feature attribution methods (e.g., IME, LIME, KernelSHAP) work regardless of the specific model being explained. Two distinct shortcomings: (1) their sampling-based estimates of feature importance are inherently variable, and (2) they have a high computational cost which may not be tractable for large pipelines.

Model specific local feature attribution methods (i.e., attribution methods that work for specific types of models) are often much faster than model-agnostic approaches, but generally cannot be used to explain a series of models (e.g., DeepLIFT).

We present Generalized DeepSHAP (G-DeepSHAP)—a local feature attribution method that is faster than model-agnostic methods and can explain complex series of models that preexisting model-specific methods cannot.

G-DeepSHAP is based on connections to the Shapley value, a concept from game theory that satisfies many desirable axioms.

Contributions: 
- a theoretical framework that connects the rules introduced in DeepLIFT to the Shapley value with an interventional conditional expectation set function (ICE Shapley value).
- ICE Shapley value decomposes into an average over single baseline attributions where a single baseline attribution explains the model for a single sample ([[explicand]]) by comparing it to a single sample (baseline).
- a generalized rescale rule to explain a complex series of models by propagating attributions while enforcing efficiency at each layer. This framework extends DeepSHAP to explain any series of models composed of linear, deep, and tree models.
- a group rescale rule to propagate local feature attributions to groups of features

Many feature attribution methods must define the absence of a feature, often by masking features according to a single baseline sample (single baseline attribution). In contrast, we show that under certain assumptions, the correct approach is to use many baseline samples instead. We show that using many baselines avoids bias that can be introduced by single baseline attributions (section Baseline distributions avoid bias). 

In the biological datasets (21–24), we qualitatively assess group feature attributions based on gene sets identified in prior literature (section Group attributions identify meaningful gene sets). 

G-DeepSHAP can use feature attributions to ask many important scientific questions by explaining different parts of the series of models (Fig. 1d). When features used by upstream models are semantically meaningless (deep feature extraction) or hard to understand (stacked generalization), G-DeepSHAP provides explanations in terms of the original features which can often be more intuitive, especially for non-technical consumers. G-DeepSHAP enables attributions with respect to different aspects of model behavior such as predicted risk or even errors the model makes (loss explanation). Finally, using the group rescale rule enables users to reduce the dimensionality of highly correlated features which makes them easier to understand (group explanation).

We improve upon two previous approaches (DeepLIFT17, DeepSHAP16) that propagate attributions while maintaining efficiency with respect to a single baseline. We make two improvements: (1) we compare to a distribution of baselines, which decreases the reliance of the attributions on any single baseline (section Baseline distributions avoid bias) and (2) we generalize the rescale rule so that it applies to a series of mixed model types, rather than only layers in a deep model. More precisely, a closely related method named DeepSHAP was designed to explain deep models (f : Rm ! R)16, by performing DeepLIFT17 using the average as a baseline16 (Methods section Differences to previous approaches). Using a single average baseline is not the correct approach to explain nonlinear models based on connections to Shapley values with an interventional conditional expectation set function and a flat causal graph. we show that the correct way to obtain the interventional Shapley value local feature attributions is to average over single baseline feature attributions.

G-DeepSHAP is an approximate method, meaning that it is biased for the true interventional Shapley values. However, this bias allows G-DeepSHAP to be drastically faster than alternative approaches. 


## Results 


### Baseline distributions avoid bias 
We aim to demonstrate that single baselines can lead to bias in explanations by comparing attributions using either a single baseline (an all-black image) as in DeepLIFT or a random set of 1000 baselines (random training images) as in G-DeepSHAP. **Although the black pixels in the image are qualitatively important, using a single baseline leads to biased attributions with little attribution mass for black pixels.** In comparison, averaging over multiple baselines leads to qualitatively more sensible attributions. Quantitatively, we show that despite the prevalence of darker pixels (pixel distribution plots in Fig. 2), single baseline attributions are biased to give them low attribution, whereas averaging over many baselines more sensibly assigns a large amount of credit to dark pixels (attribution distribution plots in Fig. 2). 
![[Pasted image 20240225183642.png]]


### Natural scientific questions with baseline distributions
To demonstrate the importance of baseline distributions as a parameter, we explain an MLP for predicting 15- year mortality in the NHANES I data set. We use G-DeepSHAP to explain an explicand relative to a baseline distribution drawn uniformly from all samples (Fig. 3a (top)). 

We can manually select a baseline distribution of older males to reveal novel insights, as in Fig. 3a (bottom). The impact of gender is gone because we compare only to males, and the impact of age is lower because we compare only to older individuals. This example illustrates that the baseline distribution is an important parameter for feature attributions.
![[Pasted image 20240226092117.png]]


We propose k-means clustering to select a baseline distribution (detail in Methods section Selecting a baseline distribution). 

In Fig. 3b, we show clusters according to age and gender. Then, we explain many older male explicands using either a general population or an older male population baseline distribution (Fig. 3c).

![[Pasted image 20240226092714.png]]
When we compare to the older male baselines, the importance of age is centered around zero, gender is no longer important, and the importance orderings of remaining features change. 

The inquiry we make changes from “What features are important for older males relative to a general population?” to “What features are important for older males relative to other older males?”

To quantitatively evaluate whether our attributions answer the second inquiry, we can ablate features in order of their positive/negative importance by masking with the mean of the older male baseline distribution (Fig. 3d, (Methods section Ablation tests)). In both plots, lower curves indicate attributions that better estimated positive and negative importance.

For both tests, attributions with a baseline distribution chosen by k-means clustering substantially outperforms a baseline distribution drawn from the general population.

![[Pasted image 20240226093910.png]]

Our recommendation is to choose baseline distributions by clustering according to non-modifiable, yet meaningful, features like age and gender. This yields explanations that answer questions relative to inherently interpretable subpopulations. 

The first advantage is that choosing baseline distributions in this way decreases variance in the features that determined the clusters and subsequently reduces their importance to the model. 


### Group attributions identify meaningful gene sets
We explain two MLPs trained to predict Alzheimer’s disease status and breast cancer tumor stage from gene expression.

Gene expression data is often extremely high dimensional; as such, solutions such as [[gene set enrichment analysis (GSEA)]] are widely used.

We aim to attribute importance to gene sets while maintaining efficiency by proposing a group rescale rule. This rule sums attributions for genes belonging to each group and then normalizes according to excess attribution mass due to multiple groups containing the same gene. It generalizes to arbitrary groups of features beyond gene sets, such as categories of epidemiological features (e.g., laboratory measurements, demographic measurements, etc.).

In Fig. 4, we can validate several key genes identified by G-DeepSHAP. For Alzheimer’s disease, the overexpression of SERPINA3 has been closely tied to prion diseases, and UBTD2 has been connected to frontotemporal dementia—a neurodegenerative disorder43. For breast cancer tumor stage, UBE2C was positively correlated with tumor size and histological grade
![[Pasted image 20240226101405.png]]

In addition to understanding gene importance, understanding higher-level importance can be obtained using gene sets, i.e., groups of genes defined by biological pathways or co-expression.

We obtain gene set attributions by grouping genes according to curated gene sets from the KEGG (Kyoto Encyclopedia of Genes and Genomes) pathway database (https://www.gsea-msigdb.org/gsea/msigdb/collections.jsp#C2).

For Alzheimer’s disease, the glyoxylate and dicarboxylate metabolism pathway was independently identified based on metabolic biomarkers45; several studies have demonstrated aberrations in the TCA cycle in Alzheimer’s disease brain46; and alterations of purine-related metabolites are known to occur in early stages of Alzheimer’s disease. For breast cancer, many relevant proteins are involved in ubiquitinproteasome pathways48 and purine metabolism was identified as a major metabolic pathway differentiating a highly metastatic breast cancer cell line from a slightly metastatic one.

### Loss attributions provide insights to model behavior
We examine an NHANES (1999–2014) mortality prediction GBT model to show how explaining the model’s loss (loss explanations) provides important insights different from insights revealed by explaining the model’s output (output explanations).

We can explain a binary classification model in terms of its log-odds predictions, its probability predictions or its loss computed based on the prediction. We focus on local feature attributions that explain per-sample loss.

We train our model on the first five release cycles of the NHANES data (1999–2008) and evaluate it on a test set of the last three release cycles (2009–2014) (Fig. 5a). We simulate a covariate shift in the weight variable by re-coding it to be measured in pounds, rather than kilograms, in release cycles 7 and 8 (Fig. 5b). Then, we ask, “Can we identify the impact of the covariate shift with feature attributions?” Comparing the train and test output attributions, release cycles 7 and 8 are skewed, but they mimic the same general shape of the training set attributions. 

![[Pasted image 20240226114458.png]]

we can identify that the falsely increased weight leads to many misclassified samples where the loss weight attribution exceeds the expected loss. Although such debugging is powerful, it is not perfect. Note that in the negatively labeled samples, we cannot clearly identify the covariate shift because higher weights are protective and lead to more confident negative mortality prediction.



![[Pasted image 20240226115146.png]]
We examine the natural generalization gap induced by covariate shift over time, which shows a dramatically different loss in the train and test sets (Fig. 5c).

We can quantitatively verify that negative blood lead affects model performance more in the test set by ablating blood lead for the top 10 samples in the train and test sets according to their loss distributions. From this, we can see that blood lead constitutes a substantial covariate shift in the model’s loss and helps explain the observed generalization gap.

![[Pasted image 20240226115544.png]]
We can visualize the impact on the model’s loss of ablating by output attributions compared to ablating by loss attributions (Fig. 5d). This ablation test (Methods section Ablation tests) asks “What features are important to the model’s performance (loss)?” Ablating the positive and negative attributions both increase the mean model loss by hiding features central to making predictions. However, ablating by the negative loss attribution directly increases the loss far more drastically than ablating by the output. More so, ablating positive loss attributions clearly decreases the mean loss, which is not achievable by output attribution ablation.

### Explaining deep image feature extractors
We compare G-DeepSHAP explanations to a number of model-agnostic explanations for a series of two models: a CNN feature extractor fed into a GBT model that classifies MNIST zeros. In this example, nonlinear transformations of the original feature space improve the performance of the downstream model (Supplementary Notes Section 2.6) but make model-specific attributions impossible. 

Qualitatively, we can see that G-DeepSHAP and IME are similar, whereas KernelSHAP is similar for certain explicands but not others (Fig. 6a).
![[Pasted image 20240226120521.png]]
### Explaining distributed proprietary models
G-DeepSHAP explanations for a consumer scoring example that feeds a simulated GBT fraud score model and a simulated MLP credit score model into a GBT bank model. Consumer scores (e.g., credit scores, fraud scores, health risk scores, etc.) describe individual behavior with predictive models.

Explaining the bank model in Fig. 7a will tell us that fraud and credit scores are important (in Fig. 7c), but these scores are inherently opaque to consumers. A better solution might be model-agnostic methods that explain the entire pipeline at once.

In Fig. 7a, a single institution would have to obtain access to fraud, credit, and bank models to use the standard model-agnostic approaches (Fig. 7b (left)). This may be fundamentally impractical because each of these models is proprietary. This opacity is concerning given the growing desire for transparency in artificial intelligence.

G-DeepSHAP naturally addresses this obstacle by enabling attributions to the original features without forcing companies to share their proprietary models if each institution in the pipeline agrees to work together and has a consistent set of baselines. 
![[Pasted image 20240226120847.png]]In particular, in Fig. 7a, the lending institution can explain its bank model in terms of bank features and fraud and credit scores. The bank then sends fraud and credit score attributions to their respective companies, who can use them to generate G-DeepSHAP attributions to the original fraud and credit features. The fraud and credit institutions then send the attributions back to the bank, which can provide explanations in terms of the original, more interpretable features to their applicants (Fig. 7d).

We first quantitatively verify that the G-DeepSHAP attributions for this pipeline are comparable to the model-agnostic approaches in Fig. 7b.


We can qualitatively verify the attributions in Fig. 7c, d. In Fig. 7c, we find that the fraud and credit scores are extremely important to the final prediction. In addition, bank features include low revolving balance divided by credit limit (NetFractionRevolvingBurden) and a low number of months since inquisitions (MSinceMostRecentInqExcl7Days) are congruously important to good risk performance.

## Discussion