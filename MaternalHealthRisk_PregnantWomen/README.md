# Maternal Health Risk Prediction Using IoT Vital Signs

## 1. Project Overview

This project aims to predict the **maternal health risk level** of pregnant women using six easily collected health measurements:

* Age
* Systolic Blood Pressure (SBP)
* Diastolic Blood Pressure (DBP)
* Blood Sugar (BS)
* Body Temperature
* Heart Rate

The dataset contains information from **1,014 pregnant women in rural Bangladesh** and classifies each woman into three risk levels:

**Low Risk | Mid Risk | High Risk**

The main goal is to investigate whether these simple health measurements can be used to support **early risk screening**, especially in areas where access to healthcare professionals and medical equipment may be limited.

---

# 2. Data Preparation

The original dataset contained **1,014 records**.

There were **no missing values** in the dataset.

However, some unusual Heart Rate values were identified. Using the IQR method, records outside the range of **60–90 beats per minute** were removed.

After removing these records, the dataset contained:

**919 records**

The six health measurements were then examined to determine whether they were related to maternal risk level.

---

# 3. Are the Health Measurements Related to Risk Level?

Before building the prediction models, statistical tests were used to determine whether the six features differed between the three risk groups.

Because the data did not follow a normal distribution, the **Kruskal-Wallis test** was used.

### Result

All six features showed statistically significant differences between the risk groups:

| Feature          | Result      |
| ---------------- | ----------- |
| Age              | Significant |
| Systolic BP      | Significant |
| Diastolic BP     | Significant |
| Blood Sugar      | Significant |
| Body Temperature | Significant |
| Heart Rate       | Significant |

All features had **p < 0.001**.

This suggests that **all six measurements contain useful information for distinguishing maternal risk levels**.

### Most important finding

Among the six features, **Blood Sugar showed the strongest statistical relationship with risk level**.

It was followed by:

1. Blood Sugar
2. Systolic Blood Pressure
3. Diastolic Blood Pressure
4. Other health measurements

Therefore, blood sugar and blood pressure appear to provide particularly useful information for identifying differences in maternal risk.

---

# 4. Class Distribution

The three risk groups were not perfectly balanced.

| Risk Level | Percentage |
| ---------- | ---------: |
| Low Risk   |        40% |
| Mid Risk   |        34% |
| High Risk  |        25% |

Although the classes were somewhat imbalanced, each group contained enough observations for model training and evaluation.

SMOTE was also tested to increase the number of minority-class observations.

However, the SMOTE-based Random Forest model achieved only **69.6% accuracy**, so this approach was not selected as the main model.

---

# 5. Model Development

Three machine-learning models were compared:

* **K-Nearest Neighbors (KNN)**
* **Support Vector Machine (SVM)**
* **Artificial Neural Network (ANN/MLP)**

The models were trained using standardized features.

Model parameters were selected using **stratified 5-fold cross-validation**, and the final performance was evaluated using a separate test set containing **276 records**.

---

# 6. Model Performance

| Model   | Test Accuracy | High-Risk Recall | Mid-Risk Recall | Low-Risk Recall |
| ------- | ------------: | ---------------: | --------------: | --------------: |
| **KNN** |     **77.9%** |              86% |         **72%** |             77% |
| ANN     |         72.5% |          **87%** |             60% |               — |
| SVM     |         69.6% |                — |             61% |               — |

### Best Model: KNN

The **KNN model achieved the highest accuracy at 77.9%**.

It also provided the most balanced performance across the three risk groups.

The best KNN model used:

**k = 1**

This means that the prediction was based on the closest observation in the training data.

---

# 7. What Did the Models Predict Well?

One important pattern appeared across the models.

### High-risk cases were easier to identify

The models generally performed well when identifying **high-risk pregnancies**.

For example:

* KNN correctly identified **86%** of high-risk cases.
* ANN correctly identified **87%** of high-risk cases.

This is an important result because correctly identifying high-risk cases can help healthcare workers prioritize women who may need further medical assessment.

### Mid-risk cases were more difficult

The **mid-risk group was consistently the hardest class to predict**.

For example:

* KNN: 72% recall
* SVM: 61% recall
* ANN: 60% recall

This may be because mid-risk cases have health measurements that are more similar to either low-risk or high-risk cases.

In other words, the boundary between the three groups is not always clear.

---

# 8. What Do These Results Mean?

## 8.1 The six health measurements contain useful information

The statistical analysis showed that all six measurements were significantly associated with maternal risk level.

This means that measurements such as blood pressure, blood sugar, age, temperature, and heart rate can provide useful information when assessing maternal health risk.

---

## 8.2 Blood Sugar appears to be particularly important

Blood sugar showed the strongest statistical difference between the three risk groups.

The Kruskal-Wallis test produced:

**F = 245, p ≈ 6.6 × 10⁻⁵⁴**

This indicates a very strong statistical association between blood sugar and risk level in this dataset.

However, this does **not** mean that blood sugar alone causes maternal risk.

It means that blood sugar values were strongly different across the risk groups in this dataset.

---

## 8.3 A simple model can provide useful predictions

The best model achieved approximately **78% accuracy** using only six health measurements.

This suggests that machine learning could potentially be useful as a **screening or decision-support tool**.

Because the dataset uses relatively simple measurements, this approach could be interesting for healthcare environments where more advanced medical resources are limited.

However, the model should be considered a **supporting tool rather than a replacement for medical professionals**.

---

## 8.4 KNN performed better than more complex models

An interesting finding was that KNN performed better than both SVM and ANN.

This shows that a more complex model does not always produce better results, particularly when working with a relatively small tabular dataset.

For this dataset:

**KNN → 77.9%**
**ANN → 72.5%**
**SVM → 69.6%**

Therefore, the simpler KNN model was the best-performing approach.

---

# 9. Key Findings at a Glance

### All six measurements were useful

Age, blood pressure, blood sugar, body temperature, and heart rate all showed significant differences between maternal risk groups.

### Blood sugar had the strongest association

Blood sugar showed the strongest statistical relationship with maternal risk level, followed by blood pressure.

### KNN was the best model

KNN achieved the highest test accuracy:

**77.9%**

### High-risk cases were detected well

KNN identified approximately **86% of high-risk cases**.

### Mid-risk cases were difficult

Mid-risk cases were more difficult to distinguish from low- and high-risk cases.

This is the main weakness of the current models.

---

# 10. Limitations

Several limitations should be considered.

### 1. The dataset is relatively small

The final dataset contained 919 records, which is relatively small for developing a healthcare prediction system.

### 2. The data come from one dataset

The data were collected from pregnant women in rural Bangladesh. Therefore, the results may not automatically apply to other populations or healthcare settings.

### 3. Accuracy is not enough for clinical use

Although KNN achieved 77.9% accuracy, approximately **22% of test cases were still classified incorrectly**.

Therefore, the model should not be used as the only basis for making medical decisions.

### 4. Mid-risk classification needs improvement

The model had difficulty distinguishing mid-risk cases.

Future work should investigate why these cases overlap and whether additional features could improve their classification.

---

# 11. Conclusion

This project shows that **maternal health risk can be predicted to some extent using six basic health measurements: age, blood pressure, blood sugar, body temperature, and heart rate.**

All six measurements showed significant differences between maternal risk groups, with **blood sugar showing the strongest statistical association**, followed by blood pressure.

Among the machine-learning models tested, **KNN performed best**, achieving **77.9% accuracy** on the independent test set and providing relatively balanced performance across the three risk groups.

The model was particularly effective at identifying **high-risk cases**, while **mid-risk cases remained more difficult to classify**.

Overall, the results suggest that a simple machine-learning model could potentially support **early maternal risk screening**, particularly in resource-limited settings. However, the model should be used as a **decision-support tool alongside healthcare professionals**, rather than as a replacement for clinical assessment.

**In summary:**

> **Simple health measurements + machine learning can provide useful information for maternal risk screening, but further validation and improvement are needed before clinical use.**
