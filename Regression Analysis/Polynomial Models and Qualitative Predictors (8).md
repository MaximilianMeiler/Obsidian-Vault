Previous lecture: [[Multiple Linear Regression II (7)]]


What if we add extra terms containing polynomial factors of all our predictors?
- ![[Pasted image 20241104133814.png]]
- Approaches
	- Start with a lower order model first. We want the simplest model possible
	- Multicollinearity can be an issue.
		- Instead, we fit against transformed predictors $x_{i}= X_{i}-\bar{X}$ ("center" each one) to remove this impact

### Categorical predictors

We turn a set of categories into a variable:
![[Pasted image 20241106131513.png]]
- Note that in this case, X of 1 just makes a + beta term - this beta will just get incorporated into the Y intercept!
	- $\beta_2$ would just end up being the difference in average Y between males and females!
- However, if we use an interaction term $\beta_3X_1X_2$, the slope will also change
	- $\beta_3$ is the change in slope when comparing average Y between males in females (whereas $B_2$ is the change in intercept)
	- We can run a hypothesis test to see if $\beta_3$ is 0 (the two models have the same slope), or if $\beta_{3}= \beta_{2}= 0$ (the two models are exactly the same)

But what about more than 2 categories?
- This means we establish a rigid "progression" between the predictors and Y ![[Pasted image 20241106132355.png]]
- Instead, what we can do is give each possible category a binary 0/1 value
	- categories-1 bits, with each category having either a 0 in each category or a 1 in just one category
- Again, we need to add interaction terms for the slopes not to be the same! ![[Pasted image 20241108125727.png]]

Several categorical predictors
- Adding terms individually does still provide a structure to the data (here, being female always adds a +2 term): ![[Pasted image 20241108125844.png]]
	- To correct this, we can either split into more independent variables: ![[Pasted image 20241108125928.png]]
	- Or we add an interaction term $\beta_{4}X_{i2}X_{i3}$


Next lecture: [[Model Building (9)]]