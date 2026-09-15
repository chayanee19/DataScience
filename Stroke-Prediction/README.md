# Stroke Risk Prediction

Strokes are caused by blocked blood flow to the brain (ischemic stroke) or sudden bleeding in the brain (hemorrhagic stroke). Many things raise your risk of stroke. Some of these risk factors can be changed to help prevent a stroke or future strokes.

Factors that can control account for 82% to 90% of all strokes:
- High blood pressure
- Obesity
- Physical inactivity
- Poor diet
- Smoking

Other risk factors are based on lifestyle, genetics, and environment.

**Age**, the risk is higher for babies under the age of 1 and for adults as they grow older.\
**Anxiety, depression, and high stress levels**, as well as working long hours and not having much contact with family, friends, or others outside the home, may raise your risk for stroke.\
**Family history and genetics** play a role as well. Your risk of having a stroke is higher if a parent or other family member has had a stroke, particularly at a younger age. Certain genes affect your stroke risk, including those that determine your blood type. People with blood type AB (which is not common) have a higher risk.\
**Living or working in areas with air pollution** can also contribute to stroke risk.\
**Other medical conditions**, such as sleep apnea, kidney disease, and migraine headaches, are also factors.\
**Other unhealthy lifestyle habits**, including drinking too much alcohol, getting too much sleep (more than 9 hours), and using illegal drugs such as cocaine, may raise stroke risk.\
**Race and ethnicity** is another factor. In the United States, stroke occurs more often in Black, Alaska Native, American Indian, and Hispanic adults than in white adults.\
**Sex** can play a role in risk for stroke. At younger ages, men are more likely than women to have a stroke. But women tend to live longer, so their lifetime risk of having a stroke is higher. Women who take birth control pills or use hormone replacement therapy are at higher risk. Women are also at higher risk during pregnancy and in the weeks after giving birth. High blood pressure during pregnancy — such as from preeclampsia — raises the risk of stroke later in life.\
**Viral infections or conditions**, such as lupus or rheumatoid arthritis, can cause inflammation.

Information link : https://www.nhlbi.nih.gov/health/stroke/causes




# Conclusion
**ROC (Receiver Operating Characteristic) Curve** is a graphical method used to evaluate the performance of classification models. It illustrates the trade-off between the **True Positive Rate (TPR)** and the **False Positive Rate (FPR)** at different classification thresholds.

**AUC (Area Under the ROC Curve)** represents the area under the ROC curve and provides an overall measure of a classification model's ability to distinguish between the positive and negative classes.

A good classification model should achieve a **high True Positive Rate** while maintaining a **low False Positive Rate**. Therefore, a higher AUC generally indicates better overall discriminatory performance.

Based on the ROC curve, **Logistic Regression achieved the highest AUC among the three models**, indicating that it had the best ability to distinguish between patients with and without stroke in this dataset. Therefore, Logistic Regression was selected as the best-performing model among **Logistic Regression, Decision Tree, and Random Forest** for stroke prediction in this study.

The **p-values** from the statistical comparison also indicated that the performance differences among the three models were **statistically significant**.
