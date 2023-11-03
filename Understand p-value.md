p**-value**, short for **probability value**, measures how likely a result occurs through chance alone.

![[Pasted image 20231103131307.png]]
Throughout this course, we'll see that most statistical analysis boils down to these steps:

1. Form a **hypothesis**, which is an assumption made before experimentation.
    
2. Decide on a criterion that rejects the hypothesis if the experimental results are too unlikely.
    
3. Gather and analyze data, and then reject or don't reject the hypothesis based on the results.

## The Z-statistic

This lesson kicks off our coverage of the �Z-test, a powerful tool for testing a statistical hypothesis when the underlying distribution is normal and the population variance is known.

Central to every �Z-test is something called the �Z-statistic, which emerges directly from the central limit theorem.

The name of the game in hypothesis testing is finding evidence for remarkable claims — in particular, that Fat Blaster leads to weight loss when used as directed.

Our default assumption, called the **null hypothesis** or H0, is the belief that the drug has no impact on weight.

The **alternative hypothesis**, HA,HA​, is the belief that weight loss is likely when the drug is used.

The alternative hypothesis is the effect that we're testing. We aren’t interested in both weight loss and weight gain, which is μ≠0. Instead, we're specifically interested in finding that the amount of weight loss is greater than zero, which is μ>0.

Now that we specified our hypotheses, we're ready to take some sample data and try to identify whether or not it supports the null hypothesis.

**The way this typically proceeds is by comparing the sample data to the data we would expect assuming the null hypothesis is **true**.**

If our sample is highly improbable or “extreme” — given what we'd expect when the null hypothesis describes reality — then the sample is **not** strong evidence in favor of H0​.

The purpose of the �Z-test — and many other statistical tests — is to facilitate this comparison.