# [[#Sigmoid function]] 
$$g(z)=\frac{1}{1+e^{-z}}\quad 0<g(z)<1$$
```desmos-graph
top = 1.1
bottom = -0.1
right = 3
left = -3
---
y=\frac{1}{1+e^{-x}}|0<y<1
```
- Outputs between **0** and **1**
# [[Logistic regression]] model 
- Step 1: A [[Linear regression]] function is $$z=\vec{w}\cdot\vec{x}+b$$
- Step 2: Pass $z$ to [[#Sigmoid function]] $$g(z)=\frac{1}{1+e^{-z}}$$
- [[Logistic regression]] model: $$f_{\vec{w},b}(\vec{X}=g(\vec{w}\cdot\vec{X}+b)=g(z)=\frac{1}{1+e^{-(\vec{w}\cdot\vec{X}+b)}}$$
# Interpretation of [[Logistic regression]] output 
[[02. Probability]] that class is **1**: $$f_{\vec{w},b}(\vec{x})=\frac{1}{1+e^{-(\vec{w}\cdot\vec{x}+b)}}$$
Example:
- $x$ is "tumor size"
- $y$ is $0$ (**not malignant**) or $1$ (**malignant**)
$f_{\vec{w},b}(\vec{X})=0.7 \quad \text{70\% chance that }x\text{ is 1}$
[[02. Probability]] that$y$ is $1$, given input $\vec{x}$, parameters $\vec{w},b$: $$f_{\vec{w},b}(\vec{X})=P(y=1|\vec{x};\vec{w},b)$$
$P(y=0)+P(y=1)=1$
# Decision boundary
- A decision boundary is **a line (in the case of two features), where all (or most) samples of one class are on one side of that line, and all samples of the other class are on the opposite side of the line**
![[Pasted image 20230823150952.png]]
When is $$
\begin{equation}
\begin{split}
f_{\vec{w},b}(\vec{X})\geq0.5? \\
g(z)\geq0.5\\
z\geq 0 \\
\text{If }\vec{w}\cdot\vec{x}+b\geq0 \text{ then } \hat{y}=1 \\
\text{else }\hat{y}=0
\end{split}
\end{equation}$$
## Non-linear [[#Decision boundary]]
![[Pasted image 20230823151223.png]]
- Can use [[Polynomial regression]] to make complex [[#Decision boundary]]
# [[Cost function]] of [[Logistic regression]]
- Convex 
- Can reach a global minimum
$$\begin{align*}\\
L(f_{\vec{w},b}(\vec{X}^{(i)}),y^{(i)}) &= \left\{ \begin{array}{ll} -\log(f_{\vec{w},b}(x^{(i)})) & \text{if } y^{(i)} = 1 \\ -\log(1-f_{\vec{w},b}(x^{(i)})) & \text{if } y^{(i)} = 0 \end{array} \right. \\
\end{align*}$$
- When $y^{(i)}=1$
	- As $f_{\vec{w},b}(\vec{X}^{(i)})\rightarrow1\text{ then loss } \rightarrow0$ 
	- As $f_{\vec{w},b}(\vec{X}^{(i)})\rightarrow0\text{ then loss } \rightarrow\infty$
	- Loss is lowest when $f_{\vec{w},b}(\vec{X}^{(i)})$ predicts close to true label $y^{(i)}$.
![[Logistic regression 2023-08-24 20.44.04.excalidraw]]
- If $y^{(i)}=0$
	- As $f_{\vec{w},b}(\vec{X}^{(i)})\rightarrow0\text{ then loss } \rightarrow0$ 
	- As $f_{\vec{w},b}(\vec{X}^{(i)})\rightarrow1\text{ then loss } \rightarrow\infty$
	- The further prediction $f_{\vec{w},b}(\vec{X}^{(i)})$ is from target$y^{(i)}$, the higher the loss.
![[Drawing 2023-08-24 20.58.59.excalidraw]]
# Simplified loss function
- Loss function: $$L(f_{\vec{w},b}(\vec{X}^{(i)}),y^{(i)})=-y^{(i)}\log{(f_{\vec{w},b}(\vec{x}^{(i)}))}-(1-y^{(i)})\log{(1-f_{\vec{w},b}(\vec{x}^{(i)}))}$$
	- Convex (single global minimum)
- [[Cost function]]: $$\begin{align*}J(\vec{w},b) &=\frac{1}{m}\sum\limits_{i=1}^{m}[L(f_{\vec{w},b}(\vec{X}^{(i)}),y^{(i)})]\\ &=-\frac{1}{m}\sum\limits_{i=1}^{m}[y^{(i)}\log{(f_{\vec{w},b}(\vec{x}^{(i)}))}+(1-y^{(i)})\log{(1-f_{\vec{w},b}(\vec{x}^{(i)}))}]\end{align*}$$
	- Derived from statistics using [[Maximum likelihood estimation]] to find parameters for different models
# [[Gradient Descent]] implementation
## Training [[Logistic regression]] 
- Find $\vec{w},b$
- Given new $\vec{x}$, output $f_{\vec{w},b}(\vec{X})=\frac{1}{1+e^{-(\vec{w}\cdot\vec{x}+b)}}$ 
## [[Gradient Descent]] for [[Logistic regression]] 
repeat {
$$
\begin{align*}\\
w_{j} &= w_j-\alpha[\frac{1}{m}\sum\limits_{i=1}^{m}(f_{\vec{w},b}(\vec{x}^{(i)})-y^{(i)})x_{j}^{(i)}]\\
b &= b-\alpha[\frac{1}{m}\sum\limits_{i=1}^{m}(f_{\vec{w},b}(\vec{x}^{(i)})-y^{(i)})] 
\end{align*}
$$
} simultaneous updates
Same concepts:
- Monitor [[Gradient Descent]] ([[Learning curve]])
- Vectorized implementation
- [[Feature Scaling]]