Work done by: Farah Makkawi
For my part of the group project, I loaded and cleaned the dataset and created a simple visualization showing the distribution of BEV vs PHEV vehicles. Then I built a Logistic Regression model to predict whether an electric vehicle is a BEV or PHEV using Model Year, Electric Range, and Base MSRP. The accuracy and confusion matrix help evaluate the model performance. This completes my contribution.

“For my part, I started by loading the dataset and cleaning it. I removed missing values and only kept vehicles registered in Washington State. This helped make sure our model works with clean and reliable data.”

“Then I created a simple bar chart to show how many vehicles are BEV and how many are PHEV. As we can see, BEVs are much more common in the dataset. This is important because later the model predicts BEVs much better than PHEVs because it has more examples to learn from.” “This bar chart shows the number of Battery Electric Vehicles (BEVs) compared to Plug-in Hybrid Electric Vehicles (PHEVs) in the dataset. As we can see, there are much more BEVs than PHEVs.
This was important for us to notice because it explains why the Logistic Regression model predicted BEVs very accurately, but struggled with PHEVs — simply because the data has many more BEV examples to learn from.
So this EDA helped us understand the class imbalance before building the model.”

- “After that, I built a Logistic Regression model to predict whether a car is BEV or PHEV. I used three features: Model Year, Electric Range, and Base MSRP. The model achieved about 80.7% accuracy.”
- “For BEV vehicles (class 1), the model did very well.
 It had a precision of 0.81, recall of 0.99, and an f1-score of 0.89.
 This means that when the model predicts a car is BEV, it’s correct 81% of the time,
 and it successfully detects 99% of all BEV vehicles. So almost all BEVs were correctly classified.”
-“But for PHEV vehicles (class 0), the model struggled.
The recall is only 0.08, which means it correctly identified just 8% of PHEVs,
and it incorrectly classified most PHEVs as BEVs.”
-“The main reason is because the dataset is imbalanced — we have much more BEV data than PHEV, so the model learns to predict BEV more often. This is confirmed by the graph I showed earlier.”
-“In the confusion matrix, we can see that the model correctly predicted 41,789 BEVs,
but only 822 PHEVs were correctly detected.
It misclassified 9,953 PHEVs as BEVs, which is because the model tends to choose the majority class.”
-“So overall, the model is strong in predicting BEVs but weak for PHEVs because of the class imbalance. In future work, we could improve this by balancing the dataset or using different modeling techniques.”

One-Shot Version 
“The Logistic Regression model had 80.7% accuracy. It performed really well for BEVs with 99% recall but poorly for PHEVs with only 8% recall. This happened because there are many more BEV vehicles in the dataset, so the model learned to predict BEV more often. The confusion matrix shows this clearly—almost all BEVs were detected correctly, but most PHEVs were mistaken for BEVs.”





Jonathan Rodriguez
	WHAT I HAVE DONE
Added comments throughout the program
Added the prediction for class probabilities


—NOTES—
Filtering data to just WA can reduce data size, which can create class imbalance.
Ovr and OvO are mainly useful for multi-class classification (More than 2).
Our Ovr and Ovo are equivalent to one another due to only using 2 classes

—COMMENTS THAT CAN BE FOUND IN THE CODE—
First Chunk of code (# Data Loading and Cleaning)
Cleaning and setting the data up for the rest of the project.
Loads the data set
Cleans out any data that is not wanted
Special characters that may not be supported 
Skips rows that have formatting issues
Filters out to only include WA (Washington)
Removes rows that have missing values
Shows the first 5 rows of the cleaned dataset

Second Chunk of code (Basic EDA – Simple visualization)
The bar graph displays the number of BEV and PHEV in the data set. There are far more BEVs than PHEVs. 42,018 BEV and 10,775 PHEV

Third chunk of code( # Logistic Regression Model)
Converts the electric vehicle type into a binary variable:
1 = BEV (Battery Electric Vehicle)
0 = PHEV (Plug-in Hybrid Electric Vehicle)
Needed for logistic regression to predict binary outcomes
X is used to predict EV type
Y is the target variable
BEV or PHEV
Splitting the dataset
80% training, 20% testing
stratify=y ensures the proportion of BEV/PHEV is the same in both sets.


random_state=42 makes the split reproducible.
Feature scaling
Standardizes the features so they all have the same scale.
Important for logistic regression when features have very different ranges
Training logistic Regression
max_iter=1000 ensures convergence if the default 100 iterations is not enough.


The model learns the relationship between features and is_bev.
Making Predictions
predict → predicts class labels (0 or 1).


predict_proba → predicts probabilities for each class.


log_model.classes_ shows the order of classes in predict_proba
Evaluating the model

Fourth chunk (Compare One-Vs-All (OvR) and One-Vs-One (OvO)
Imports
OneVsRestClassifier (OvR): Trains one classifier per class. Each classifier predicts whether a sample belongs to that class or not.


OneVsOneClassifier (OvO): Trains one classifier for every pair of classes, comparing them directly.


LogisticRegression: Base model used for both strategies.
Create OvR and OvO models
Fitting the models
Both models are trained on the scaled training data.


After this, they can predict class labels for new data.
Evaluates accuracy
.score() computes the accuracy on the test set.


Accuracy = proportion of correct predictions.

—Interpretation of OvO and OvR—
Both OvR and OvO achieve ≈ 80.7% accuracy on the test set.
This means the model correctly predicts whether a vehicle is a BEV or PHEV about 8 times out of 10.
Ovr and OvO is a binary classification problem (1, 0[BEV, PHEV]) they behave the same
Meaning since there is only 2 classes we get the same percentage
Adding a three class would make OvO and OvR more viable for this dataset and make the differences appear.
There is still that 20% where the logistic regression model misclassified, but if we add more features it could be improved.
Wrap up
Both the One-vs-Rest and One-vs-One logistic regression models achieve approximately 80.7% accuracy in predicting whether an electric vehicle is BEV or PHEV. Since this is a binary classification problem, the two approaches produce identical results. The model shows a reasonable predictive ability, though some misclassifications remain.
features used that influences the prediction
X is used to predict EV type
Model Year, Electric range, Base MSRP
The logistic regression model shows that newer, longer-range, and slightly more expensive electric vehicles are more likely to be BEVs. The most influential feature is Model Year, suggesting that recent market trends favor BEVs. Electric Range also contributes positively, indicating that BEVs tend to have longer ranges than PHEVs. Base MSRP has a smaller effect but still slightly increases the likelihood of being BEV. These insights align with expectations: newer BEVs tend to have higher ranges and slightly higher prices compared to PHEVs.




Ousmane kandji 
Boxplot visualization
The boxplot comparing prices across the top 10 manufacturers provides a deeper understanding of how vehicle costs vary by brand. Unlike a simple count plot, this visualization highlights the full distribution of prices, including the median, spread, and presence of outliers for each manufacturer. From this chart, we can see that some manufacturers have consistently higher-priced vehicles, while others offer a wider range of prices that may include both budget-friendly and premium models. The differences in box heights and whisker lengths show how diverse each manufacturer's pricing strategy is. Overall, this visualization helps us identify which manufacturers tend to offer more expensive electric vehicles and which ones provide more affordable or varied options.

Geographic Distribution of EVs (Latitude vs Longitude)
The geographic scatter plot displays the latitude and longitude of all EVs in the dataset, showing where electric vehicles are most commonly registered. We can see that the points are concentrated in specific regions, indicating that EV adoption is higher in certain areas. These clusters typically occur in urban or suburban locations where charging infrastructure is more accessible. The visualization helps highlight regional patterns in EV presence and allows us to see how location may influence EV usage. Overall, this plot provides a clear picture of where electric vehicles are most densely located.


