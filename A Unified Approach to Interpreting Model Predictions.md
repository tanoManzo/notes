

## Introduction

The ability to correctly interpret a prediction model’s output is extremely important. In some applications, simple models (e.g., linear models) are often preferred for their ease of interpretation, even if they may be less accurate than complex ones.

A wide variety of different methods have been recently proposed to address this issue [5, 8, 9, 3, 4, 1]. But an understanding of how these methods relate and when one method is preferable to another is still lacking.

We present a novel unified approach to interpreting model predictions.

1. We introduce the perspective of viewing any explanation of a model’s prediction as a model itself, which we term the *explanation model*.
2. We then show that game theory results guaranteeing a unique solution apply to the entire class of additive feature attribution methods (Section 3) and propose SHAP values as a unified measure of feature importance.
3. We propose new SHAP value estimation methods and demonstrate that they are better aligned with human intuition.

## Additive Feature Attribution Methods

For complex models, a simpler explanation model is define as any interpretable approximation of the original model.