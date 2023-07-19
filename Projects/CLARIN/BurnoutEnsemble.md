*by Merhbene et al.*

## Abstract
Burnout, a state of emotional, physical, and mental exhaustion caused by excessive and prolonged stress, is a growing concern. It is known to occur when an individual feels overwhelmed, emotionally exhausted, and unable to meet the constant demands imposed upon them. Detecting burnout is not an easy task, in large part because symptoms can overlap with those of other illnesses or syndromes. This work demonstrates the effectiveness of NLP and machine learning methods in detecting indicators for burnout.

## Intro

Stress at the workplace is an increasingly relevant topic. In a study involving almost 10,000 working adults in eight territories throughout Europe, it was found that 18% of the respondents feel stressed daily, and three out of ten participants feel so stressed that they have considered finding a new job ([ADP, 2018](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B1)).

A Swiss study ([SECO, 2015](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B36)) estimates that 24.2% of employees feel often or always stressed at their workplace, while 35.2% feel mostly (22.2%) or always (13%) exhausted at the end of the working day.

The Stress in America's Report of 2019 by the American Psychological Association shows that Americans consider a healthy stress level at an average of 3.8 (scale ranging from 1 to 10, where 10 is “a great deal of stress” and 1 is “little or no stress;”) however, they report having experienced an average stress level of 4.9 ([American Psychological Association, 2019](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B2)).

This stress can lead to workplace burnout. In 2019, the WHO included burnout in the 11th Revision of the International Classification of Diseases (ICD-11) as a syndrome.[1](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#note1) In particular, during the pandemic crisis, burnout in the healthcare sector was an important issue: it has been shown, for instance, that the COVID-19 crisis has had an overwhelming psychological impact on intensive care workers ([Azoulay et al., 2020](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B3)).

Identifying burnout syndrome is complex because symptoms can overlap with other diseases or syndromes ([Jaggi, 2019](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B20)). In particular, the overlap between depression and burnout is an important subject of scientific discussion, e.g., ([Schonfeld and Bianchi, 2016](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B34)).

In clinical intervention and field research, burnout is typically detected via the use of inventories. Potential burnout patients fill out a psychological test, usually in the form of a questionnaire with scaled-response answers (e.g., not at all, sometimes, often, very often). Although such inventories are used in most studies and are well-established in the clinical environment, major limitations have been identified. For example, in personality inventories, participants are liable to fake their results, e.g., ([Holden, 2007](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B19)). They may adapt their responses in high-stake situations in order to increase their chances for the desired outcome ([Lambert, 2013](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B23)). A further issue with inventories is known as extreme response bias (ERB); some respondents will tend to choose (or avoid) only the highest or the lowest options in such tests ([Greenleaf, 1992](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B16); [Brulé and Veenhoven, 2017](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B6)). It has also been shown that on self-reported tests for subjective well-being, the respondent's mood during testing sometimes contributes as a predictor ([Diener et al., 1991](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B14)). Furthermore, defensiveness (the denial of symptoms) and social bias can influence the outcome of inventories ([Williams et al., 2019](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B42)).


Previous studies have demonstrated promise in such methods ([Burisch, 2014](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B7)), but, in practice, the manual effort of analyzing the resulting data often results in untenable overhead costs. Fortunately, recent developments in the field of natural language processing (NLP) make approaches using such unstructured textual data feasible. It has been shown that computational linguistic markers can be used to predict depressivity of the writer ([Havigerová et al., 2019](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B17)). For example, such work concentrates on suicide risk assessment ([Morales et al., 2019](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B28)), ([Just et al., 2017](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B22)), depression ([Moreno et al., 2011](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B29)), ([Schwartz et al., 2014](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B35)), post-partum depression ([De Choudhury et al., 2013](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B11)), ([De Choudhury et al., 2014](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B12)), or different mental health signals ([Coppersmith et al., 2014](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B10)). In some cases, data from Reddit online forums have been used, for example, to detect mental health disorders ([Thorstad and Wolff, 2019](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B40)), anxiety ([Shen and Rudzicz, 2017](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B37)), or depression ([Tadesse et al., 2019](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B39)).

**Burnout detection in data extracted from issues and comments posted within software development tools have been studied ([Mäntylä et al., 2016](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B26)). The authors used the valence-arousal-dominance (VAD) model to study burnout risk in a corporate setting. This model distinguishes three emotions: _valence_ (“the pleasantness of a stimulus,”) _arousal_ (“the intensity of emotion provoked by a stimulus,”) and _dominance_ (“the degree of control exerted by a stimulus”) ([Warriner et al., 2013](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B41)). To measure burnout risk, the metric is based on low valence and dominance and high arousal ([Mäntylä et al., 2016](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B26)).**

The work in this article addresses the following objectives:
- It evaluates whether NLP methods applied to free text are an effective means to detect indicators for burnout, compared to a control group using general text samples, and a control group with depression-related texts.
- In particular, it investigates how the use of an ensemble classifier can leverage the accuracy of such methods.
- Furthermore, the approach is compared to single machine learning classifiers such as logistic regression.

###  Datasets for Experiments

Using the raw data consisting of 13,216 posts labeled _no burnout_ (control group), 352 labeled _burnout_, and 979 labeled _depression_, four datasets for use in the experiments were compiled. Dataset statistics are presented in [Table 1](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#T1).

Dataset 1: Burnout vs. No Burnout (BNB): It combines the 13,216 _no burnout_ posts with the 352 _burnout_ posts, resulting in a highly unbalanced dataset of size 13,568.

Dataset 2: Burnout vs. No Burnout (Balanced) (BNB-Balanced): Balanced dataset of 704 posts, of which, 352 posts are selected from the _no burnout_ dataset through random sampling (without replacement). Additionally, an equal number of 352 posts are added from the _burnout_ data.

Dataset 3: Burnout vs. No Burnout (No Keywords) (BNB-No-Keywords): It is obtained from Dataset 2 by removing the keywords from the _burnout_ dataset that were used during data collection to search for burnout-related posts: “burnout,” “burn-out,” “burning out,” etc.

Dataset 4: Burnout vs. Depression (BD): Balanced dataset of 704 entries, of which 352 posts are selected from the _depression_ dataset through random sampling (without replacement). Further, an equal number of 352 posts are added from the _burnout_ data.

## Discussion

The work presented in this article makes the following contributions:

• It demonstrates that NLP methods applied to free text are an effective means to detect indicators for burnout, measured against both a control group of general text and a group composed of text samples related to depression.

• A machine learning ensemble classifier trained on data from Reddit posts to detect burnout indicators with a promising accuracy is presented.

• A range of machine learning classifiers trained to detect burnout indicators are compared, showing in particular that the presented ensemble classifier outperforms two single classifier baselines: logistic regression classifiers trained on either a large unbalanced dataset or an undersampled balanced dataset. The best-performing model attained a balanced accuracy of 93%, F1 score of 0.43, and recall of 93% on unbalanced test data.

Clinical data also have the advantage of more closely resembling the data such models are expected to be applied to in the future. A first attempt of working with clinical data to detect burnout has shown promising results. By presenting a dataset from real-world burnout patient data, [Nath and Kurpicz-Briki (2021)](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B30) managed to go beyond typical burnout detection approaches, which usually includes the use of inventories with scaling questions and worked on applying NLP to mental health. The dataset consisted of data extracted from German-language interviews with burnout patients, a control group, and experts. The authors proceeded to train an SVM classifier on the dataset and ended up achieving accuracy greater than their original baseline.

Depression and burnout are not disjoint categories, and some degree of classification ambiguity is inevitable. This overlap is a significant object of scientific investigation, e.g., by [Schonfeld and Bianchi (2016)](https://www.frontiersin.org/articles/10.3389/fdata.2022.863100/full#B34). The work in this article provides evidence of the non-trivial nature of differentiating burnout and depression. Ongoing work of the authors aims to more closely analyze the markers that indicate and differentiate depression and burnout in free text first-person accounts.

### Data Availability Statement

The datasets presented in this article are not readily available because the collected online data can be subject to change (e.g., deletions) over time. A similar dataset can be created following the instructions in the article.