

We have chosen hyperparameters that do not modify the original N-CNN architecture, but mainly its learning rate and training regularization.


In this context, this paper investigates the effects of hyperparameter optimization on classification metrics, explainability and reliability discussing their potential impact on clinical practice. 

Specifically, we replaced the single output neuron activated by a sigmoid function with two neurons activated by a softmax function, being each neuron responsible for providing normalized probabilities for the respective classes.


## review 

- assume the audience knows N-CNN acronyms. It should be explained. 
- not clear why they needed to change the output architecture. The output is binary, therefore the probability is complementary (e.g., pain 0.7 as output, it means no-pain 0.3). 
- Not clear the decision of the scoring system for NFCS. Not motivated either. 
- Not clear the +2.5 in the Sigmoid eq 1. 
- Figure 1 shows that a modification of the output layer is not needed. 
- 

#research #paper #health #knowledge #workshop #Explainability