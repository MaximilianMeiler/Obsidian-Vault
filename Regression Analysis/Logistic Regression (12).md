Previous lecture: [[Additional Remedial Measures (11)]]


We talked about categorical predictors, but what if $Y$ is binary?
- We use $\pi$ to represent the probability of $Y$ being 1
	- Otherwise, $Y$ is 0 with a probability $1-\pi$
- Expected value $E(Y) = (1)(\pi) + 0(1-\pi) = \pi$
- We represent the graph as a sigmoid $G(t) = \frac{e^{t}}{1+e^{t}}$
- We set $\pi$ to $G(t)$ and solve for $t$, yielding $t = ln(\frac{\pi}{1-\pi})$
	- These are the **log odds** (not the *probability*!)


$$ln\left(\frac{\pi_{i}}{1-\pi_{i}}\right)= \beta_{0} + \beta_{1}X_{i} + ...$$
- Solving for $\pi_{i}$ yields $G(\beta_{0}+\beta_{1}X_{i}+...)$
	- $X = \frac{-b_{0}}{b_{1}}$ always equals $Y = .5$
	- For every one-unit increase in $X$, the odds of success change by $e^{\beta_{1}}$, which is called the **odds ratio**
		- $e^{b_{1}}= 1.0191$. Subtract 1 for $.0191$, there is a $1.91\%$ increase in odds of $Y$ for every one-unit increase in $X$