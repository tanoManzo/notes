We evaluate our model on a wide range of well-known clinical reasoning challenges that are directly pertinent to many real-world clinical research tasks:

- identifying clinical concepts of type problems, treatments, tests, and inferring relations between them from clinical text;
- identifying the mentions of temporal expressions, clinical departments, evidential, and occurrences, inferring whether pairs of sentences are semantically equivalent, contradicting or neutral to each other; 
- assigning diagnostic codes to a patient’s discharge report, and inferring the therapeutic classes of medications administered to a patient from their discharge reports. 

We find that a language model trained solely on text specific to a large medical center performs well on all these benchmarks and seems to be useful for a broad range of downstream language-related tasks as conducted within a given medical center. The promising performance of the model also highlights the utility of developing large, deidentified EHR datasets at medical centers to support clinical research and improve the state-of-the-art performance in clinical language processing.