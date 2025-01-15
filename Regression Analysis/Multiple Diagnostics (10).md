Previous lecture: [[Model Building (9)]]


Diagnostic tools
- Residual plots
	- Creating a residual plot against every single $X$ can be cumbersome. Alternatively, we start with an $e_i$ vs $\hat{Y_{i}}$ plot to check for the previously mentioned violations
- Added variable plot
- Identifying Extreme/Influential Data Points
- Detecting multicollinearity

Residual plots
- Look for nonlinear patterns among residuals, changes in variability, or extreme data points in $X_i$ or $e_{i}$

Added variable plot
- Checking to remove a predictor $X_1$
	- Fit a model of $Y$ versus all other predictors
	- Fit a model $X_1$ vs all other predictors
	- Plot $e_{i}(X_{1})$ vs $e_{i}(Y)$
		- If this is linear, include $X_{1}$ as a linear term
		- If this is curved, include $X_1$ as a higher-order term
		- If this is random, do not include $X_{1}$

Extreme data points
- Point types
	- Extreme in X, but Y is consistent with model
		- This does not alter model fit
	- Extreme in Y, but not in X
		- Usually doesn't strongly influence model fit
	- Extreme in both X and Y
		- This point is **influential**
- Identifying points extreme in Y
	- Residual: $e_{i} = Y_{i}-\hat{Y_i}$
	- Standardized residual: $e_{i^{*}}= \frac{e_i}{\sqrt{MSE}}$
	- Studentized residual: $r_{i} = \frac{e_i}{\sqrt{MSE(1-h_{ii})}}$
		- $h_{ii}$ is the $(i, i)$th element of $H = X(X'X)^{-1}X'$
		- This is less than the standardized residual
	- Studentized deleted residual: $t_{i} = \frac{e_i}{\sqrt{MSE_{(i)}(1-h_{ii})}}$
		- $MSE_{(i)}$ is the $MSE$ of the model fitted without the $i$th data point
		- If $|t_{i}|> t(1-\frac{a}{2n}, n-p-1)$, the point is extreme in $Y$
- Identifying points extreme in X
	- $h_{ii}$ is called the **leverage** of the $i$th data point
		- The larger the value, the more impactful the point (from $0-1$) and the smaller the $e_i$
		- A leverage value is considered large if $h_{ii} \geq \frac{2p}{n}$
- Identifying influential data points
	- $DFFITS_{i}=\frac{\hat{Y}_{i}-\hat{Y}_{(i)}}{\sqrt{MSE_{(i)}h_{ii}}} = t_i\sqrt{\frac{h_{ii}}{1-h_{ii}}}$
		- $t_i$ is the studentized deleted residual
		- The point is influential if this value is greater than 1
	- Cook's Distance $D_{i} = \frac{\sum{(\hat{Y}_{j}-\hat{Y}_{j(i)})^{2}}}{pMSE} = \frac{e^2_{i}h_{ii}}{pMSE(1-h_{ii})^2}$
		- The numerator represents plugging in all points to a model with the queries point removed
		- $D_{i}$ is considered large if it is greater than $F(.5, p, n-p)$
	- $DFBETA_{k(i)} = \frac{b_{k}-b_{k(i)}}{\sqrt{MSE_{(i)}[(X'X)^{-1}]_{k+1,k-1}}}$
		- $b_{k}$ is the k'th slope of the corresponding model
		- This measures the change in a certain slope when a certain data point is deleted
		- Considered large when greater than 1
- Detecting multicollinearlity
	- Variance Inflation Factor $VIF_{k} = \frac{1}{1-R_k^2}$
		- Measures how predictable $X_{k}$ is from a function of the other $p-1$ predictors
		- $R^2_k$ is taken from the model of $X_{k}$ vs the other predictors
		- Closer to 1 is better. If $VIF_{k}> 10$, $k$ is subject for deletion
		- If $\bar{VIF} = \frac{1}{p-1}\sum{VIF_k}$ is greater than 3, a simpler model is better


Next lecture [[Additional Remedial Measures (11)]]
