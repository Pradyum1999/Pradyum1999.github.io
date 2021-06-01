---
header:
  overlay_image: /assets/images/code.jpg
  caption: "Photo credit: [**Marcus Spiske**](https://unsplash.com)"
permalink: /portfolio/self-projects/
date: 2021-05-29
toc: true
toc_label: "Contents"
---

# Project 1: Predict Call Drop Category.

I finished this project in Apr'20. There is _no Github solution_ that I could find for this project. As such, every step & code was developed based on my own thinking which I believe strongly represents my understanding of applying ML concepts.

## Introduction
The data is captured for various service providers, at multiple locations, network types
3G, 4G, 2G, ratings, coorditanes etc. The data attached is for two different months. Predict Call Drop Category using ML algorithms.

## Data
* Call Drop Category: Target Variable. (3 different categories)
* Operator: Categorical (10 different categories) 
* Status: Categorical (3 categories: Indoor, Outdoor, Travelling)
* Network type: Categorical (4 categories: 2G, 3G, 4G, Unknown)
* Rating: Ordinal (1-5)
![rating](/assets/images/sp/rating.png)
* Latitude
* Longitude
* State Name

## Evaluation metric
**F-1 Score & Confusion Matrix plot**: F1 score is the harmonic mean of [precision](https://en.wikipedia.org/wiki/Precision_and_recall) & [recall](https://en.wikipedia.org/wiki/Precision_and_recall)

**Logic & sources**: 
* F1-score metric is used to find an equal balance between precision and recall, which is extremely useful in most scenarios when we are working with imbalanced datasets (i.e., a dataset with a non-uniform distribution of class labels). [here](https://sebastianraschka.com/faq/docs/computing-the-f1-score.html)

* Importance of balance between precision & recall. [here](https://developers.google.com/machine-learning/crash-course/classification/precision-and-recall)

* Intuition: For other similar self projects, I have used accuracy score, balanced score, roc-auc-score, r2-score (regr.). Through those projects, I have found f1 score to represent model variance explanation the best. 

## Algorithm attempts
Did dummy variable encoding.
* Null values: Only State names are missing & a huge number. Therefore, dropped State-name variable

![null](/assets/images/sp/null.png)

### Attempt 1: 
Linear regression & Label encoder. Dropped State-Name, Operator, Network-Type columns.

![linear](/assets/images/sp/attempt1.png)

### Attempt 2:
**Satisfactory** category prediction only attempt.

Applied **Logistic Regression**, found the coefficients

![logreg](/assets/images/sp/logreg.png)

**Metric**

![logreg](/assets/images/sp/logreg2.png)

![logreg](/assets/images/sp/confusion_matrix.png)

### Attempt 3:
Trying to predict all the 3 classes simultaneously.

**Two Methods**:

**Multi-label**: If classes are not mutually exclusive.

**Multi-class**: If classes are mutually exclusive.

In our case, the classes: (Poor network, Satifactory, Call Dropped) are mutually exclusive, therefore I went with multi-class classification. 
F1 Score was not up to mark. Accuracy Score: 0.75. Went ahead with Attempt 2.

# Project 2: ML model deployment.

I finished this project in Mar'20 after finishing my _IBM ML specilisation_ (Kindly see resume).
* Link to the app: [App Link](http://insurance-cost-model.herokuapp.com/); 
* If above link not working please copy-paste: http://insurance-cost-model.herokuapp.com/
* Link to the full repo: [github](https://github.com/Pradyum1999/Medical_Insurance_Cost_Model_Deployment)

## Introduction
Developing models is excellent, but, I received this particular advice multiple times: "Do not let your model sit on localhost! Deploy it!!"
As such, I picked up the Insurance Cost Prediction project & deployed it through Heroku.

## Data & Model Development
Data:- 
6 input variables (x): Categorical - 3 (gender, smoker, region), Numerical - 3 (Age, BMI, Children)
1 target variable (y): Insurance charges.

Model Development Steps:
* References
* Import Data
* EDA
* Missing Values Imputation (No null values here, but I have tried Mean, Median, Mode imputation in other projects of mine.)
* Data Split into training & testing
* ML model: Lasso Regression (Finalised)
* Accuracy (R2-Score: ~ 0.8 accuracy )

## Model Deployment:
* Model pickle -> Flask -> App -> Frontend -> Run & edit on localhost.
* Requirements.txt -> Procfile -> Heroku CLI -> git push heroku master!
<!------------------------------------ FOOTER -------------------------------->
