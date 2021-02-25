# Data Analysis for the Systematic Literature Review of DL4SE

> *Last update:* August 22nd 2020; *Maintaned by* @danaderp, @cawatson, @kpmoran, @ncoop57

- [A List of Deep Learning in Software Engineering](https://github.com/WM-CSCI-435-F19/dl4se/edit/master/data/)
- [Data Mining Tasks for the SLR of DL4SE](https://github.com/WM-CSCI-435-F19/dl4se/tree/master/rapidminer)
- [Results & Arguments](https://github.com/WM-CSCI-435-F19/dl4se/tree/master/results/README.md)
- [Data Extraction and Taxonomy](https://github.com/WM-CSCI-435-F19/dl4se/blob/master/data/RQ-Taxonomy.xlsx)
- [Supplementary Data Extraction](https://github.com/WM-CSCI-435-F19/dl4se/blob/master/data/Supplementary%20Extraction%20Form.xlsx)

Data Analysis is the process that supports decision-making and informs arguments in empirical studies. Descriptive statistics, Exploratory Data Analysis (EDA), and Confirmatory Data Analysis (CDA) are the approaches that compose Data Analysis [(Xia & Gong; 2014)](https://www.emerald.com/insight/content/doi/10.1108/BIJ-08-2012-0050/full/html). An Exploratory Data Analysis (EDA) comprises a set of statistical and data mining procedures to describe data. We ran EDA to provide statistical facts and inform conclusions. The mined facts allow attaining arguments that would influence the Systematic Literature Review of DL4SE.

The Systematic Literature Review of DL4SE requires formal statistical modeling to refine the answers for the proposed research questions and formulate new hypotheses to be addressed in the future. Hence, we introduce DL4SE-DA, a set of statistical processes and data mining pipelines that uncover hidden relationships among Deep Learning reported literature in Software Engineering. Such hidden relationships are collected and analyzed to illustrate the state-of-the-art of DL techniques employed in the software engineering context.   

![Venue Distribution](https://wm-semeru.github.io/dl4se/results/descriptive/[venue]paper-distribution.png)

Our DL4SE-DA is a simplified version of the classical Knowledge Discovery in Databases, or KDD [(Fayyad, et al; 1996)](https://www.aaai.org/ojs/index.php/aimagazine/article/view/1230). The KDD process extracts knowledge from a DL4SE structured database. This structured database was the product of multiple iterations of data gathering and collection from the inspected literature. The KDD involves five stages:

1. *Selection*. This stage was led by the taxonomy process explained in section xx of the paper. After collecting all the papers and creating the taxonomies, we organize the data into 35 features or attributes that you find in the [repository](https://github.com/WM-CSCI-435-F19/dl4se/blob/master/data/Dl4SE-Dataset.csv). In fact, we manually engineered features from the DL4SE papers. Some of the features are venue, year published, type of paper, metrics, data-scale, type of tuning, learning algorithm, SE data, and so on.   
2. *Preprocessing*. The preprocessing applied was transforming the features into the correct type (nominal), removing outliers (papers that do not belong to the DL4SE), and re-inspecting the papers to extract missing information produced by the normalization process. For instance, we normalize the feature “metrics” into “MRR”, “ROC or AUC”, “BLEU Score”, “Accuracy”, “Precision”, “Recall”, “F1 Measure”, and “Other Metrics”. “Other Metrics” refers to unconventional metrics found during the extraction. Similarly, the same normalization was applied to other features like “SE Data” and “Reproducibility Types”. This separation into more detailed classes contributes to a better understanding and classification of the paper by the data mining tasks or methods.  
3. *Transformation*. In this stage, we omitted to use any data transformation method except for the clustering analysis. We performed a Principal Component Analysis to reduce 35 features into 2 components for visualization purposes. Furthermore, PCA also allowed us to identify the number of clusters that exhibit the maximum reduction in variance. In other words, it helped us to identify the number of clusters to be used  when tuning the explainable models.  
4. *Data Mining*. In this stage, we used three distinct data mining tasks: Correlation Analysis, Association Rule Learning, and Clustering. We decided that the goal of the KDD process should be oriented to uncover hidden relationships on the extracted features (Correlations and Association Rules) and to categorize the DL4SE papers for a better segmentation of the state-of-the-art (Clustering). A clear explanation is provided in the subsection “Data Mining Tasks for the SLR od DL4SE”. 
5.*Interpretation/Evaluation*. We used the Knowledge Discover to automatically find patterns in our papers that resemble “actionable knowledge”. This actionable knowledge was generated by conducting a reasoning process on the data mining outcomes. This reasoning process produces an argument support analysis (see this [link](https://github.com/WM-CSCI-435-F19/dl4se/tree/master/results)). 

We used RapidMiner as our software tool to conduct the data analysis. The procedures and pipelines were published in our repository.


![Meaningful Association Rules Recovered](https://wm-semeru.github.io/dl4se/results/association/association_rules.png)
Overview of the most meaningful Association Rules. Blue rectangles are Premises and yellow are Conclusions. An arrow connecting a Premise with a Conclusion implies that given some premise, the conclusion is associated. E.g., Given that an author used Supervised Learning, we can conclude that their approach is irreproducible with a certain Support and Confidence.

**Support = Number of occurrences this statement is true divided by the amount of statements**
**Confidence = The support of the statement divided by the number of occurrences of the premise**
