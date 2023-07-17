[[NLP]]

**Chris Manning** (Stanford):  
- Linguistics, AI, mentioned Chomsky (human cannot learn language only from the data), 
- Transformer Architecture, Attention (soft tree structure), what transformers learn during the training (e.g., co-reference facts). 
- Paper on Neural Machine Translation (foundation of NLP, Attention, probabilistic model technique, etc.).
- Language models give you probability distribution of a sequence of words.
- Less attention to the syntax, more attention to the data. 
- Attention-based model, at any point in the sequence, you can calculate out a connection to other words. Use this Attention you can create a vector, which will help for the next. Instead of to keep all the sequence, you only keep these vectors to check the Attention for that word (you look back).
- Bi-linear attention, two vectors, one matrix in the middle. Matrix by vector by vector is the attention score. Only the dot-prod is too rigid. The matrix will allow you to focus on parts of the two vectors. That matrix can be the product of two lower ranked matrices. Those matrices can be multiplied by the two vectors, which it is more computational efficient.  
- Author of Glove paper. Give a better understanding. Latent Semantic Analysis, vector representation of word meaning. Singular Value Decomposition. Reducing rank. 
- Scaling of NLP models. BERT 2018 good enough for smaller task NED, QA, etc. 
