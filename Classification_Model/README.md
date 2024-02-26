## Objective
Demonstrate the value and applicability of predictive analytics in competitive Esports, leveraging a unique dataset to predict the outcome of a game within the first 10 minutes

## Modelling
- Model testing:
    - Logistic Regression
    - Decision Tree
    - Random Forest
    - Light GBM
    - XGBoost
    - GradientBoostingClassifier
- Hyper-parameter tuning: grid search for all the models tested.
- Model selection: based on the accuracy score, we select Logistic Regression as our best performed model.

## Result
- Logistic Regression: Achieved an accuracy of 72.47%.
- Decision Tree: Initially yielded an accuracy of 67.61%. We further experimented with a simplified version, maintaining the same accuracy, and an optimized version, which improved accuracy to 70.11%.
- Random Forest: Provided a slight improvement over the optimized decision tree with an accuracy of 70.78%.
- LightGBM: Showed promising results with an accuracy of 71.12%.
- XGBoost: Emerged as the top-performing model with an accuracy of 71.99%.
- Gradient Boosting: Close behind XGBoost, it achieved an accuracy of 71.46%.
