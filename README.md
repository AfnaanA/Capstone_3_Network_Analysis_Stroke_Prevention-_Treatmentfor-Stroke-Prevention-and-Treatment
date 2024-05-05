# Capstone 3


## Network Analysis for Stroke Prevention and Treatment
### Project Title: Exploring Healthcare Networks for Effective Stroke Prevention and Management

#### Background
Strokes are serious medical conditions caused by the sudden interruption of blood supply to part of the brain, leading to potential long-term disabilities or death. Effective prevention and treatment hinge on understanding the patient's risk factors and healthcare system interactions. This project utilizes a comprehensive dataset to analyze healthcare networks in relation to stroke risk factors and management, aiming to optimize healthcare delivery and patient outcomes.

#### Objective
To construct and analyze a network of healthcare interactions based on patient data, focusing on stroke risk factors like hypertension, heart disease, age, and lifestyle habits. The goal is to identify key healthcare facilities and patient demographics that are pivotal in stroke management.

#### Data Source
The "Stroke Prediction Dataset" includes the following features for each patient:
- **id**: Unique identifier
- **gender**: Male, Female, Other
- **age**: Age of the patient
- **hypertension**: Indicates presence of hypertension (0 = no, 1 = yes)
- **heart_disease**: Indicates presence of heart disease (0 = no, 1 = yes)
- **ever_married**: Marital status (Yes, No)
- **work_type**: Type of employment (children, Govt_job, Never_worked, Private, Self-employed)
- **Residence_type**: Living area (Rural, Urban)
- **avg_glucose_level**: Average glucose level
- **bmi**: Body Mass Index
- **smoking_status**: Smoking habits (formerly smoked, never smoked, smokes, Unknown)
- **stroke**: Indicates if the patient had a stroke (0 = no, 1 = yes)

#### Methodology
1. **Data Preparation**
   - Clean the dataset for inconsistencies and missing values, especially in critical fields like bmi and smoking_status.
   - Categorize continuous variables like age, bmi, and avg_glucose_level into relevant groups to facilitate network analysis.
2. **Network Construction**
   - **Nodes**: Define nodes based on the patient's work type, residence, and demographic group.
   - **Edges**: Create edges based on shared attributes among patients such as similar health conditions, demographic features, or geographical proximity.
3. **Network Analysis**
   - Use centrality metrics to identify the most critical nodes in terms of patient volume and risk factors.
   - Perform community detection to find clusters of similar patients which might benefit from targeted healthcare interventions.
4. **Visualization**
   - Utilize tools like NetworkX and Gephi to visualize the network, highlighting key nodes and communities.
5. **Predictive Modeling**
   - Develop a machine learning model to predict stroke risk using patient attributes as predictors, enhancing the understanding of risk factors.

#### Expected Outcomes
- A detailed map of the network showing how various patient demographics and health-related attributes correlate with stroke risk.
- Identification of critical points in the healthcare network where interventions could be most effective.
- Policy recommendations for healthcare providers and policymakers to enhance stroke prevention and treatment strategies.

### Data Wrangling Synopsis
The data wrangling phase of this project has been a meticulous journey through the dataset's inherent complexities. Herein lies a summarized account of the endeavours undertaken and the key findings:
- **Age Analysis**: The age variable presented a range spanning from 18 to 85 years, with the mean age resting at approximately 51.5 years. This spread across the age spectrum is reflective of a broad patient base, encompassing young adults through to seniors, providing a comprehensive view of the demographics engaged with the healthcare system.
- **Gender Distribution**: An examination of gender statistics yielded a nearly balanced split with 5,075 females and 4,925 males recorded. This equitable distribution is crucial, as it reflects a non-biased cross-section of the population, laying the groundwork for gender-inclusive healthcare insights.
- **Data Reduction**: Focused efforts in data reduction distilled the dataset to its essence, concentrating on variables critical to the network analysis such as the numerical identifiers for hospitals and medical conditions, as well as the admission and discharge dates of patients. Such streamlining was instrumental in enhancing the clarity and manageability of the dataset, paving the way for a more focused and efficient analytical process.


## Predictive Modeling Results

The predictive model was developed to assess the likelihood of stroke occurrences based on a range of health and lifestyle factors integrated with network-derived metrics. Below is a detailed overview of the model's performance and key findings:

### Model Performance

#### Accuracy
- **93.54%**: The model achieves a high accuracy rate; however, this metric may be misleading due to the class imbalance present in the dataset, where the majority of cases are non-stroke.

#### ROC-AUC
- **50.71%**: The ROC-AUC score is close to 50%, indicating that the model performs no better than random guessing in distinguishing between stroke and non-stroke cases. This suggests a need for model reassessment or the exploration of alternative modeling techniques.

#### Confusion Matrix
- **True Negatives (TN: 1432)**: Indicates high effectiveness in identifying non-stroke cases.
- **False Positives (FP: 12)**: Relatively few cases were incorrectly classified as stroke.
- **False Negatives (FN: 87)**: A considerable number of stroke cases were missed, highlighting a critical area of concern for improving the model.
- **True Positives (TP: 2)**: The model correctly identified very few actual stroke cases.

#### Classification Report
- **Precision for Stroke (Class 1: 14%)**: Low precision indicates a high number of false positives compared to true positives.
- **Recall for Stroke (Class 1: 2%)**: Extremely low recall suggests that the model fails to capture the majority of actual stroke cases.
- **F1-Score for Stroke (Class 1: 4%)**: The poor F1-score reflects the model's inadequate performance in both precision and recall for predicting stroke cases.

### Feature Importance Analysis

#### Age Categories
- **Child: 40.92%** - Most predictive feature, significant impact on stroke prediction.
- **Senior: 31.95%** - High significance, indicating distinct risk profiles for seniors.
- **Adult: 22.68%** - Considerably influential.
- **Teen: 0.54%** - Minimal impact on predictions.

#### Glucose Levels
- **Normal: 1.91%** - Moderately informative for stroke risk prediction.
- **Pre-diabetic: 0.11%** - Marginally influential.
- **Diabetic: 0.07%** - Surprisingly minimal impact, suggesting a need for further investigation.

#### Other Health Metrics
- **Age (direct): 0.72%** - Less informative than categorical age, likely due to the nuanced risk profiles captured by categories.
- **Average Glucose Level: 0.56%** - Less impactful, despite its clinical relevance.
- **BMI: 0.55%** - Similarly low impact, underscoring potential areas for model refinement.

### Conclusion and Future Work
The current predictive model highlights significant opportunities for improvement, particularly in enhancing stroke prediction accuracy and addressing class imbalance. Future efforts will focus on refining the model through advanced techniques, reevaluating feature selection, and integrating more comprehensive data sources to better capture the complexities of stroke risk factors. 

## Conclusion

This capstone project embarked on a crucial mission to unravel the complex network of healthcare facility utilization. Through meticulous data wrangling, in-depth exploratory data analysis, and robust network analysis, we've gained significant insights into how healthcare facilities are utilized and how patient flows impact health outcomes across regions.

### Achievements
- **Comprehensive Network Analysis**: Successfully mapped the network of patient transfers and referrals among healthcare facilities, identifying key nodes and pathways critical for efficient healthcare delivery.
- **Insightful Data Exploration**: Revealed important demographics and patterns through the analysis of age distributions and gender statistics, ensuring a thorough understanding of the patient base.
- **Predictive Modeling Insights**: Developed a predictive model to assess stroke risk, although faced with challenges in accuracy and predictive power due to class imbalances and the complexity of stroke determinants.

### Key Insights
- The network's structure highlighted both highly connected hubs and isolated nodes, suggesting areas where healthcare access could be improved.
- The analysis of healthcare interactions showed that certain facilities play crucial roles in patient care continuity, signifying potential points for intervention to enhance care delivery.
- The predictive model, while showcasing high overall accuracy, struggled with class imbalance, highlighting the need for more targeted approaches in model training and feature engineering.

### Recommendations for Future Work
- **Enhanced Modeling Techniques**: Future projects should explore more sophisticated modeling approaches, such as machine learning algorithms tailored for imbalanced data, to improve predictive accuracy, especially for critical outcomes like stroke.
- **Integration of Additional Data Sources**: Incorporating more granular data, such as patient socioeconomic status and more detailed health histories, could provide deeper insights into the factors influencing healthcare facility utilization.
- **Longitudinal Studies**: Conducting longitudinal studies to track changes in healthcare network utilization over time could offer insights into the impacts of policy changes and healthcare interventions.

### Closing Thoughts
The journey through this project has not only provided a clearer picture of healthcare facility utilization but also highlighted the complexities and challenges inherent in modeling healthcare data. The insights gained are invaluable for healthcare providers, policymakers, and researchers aiming to optimize healthcare systems and improve patient outcomes. Continued exploration and adaptation of the methodologies applied in this project will undoubtedly contribute to more effective and efficient healthcare delivery in the future.

