# No show on appointment predictor

Analysis of the Appointments No-Show dataset, based on medical appointments data in Brazil. Particularly, investigating if there are any factors that influence the appointment attendance (independent variable).

This dataset required some wrangling to address: missing data, correcting data types, removing outliers, and fixing miss-entries. Since the response class is very unbalanced (4:1 ratio), we used an oversampling technique (SMOTE) to avoid model overfitting.

After investigating which variables correlate to the attendance rate, and performing some feature engineering to create dummy variables, we conduct a Recursive Feature Elimination with Cross-Validation to identify the most important explanatory variables.

Finally, the Logistic Regression model is fitted and evaluated.


## Tech Stack

**Python:** Pandas, Numpy, Matplotlib, Statmodels, Scikit-Learn, Jupyter Notebook, imblearn

**Model:** Logistic Regression: Odds Ratio, Confusion Matrix,
Oversampling (Synthetic Minority Oversampling Technique - SMOTE)


## Author

- [@Zarich12](https://www.github.com/Zarich12)


## Key Findings

* Gender does not seem to have any impact with the attendance rate;
Age groups:
* Less than 5 years and over 45 years old: seems to be more likely to show up
* Between 5 and 45 years old: seems to be less likely to show up
Date difference between appointment and when it was scheduled:
* Appointments scheduled up to 4 days in advance: seems to be more likely to show up
* Appointments scheduled more than 7 days in advance: less likely to attend
Neighborhood groups:
* Group 1 (Jardim Camburi, Jardim da Penha, Santa Martha): seems to be more likely to show up
* Group 2 (Itararé, Jesus de Nazareth, Santos Dumont): seems to be less likely to show up
* Patients receiving Scholarship (Bolsa Familia) are less likely to show up;
* Medical Conditions: patients suffering from alcoholism and diabetes seems to be slightly more likely to attend
* SMS reminder: even though there is evidence receiving an SMS reminder seems to make the patients less likely to show up, we should ignore this variable due to lack of explainability.


## After Logistic Regression Insights
After fitting a Logistic Regression model, we ended up with 12 best performing and statistically significant explanatory variables. Their coefficients have the correct expected signal, based on the initial analysis.
According to the Odd's ratio analysis, we are able to rank the features based on their impact on the attendance rate:

* Appointments scheduled less than 4 days in advance are 2.3 times more likely to attend;
* Patients between the ages of 13 and 21 years old were 1.6 times less likely to show up;
Tied in third place being 1.5 times less likely to show up:
* Appointments scheduled more than 7 days in advance
* Patients between the ages of 21 and 30 years

Tied in the forth place being 1.4 times less likely to show up
* Patients within the ages of 5 to 13 years were 1.4 times less likely to show up;
* Patients residing in one of the neighborhoods in Group 2 (Jesus de Nazareth, Itarare, Santos Dumont)

Tied in fifth place being 1.3 times more likely to show up:

* Patients residing in one of the neighborhoods in **Group 2** *(Jesus de Nazareth, Itarare, Santos Dumont)*
* Patients between age 37 and 45 years

Tied in sixth place, being 1.2 times less likely to show up:

* Patients participating in the governmental assistance program (scholarship: Bolsa Familia)
* Patients with diabetes
* Patients between the ages of 30 to 37 years

Tied in seventh place, being 1.1 times more likely to show up to their scheduled appointment:
* Patients residing in one of the neighborhoods in Group 1 (Santa Martha, Jardim da Penha, Vila Rubim) are 1.1 times more likely to attend.
* Patients between 59 and 68 years old
* Patients between 68 and 102 years old

## FAQ

#### Can you merge the variables with simmilar impact?

It is possible to see that some variables actually have a similar impact. These age groups could be merged together and the dummy variable would still be able to capture its influence.

#### What is the accuracy of your Logistic Regression Model?

The final Logistic model is quite pessimistic, making several predictions that a patient would NOT show up for their appointment, but only getting it right 30% of the time. By contrast, the model doesn't make as much positive predictions as it should - since the vast majority of outcomes in the testing sample is positive.

Interestingly, this suggests the synthetic generated observations in our training sample (in order to balance the classes) did indeed protect the model from overfitting. This seem to be a good approach for handling datasets with unbalanced classes.

Overall, the Logistic model predicts the right outcome 63% of the time. Which is better than flipping a coin, but still has room for improvement before it can be considered useful.

#### What are some recommendations for future Research?

The advantage of using a Logistic Regression model is it's explanatory power: it allows for interesting inference capabilities such as Odd's Ratio and Elasticity analysis. Although it lacks prediction accuracy power.

For this particular case study, the inference power of the Logit model is rendered useless, since the doctors cannot control the characteristics of their patients. Their main goal is to accurately predict whether or not a patient is going to show up for their scheduled appointment.

Therefore, it would be interesting to fit the data using more advanced methods, such as Naive Bayes, Support Vector Machine (SVM), Boosting, Random Forest, and even Artificial Neural Network.
## 🚀 About Me
- 🌱 I’m currently learning Machine Learning and Data Science using python
- 💞️ I’m looking to collaborate on any development project
- 📫 How to reach me: richieans12@gmail.com


