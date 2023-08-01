This paper explores whether some of the Hugging Face models can be used for sentiment analysis in
notes written by clinicians. There is a fair bit of novelty in this paper, and it would be nice to discuss at
AMIA. 

- [ ] My primary reservations are related to rationale for cohort selection and then the potential mis-
interpretation of results in the tables (see below).




- [x] There were several missing words related to the "Section" at the end of the Introduction.
	- We edited the introduction to fix the reported issue. 


- [X] The background information related to using sentiment analysis techniques from social media provides a strong rationale for the importance of this study.
	- the related work section was expanded to include studies that apply sentiment analysis techniques in social media.

- []it's unclear why the authors selected neonatal patients who lived less than 1 year.
- With the low agreement by human annotators, it's possible we're asking too much of language models -
it was interesting just to see the level of disagreement among humans in this paper.
- I'm glad to see BLOOM was assessed - we need more findings reported for this model in academia.
- It's good to see your transparency about the differences in labeling options for the various models.
- I don't understand why the authors reported greater performance of all models in Table 2 (few-shot)
compared to Table 1 (zero shot). For example, micro-F1s in Table 1 were 0.7604 for ROBERTa while the
highest in Table 2 was 0.7128 for MiniLM and BLOOM. I'd encourage the authors to look at their results
again and/or clarify their statement.