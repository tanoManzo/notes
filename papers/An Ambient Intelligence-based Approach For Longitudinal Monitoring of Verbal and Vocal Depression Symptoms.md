[[burn-out]]

Depression affects not only a person’s mood but also their speech patterns. Individuals with depression may exhibit changes in speech, such as slower speech rate, longer pauses, reduced pitch variability, and decreased overall speech fluency. 

To overcome these issues, we propose a one-shot learning framework for detecting depression relapse from speech. We define depression relapse as the similarity between the speech audio and textual encoding of a subject and that of a depressed individual. To detect depression relapse based on this definition, we employ a Siamese neural network that models the similarity between of two instances.

Major Depressive Disorder (MDD) is a mood disorder that has detrimental effects on an individual’s cognition, emotions, and daily functioning. It is primarily characterized by persistent feelings of sadness, anger, and loss of interest in activities. MDD is among the most prevalent mental disorder, impacting over 300 million people globally [14]. Furthermore, recent studies have indicated a significant rise in mental health issues, including anxiety, stress, and depression, during the COVID-19 pandemic [27].

previous research on relapse prediction primarily relies on clinical variables such as age, gender, medication types, number of episodes, symptom severity, cognitive markers, and medical image data [1, 4, 26, 25]. However, these approaches have overlooked other important attributes, such as the analysis of speech patterns and facial expressions.

In this paper, we propose a robust approach that deals with depression relapse data scarcity. The proposed approach is based on one-shot learning. We define depression relapse as the closeness of the speech encoding of a subject to that of a depressed subject. By modeling the similarity between two instances, Siamese neural network is chosen as a suitable candidate for depression relapse detection following the proposed definition. The proposed approach investigates the predictive power of audio and textual encodings of the speech for depression relapse prediction using Siamese neural network architecture. Three Siamese networks built using (1) MFCC audio features, (2) VGGish audio features, and (3) audio-textual fusion features are compared and investigated for the relapse identification task. To our knowledge, this work is the first to tackle the prediction of depression relapse based on verbal and non-verbal cues in a speech, and to employ one-shot learning for this task.


### review 

- **to correct, missing point (2):** The proposed framework is composed of four stages: (1) pre-processing audio data augmentation (section 3.1), (3) audio-textual features extraction (section 3.2), and (4) one-shot learningbased depression relapse detection (section 3.3). Each of these steps are detailed in the following.
- introduced too late, nor explained notation inside: Fig. 1: Proposed multimodal-based Siamese networks for depression relapse detection.
-  avoid to explain known concept. Just add reference etc. (e.g.,DFT, Hamming Window, )