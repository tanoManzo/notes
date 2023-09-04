

Authors developed Gaussian Process for Stage Inference (GPSI) approach to uncover chronic disease progression patterns using synthetic and real-world data from several diseases.  

Slow progression and heterogeneous manifestations make it challenging to model the transition from normal to disease status. As patient conditions are only observed at discrete timestamps with varying intervals, an incomplete understanding of disease progression and heterogeneity affects clinical practice and drug development.

Our study demonstrated that an unsupervised approach can disentangle temporal and phenotypic heterogeneity and identify population subgroups with common patterns of disease progression. Based on the differences in these features across stages, physicians can better tailor treatment plans and medications to individual patients.


GPSI identified genotypes of based on image features, where these subgroups corresponded to different , indicating the bone-remodeling and overweighted-related pathways. 

Second, GPSI differentiated BP into two distinct developmental patterns and defined the contribution of specific brain region atrophy from early to advanced disease stages, demonstrating the ability of the GPSI to identify diagnostic subgroups. 

Third, HCC progression patterns were well reproduced in the two independent UTHealth and TCGA datasets.

These two examples demonstrated that the GPSI can identify subgroups with different temporal progression patterns. Furthermore, from the HCC data set, the GPSI provided more refined staging information for each patient, enabling early detection of HCC. Finally, compared with the current Liver Imaging Reporting and Data System (LI-RADS) [8], our comprehensive grading system achieved a more accurate diagnosis classification.

Our proposed model utilizes the GP to establish the stochastic mapping from a latent stage space to an observed EHR space. This expected mapping is usually defined by the mean function of the GP, while the covariance function describes the covariance between two arbitrary points in the latent space. In practice, using a mean function of 0 is common for simplicity, especially with insufficient prior knowledge about the function to be studied. Meanwhile, the covariance function controls the second-order statistics and is chosen based on different second-order features, such as smoothness and periodicity.

-------

Authors implemented Gaussian Process for Stage Inference (GPSI) algorithm to reveal chronic disease patterns over time. Authors applied GPSI to several datasets and compare it to state-of-the-art approaches to identify distinct longitudinal progression patterns (e.g., SuStaIn). GPSI identifies genotypes of based on image features in the Osteoarthritis dataset,  development patters in the bipolar disorder dataset, and  progression patterns for hepatocellular carcinoma datasets. 

The approach is solid and sound. However, a few descriptions/motivation can be added to enhance the quality of the research. 

Authors should clarify the choice of k-means in the general procedure of Figure 1b to estimate subgroups and stage inference with GP.
- Other algorithm instead of K-means. And other approaches for the number of clusters. 
- Describe why SuStaIn seems to outperform GPSI at early stages. 

----