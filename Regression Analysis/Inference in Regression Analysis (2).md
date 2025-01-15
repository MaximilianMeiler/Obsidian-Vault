Previous lecture: [[Simple Linear Regression (1)]]


If $Y_{i} \approx N(\mu_{i}, \sigma_{i}^2)$ and each $Y_i$ is independent, and $a_{1}, a_{2}, ..., a_n$ are known constants, then:
- A linear combination of independent normal random variables is itself a normal random variable. ![[Pasted image 20240904133856.png]]

**Theorem**: $b_0$ and $b_1$ are linear combinations of the $Y_i$'s.
- That is, we can write $b_{0}= \sum^n_{i=1} k_{i}Y_{i}$
- **Proof** ![[Pasted image 20240906125357.png]]

We know $b_0$ and $b_1$ are normal variables, so what can we conclude?
-  $b_{1} \approx N(\beta_{1}, \frac{\sigma^2}{S_{XX}})$
-  ![[Pasted image 20240906130041.png]]
- ![[Pasted image 20240906130143.png]]![[Pasted image 20240909131003.png]]
- $\sigma_{i=1}^{n} k_{i}X_{i} = $

$E(b_{1}) = \beta_1$
- So $b_1$ is an **unbiased estimator** of $\beta_1$
$Var(b_{1)}= Var(\sum^{n}_{i=1}k_iY_{i)}= \sum^{n}_{i=1}Var[k_iY_{i]}= \sum^{n}_{i=1}k_i^{2}Var(Y_{i}) = \sum^{n}_{i=1}k_{i}^{2}\sigma^{2} = \sigma^{2}\sum^{n}_{i=1}k_{i}^{2} = \frac{\sigma^2}{S_{XX}}$
- We can put the variance inside the sum, because we know each term is independent, meaning the total variance is just the sum of its parts 
- We can take the $k_i$ outside of the variance because we treat all $X$-related terms as constants!

#### Example
- From 93 samples, we have least-squares estimators of $b_{0}= -25.2$ and $b_{1}= 75.6$
- We're testing our null hypothesis $H_0: B_{1}= 0$ (no relation between X and Y)
- $b_{1} \approx N(\beta_{1}, \frac{\sigma^2}{S_{XX}})$
	- $S_{XX} = \sum_{i}(X_{i}-\bar{X})^{2}= 25.38$
- Suppose our variance $\frac{\sigma^2}{S_{XX}}$ was equal to 2500. Then our std deviation would be $\sqrt{2500} = 50$.
	- Assume the null hypothesis is true - $\beta_1$ is 0. Here, a variance of 50 means that 75.6 falls within a 95% confidence interval (2 standard deviations -> -100 to 100!)
	- Here, we would fail to reject the null hypothesis
- Suppose our variance $\frac{\sigma^2}{S_{XX}}$ was equal to 100. Then our std deviation would be $\sqrt{100} = 10$.
	- Assume the null hypothesis is true - $\beta_1$ is 0. Here, a variance of 10 means that 75.6 falls outside a 95% confidence interval (2 standard deviations -> -20 to 20!)
	- Here, we would reject the null hypothesis
- So, our 95% confidence interval for $\beta_1$ is $b_{1} +- 1.96(\sqrt{\frac{\sigma^{2}}{S_{XX}}})$
	- However, we don't know $\sigma$ - can we use $s$ as a replacement?

#### Confident Intervals and Tests for $\beta_1$
- Many observations with the same X, what do we expect the mean Y of those to be?
- Let's transform $b_1$ into a standard normal random variable: $\frac{b_{1} - \beta_{1}}{\sqrt{\frac{\sigma^{2}}{S_{XX}}}} \approx N(0, 1)$
- If we replace $\sigma^2$ with our estimate of it ($MSE$), we get $\frac{b_{1} - \beta_{1}}{\sqrt{\frac{s^{2}}{S_{XX}}}} \approx t(n-2)$
	- t-distribution with n-2 degrees of freedom. This approaches a normal distribution as n -> $\infty$
- $\alpha$ is called the level of significance
	- It is the probability of a TYPE 1 ERROR - $P(\text{reject }H_{0}| H_{0} \text{ true})$
	- We want to minimize this - usually .01, .05, .1
- ![[Pasted image 20240909125502.png]]
	- $t(1-\frac{a}{2}, n-2)$ is the $1- \frac{a}{2}$ percentile value of the $t(n-2)$ distribution
	- $1 - \frac{a}{2}$ is the area to the left of the 1-a/2 (a/2 to the right, everything else on the left)
	- n-2 are just the degrees of freedom
	- "With probability 1-a, we believe $\beta_1$ is between \<the two values\>"
- When testing, we usually take on the null typothesis $\beta_{1}= c$, where $c = 0$
	- Two-sided test: $H_{a}: \beta_{1} \neq c$
		- Reject $H_0$ if $|{t^{*}}| > t(1 - \frac{a}{2}; n -2)$
	- One-sided test: $H_{a}: \beta_{1} < c$
		- Reject $H_0$ if ${t^{*}} < -t(1 - a; n -2)$
	- One-sided test: $H_{a}: \beta_{1} > c$
		- Reject $H_0$ if ${t^{*}} > t(1 - a; n -2)$
- **Test statistic**: $t^{*} = \frac{b_{1}-c}{\sqrt{\frac{MSE}{S_{XX}}}}$
	- Our critical point that boundaries random and sus values
- **p-value**: The probability of a *more extreme* $t^*$ then  the one we got, given that $H_{0}$ is true ![[Pasted image 20240909131634.png]]
	- It's the chance of randomly getting one of those extreme $t^*$ if $H_0$ is true
	- If this is less than $\alpha$, we reject $H_0$
	- `pt()` in r is used to find area under the curve (probability) given a critical point
		- `qt()` is for finding a critical value given a probability/area

#### Confidence Intervals for Mean Responses
- Say we just make 1 new observation for an X, what do we expect the Y to be?
	- ITS MORE THAN ONE THE ONE WAY BELOW IS JUST ONE
- ![[Pasted image 20240909133723.png]]
	- $Var(\hat{Y}_{h})= \sigma^{2}(\frac{1}{n} + \frac{(X_{h}-\bar{X}^2)^2}{S_{XX}})$ 
	- This is a standard normal distribution and thus can be tested on! ![[Pasted image 20240909133902.png]]
- We again don't know $\sigma^2$, so we sub in $MSE$
	- This makes the distribution follow a $t(n-2)$ distribution
- The confidence interval looks like: ![[Pasted image 20240909134051.png]]
	- We are *a*% confident that the $Y$ is between *lower* and *upper* for $X = X_{i}$

#### Prediction Interval for $Y_{h(new)}$
- Here, we're predicting a new observation $X_{h(new)}$
- ![[Pasted image 20240911125945.png]]
	- Notice that the mean of this distribution is ALSO an interval. This means the mean could be the lowest possible al of the interval, or the highest! So we expect the new interval to be a bit larger.
- $E[Y_{h(new)}] +- z(1 - \frac{\alpha}{2} - \sigma)$ = 
- ![[Pasted image 20240911131201.png]]
	- 0 because both are $\beta_{0}+ \beta_{1}X_{h}$
- ![[Pasted image 20240911131243.png]]
	- = $\sigma^{2} + \sigma^{2}[\frac{1}{n} + \frac{(X_{h} - \bar{X})^{2}}{S_{XX}}]= \sigma^2[1 + \frac{1}{n} + \frac{(X_{h} - \bar{X})^{2}}{S_{XX}}]$
	- We replace $\sigma^2$ with MSE
- FINAL INTERVAL: $\hat{Y_{h}} +- t(\frac{1-a}{2}, n-2)\sqrt{MSE[1 + \frac{1}{n} +  \frac{(X_{h} - \bar{X})^{2}}{S_{XX}}]}$
	- Note - the +1 in the deviation denotes the wider distribution!

#### Analysis of Variance
- A difference from a value and the mean value can be expressed by the sum of the residual and the difference between the expected val and the mean![[Pasted image 20240913125611.png]]
	- **Total sum of squares**: Total variabilities among all $Y$s
		- $SSTO = \sum^n_{n=1}(Y_{i}-\bar{Y})^2$
	- **Error sum of squares**: Variabilities of $Y$s around the regression line. Amount that's not explained by the line
		- $SSE = \sum^n_{i=1}(Y_{i} - \hat{Y}_{i})^2$ = $\sum^n_{i=1}e^{2}_i$
	- **Regression sum of squares** The variability among the $Y$s that is explained by the prediction line
		- $SSR = SSTO - SSE = \sum_{i=1}^{n}(\hat{Y}_{i} - \bar{Y})^2$
		- Proof: Sub as the graph shows for SSTO, Expand the square in the sum, the remaining terms will cancel: ![[Pasted image 20240913130347.png]]
	- Note - degrees of freedom
		- Defined as the number of independent values used in a calculation
		-  Take the number of independent values that are used in the calculation of that statistic
			- These values will be random
		- Subtract 1 for every constraint associated with the calculation.
			- A constraint is an equation that relates all the quantities involved in the equation/statistic given
	- Degrees of Freedom
		- We treat our $Y_{1...n}$ as random, and $X$s as constant
		- $SSTO$: n-1
			- n random values $Y_{1...n}$ 
			- $\bar{Y} = \frac{1}{n}\sum^n_{i=1}(Y_{i})$ - counts as a constraint
		- $SSE$: n-2
			- n random values $Y_{1...n}$ 
			- $\sum^{n}_{i=1}(Y_{i}- \hat{Y}_{i})= 0$ - one constraint
			- $\sum^{n}_{i=1}(e_{i}\hat{Y}_{i}) = \sum^{n}_{i=1}(Y_{i}-\hat{Y}_{i})\hat{Y}_{i} = 0$ - another constraint
		- $SSR$: 1
			- $\bar{Y}_{i}-\hat{Y} = b_{0} + b_{1}X_{i}-\bar{Y} = \bar{Y} - b_1\bar{X}+b_{1}X_{i}-\bar{Y} = b_{1}(X_{i}-\bar{X})$
				- Only $b_{1}$ counts as a random quantity here
	- ![[Pasted image 20240913132448.png]]
	- F-testing
		- $F^{*} = \frac{MSR}{MSE}$
		- Reject $H_{0} if $F^*  > F(1-\alpha, n-2)$
			- Rejects iff the t-test rejects
			- F-testing requires 2 degrees of freedom - one from the numerator ($MSR$), and one from the denominator ($MSE$)
	- For SLR, $F^{*} = t^{*2}$![[Pasted image 20240913133116.png]]
- Check last page of notes for an example of this test!

#### Coefficient of determination
- How useful is the linear relationship between $X$ and $Y$?
	- $r^2$ is the fraction of total variability among $Y_i$s that is explained by a linear relationship to $X_{i}$. The larger $r^2$ is, the more useful the linear relationship.
- $r^{2} = \frac{SSR}{SSTO} = \frac{SSTO-SSE}{SSTO} = 1 - \frac{SSE}{SSTO}$
	- Between 0 and 1
	- If $\hat{Y}_{i} = Y_{i}$, $SSE = 0$ and $r^{2} = 1$
	- If $b_{1} = 0$, $\hat{Y}_i = \bar{Y}$, and $SSR = r^{2} = 0$
		- This only means that the X/Y relationship is not *linear*
- $r^2$ is just equal to the correlation coefficient, $r$, squared
	- $r = \frac{\sum^{n}_{i=1}(x_{i}-\bar{x})(y_{i}-\bar{y})}{\sqrt{\sum^{n}_{i=1}(x_{i}-\bar{x})^2}\sqrt{\sum^{n}_{i=1}(y_{i}-\bar{y})^2}}$
	- $r^{2}= \frac{SSR}{SSTO} = \frac{\sum^{n}_{i=1}(\hat{y_{i}}-\bar{y})^2}{\sum^{n}_{i=1}(y_{i}-\bar{y})^2}$
	- Proof: ![[Pasted image 20240918101632.png]] ![[Pasted image 20240918101703.png]]
	- This also shows how $r = b_{1}\sqrt{\frac{S_{XX}}{SSTO}}$, or how $r$ and $b_1$ should always have the same sign!


Next lecture: [[Diagnostics and Remedial Measures (3)]]