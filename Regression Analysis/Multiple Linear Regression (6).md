Previous lecture: [[Matrix Algebra (5)]]

*What if we have multiple Xs?*

Simplest MLR model: $Y_{i} = \beta_{0}+\beta_{1}X_{i1} + \beta_{2}X_{i2} + \epsilon_i$
	- Now, we add an extra unknown param $\beta_2$ and an extra constant $X_{i2}$
- Interpretation of $\beta$s isn't so straightforward 
	- "For every 1-unit change in $X_1$, we expect $E(Y)$ to change by $\beta_1$ while $X_2$ is held constant"
- Essentially composed of a bunch of different SLR models with different intercepts but constant slopes
- Forms a plane in 3d space! ![[Pasted image 20241014130146.png]]

What if we wants slopes to change based on variable relation?
- Ex. with a larger $X_1$, we want $X_2$ to increase Y at a more rapid rate
- Add an interaction term: $Y_{i} = \beta_{0}+\beta_{1}X_{i1} + \beta_{2}X_{i2} + \beta_{3}X_{i1}X_{i2}$
	- Now, with a fixed $X_1$, the slope for $X_2$ still changes based on $X_2$'s value!

General Linear Regression Model
- $Y_{i} = \beta_{0} + \beta_{1}X_{i1} + ... + \beta_{p_1}X_{ip-1} + \epsilon_i$
- Either there are p-1 different predictors (Xs), or some predictors are functions of others!
	- Even though the data is non-linear in the latter case, the $\beta$ parameters are still linear multipliers
- Polynomial regression
	- $Y_{i}= \beta_{0}+\beta_{1}X_{i}+\beta_{2}X_{i}^{2} + \epsilon_{i}$
	- This is just a MLR of 2 variables, one corresponding to $X$ and one to $X^2$
- Non-general examples:
	- $Y_{i} = \beta_{0}e^{\beta_{1}X_{i}}$
- In matrix terms:
	- Y is still $n \times 1$, but X is now $n \times p$ and $\beta$ is $p \times 1$ ![[Pasted image 20241014132359.png]]
	- $e \approx N(0, \sigma^{2}I)$
	- $\beta$ and $\sigma^2$ are unknown parameters
	- $X$ is a $n \times p$ matrix of fixed known constants
	- Estimate $\beta$ by minimizing $Q = (Y-X\beta)'(Y-X\beta) = \epsilon'\epsilon = \sum{\epsilon^2_i}$
	- Estimates: $b_{p \times 1} = (X'X)^{-1}X'Y$
	- Fitted vals: $\hat{Y}_{n \times 1} = Xb$
	- Residuals: $e_{n \times 1} = Y - X(X'X)^{-1}X'Y = Y - HY = (I-H)Y$
- ANOVA
	- Formulas are the same: ![[Pasted image 20241014133215.png]]
	- Degrees of freedom
		- SSTO still has n-1 degrees of freedom
		- SSR now has p-1 because of the p-1 different slopes in $\hat{Y_{i}}$
		- SSE thus has n-p degrees of freedom
	- SSTO is also equal to $\sum{Y_{i}^{2}} - \frac{1}{n}(\sum{Y_{i}})^2$
		- $\sum{Y_{i}^{2}} = Y'Y$
		- Y'JY = $[Y_{1},...,Y_{n}] [1,...,1/.../1,...,1][Y_{1}/.../Y_{n}]$
			= $[Y_{1}, ..., Y_{n}][\sum{Y}/.../\sum{Y}] = (\sum{Y_{i}})^2$
		- $SSTO = Y'Y - \frac{1}{n}Y'JY$
	- SSE = $(Y-Xb)'(Y-Xb)$
		- $= Y'Y-Y'Xb-b'X'Y+b'X'Xb$
			- All of these reduce to $1 \times 1$ matrices!
		- $= Y'Y - 2Y'Xb + b'X'X(X'X)^{-1}X'Y$
		- $= Y'Y - 2Y'Xb + b'X'Y$
		- $= Y'Y - 2Y'Xb + Y'Xb$
		- $=Y'Y - Y'Xb = Y'Y - b'X'Y$
	- SSR = SSTO - SSE = $b'X'Y - \frac{1}{n}Y'JY$
	- Final table: ![[Pasted image 20241016130229.png]]
- F-testing
	- $H_0$: All $\beta$s are 0, $H_A$: not all $\beta$s are 0
	- Test statistic: $F^{*}= \frac{MSR}{MSE}$
	- Reject $H_00$ if $F^{*} > F(1-\alpha, p-1, n-p)$
	- Coefficient of determination is still $\frac{SSR}{SSTO}$
- Inferences about regression parameters
	- Recall,
		- $E[b] = E[(X'X)^{-1}X'Y] = (X'X)^{-1}X'E[Y] = (X'X)^{-1}X'(X\beta) = \beta$
		- $Var(b) = \sigma^{2}(X'X)^{-1}$
		- Thus, $b_{k}\approx N(\beta_{k}, \sigma^{2}[(X'X)^{-1}]_{k+1, k+1})$
			- This allows you to determine a variance of a specific beta
	- T-tests: ![[Pasted image 20241016131713.png]]
		- Test statistic: $t^{*} = \frac{b_k}{\sqrt{MSE(X'X)^{-1}_{k+1, k+1}}}$
		- Beta interval: ![[Pasted image 20241016132055.png]]
		- Mean interval: ![[Pasted image 20241016132639.png]]
		- Value interval: add "1" inside the MSE term

What if we want to find joint confidence intervals?
- We use the same technique. 
- $X'_{hg}b = \pm t(1-\alpha/(2g),n-p)\sqrt{MSE}$

Degrees of freedom
- We can find df by starting with n (the number of independent random variables), then subtracting the number of constraints needed to define a statistic
	- $SSTO$ $(\sum{(Y_{i}- \bar{Y})^2})$ still has a df of $n-1$
		- n independent random variables $Y_{1}...Y_{n}$
		- 1 constraint: [COMPLETE]
	- $SSE$ $(\sum{(Y_{i}-\hat{Y_{i}})^2})$ has a df of n-p
		- n independent random variables $Y_{1}...Y_{n}$
		- p constraints: $\sum{e_{i}} = 0$, $\sum{e_{i}\hat{Y_{i}}} = 0$
			- Now, $\sum{e_{i}\hat{Y_{i}}} = \sum{e_{i}(b_{0}+ b_{1}X_{i1} + ... + b_{p-1}X_{ip-1})} = b_{0}\sum{e_{i}} + b_{1}\sum{e_{i}X_{i1}} + ... + b_{p-1}\sum{e_{i}X_{ip-1}}$
			- Each $b_{k}\sum{e_{i}X_{ik}} = 0$, leading to p-1 + 1 = p constraints total
	- $SSR$ $\sum{(\bar{Y_{i}} - \hat{Y})^2}$ has a df of p -1
		- Random variables: $\bar{Y} = b_{0}+ b_{1}\bar{X_{1}} + ...  + b_{p-1}\bar{X}_{p-1}$
			- $\hat{Y_{i}} - \bar{Y} = b_{1}(X_{i1} - \bar{X_{1}}) + ... + b_{p-1}(X_{i,p-1}-\bar{X}_{p-1})$
			- Each of the resulting b's is a random variable. Since we cancelled $b_{0}$, we end up with a df of $p-1$
- Through matrices
	- Examine the rank of the matrix that defines each quantity
	- A quantity is written in quadratic form if it is written as $Y'AY$
	- $SSTO = Y'Y - \frac{1}{n}Y'JY = Y'IY - Y'(\frac{1}{n}J)Y = Y'(I - \frac{1}{n}J)Y$
		- Rank($I - \frac{1}{n}J$) = n-1
	- $SSE = (Y - \hat{Y})'(Y-\hat{Y}) = Y'Y - Y'\hat{Y} - \hat{Y}'Y + \hat{Y}'\hat{Y}$
		$= Y'Y - Y'HY - YH'Y + Y'H'HY = Y'Y - Y'HY - Y'HY + Y'HY$  $=Y'Y - Y'HY = Y'(I-H)Y$
		- Rank($I - H$) = n-p
	- $SSR = Y'\left(\left(I - \frac{1}{n}J\right)- (I - H)\right)Y$


Next lecture [[Multiple Linear Regression II (7)]]