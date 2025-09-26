# Task-4-Classification-with-Logistic-Regression

1. Data Acquisition and Preparation (Pandas, Scikit-learn)
This project initiated with the acquisition of the Wisconsin Breast Cancer (Diagnostic) Dataset, a classic and highly imbalanced binary classification dataset. Using Pandas, the dataset was loaded and inspected, confirming 30 numerical features and the binary target variable (Malignant or Benign). The core preprocessing steps were executed using Scikit-learn: first, the data was partitioned into 70% training and 30% testing sets via train_test_split, ensuring stratification to maintain the original class proportion in both subsets. Crucially, all 30 features were then standardized using the StandardScaler. This standardization (Z-score normalization) is mandatory for Logistic Regression, as it ensures that all features contribute equally to the distance-based optimization process, promoting faster and more reliable model convergence.

2. Model Training and Interpretation (Scikit-learn)
The LogisticRegression model from Scikit-learn was initialized and trained on the standardized training data. Upon fitting the model, its intrinsic mechanism was partially revealed by examining the learned coefficients. These coefficients represent the impact of a one-unit change in a feature on the log-odds of the tumor being Benign. By analyzing the magnitude and sign of these coefficients, we could interpret which cellular characteristics (e.g., worst radius, mean concavity) were the strongest statistical predictors of malignancy or benignancy, confirming the model's adherence to known medical principles of the data.

3. Comprehensive Model Evaluation (Scikit-learn, Matplotlib)
The model's predictive power was thoroughly assessed on the held-out test set using a suite of quantitative metrics. The Confusion Matrix provided a breakdown of correct and incorrect predictions (True Positives, False Negatives, etc.). This foundation fed into the Classification Report, which delivered key operational metrics like Precision (the accuracy of positive predictions), Recall (the model's ability to find all positive samples), and the F1-Score. Furthermore, the model's overall discriminative capability was captured by the ROC-AUC score. This metric, visualized via the Receiver Operating Characteristic (ROC) curve using Matplotlib, demonstrated how well the model separated the two classes across all possible probability thresholds, showcasing its robustness independent of a single threshold choice.

4. Conceptual Core and Optimization (Scikit-learn, Matplotlib)
The final phase explored the theoretical and practical application of the classification process.  ​
I demonstrated threshold tuning using the Precision-Recall curve. In a critical domain like healthcare, the default 0.5 threshold may be insufficient. By analyzing the tradeoff, I showed how to strategically lower the threshold to prioritize Recall for the Malignant class, thereby minimizing the crucial False Negative rate (missed cancer diagnoses), even at the cost of accepting a slightly higher False Positive rate.

The Sigmoid Function (or Logistic Function) is the mathematical core of Logistic Regression; it is what differentiates it from simple linear regression.

What it is:
The sigmoid function, denoted as σ(z), is an S-shaped curve that takes any real-valued number as input and maps it to a value between 0 and 1.

The formula is:

σ(z)= 
1+e 
−z
 
1
​
 
where z is the output of the linear model (i.e., z=β_0+β_1x_1+⋯+β_nx_n).

Why it's necessary for Classification:
Probability Transformation: The linear part of the model (z) can output any number (e.g., −100 or +500). Since we need a classifier to output a probability—a value between 0 and 1—the sigmoid function forces this transformation.

Mapping to Likelihood:

If the linear output z is very large and positive, σ(z) approaches 1 (high probability of being Class 1).

If the linear output z is zero, σ(z) equals 0.5 (50/50 probability).

If the linear output z is very large and negative, σ(z) approaches 0 (high probability of being Class 0).

In simple terms: The linear model determines a "score" (z). The sigmoid function then converts that score into a smooth, interpretable probability of the event (like "Benign") occurring. This probability is then compared against your chosen threshold (default 0.5) to make the final binary classification.
