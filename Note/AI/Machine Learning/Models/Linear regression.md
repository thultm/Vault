# Defination
- Is a supervised learning algorithm
- Terminology
	- [[Training set]]: Data used to train the model. Include:
		- Features
		- Targets
- Notation
	- `m`: Number of training examples
	- `x's`: "input" variable / features
	- `y's`: "output" variable / "target" 
	- $(x,y)$ - one training example
	- $(x^{(i)},y^{(i)})$ - the $i^{th}$ training example

| Size in $\text{feet}^{2}$ (x) | Price ($) in 1000's (y) |
| -----------------------------:|:-----------------------:|
|                          2104 |           460           |
|                          1416 |           232           |
|                          1534 |           315           |
|                           852 |           178           |
|                           ... |           ...           |
![[Linear Regression - Process.excalidraw]]
[[Linear regression]] formula:
$$f_{w,b}(X)=wX+b$$
$w,b$: parameters (coefficients or weights)
## What do $w,b$ do?
# [[Gradient Descent]] for [[Linear regression]]  

- We have:
	- [[Linear regression]] model: $$f_{w,b}(x)=wx+b$$
	- [[Cost function]]: $$J(w,b)=\frac{1}{2m}\sum\limits_{i=1}^{m}(f_{w,b}(x^{(i)}-y^{i)})^{2}$$
	- [[Gradient Descent]] algorithm: repeat until convergence {
	  $$w=w-\alpha \frac{\partial}{\partial w}\: J(w,b)\; \rightarrow \frac{1}{m}\sum\limits_{i=1}^{m}(f_{w,b}(x^{(i)}-y^{(i)})x^{(i)}$$
	    $$b=b-\alpha \frac{\partial}{\partial b} \: J(w,b) \rightarrow \frac{1}{m}\sum\limits_{i=1}^{m}(f_{w,b}(x^{(i)}-y^{(i)})$$}
# Multiple Features 
- Previously: $f_{w,b}(x)=wx+b$
- Multiple features:  $$f_{\vec{w},b}(\vec{X})=\vec{w}\cdot \vec{x}+b=w_{1}x_{1}+w_{2}x_{2}+...+w_{n}x_{n}+b$$
	- With:
		- $\vec{w}=\begin{bmatrix}w_{1} & w_{2} & w_{3} & ... & w_{n}\end{bmatrix}$: parameters of the model
		- $b$ is a number 
		- $\vec{x}=\begin{bmatrix}X_{1} & X_{2} & X_{3} & ... & X_{n} \end{bmatrix}$
## [[#Vectorization]]
Example:
- Parameters and features
	- $\vec{w}=\begin{bmatrix}w_{1}&w_{2}&w_{3}\end{bmatrix}$
	- $b$ is a number
	- $\vec{x}=\begin{bmatrix}x_{1}&x_{2}&x_{3}\end{bmatrix}$
- In linear algebra: count from 1
- In code: count from 0
```python
w=np.array([1.0,2.5,-3.3])
b=4
x=np.array([10,20,30])
```
- Without [[#Vectorization]]$$f_{\vec{w},b}(\vec{X})=\sum\limits_{j=1}^{n}w_{j}x_{j}+b$$
  ```python
  f = 0
  for j in range(0,n):
      f = f + w[j] * x[j]
  f = f + b
```
- [[#Vectorization]]: $$f_{\vec{w},b}(\vec{X})=\vec{w}\cdot\vec{x}+b$$
  ```python 
  f = np.dot(w,x) + b
```
> [[#Vectorization]] make the code shorter and run much faster.

- Advantage of vectorization:
	- Efficient $\rightarrow$ Scale to large datasets