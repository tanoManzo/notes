# Entity Description Generation by Exploring Knowledge Graph
Link: [paper](https://aclanthology.org/2020.emnlp-main.90/)

Knowledge-graph-to-text generation, automatically converting knowledge into natural language, is a task in natural language processing (NLP). The task takes as input some structured knowledge, such as resource description framework (RDF) triples of [[WebNLG]] , key-value pairs of WIKIBIO (Lebret et al., 2016) and E2E (Novikova et al., 2017), to generate natural text describing the input knowledge.

In essence, the task can be formulated as follows: given a main entity, its one-hop attributes/relations (e.g., WIKIBIO and E2E), and/or multi-hop relations (e.g., [[WebNLG]]), the goal is to generate a text description of the main entity describing its attributes and relations

In order to facilitate the study, we introduce a new dataset, namely entity-to-description (ENT-DESC) extracted from Wikipedia and Wikidata, which contains over 110k instances. Each sample is a triplet, containing a set of entities, the explored knowledge from a knowledge-graph, and the description.

![Exemple](https://d3i71xaburhd42.cloudfront.net/dab2e008216068c00d359684d6b0c3887d062de1/1-Figure1-1.png)
Figure 1: An example showing our proposed task.

Our dataset is not only more practical but also more challenging due to lack of explicit alignment between the input and the output. Therefore, some knowledge is useful for generation, while others might be noise.

We present a multi-graph convolutional networks (MGCN) architecture by introducing multigraph transformation incorporated with an aggregation layer. Multi-graph transformation is able to represent the original graph information more accurately, while the aggregation layer learns to extract useful information from the KG.

Main contributions include:
- construct a large-scale dataset ENT-DESC for a more practical task of entity description generation by exploring KG.
- propose a multi-graph structure transformation approach that explicitly expresses a more comprehensive and more accurate graph information, to overcome limitations associated with Levi graphs.

MGCN model incorporated with aggregation methods outperforms strong baselines by effectively capturing and aggregating multi-graph information.

![architecture](https://d3i71xaburhd42.cloudfront.net/dab2e008216068c00d359684d6b0c3887d062de1/5-Figure3-1.png)
Figure 3: Overview of our model architecture. There are n MGCN layers in the multi-graph encoder, and 2 LSTM layers in the decoder. h(k−1) is the input graph representation at Layer k, and its 6 copies together with the corresponding adjacent matrices Ai’s of transformed graphs in the multi graph (refer to Figure 4) are fed into individual basic encoders. Finally, we obtain the graph representation h(k) for the next layer by aggregating the representations from these encoders.