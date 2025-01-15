#### Overview and definitions
- **Y** (dependent variable) - our variable of interest
- **X** (independent variable) - what we use to predict Y
- **Discrete variable** - countable sample space (counts, gender)
- **Continuous variable** - uncountable sample space (length, weight, time)
- We assume that $Y$'s expected value depends on $X$
	- The experimental val of $Y$ - $(E(Y))$, can be written as a deterministic function of $X$ - ($f(X)$)
		- Deterministic - only 1 output associated per an input
	- Ex. simple linear regression: $\beta_{0} + \beta_{1}X_i$
	- Ex. quadratic regression: $\beta_{0} + \beta_{1}X_{i} + \beta_{2}X_{i}^2$
	- Betas represent unknown population parameters, we estimate them with our sample
#### Simple Linear Regression (SLR)
- Represented by a slope-intercept equation: $\beta_{0} + \beta_{1}X_i$
	- Difference between a point $X^*$ and $X^{*}+ 1$: $(\beta_{0} + \beta_{1}(X^{*}+ 1)) - (\beta_{0} + \beta_{1}X^{*}) = \beta_1$ (slope!)
- This forms a imperfect statistical relation, not an exact functional relation
- The independent variable is a random variable with an expected value, which is a linear function on the dependent variable
	- ![[Pasted image 20240823133853.png]]
- Given data $(X_{1}, Y_{1})...(X_{n}, Y_n)$ and a slope-intercept equation $Y_{i}= \beta_{0} + \beta_{1}X_{i} + \epsilon_i$,
	- $Y_i$ is the value of the **response variable** in trial $i$
	- $X_i$ are **fixed known constants**
	- $\epsilon_i$ are independent, identically distributed **random errors**
		- $E(\epsilon_{i}) = 0$, $Var(\epsilon_{i})= \sigma^2$
	- $\beta_0$, $\beta_1$, and $\sigma^2$ are **unknown parameters**

#### Summation notes
- Properties
	- Summing constants = bounds\*constant
	- + and - can be distributed
	- Constants can be factored out
- $\bar{X}$ = sample mean
- $\bar{X} = \frac{1}{n}\sum_{i=1}^{n} (X_{i}- \bar{X}) = \sum_{i=1}^{n} X_{i} - \sum_{i = 1}^{n} \bar{X} = n\bar{X} - n\bar{X} = 0$
- $\sum_{i = 1}^{n}(X_{i}- \bar{X})^{2}= \sum_{i = 1}^{n}(X_{i}- \bar{X})(X_{i}- \bar{X})$
	- = $\sum_{i = 1}^{n}(X_{i}- \bar{X})X_{i} - (X_{i}- \bar{X})\bar{X}$
	- = $\sum_{i = 1}^{n}(X_{i}- \bar{X})X_{i} - \sum_{i = 1}^{n}(X_{i}- \bar{X})\bar{X}$
	- = $\sum_{i = 1}^{n}(X_{i}- \bar{X})X_{i} - \bar{X}\sum_{i = 1}^{n}(X_{i}- \bar{X})$
	- = $\sum_{i = 1}^{n}(X_{i}- \bar{X})X_{i}$ 
	- = $\sum_{i = 1}^{n}X_{i}^2- \sum_{i = 1}^{n}(\bar{X}X_i)$
	- = $\sum_{i = 1}^{n}X^{2_{i}}- n\bar{X}^2$

#### The expectation operator
- Let $Y$ be a discrete random variable which take values $y$ with probabilities $p$
	- $E[g(Y)] = \sum_{i = 1}^{n}g(y_i)p_i$
	- $E[K] = K$, where $K$ is a constant
	- Constant factoring: $E[KY] = KE[Y]$
	- +/- distribution: $E[X+Y] = E[X] + E[Y]$
	- If $\mu_{Y}= E[Y]$, then $E[(Y - \mu_{Y})]= 0$
		- Average deviation from the mean is always 0
- Variance
	- $Var[Y] = E[(Y - \mu_{Y})^2]$
		- = $E[Y^{2} - 2Y\mu_{y} + \mu_y^2]$
		- = $E[Y^{2}] - 2\mu_{y}E[Y] + E[\mu_y^2]$
		- = $E[Y^{2}] - 2\mu_{y}^{2}- \mu_{y}^{2}$
		- = $E[Y^{2}]- E[Y]^2$
	- $Var[K] = 0$
	- $Var[KY] = K^2Var[Y]$
		- = $E(KY - E[KY])^2$
		- = $E(KY - KE[Y])^2$
		- = $K^2E(Y - E[Y])^2$
	- $Var[X + Y] = Var[X] + Var[Y]$, if $X$ and $Y$ are independent
		- = $E[(X+Y - E[X+Y])^2]$
		- = $E[(X - E[X] + Y - E[Y])^2]$
		- = $E[(A^{2} + 2AB + B^2)]$, where $A = X - E[X]$ and $B = Y - E[Y]$
		- = $Var[X] + 2Cov(X, Y) + Var[Y]$
- Covariance
	- $Cov(X, Y) = E[(X - E[X])(Y - E[Y])]$
	- If $X$ and $Y$ are independent, $Cov(X, Y) = 0$
	- $Cov(X, K) = 0$, where $K$ is a constant

#### Consequences of the SLR Model
- The response ($Y_i$) is the sum of the constant term $\beta_{0}+ \beta_{1}X_i$ and the random term $\epsilon_i$
	- Thus, $Y_i$  is a random, non-deterministic variable
- $E(Y_{i})= \beta_{0}+ \beta_1X_i$
	- The expected value of $\epsilon_i$ is 0!
	- This is the regression function that forms our best fit line
- $Var(Y_{i}) = Var(\beta_{0}+ \beta_{1}X_{i}+ \epsilon_{i}) = Var(\epsilon_{i}) = \sigma^2$
	- This variance is constant for all $Y_i$
- Definition
	- The model is *simple* because it predicts $Y$ with only one $X$
	- The mode is $linear$ because the regression function is linear in its parameters
		- $\beta$ is always linear (not $X$)
- Variable creation
	- The **Least-Squares criterion** says to choose the line which minimizes the sum of squared distances between the true and predicted sample values
		- Minimize $Q = \sum^n_{i=1}(Y_{i}- (\beta_{0}+ \beta_{1}X_{i}))^2$
		- We can minimize by setting the derivatives to 0: ![[Pasted image 20240828131558.png]]![[Pasted image 20240828131756.png]]
	- This leads to: ![[Pasted image 20240828131921.png]]
	- Simplification for $b_1$:  $$b_{1} = \frac{\sum^{n}_{i=1}X_{i}Y_{i}- n\bar{X}\bar{Y}}{\sum_{i = 1}^{n}X^{2}_{i}- n\bar{X}^2}$$
	- When interpreting these values, remember that everything is "on average": ($b_{1}$: "increase by 11 ON AVERAGE", $b_0$: "AVERAGE number of hours")

#### Properties of Least-Squares Estimators
- The **Gauss Markov Theorem** states that the Least Squares Estimators are **unbiased** ($E[b] = \beta$) and have **minimum variance** among all unbiased linear estimators
	- $\beta$ = population parameters

#### Properties of the Estimated Regression Function
- Regression function: $E(Y)= \beta_{0}+ \beta_1X$
- Estimated regression function: $\hat{Y} = \hat{E}(Y) = b_0+ b_1X$
	- $\hat{Y}_{i}$ is the **fitted value** at $X_i$
- **Residual**: $e_{i}= Y_{i}- \hat{Y}_i$
	- Sum of residuals is 0
		- The sum of observed values equals the sum of fitted values
	- The sum of squared residuals is a minimum
	- The sum of the residuals weighted by $X_i$ is 0
	- The sum of the residuals weighted by $\hat{Y}_i$ is 0
	- Note - **errors** ($\epsilon_i$) are calculated using the beta (population) parameters. $e_i$ is an attempt to estimate $\epsilon_i$, but $\epsilon_i$ is **not a parameter**,  it's a random quantity.
- The regression line always passes through the point $(\bar{X}, \bar{Y})$

#### Estimation of $\sigma^2$ using SLR
- In a population of independent and identically distributed $Y$s, $E(Y_{i})= \mu$ and $Var(Y_{i})= \sigma^2$
- Obtaining variance:
	- Square the difference between each observation and the estimate of its mean $(Y_{i} - \bar{Y})^2$ 
		- $\mu = \bar{Y}$
	- Then, divide by degrees of freedom $(n-1)$
		- Degrees of freedom: n - (# other params used in the estimation ($\mu$))
- In the SLR model with $E(Y_{i})= \beta_{0} + \beta_{1}X_i$, the $Y_i$'s are independent but NOT IDENTICALLY DISTRIBUTED (we expect $Y_i$s to be different)
	- $\sum^n_{i=1}(Y_{i} - \hat{E}(Y_{i}))^2$ = $\sum^n_{i=1}(Y_{i} - (b_{0}+ b_{1}X_{i}))^2$ = SSE
		- Sum of squared residuals
	- MSE (error mean square) = SSE / (n-2)
		- $s^2$ (MSE) is an unbiased estimate of $\sigma^2$
			- $E(MSE) = \sigma^2$
			- $E(b_{0})= \beta_0$
			- $E(b_{1}) = \beta_{1}$

#### Normal Error Regression Model
- Th least-squares method provides the minimum-variance unbiased point estimators of $\beta_0$ and $\beta_1$
- However, we need to make assumptions about the distribution of the $\epsilon_i$
	- $E[\epsilon_{i}]= 0$, and $Var[\epsilon_{i}] = \sigma^2$
	- Uniform, Normal, and Skewed distributions would all work!
- The **normal error regression model** assumes that $\epsilon_i$'s are independent $N(0, \sigma^{2})$ **random errors**
	- $Y_{i}= \beta_{0} + \beta_{1}X_{i} + \epsilon_i$
	- $E[Y_{i}] \approx N(\beta_{0} + \beta_{1}X_{i}, \sigma^2)$
	- Probability density function: ![[Pasted image 20240904131905.png]]
	- Likelihood function: ![[Pasted image 20240904132151.png]]
	- Derive to solve for the Maximum Likelihood Estimators for $\beta_{0}, \beta_{1}, \sigma^2$ ($b_{0}, b_{1}, s^2$) ![[Pasted image 20240904132321.png]]

#### Motivate Inference in SLR Models$
- Say we find $b_{0}$ and $b_{1}$ for two unrelated variables - it may occur that $b_{1} \neq 0$
	- However, this doesn't mean our variables are necessarily related
	- $b_1$ is a random variable because it depends on the $Y_i$s used to calculate it!
	- If we recalculated $b_1$ many times with new data, we can see the probability if the population parameter is actually equal to 0: ![[Pasted image 20240904133015.png]]


Next lecture: [[Inference in Regression Analysis (2)]]