Previous lecture: [[Inference in Regression Analysis (2)]]

### Assumptions and Violations
So far, we assume with our data that
- $Y_{i}= \beta_{0}+ \beta_{1}X_{i}+ \epsilon_{i}$
- and $\epsilon_{i} \approx N(0, \sigma^2)$
- and $\beta_{1}$, $\beta_0$, and $\sigma^2$ are unknown parameters
- and $X_i$s are fixed constants
What could run counter to these assumptions?
- The regression function just isn't linear
- Error terms don't have a constant variance $\sigma^2$
- Error terms are not independent
- Model fits all but a few outliers
- Errors aren't normally distributed
- SLR isn't reasonable - more predictors ($X$s) are necessary!

We can use **residual plots** to diagnose these problems
- Residuals: $e_{i}= Y_{i}- \hat{Y_{i}} = Y_i -(b_{0}+ b_{}X_{i})$
	- Sample mean: $\bar{e} = \frac{1}{n}\sum_{i}e_{i}=0$
	- Sample variance: $\frac{1}{n-2}\sum_{i}(e_{}-\bar{e})^{2}= MSE$
- We will also use standardized residuals to identified outliers
	- $e_{i}^{*} = \frac{e_{i}}{\sqrt{MSE}}$

Nonlinearity of Regression Function
- Residual plot against $X$![[Pasted image 20240918125954.png]]
	- Remedy: transformation on $X$ or $Y$ ($X$  -> $X^2$, $e^x$, $ln(x)$)
- ![[Pasted image 20240918131103.png]]
	- First: acceptable
	- Second: violation of linear assumption - periodic pattern, transform X
	- Third: violation of another assumption - uneven distribution around y=0, $\epsilon$ isn't normally distributed

Nonconstancy of Error Variance
- Error variance changes as X changes![[Pasted image 20240918131638.png]]
	- Remedy: transform Y

Nonindependence of Error Terms
- This seems like a reasonable distribution: ![[Pasted image 20240918131954.png]]
- But let's say we have data collected in a certain order, and we order by the residuals by that new variable:![[Pasted image 20240918132125.png]]
	- So when data is collected in a specific order, make sure to plot the residuals vs that order to check for another pattern!

Model fits all but a few observations
- Rule of thumb - if $|e^*_{i}|> 3$, check these observations
- Building a regression equation with and without the outliers can help ![[Pasted image 20240918132712.png]]
- Remedies: 
	- Delete outliers
	- Create an *indicator variable* for the outlier as a new predictor variable
		- Ex. 1 if X is an outlier, 0 if an X isn't

Errors aren't normally distributed
- We can assume that the error terms are distributed along $N(0, \sigma^2)$ if the residuals appear to be iid $N(0, MSE)$
- How do we check?
	- Calculate the $e_{i}^{*}$s and order them in ascending order
	- Plot these against their expected values in a normal probability plot
	- They are plotted against a standard normal distribution so that they should form a straight line. If we don't see a straight line, errors may not be normally distributed: ![[Pasted image 20240918133516.png]]
- Remedy: use a transformation, typically on Y
- Use `qqnorm()` in r to display points against a normal distribution

Omission of important predictors
- Plotting the residuals vs. another variable $Z$ may lead to new patterns being uncovered ![[Pasted image 20240920130207.png]]
	- Any pattern (doesn't have to be linear) indicates a violation of this assumption
- Remedy: convert to a multiple regression model!

### Example
- $e^{*}_{i} = \frac{e_{i}}{\sqrt{MSE}}$ = $\frac{Y_{i}-\hat{Y}_i}{\sqrt{\frac{SSE}{n-2}}}$
- Analyzing r summary table
	- Std. error: ${\sqrt{\frac{MSE}{S_{XX}}}}$
	- t value: test statistic - $\frac{b_1}{\sqrt{\frac{MSE}{S_{XX}}}}$

### Transformations
- If we had the function $y = x^2$,
	- Plotting the data along the axes $(x^{2}, y)$ would form a straight line! 
	
There are two situations in which transformations may help:
- Nonlinear regression function with constant error variances
	- Typical remedy - just transform $X$
	- Our $\hat{Y}$ would just use this transformed $X$ - (ex. $Y = \beta_{0} + \beta_{1}\sqrt{X}$)
- Nonlinear regression function with nonconstant error variances
	- Typical remedy - transform $Y$, maybe even $X$ as well
		- Adjusting y changes how data is spread out

Transformation prototypes:
-  Transformations on Y: ![[Pasted image 20240923125639.png]]
	- Try $\sqrt{Y}$, $log(Y)$ ($ln(Y)$ is very popular) or $\frac{1}{Y}$
- Transformations on X:![[Pasted image 20240923125720.png]]
	- Try $\sqrt{X}$, $log(X)$, $X^2$, or $\frac{1}{X}$

Box-Cox transformation
- Procedure that automatically identifies a transformation for $Y$
	- Transform $Y$ as a power transformation: $Y^{'} = Y^{\lambda}$
		- Exception: If $\lambda = 0$, then $Y^{'} = ln(Y)$
	- The regression model becomes $Y_{i}^{\hat{\lambda}} = \beta_{0}+ \beta_{1}X_{i} + \epsilon_i$
		- In r, use `boxcox(Y ~ X)` to find the optimal lambda $\hat{\lambda}$
- Benefits
	- Helps stabilize the variance when it is non-constant
	- Helps when residuals aren't normally distributed
- Drawbacks
	- The outcome $Y$ must be positive. Otherwise, we need to add a constant $C$ to all $Y_{i}$ such that every $Y_{i} + C > 0$
		- Usually, $C = -min(Y_{i}) + .0000001$
	- The method may not work well when there is a clear non-linear relationship
		- You may want to just transform on X first instead
	- It's more difficult to interpret the model coefficient after a transformation on $Y$
	- When outliers are present, the method may have trouble identifying an appropriate $\lambda$


Next lecture: [[Simultaneous Inferences (4)]]