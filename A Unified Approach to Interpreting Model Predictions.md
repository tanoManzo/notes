

## Introduction

The ability to correctly interpret a prediction model’s output is extremely important. In some applications, simple models (e.g., linear models) are often preferred for their ease of interpretation, even if they may be less accurate than complex ones.

A wide variety of different methods have been recently proposed to address this issue [5, 8, 9, 3, 4, 1]. But an understanding of how these methods relate and when one method is preferable to another is still lacking.

We present a novel unified approach to interpreting model predictions.

1. We introduce the perspective of viewing any explanation of a model’s prediction as a model itself, which we term the *explanation model*.
2. We then show that game theory results guaranteeing a unique solution apply to the entire class of additive feature attribution methods (Section 3) and propose SHAP values as a unified measure of feature importance.
3. We propose new SHAP value estimation methods and demonstrate that they are better aligned with human intuition.

## Additive Feature Attribution Methods

For complex models, a simpler explanation model is define as any interpretable approximation of the original model.

Let f be the original prediction model to be explained and g the explanation model. Here, we focus on [[local methods]] designed to explain a prediction f(x) based on a single input x, as in LIME. Explanation models often use simplified inputs x' that map to the original inputs through a mapping function x = hx(x'). Local methods try to ensure g(z') ~= f(hx(z')) whenever z' ~= x'.
(Note that hx(x') = x even though x' may contain less information than x because hx is specific to the current input x.)

**Definition 1**
![[Pasted image 20240223150753.png]]
### LIME

The LIME method interprets individual model predictions based on locally approximating the model around a given prediction. LIME is additive feature attribution method.

LIME refers to simplified inputs x' as *interpretable inputs* (mapping of the original input simplied).

Faithfulness of the explanation model g(z0) to the original model f(hx(z0)) is enforced through the loss L over a set of samples in the simplified input space weighted by the local kernel.

### DeepLIFT
A recursive prediction explanation method for deep learning. It attributes to each input xi a value C that represents the effect of that input being set to a reference value as opposed to its original value.

### Layer-Wise Relevance Propagation
The layer-wise relevance propagation method interprets the predictions of deep networks. It is equivalent to DeepLIFT with the reference activations of all neurons fixed to zero.

### Classic Shapley Value Estimation
Three previous methods use classic equations from cooperative game theory to compute explanations of model predictions: Shapley regression values [4], Shapley sampling values [9], and Quantitative Input Influence [3].

**Shapley regression values** are feature importances for linear models in the presence of [[multicollinearity]]. This method requires retraining the model on all feature subsets. **It assigns an importance value to each feature that represents the effect on the model prediction of including that feature.** To compute this effect, a model is trained with that feature present, and another model is trained with the feature withheld. Then, predictions from the two models are compared on the current input. Since the effect of withholding a feature depends on other features in the model, the preceding differences are computed for all possible subsets. The Shapley values are then computed and used as feature attributions.


**Shapley sampling values** are meant to explain any model by: (1) applying sampling approximations, and (2) approximating the effect of removing a variable from the model by integrating
over samples from the training dataset. it is also an additive feature attribution method.

**Quantitative input influence** is a broader framework that addresses more than feature attributions.


## Simple Properties Uniquely Determine Additive Feature Attributions

The first desirable property is local accuracy. When approximating the original model f for a specific input x, local accuracy requires the explanation model to at least match the output of f for the simplified input x' (which corresponds to the original input x).

![[Pasted image 20240223151341.png]]
The second property is missingness. If the simplified inputs represent feature presence, then missingness requires features missing in the original input to have no impact.

![[Pasted image 20240223151441.png]]

The third property is consistency. Consistency states that if a model changes so that some simplified input’s contribution increases or stays the same regardless of the other inputs, that input’s attribution should not decrease.

![[Pasted image 20240223151544.png]]![[Pasted image 20240223151622.png]]

Theorem 1 follows from combined cooperative game theory results, where the values phi<sub>i</sub> are known as Shapley values [6]. Young (1985) demonstrated that Shapley values are the only set of values that satisfy three axioms.

The following section proposes a unified approach that improves previous methods, preventing them from unintentionally violating Properties 1 and 3.

