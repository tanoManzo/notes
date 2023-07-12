
The Healthy People 2030 initiative [60], developed by the US Department of Health and Human Services, describes SDOH as "the conditions in the environments where people are born, live, learn, work, play, worship, and age that affect a wide range of health, functioning, and quality-of-life outcomes and risks." 

They grouped SDOH into five key domains: 
	1) economic stability [19, 119], 
	2) education access and quality [54, 75], 
	3) health care and quality [65], 
	4) neighborhood and built environment [76, 93], and 
	5) social and community context [26, 91].

Population health studies have identified many SDOH to be strongly correlated with acute and chronic conditions [6, 39, 42, 47, 105]. SDOH are also underlying, contributing factors of health disparities (e.g., poverty [33, 48, 131], unequal access to health care [26, 36], low educational attainment [8, 37, 54], and segregation [23, 110]). **However, to date, there has been less focus in the ML community to include SDOH in common EHR prediction tasks because many SDOH measures are poorly collected, lack granularity, or are simply unavailable.**

In this work, we investigate the impact of incorporating SDOH features on common EHR prediction tasks in the intensive care unit (ICU). We first link MIMIC-IV [70], a publicly available EHR database, to external SDOH databases based on patient zip code.

We then train models on the common tasks of mortality and readmission risk, evaluating the contribution of SDOH as compared to the EHR data alone. We find that adding SDOH does not improve model performance in the general patient population. We do note that, as compared to the EHR data alone, incorporating SDOH can lead to better-calibrated and fairer models in specific subgroups, with varying levels of contribution depending on the population and predictive task.

Our work makes three main contributions. • We release a publicly accessible database that combines EHR data with SDOH measures. To the best of our knowledge, this is the first public EHR database that contains structural features that span all five defined SDOH domains. The database will enable new studies on the relationship between community health and individual clinical outcomes. • We investigate the impact of incorporating SDOH in predictive models across three tasks, three model classes, and six patient populations. We find that the inclusion of SDOH can improve performance for certain vulnerable subgroups. • We demonstrate that SDOH features enable more fine-grain audits of algorithmic fairness, reporting the FPR parity – the difference in false positive rates (FPR) – across intersectional patient subgroups.

Discussion 

Overall, our analysis validates previous findings that community level SDOH features do not improve the accuracy of clinical prediction tasks [29] in both a multi-year cohort and a geographically diverse cohort. 

The healthcare system plays a vital role in collecting, using, and sharing actionable SDOH data [99]. To facilitate this effort, providers and operations staff across care settings should focus on actions that enhance the standardization and integration of SDOH data. Organizations such as the Office of National Coordinator for Health IT (ONC), the Joint Commission, and Health Level Seven International (HL7) are all leading efforts to further SDOH interoperability and standards [102, 112]. It should also be a focus to provide sufficient training and education for the staff who are collecting and encoding the data from the patients while adhering to cultural competency, privacy, and confidentiality standards [89].


A promising direction forward is to look beyond the clinical walls and understand the conditions that affect the health of the people upstream [88]. The growing evidence around the association between SDOH and health outcomes calls for targeted action, but there is a lack of consensus on what interventions would work [88]. Progress in evidence-informed policymaking requires a commitment to enhancing our current understanding of how SDOH affect different populations and ways to measure the effectiveness of interventions targeting specific SDOH domains. Thus, community-level SDOH features are essential for evaluating and monitoring health disparities [111]. By evaluating fairness using intersectional social identities, we could better account for the socially constructed nature of protected attributes such as race and gender. Capturing SDOH provides information on the social processes that created health disparities in the first place [26, 54, 81]. Audits of biases from the lens of SDOH are also more actionable because these features are not social constructs but modifiable factors that can be addressed [111].

Future Work

While our work shows that the inclusion of SDOH has minimal impact on three common EHR prediction tasks in the general patient population, they could be more helpful in other tasks and patient groups. Specifically, we did not include any phenotype prediction tasks. Given the associations between SDOH and chronic diseases [6, 31], it is possible that SDOH features are good risk predictors for specific comorbidities. In addition, SDOH could be important to account for in the estimations of treatment effects, which several studies have done using the MIMIC database but without SDOH data [67, 77, 142].

CONCLUSION

This work advances our understanding of the impact of SDOH on health prediction. First, we develop a new EHR-SDOH dataset by linking a popular EHR database, MIMIC-IV, to public community level SDOH databases. This dataset can be used to uncover underlying trends between community health and individual health outcomes and provide more benchmarks for evaluating bias and fairness. Second, we demonstrate that incorporating SDOH features in certain vulnerable subgroups can improve model performance. The value of adding SDOH features, however, is dependent on the characteristics of the cohort and the prediction task. Third, we highlight that algorithmic audits conducted through the lens of SDOH are more comprehensive and actionable. However, the lack of access to high-resolution, individual SDOH data is a limitation of the study. To address this, future work should focus on collecting individual-level SDOH features and accounting for them in analyses to address patient needs better and promote health equity.

#research 