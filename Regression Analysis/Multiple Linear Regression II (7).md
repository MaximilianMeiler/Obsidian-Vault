Previous lecture: [[Multiple Linear Regression (6)]]

## New Predictors
Let's say A and B are sets where $A \subset B$
- Let g be a function that is defined on these sets
- It follows that $min(g(x) | x \text{ in } A) \geq min(g(x) | x \text{ in } B)$
- Thus, B has A's predictor variables ($X$s) plus more

Remember, $SSE$ is the sum of squares not explained by the regression line
- $SSE(A) \geq SSE(B)$ - each predictor variable added decreases SSE
$SSTO = \sum(Y_{i}-\bar{Y})^2$ 
- This does not depend on the regression predictors $X$ and stays constant
- As $SSTO = SSR + SSE$, $SSR(B) \geq SSR(A)$

Adjusted r-squared $1-\frac{SSE}{SSTO}\frac{n-1}{n-p}$
- As $p \geq 1$, $R^{2}_{A}\leq R^{2}$
- This penalizes us for adding new predictors to the model!

Extra sums of squares
- Let A and C be sets of predictors with no overlap
- $SSR(A \cup C) \geq SSR(A)$
- $SSR(C|A) = SSR(A \cup C) - SSR(A)$
	- The extra variability explained by adding the variables in C to A
- $SSR(X_1,...X_{3}) = SSR(X_{1}) + SSR(X_{2}|X_{1}) + SSR(X_{3}|X_{1}X_{2})$
	- Each terms has a df of one, for p-1 total

### Testing predictor subsets
- Let C be a modeI with a few predictors removed
- $H_{0}$ - $\beta_{i1} = ... = \beta_{ik} = 0$
- $H_{A}$ - at least one $\beta_{ij} \neq 0$
- $$F^{*} = \frac{(SSE(reduced) - SSE(full))/(dfE_{reduced} - dfE_{full})}{SSE(full)/dfE_{full}}$$ ![[Pasted image 20241030125618.png]]
- We reject $H_{0}$ if $F^{*}_{k} \geq F(1-\alpha, v_{1}, v_2)$

### Testing single predictors
- $H_{}$ - $\beta_{k}= 0$, $H_{A}$ - $\beta_{k} \neq 0$
- $t_{k}^{*} = \frac{b_{k}-0}{s(b_k)}$
	- Bottom term is equal to standard error (sqrt mse variance)
- Reject if $|t_{k}^{*}| \geq t(1-\frac{\alpha}{2},n-p)$
- This can also be done with an F-test on a one-parameter subset!
	- $F^{*}_{k} = (t^{*}_k)^2$
	- $F^{*}_{k} = \frac{SSE(reduced)-SSE(full)}{SSE(full)/(n-p)} = \frac{SSR(full)-SSR(reduced)}{SSE(full)/(n-p)}$ $= \frac{SSR(X_{k}|remainingXs)}{SSE(full)/(n-p)}$
	- $F^{*}_{k}\geq F(1-\alpha, 1, n-p)$

### Coefficient of Partial Determination
- SSR(A)$: Variability among the Ys explained by the predictors in A
- $SSE(A)$: Variability among the Ys NOT explained by the predictors in A
- $SSR(C|A)$: Variability among the Ys explained by predictors in C beyond what is explained by the predictors in A
- $R^{2}_{C|A} = \frac{SSR(C|A)}{SSE(A)}$
	- The fraction of variability that isn't explained by A, but is now explained by C

## Multicollinearity
-  Some predictors may be effective in modeling other predictors
	- This means info about Y is duped among your predictors
	- If $X_{1}$ and $X_{2}$ are UNcorrelated, $SSR(X_{1}) = SSR(X_{1}|X_{2})$
	- If $X_{1}$ and $X_{2}$ are correlated, predictions and coefficients become unstable during partial interactions
		- Can both be significant individually, but neither together
- For now, we merely drop one of the predictors


Next lecture [[Polynomial Models and Qualitative Predictors (8)]]