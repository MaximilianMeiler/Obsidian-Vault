Previous lecture: [[Polynomial Models and Qualitative Predictors (8)]]


### Experiments and observational studies

Purely controlled experiment
- Controlled predictor variables
- Rarely any need to reduce the number of variables
	Controlled experiment with covariates
- Some predictor variables are controlled, but other covariates are not controlled
- Remove any observed covariates that don't reduce error variance
Confirmatory observational studies
- Many predictors are observed, but only a few are controlled
- Mainly used to confirm if controlled predictors are meaningful
Exploratory observational studies
- Predictors are observed that are believed to influence the response
- Reduction is always done to find a specific set of meaningful predictors

### Strategies for model building

Try different models
- Use models that make sense to experts
- Try first and second order models
- Eliminate complicated structures that aren't confirmed by the data
Model reduction
- Eliminate predictors that aren't shown to be useful by the data
- Keep lower order terms when higher order terms are confirmed

### Subset selection

- Test all models of 2 predictors, of 3, ..., the model with all $p-1$  predictors
	- Total number to test: $2^{p-1}-1$

### Model selection criteria

Let P be the full number of parameters, and p for the reduced number

Coefficient of multiple determination
- $R^{2}_{p}= \frac{SSR_{p}}{SSTO} = 1 - \frac{SSE_{p}}{SSTO}$
- Never decreases as predictors are added. Look for a point of diminishing returns

Adjusted $R^2$
- $R^{2}_{a,p}=1-(\frac{n-1}{n-p})\frac{SSE_{p}}{SSTO}$
- Seek the model that maximizes $R^2_{a,p}$

Mallows $C_p$
- $C_{p}= \frac{SSE_{p}}{MSE(X_{1},...,X_{P})} - (n-2p)$
- Choose the model with the smallest p such that $C_{p}\approx p$

Akaike Information Criterion (AIC)
- $AIC_{p} = nln\left(\frac{2\pi SSE_{p}}{n}\right)+ 2(p+1)+n$
- Goal is to minimize $AIC_p$

Bayesian Information Criterion (BIC)
- $BIC_{p} = nln\left(\frac{2\pi SSE_{p}}{n}\right)+ ln(n)(p+1)+n$
- Goal is to minimize $BIC_p$
- AIC and BIC can both be negative

Prediction sum of squares (PRESS)
- The goal of linear regression is to minimize $SSE = \sum(Y_{i}-\hat{Y}_{i})^2$
- $PRESS_{p} = \sum(Y_{i}-\hat{Y}_{(i)})^2$
	- $\hat{Y}_{(i)}$ is the predicted response corresponding to the i-th data point being deleted and the model fitted on the remaining $n-1$ data points
	- We select a model with a small $PRESS_{p}$, hopefully close to $SSE_{p}$

### Regression Model Building

With too many predictor variables, trying each model becomes infeasible. We present a few new approaches for this setting.

Backward Elimination (Top-down)
- Select a significance level to stay in the model ($\alpha_{S} = .2$)
- We start with the model with all predictors
- Consider the predictor with the lowest t-statistic / highest p-value
	- If this p-value is $>\alpha_S$, remove the predictor and refit the model
- We stop iterating once all remaining predictors have p-values $\leq \alpha_S$

Forward selection (bottom-up)
- Fit all *simple* linear regression model
- Consider the predictor with the highest t-statistic / lowest p-value
	- If $p \leq \alpha_{E}$, fit all two variable models that include this predictor
- Stop iterating when all predictors have p-values $\leq \alpha_E$

Stepwise regression
- Choose an entry significance level $\alpha_E$ and stay level $\alpha_S$ where $\alpha_{E} < \alpha_S$
- Start like forward selection where new variables must have p-value $\leq \alpha_E$
- Retest all old variables against a p-value of $\alpha_S$ to stay in the model
- Continue iterating until no new variables can be entered and no old ones need to be removed

### Model validation

It's always best to assess performance based on a separate set of data (not the training data)
- For the new set, calculate $MSE^{*} = \frac{\sum(Y_j^{*}-\hat{Y_j^{*}})^2}{m}$
- A similar MSE is good
- If no new data exists, use $PRESS_{p}= \sum(Y_{i}-\hat{Y_{(i)}})^2$ and divide by $n$


Next lecture: [[Multiple Diagnostics (10)]]