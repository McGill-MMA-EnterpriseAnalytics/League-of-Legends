## Step 1: Check collinearity
- Drop columns that are highly correlated

## Step 2: Feature engineering
- Add relevant columns based on the existing columns (EXPLAINATION HERE ??)
    - blueHelpful:
    - redHelpful: 
    - blueJunglePercentage:
    - redJunglePercentage:
    - redWardsRemaining:
    - blueWardsRemaining:

## Step 3: Modelling
- Model testing:
    - Logistic Regression
    - Random Forest (including Decision Tree)
    - Light GBM
    - XGBoost
    - GradientBoostingClassifier
- Hyper-parameter tuning: grid search for all the models tested.
- Model selection: based on the accuracy score, we select Logistic Regression as our best performed model.

## Step 4: Casual inference 
- Feature selection:
    - Even after feature selection during modelling, it is still better to keep all the relevant features for analyzing casual inference.
    - Some simple feature selection but the same feature engineering method as done in modelling part.
- Correlation and association graph:
    - Determine the treatment based on the highest correlation.
- Building model:
    - Even though GradientBoostingClassifier is the highest accuracy score from our modelling, causal inference requires more than just predictive accuracy; it involves estimating causal effects and making inferences about how changes in one variable affect another.
    - Still want to consider the accuracy score we got before, but also models like logistic regression are often preferred for causal inference because their coefficients directly indicate the effect of each feature on the outcome.
    - We chose LogisticRegression() as our base model.
- Different learners:
    - S learner, X learner, T learner, R learner
    - Initial approach:
        - Reference: https://github.com/uber/causalml/blob/master/tests/test_meta_learners.py
        - The idea is "Check if the cumulative gain when using the model's prediction is higher than it would be under random targeting".
        - Our result/error may suggests that the model's prediction is not performing better than random targeting according to the current evaluation metric.
    - So we end up using Average Treatment Effect, Lower Bound CI', and Upper Bound CI as part of our learner evaluation.
    - X learner is the best out of four.
    - EXPLAIN THE CUMULATIVE GAIN CURVE HERE: ???
- Feature importance:
    - Apply the base model and learner we selected.
    - EXPLAIN MORE HERE: ???
 
- Result:
    - The estimated average treatment effect (ATE) for all learners is positive, indicating that increasing the "blueGoldDiff" (blue team gold difference) increases the likelihood of the "blueWin" result.
    - The confidence intervals do not include 0, implying that these effects are statistically significant. This means that the correlation between "blueGoldDiff" and "blueWin" is unlikely to be due to chance.
    - Business implementation: Teams could use this information to focus on methods to boost their gold advantage over the other side ("blueGoldDiff"). For example, they may prioritise goals such as gaining more towers, neutral objectives (such as dragons or barons), or farming efficiently to gain more gold, knowing that doing so boosts their chances of winning ("blueWin").