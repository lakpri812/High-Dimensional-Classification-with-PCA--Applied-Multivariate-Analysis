# High Dimensional Classification with PCA

Project Overview: 
A thorough analysis of the Human Activity Recognition Using Smartphones Dataset was conducted in view of solving challenges of high-dimensional feature spaces for classification. The project exemplifies the application of reduction techniques such as PCA and Kernel PCA to enhance classification performance.

The data acquisition and preparation part is elaborated as follows: 

### 1. Data acquisition and preparation in detail. 
- The Human Activity Recognition Using Smartphones Dataset has 7352 training observations and 561 numeric features. 
- The dataset has motion sensor readings (accelerometer and gyroscope) from smartphones that 30 subjects wore. 
- There were six classes for activity: walking, walking upstairs, walking downstairs, sitting, standing, and laying. 
- The feature names and activity labels were loaded for the proper assignment of column names. 
- The training data (features, activities, subjects) was combined to form a unique dataset (70% of data). 
- The test data were combined in the same way (30% of data). 
- Activities (numeric) were replaced with descriptive labels. 
- It was confirmed that the dataset was already standardized, with features scaled and bounded between -1 and 1. 
- It was confirmed that there were no null values or duplicates in the dataset.

#### 2.Exploratory Data Analysis
- Detailed EDA was carried out to gain insight into the distribution of features and relationships.
- Plots were developed to visualize instances in each class and the distribution of each feature.
- Boxplots to see the standardization, Heatmap to see high correlation between data, Stacked bar plot to see balanced data throughout participants, Histogram to see count of each activity.
- Initial application of PCA to gain insight into the inherent dimensionality of the data. Static and dynamic activities perfectly separated.
- The proportion of variance explained by the principal components was examined. Just 27 PCs sufficient for 80% of variance.
- It was found that around 65 principal components explain more than 90% of the variance.
- A scree plot was developed to visualize the cumulative explained variance.
- The loading structure of the first two principal components was analyzed to determine which features contributed the most.
- Biplots were developed to visualize the relationships between features and observations.
- UMAP and t-SNE were applied for non-linear dimensionality reduction and visualization of class separability.

### 3. Baseline Model Development
- Multiple logistic regression (MLR) was taken as a baseline classification model
  - Applied to the entire 561-feature dataset
  - Experienced underfitting issues (19.43% training accuracy, 19.63% test accuracy)
  - Metrics computed for each activity class include precision, recall, and F1 scores
  - Generated and analyzed confusion matrices

- Linear Discriminant Analysis (LDA) was the second baseline approach
  - Again applied to the entire feature set.
  - Although very accurate, signs of overfitting were present (98.32% training accuracy, 97.96% test accuracy)
  - Collinearity warnings regarding redundant features were raised
  - Has computed the performance metrics quite elaboratively for every activity class

### 4. Dimensionality Reduction using PCA
- Principal Component Analysis was applied for the reduction of 561 features into a manageable set. 
- Chose the number of components to retain based on explained variance.
- Choose that number of components which explains around 90% variance.
- The training and test datasets were transformed accordingly using the selected principal components.
- The classification models were reassessed in the PCA-reduced feature space.

- MLR with PCA:
   - Better results were obtained (92.33% training accuracy, 91.03% test accuracy)
   - There was some slight overfitting but a huge improvement over the baseline MLR
   - Revised confusion matrices and performance metrics generated

- LDA with PCA:
   - Achieved a good compromise (86.95% training accuracy, 85.1% test accuracy).
   - Compared with baseline LDA, less overfitting was observed.
   - Calculated precision, recall, and F1 scores specific for classes.

### 5. Advanced Dimensional Reduction with Kernel PCA
- Kernel PCA with RBF kernel is implemented to capture non-linear relationships of the data.
- Used to address the limitation of linear PCA.
- Analyzed how kernel PCA spreads variance across components.
- Found that around 8 kernel PCs were sufficient to explain 80% of variance.
- Applied classification models on kernel PCA-reduced features.

- MLR with Kernel PCA:
   - Resulted in underfitting (31.7% training accuracy, 26% test accuracy)
   - Classwise performance metrics were analyzed

- LDA with Kernel PCA:
   - Also underfitted (24.89% training accuracy, 32% test accuracy)
   - Not better than the standard PCA approaches.

### 6. Conclusive Comparison and Exposition of Models
- All six approaches used in modeling were compared (MLR/LDA unaugmented, PCA, and Kernel PCA).
- The modeling were evaluated on training and test accuracy and tendencies to overfitting/underfitting.
- Discussion and plots about precision, recall, and F1 scores for the recognition of each activity class were created.
- The modeling approach which gave the best compromise was determined to be LDA with PCA.
- Fair generalization without overfitting.
- Test accuracy high (85.1%).
- Well handles the curse of dimensionality.

### 7. Curse of Dimensionality Analysis
- How the curse of dimensionality appeared in this dataset was recognized and documented.
- During the LDA classification, we observed collinearity warnings referring to redundant features.
- Scree plots were used to demonstrate that most features contributed minimal unique information.
- The reason behind the necessity of dimensionality reduction for effective classification was given.
- Demonstrate how PCA tackled these problems by lowering computational complexity while safeguarding vital information.

## Key Findings and Conclusions
- LDA with PCA produced the best overall performance with optimal balance between complexity and accuracy.
- Basic MLR seriously underfitted the data while basic LDA overfitted, illustrating the need for reduction of dimensionality.
- PCA drastically improved MLR performance, creating a more balanced LDA.
- In this dataset, Kernel PCA failed to improve upon linear PCA, suggesting the relationships were effectively captured by linear PCA.
- Successfully demonstrated how dimensionality reduction resolves the curse of dimensionality in high-dimensional classification tasks.

## Technological Stack and Tools
- R programming language
- Packages: caret, e1071, ggplot2, tidyverse, factoextra
- Statistical methods: PCA, Kernel PCA, Linear Discriminant Analysis, Multiple Logistic Regression
- Dimensionality reduction: PCA, Kernel PCA, UMAP, t-SNE
- Evaluation metrics: Accuracy, Precision, Recall, F1-score, Confusion matrices

In the future, we hope to 
- Develop more advanced kernel methods for Kernel PCA (polynomial and neural network);
- Implement advanced models such as XGBoost to boost the accuracy and minimize overfitting;
- Consider the addition of dynamic activities for enhancing model robustness;
- Put into consideration the classification of activities in real time on mobile devices;
- Personalize models for individual users.

This human activity recognition project aptly showcases the real-world applications of dimensionality reduction techniques for high-dimensional data classification problems, with ramifications for wearable technology and health monitoring systems.


