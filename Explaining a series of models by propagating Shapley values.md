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

