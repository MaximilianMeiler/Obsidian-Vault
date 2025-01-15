Previous lecture: [[Simultaneous Inferences (4)]]


Notation
- m x n matrix has m rows and n columns
- Element $a_{mn}$ is in the mth row and nth column
- Vectors have just one row or column
- Transposes ($'$) are matrices with their columns and rows swapped
	- $a^{'}_{ij} = a_{ji}$
- Matrices are equal iff the dimensions and all elements match
- Addition and subtraction just adds all corresponding elements
	- The two matrices being added must be the same dimension

Matrix multiplication
- Scalar multiplication: multiply all elements by that scalar individually
- By a matrix: Can only be performed on a $a\times n$ and $n \times b$ matrix
	- Let C = AB: ![[Pasted image 20241004132012.png]]
	- Essentially, add the dot products of the corresponding row / column
	- The resulting matrix c has dimensions $a \times b$
	- Note: matrix multiplication is not commutative!

Special matrices
- A matrix is **symmetric** if $A = A^{'}$ 
	- Any symmetric matrix is square
	- Any product like $Z^{'}Z$ is symmetric
- A diagonal matrix is a square matrix where only the diagonal contains non-zero elements
- The identity matrix is a diagonal matrix containing only 1s
- **1**: A column vector with all elements 
	- **1**'**1** = n
	- **11**' = **J**
- **J**: A square matrix with all elements 1
- Zero vector: a column vector with all elements 0

Linear dependence and matrix rank
- Each matrix can be broken down into separate columns
	- If one column can be represented as a linear combination of the others, the columns of that matrix are **linearly dependent**. The matrix is **singular**.
- The **rank** of a matrix is the number of linearly independent columns

Inverting a matrix
- If $A^{-1}$ exists, $AA^{-1} = A^{-1}A = I$
- In order for a matrix to have an inverse,
	- It must be a square matrix
	- Its columns must be linearly independent
		- n = rows = cols = rank
- The inverse of a diagonal matrix - if all elements on the diagonal are nonzero, the inverse just contains all the elements' reciprocals in the same place as the original elements
- 2x2 inverses ![[Pasted image 20241007131226.png]]
	- D - determinant = $ad - bc$
	- If the determinant is 0, the matrix is singular and does not have an inverse!
- To solve an equation $Ax = B$, we can just multiply both sides by $A^{-1}$

Properties
- $(AB)C = A(BC)$
- $C(A+B) = CA+CB$
	- $(A+B)C = AC+BC$
- $(A')' = A$
- $(A + B)' = A' + B'$
- $(ABC)' = C'B'A'$
- $(AB)^{-1} = B^{-1}A^{-1}$
- $(A^{-1})^{-1} = A$

## Regression

Regression analysis
- Remember how our SLR had $Y_{i}= E(Y_{i}) + \epsilon_i$?
- We can now rewrite the model with these components: ![[Pasted image 20241004131729.png]]
- We can multiply our $n \times 2$ **design matrix** with our $2 \times 1$ coefficients: ![[Pasted image 20241004132737.png]]
- Final SLR: $\underset{\sim}{Y}$  $\tilde{Y}$ = [FIX THIS]
- Notable matrices: ![[Pasted image 20241004133319.png]]
	- $(X'X)^{-1}$ = ![[Pasted image 20241007132110.png]]

Random matrices
- A random vector is filled with random variables $Y_{1...n}$
	- The expected value of the vector is just each $Y_i$ at its expected value
	- The usual rules for expected values still work - we can factor out constant additives and multipliers
- $E(Y) = E(X\beta + \epsilon) = E(X\beta) + E(\epsilon) = XE(\beta) + E(\epsilon)$ 
- Variance
	- ![[Pasted image 20241007133343.png]]
	- If $Z_i$ and $Z_j$ are independent, $Cov(Z_{i}, Z_{j})= 0$
	- $Var(\epsilon)$ is the diagonal matrix with $\sigma^2$, or $\sigma^{2}I$
		- $Var(\epsilon_{i}) = \sigma^2$, $Cov(\epsilon_{i}, \epsilon_{j}) = 0$
	- $Var(aV + b) = Var(aV) = a^{2}Var(V)$
	- $Var(AV + B) = Var(AV) = AVar(V)A'$

SLR in matrix terms
- SLR can be compactly represented as $Y = $
- Assume that
	- $\epsilon \approx N(0, \sigma^2I)$
	- $\beta$ and $\sigma^2$ are constant parameters
	- $X$ is a constant matrix
- Thus, $E(Y) = X\beta$ and $Var(Y) = \sigma^{2}I$
- Remember the least squares criterion? ![[Pasted image 20241011125609.png]]
	- It turns out that $Z'Z = \sum{Z_{i}^2}$
		- $Z' = [Y_{1} - (\beta_{0} + \beta_{1}X_{1}), ..., Y_{n}- (\beta_{0} + \beta_{1}X_{n})]$
		- Z = $[Y_{1}/.../Y_{n}]$ - $[1, X_{1}/.../1,X_{n}][\beta_{0}/\beta_{1}]$ [COMPLETE]
- Taking the derivative to minimize gives us these equations ![[Pasted image 20241011130131.png]]
	- Or them in matrix form: ![[Pasted image 20241011130203.png]]
	- $(X'X)b = (X'Y)$ where $b = [b_{0} / b_{1}]$
	- Premultiplying with $(X'X)^{-1}$ gives $b = (X'X)^{-1}(X'Y)$

Fitted values and residuals
- The vector of fitted values $\hat{Y} = Xb = X(X'X)^{-1}X'Y = HY$
	- We call the $n \times n$ matrix  $H = X(X'X)^{-1}X'$ the **hat matrix**
		- $H$ is symmetric ($= H'$) and idempotent ($=HH$)
		- $HX = H$, $HIH = H$
	- $E[\hat{Y}] = E[HY] = HE[Y] = HX\beta = X\beta$
	- $Var[\hat{Y}] = Var[HY] = HVar[Y]H' = H(\sigma^{2}I)H= \sigma^{2}HIH = \sigma^{2}H$
- Residuals: $e = Y - \hat{Y} = IY - HY = (I-H)Y$
	- $I-H$ is also symmetric and idempotent!
	- $E[e] = E[(I-H)Y] = (I-H)E[Y] = (I-H)X\beta = X\beta - X\beta = 0$
	- $Var[e] = Var[(I-H)Y] = (I-H)Var[Y](I-H)' = (I-H)\sigma^{2}I(I-H)$
		$= \sigma^{2}(I-H)(I-H)= \sigma^2(I-H)$

Inferences in Regression Analysis
- $b = (X'X)^{-1}X'Y = CY$
	- C is a $2 \times n$ matrix of constants
- $E[b] = E[CY] = CE[Y] = (X'X)^{-1}X' X\beta = \beta$
- $Var[b] = Var[CY] = CVar[Y]C' = \sigma^{2}(X'X)^{-1}X'X(X'X)^{-1} = \sigma^{2}(X'X)^{-1} =$ ![[Pasted image 20241011132443.png]]
	- $\hat{Var}(b)$ subs $MSE$ for $\sigma^2$
	- $Var(b_{0}) = \frac{MSE}{S_{XX}}\frac{1}{n}\sum{X_{i}^2}$
	- $Var(b_{1}) = \frac{MSE}{S_{XX}}$
	- $Corr = \frac{Cov}{\sqrt{Var_{1}Var_{2}}}$ ![[Pasted image 20241011132949.png]]
- $b \approx N(\beta , \sigma^{2}(X'X)^{-1})$

Estimating the mean of the response at $X_{h}$
- $\hat{Y}_{h}= b_{0}+b_{1}X_{h}= X_{h}'b$ where $X_{h}' = [1 X_{h}]$
- $E[\hat{Y}_{h]}= E(X_{h}'b) = X_{h}'E(b) = X_{h}'\beta$
- $Var[\hat{Y}_{h}]= Var(X_{h}'b) = X_{h}'Var(b)X_{h} = X_{h}'\sigma^2(X'X)^{-1}X_{h}$
	- $\hat{Var}[\hat{Y}_{h}] = (MSE)X_{h}'(X'X)^{-1}X_{h}$
- ![[Pasted image 20241011133625.png]] ![[Pasted image 20241011133802.png]]


Next lecture: [[Multiple Linear Regression (6)]]