Previous lecture: [[Diagnostics and Remedial Measures (3)]]

## Simultaneous Inferences

We say that a Confidence Interval **covers** if it contains the true parameter
- Define $A_{2}$ to be the event that the CI for $E(Y_{2})$ covers
- Define $A_{5}$ to be the event that the CI for $E(Y_{5})$ covers
- If $P(A_{2})$ is $.95$ and $P(A_{5})$ is $.95$,  then $P(A_{2} \cap A_{5})$ is ...
	- Notes
		- $P(A \cup B) = P(A) + P(B) - P(A \cap B)$
		- $P(A \cap B) = P(A) + P(B) - P(A \cup B))$
		- $P(\bar{A}) = 1 - P(A)$
	- Proof
		- $P(A \cap B) = P(A_{2}) + P(A_{5}) - P(A_{2}\cup A_{5})$
		- $= 1 - P(\bar{A_{2}}) + 1 - P(\bar{A_{5}}) - P(A_{2} \cup A_{5})$
		- $= 1 - P(\bar{A_{2}})+ P(\bar{A_{5}}) + P(\bar{A_{2}\cup A_{5}})$
		- $\geq 1 - (P(\bar{A_{2}}) + P(\bar{A_{5}}))$
		- $1 - (\alpha + \alpha)$
- Bonferroni Inequality
	- For $g$ events $A_i$, $P(A_{1} \cap ... \cap A_{g}) \geq 1 - \sum^g_{i=1}P(\bar{A_{i}})$
	- If $P(\bar{A_{i}}) = \frac{\alpha}{g}$, $P(A_{1}\cap...\cap A_{g}) = 1-\alpha$
- This means that when calculating your confidence intervals, you must instead use a critical value of $t(1-\frac{\alpha}{2g}; n-2)$
	- Ex 90% over 5 intervals - alpha is taken over 5 for 98% for interval

What about confidence intervals for $\beta_{0}$ and $\beta_{1}$?
- Just divide the alpha for the critical value by 2! ![[Pasted image 20240925132845.png]]

Working-Hotelling Procedure
- Gives a confidence band for a whole range of data
- Formula for a specific Y: ![[Pasted image 20240925133246.png]]
	- Note: this is thinnest at $\bar{X}$
	- We are $(1-\alpha)100\%$ confident that the true regression function is within this band!
	- You can pic as many confidence intervals from this band, for as many $X_{i}$ values as you want, and the joint confidence is at least $(1-\alpha)100\%$
- Comparing interval sizes: ![[Pasted image 20240925134101.png]]
	- Working-Hotelling is always the widest because it need to allow any number of $X_{i}$s

## Regression through the origin

Sometimes, we know that $\beta_0$ should be 0 and want to force this to be the case
- This changes all our calculated estimators, and screws with $r^2$ (which has no clear meeting and can even be negative!)
	- The regression line may not even go through ($\bar{X}, \bar{Y}$) - only ($0, 0$)
	- The sum of the residuals may not be 0
- The model is now $Y_{i}= \beta_{1}X_{i}+\epsilon_{i}$
	- $\epsilon_{i}$ is still proportional to $N(0, \sigma^2)$
	- $\beta_{1}$ and $\sigma^2$ are unknown parameters
	- $X_i$s are fixed constants
- Estimation formulas
	- $b_{1} = \frac{\sum^n_{i=1}X_{i}Y_{i}}{\sum^n_{i=1}X_{i}^2}$
	- $s^{2} = MSE = \frac{1}{n-1}\sum^n_{i=1}e_{i}^2$
		- Note that the degrees of freedom has been increased to n-1, because $\beta_0$ is no longer being estimated!

## Measurement error

Measurement errors can always occur, in both $X$ and $Y$
- This is just treated as another source of randomness
- When it happens to $Y$, no biggie, it's just absorbed into $\epsilon$
- When it happens to $X$, this will cause some issues when attempting to estimate $\beta_1$

Updating our SLR to fix errors in $X$:
- We define the following: 
	- $X_{i}$: The true value of the independent variable
	- $X_{i}^{*}$: The observed value of the independent variable
		- This has an unknown measurement error $\delta_{i} = X_{i}^{*} - X_i$
- New SLR model formula: $Y= \beta_{0} + \beta_{1}X_{i}^{*} + (\epsilon_{i} - \beta_{1}\delta_{i})$
	- This is because the real $X_{i}$ is equal to $X_{i}^{*} - \delta_i$
	- Here, we have to treat $X_{i}^{*}$ as *random*, not fixed!
- We know $X_{i}^{*}$  is correlated with ($\epsilon_{i} - \beta_{1}\delta_i$) - let's determine their covariance
	- Assume $E(\epsilon_{i}) = E(\delta_{i}) = E(\delta_{i}\epsilon_{i}) = 0$
	- It follows that $E(X_{i}^{*}) = X_{i}$
	- Final calculation: ![[Pasted image 20241002133845.png]]
	- Assuming $\beta_{1} \neq 0$, then the covariance between $X^{*}$ and the errors is non-zero
- With $\beta_{1}^{*}$ being the slope with measurement error, $\beta_{1}^{*} = \left(\frac{\sigma_{x}^{2}}{\sigma_{x}^{2}+\sigma_{y}^{2}}\right)\times \beta_1$
	- Thus, $|\beta_{1}^{*}| < |\beta_1|$
- Key takeaways
	- Errors in X cause much more complication then errors in Y
	- Values of $X_{i}^{*}$ and error term $\epsilon_{i}-\beta_{1}\delta_{1}$ are dependent
	- Regression slope parameter is too small on average


Next lecture: [[Matrix Algebra (5)]]