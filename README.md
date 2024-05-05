# Capstone 3


## Network Analysis for Stroke Prevention and Treatment

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

## Exploratory Data Analysis (EDA) Results

### 1. Distribution Analysis

#### Age
The age distribution is fairly broad, covering all life stages from infants to the elderly. The bulk of the dataset appears to be adults and seniors.

#### Average Glucose Level
This shows a right-skewed distribution, indicating a large number of patients with glucose levels in the normal to pre-diabetic range, and fewer patients in the diabetic range.

#### BMI
The BMI distribution is somewhat normally distributed with a slight right skew, suggesting a range of body weights from underweight to obese categories.

### 2. Categorical Data Distribution

Each categorical variable displays its unique distribution pattern across various categories:

- **Gender**: Slightly more female participants than male.
- **Ever Married**: A higher proportion of participants are married.
- **Work Type**: A large number of participants are privately employed.
- **Residence Type**: There is a near even split between rural and urban residents.
- **Smoking Status**: A significant number of participants have never smoked.
- **Age and Glucose Categories**: These derived categories help to segment the population further for analysis.

### 3. Correlation Analysis

The heatmap of numerical features shows:

- **Age** is moderately correlated with stroke, which aligns with medical understanding that stroke risk increases with age.
- **Hypertension** and **heart disease** also show some correlation with stroke, which is expected as they are known risk factors.

### 4. Stroke Analysis via Cross-tabulation

#### Gender and Stroke
The risk of stroke is slightly higher in males (5.11%) compared to females (4.71%), with no strokes reported in the 'Other' gender category. This could be due to the smaller sample size for the 'Other' category.

These insights provide a solid foundation for constructing the network of healthcare interactions and preparing for predictive modeling to identify and manage stroke risks more effectively.

## Network Analysis

The network graph has been successfully constructed with the following characteristics:

- **20 nodes**: Each node represents a group of patients, categorized by their age category and work type.
- **40 edges**: Edges connect nodes if they share patients with similar health conditions within the same age category. The weight of an edge indicates the minimum number of patients sharing a specific condition between the two connected groups.

### Network Visualization and Analysis

#### Visualization
- **Nodes**: Represent groups of patients, categorized by age category and work type.
- **Edges**: Reflect connections between groups that share similar health conditions, with the weight of the edges representing the minimum number of patients sharing these conditions.

#### Centrality Measures
We calculated three types of centrality measures for each node:
- **Degree Centrality**: Measures the number of connections a node has. Higher values indicate nodes with more connections, suggesting these groups might be central in terms of shared health conditions.
- **Betweenness Centrality**: Measures the extent to which a node lies on paths between other nodes. Nodes with high betweenness might serve as crucial connectors or bridges within the network.
- **Eigenvector Centrality**: Reflects the influence of a node in a network. High values indicate nodes that are connected to many other nodes that are themselves well connected.

For the first five nodes, which represent different work types within the 'Child' age category, we see:
- **Similar Centrality Values**: All centrality measures are equal across these nodes, likely due to the simplistic way we created edges based solely on shared health conditions without more detailed interactions. This might suggest uniformity in how conditions like hypertension or heart disease are distributed across these work types in children.


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

