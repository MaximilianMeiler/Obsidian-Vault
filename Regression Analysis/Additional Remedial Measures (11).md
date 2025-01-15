Previous lecture [[Multiple Diagnostics (10)]]


### Nonconstant error variance
- Normally, we assume $Var(\epsilon_{i})= \sigma^2$ for all $i$
- Previously, if $Var(\epsilon_{i})$ depended on $i$, we transformed on Y
	- However, what if the relationship was already linear? This will create a nonlinear relationship instead
- Testing with a Modified Levene (Brown-Forsythe) Test
	- Calculate all the residuals for a model
	- Split the sample into $g$ groups
		- Group 1 - residuals of the lowest x-values
		- Group 2 - residuals of the highest x-values
	- $H_{0}$ - variance is constant, $H_A$ - variance is not
	- $d_{i1} = |e_{i1}-\tilde{e_1}|$, $d_{i2} = |e_{i2} - \tilde{e_2}|$ (median residual)
	- Calculate pooled variance and test statistic ![[Pasted image 20241122131104.png]]

### Weighted least squares
- Assume $\epsilon_{i} \approx N(0, \sigma^{2}_i)$
- In matrix form - $Y = X\beta + \epsilon$
- We want to choose a $\beta$ that minimizes the $\sum{w_{i}[Y_{i}-\hat{Y_{i}}]^2}$
	- This allows for the adjusting of least squares to favor points with larger weights
- $b_{w} = (X'WX)^{-1}X'WY$
	- $W$ is a nxn matrix with $w_{1}...w_{n}$ along its diagonal and 0s everywhere else
	- $E(b_{w}) = \beta$, $Var(b_{w}) = (X'WX)^{-1}$
- If we know $\sigma^2_{i}$, $w_{i}=\frac{1}{\sigma^2_{i}}$
	- Thus, $Var(Y) = W^{-1}$
- If we don't know $\sigma^2_{i}$, what do we do?
	- We could set $\sigma^{2}_{i}= e^{2}_{i}$
	- Or...
		- Find a predictor that signals non-constant variance 
		- $|e_{i}| = \alpha_{0}+\alpha_{1}X_{ik} = \epsilon_i$
			- Find the fitted equation $|\hat{e}| = a_{0}+ a_{1}X$
	- $w_{i} = \frac{1}{(a_{0}+a_{1}X_{ik})^2}$
	- Model WLS, repeat with new residuals
- This ends up letting us fit a model that puts more emphasis on low-variance points

### Ridge regression
- When multicollinearity occurs, $X'X$ is close to singular
- Instead of setting the unbiased estimator $b$ equal to $(X'X)^{-1}X'Y$,
	- We use the ridge regression estimator $b^{(r)} = (X'X+\lambda I)^{-1}X'Y$
	- Where $X$ and $Y$ are both centered and $\lambda$ is positive
- As $\lambda$ increases from 0->1, each component of $b^{(r)}$ (each intercept/slope) plateau to 0


Next lecture: [[Logistic Regression (12)]]