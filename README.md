# Diagnosing Mental Health

# 1. Background

The Research Domain Criteria (RDoC) is a framework developed by the National Institute of Mental Health (NIMH) that aims to describe functioning across several psychological domains and neurobiological levels of analysis. To a degree, the domains and techniques specified by the RDoC matrix reflect current research priorities and may influence the scope of planned research programs. The RDoC matrix originally included five domains: (1) negative and (2) positive valence; (3) cognitive systems; (4) social processes; and (5) arousal and regulatory systems. In January 2019, a sixth sensorimotor systems domain focusing on motor control and learning was added to the RDoC.


The overarching objective of this project is to provide a testbed for exploring the supposition that adding motor and sensory domains to the original RDoC Domains better captures heterogeneity within a mental health disorder. We also aim to test the relative descriptive success of these domains separately (motor; sensory; original RDoC) as well as combined.

# 2. Data and cleaning
Data was collected from 32 youth with autism spectrum disorder(ASD); 26 with developmental coordination disorder (DCD); and 34 typically developing (TD) controls, all matched for age, gender, and full scale IQ. 

It included behavioral assessments, self-report, and parent-report measures that were mapped onto either (1) the original RDoC domains, (2) a motor domain, or (3) a sensory domain.

Subjects missing more than 15% of features overall or 10% from any single category were excluded from analysis. Missing data in the remaining subjects was
imputed using the mean value of the subject’s assigned group (ASD, DCD, TD) for that feature. For each decoder (ASD vs. TD and ASD vs. DCD), the data was randomly split into 2,000 cross validation train/test sets (at a rate of 80%/20%) using stratified sampling such that each target class was proportionally represented in each split.

# 3. Model Building

We utilized a linear support vector classifier (SVC) as it was fairly robust to small amounts of data. Univariate feature selection was performed for each of the initial 2,000 CV folds, and the frequency count – the total number of times a feature was selected across CV iterations, divided by the total number of iterations, 2,000, — was saved. This process was performed for each individual (RDoC, Motor, and Sensory) and combined (e.g., RDoC + Motor + Sensory) feature sets, as well as for each decoder (ASD vs. TD and ASD vs. DCD). Any feature that was selected in more than 5% of CV iterations was selected to train our final SVC.

Classification performance was assessed with Matthew’s Correlation Coefficient (MCC) and Balanced Accuracy (BAcc). MCC is recommended for class
imbalanced decoding problems where both classification successes (e.g., true positives) and classification errors (e.g., false positives) must be considered.


# 4. Model performance 

Motor and sensory features performed similarly to RDoC features in support vector classification of 30 ASD youth against 33 typically developing controls. Combining sensory with RDoC features achieved the best classification performance, with a Matthews Correlation Coefficient (MCC) of 0.949 and balanced accuracy (BAcc) of 0.971 ( p =0.00020, calculated against a permuted null distribution).

Sensory features alone successfully classified ASD (MCC=0.565, BAcc=0.773, p =0.0222) against a clinically relevant control group of 26 youth with DCD and were in fact required to decode against DCD above chance.



