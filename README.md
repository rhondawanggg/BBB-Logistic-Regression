# BBB-Logistic-Regression

## Final Attempts:

- **Independent Variables Selected for Logistic Regression**: `art`, `geog`, `last`, `purch`, `total_spent`, and `gender_M`
- **Interaction Terms Selected for Logistic Regression**: `last` × `art`
- **Predicted Profit**: $11936.00
- **ROME**: 153.66% (0.15366)

## Regression-Based Targeting and CLV

Refine logistic regression model: Analyze the Decision Tree output. Select some features that could enhance the basic logistic regression model (i.e., add some variables and ONE Interaction term to the formula used earlier). Calculate the profitability of using this enhanced logistic regression model to target customers. 

## Part 1 - Building familiarity with BBB data using ML approaches

Assumptions for all steps:
- **Cost to reach one customer** = $0.50
- **Gross profit (contribution) per sale** = $6.00
- **Break-even response rate = 0.50 / 6.00** = 0.0833 (8.33%)
- **Mail if predicted probability** ≥ 0.0833

**Step 1 - Explore the BBB dataset**

Before we run any regressions, start by exploring the data. Look at the different variables and think about what kind of information they contain. Which variables are numeric (like last, purch, total$)? Which are categorical (like gender, product categories)? Our outcome of interest is buyer, coded 1 if the customer bought the Florence book and 0 otherwise. This matters because the type of regression we choose depends on whether the outcome is continuous or binary. Compute simple descriptive statistics: what is the mean and median of total$? What percentage of customers purchased (the overall buyer rate)? How does this break down by gender, or by product category? These quick checks give us a baseline intuition before we model.

**Step 2 - Try linear regression on a binary outcome**

As a first experiment, fit a linear regression using buyer (0/1) as the dependent variable and one predictor, such as purch. This is technically the wrong model for binary outcomes, but it is useful to see why. You will notice that predictions are not confined between 0 and 1, and coefficients are not easy to interpret in terms of probabilities. This illustrates why linear regression is not suited for yes/no outcomes.

**Step 3 - Logistic regression with one variable**

Now fit a logistic regression with buyer as the dependent variable and purch as the predictor. Logistic regression models the log-odds of purchase, but you can interpret results in terms of predicted probabilities. These predicted probabilities always lie between 0 and 1, making them meaningful for targeting. Choose a cutoff based on the break-even rate: recall from RFM that the mailing cost is $0.50 per customer and the profit per sale is $6, so the break-even response rate is 0.083 (8.3%). Target customers with predicted purchase probability greater than or equal to this threshold. For those customers, calculate the campaign economics: cost = 0.50 times the number mailed, sales = 6 times the number of actual buyers in that group, profit = sales minus cost, and ROME = profit divided by cost.

**Step 4 - Logistic regression with multiple variables**

Next, expand the model by adding more predictors, such as last, total$, and gender. Each predictor adds more information about purchase behavior. Check the significance of the coefficients and how they affect predicted probabilities. Recalculate profits and ROME using the same procedure. Compare: does this model outperform the simple one-variable logistic regression?

**Step 5 - Logistic regression with interaction terms**

Introduce the idea of interactions. An interaction allows the effect of one variable to depend on another. For example, you might test gender × art_books. This term captures whether women who buy art books are particularly likely to purchase the Florence book. Fit a model including both main effects and the interaction term. Interpret the coefficients carefully and calculate profits and ROME again. Your task is to identify other categorical variables that can be interacted with main predictors. This shows how personalized targeting (beyond just averages) can lead to higher profitability.

**Step 6 - Decision tree for feature importance**

Run a decision tree to predict buyer. The tree algorithm will rank variables by their importance in predicting purchase. Look at the feature importance list. Which variables come out on top? Use this ranking to guide which variables (and possible interactions) to include in a refined logistic regression model. This way, the decision tree helps you discover useful predictors, while logistic regression lets you interpret and calculate profitability more directly.

**Step 7 - Compare methods**

Finally, compare the profitability of different approaches. Start with mass mailing (mail everyone). Then compare profits and ROME from RFM targeting, logistic regression with one predictor, logistic regression with multiple predictors, logistic regression with interactions, and regression models guided by decision tree feature importance. Which approach yields the highest profit? Which is most efficient (highest ROME)? Discuss why more personalized, data-driven methods tend to outperform simpler approaches.

## Part 2 - Enhancing the logistic regression model 
Deliverable: refine the logistic regression by (a) adding more predictors based on decision-tree importance and your marketing intuition, (b) adding exactly ONE interaction term you can justify, and (c) comparing Profit and ROME for three strategies: RFM targeting, basic logistic (from Part 1; specify which), and your enhanced logistic regression model. You must explain why your chosen variables and the interaction make sense in terms of consumer behavior, not just because they were important in a tree. 
