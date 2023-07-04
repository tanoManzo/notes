
### Commonsense Knowledge Transfer for Pre-trained Language Models


by Wangchunshu Zhou, Ronan Le Bras, and Yejin Choi
<!-- element style="font-size: 24px"-->

---

LLMs do not possess deep semantic understanding or world knowledge like humans do

(Bender and Koller, 2020)
<!-- element style="font-size: 24px"-->

---
##### Inject commonsense knowledge into the parameters of pre-trained models



---
##### Commonsense Knowledge Graph: a semi-structured way for representing commonsense concepts

![[Pasted image 20230704165532.png]]

(Sap et al., 2020, ATOMIC)
<!-- element style="font-size: 24px"-->

---
#### Commonsense Knowledge Transfer Framework 

![[Pasted image 20230627162059.png]]
---
##### propose two commonsense-related self-supervised objectives: *commonsense text infilling and commonsense relation prediction.* 
---
#### **Commonsense text infilling** is a simple extension to the conventional text infilling objective used for pre-training BART and T5

![[Pasted image 20230627175231.png]]

---
Approach 
- <!-- element style="font-size: 28px"--> randomly select one masking scheme  
- <!-- element style="font-size: 28px"--> train the model to predict the masked spans autoregressively
<br/>
enables the model to align the surface form of human language and the underlying commonsense knowledge

---
#### Commonsense Relation Prediction: to distinguish the correct commonsense inference corresponding to the input sentence and the commonsense relation from distractors

![[Pasted image 20230627180223.png]]

