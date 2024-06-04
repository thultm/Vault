- Have some function $J(w,b)$ - [[Cost function]] for [[Linear regression]]  or any function. 
- Want $\underset{w,b}{min}\:J(w,b)$
-   Goal of [[Gradient Descent]]: $$\underset{w_{1},...,w_{n},b}{min}J(w_{1},...,w_{n},b)$$
- Outline: 
	- Start with some $w,b$ (set $w= ,b=0$)
	- Keep changing $w,b$ to reduce $J(w,b)$ (*J not always has U-curve*)
	- Until we settle at or near a minimum (*may have >1 minimum*)
# [[Gradient Descent]] algorithm
$$w_{i+1}=w_{i}-\alpha \frac{\text{d}x}{\text{d}w}\,J(w_{i},b_{i})$$
$\alpha$: [[Learning rate]]
$\frac{\text{d}x}{\text{d}w}\,J(w_{i},b_{i})$: [[Derivative]] of [[Cost function]] 
$$b_{i+1}=b_{i}-\alpha \frac{\text{d}x}{\text{d}b}\,J(w_{i},b_{i})$$
- Simultaneously update $w$ and $b$ at the same time.
- Steps:
	- $tmp\_w=w-\alpha \frac{\partial}{\partial w}\: J(w,b)$
	-  $tmp\_b=b-\alpha \frac{\partial}{\partial b}\: J(w,b)$
	- $w=tmp\_w$
	- $b=tmp\_b$
# Affected of [[Derivative]] of [[Cost function]]
![[Pasted image 20230821185051.png]]
- $$\frac{\partial}{\partial w}\:J(w,b)=\frac{d}{dw}\frac{1}{2m}\sum\limits_{i=1}^{m}(f_{w,b}(x^{(i)})-y^{(i)})^{2}=\frac{d}{dw}\frac{1}{2m}\sum\limits_{i=1}^{m}(wx^{(i)}+b-y^{(i)})^{2}=\frac{1}{2m}\sum\limits_{i=1}^{m}(f_{w,b}(x^{(i)})-y^{(i)})\cdot2x^{(i)}$$
> In summary: $$\frac{\partial}{\partial w}\:J(w,b)=\frac{1}{2m}\sum\limits_{i=1}^{m}(f_{w,b}(x^{(i)})-y^{(i)})\cdot x^{(i)}$$
# Recap
- When near a local minimum:
	- [[Derivative]] becomes smaller
	- Update steps become smaller
- Can reach minimum without decreasing [[Learning rate]].
# An alternative to [[Gradient Descent]]
- Normal equation 
	- Only for [[Linear regression]] 
	- Solve for $w,b$ without iterations
	- Disadvantages
		- Doesn't generalize to other learning algorithms.
		- Slow when number of features is large (>10,000)
	- Maybe used in [[Machine learning]] libraries that implement [[Linear regression]] 
	- [[Gradient Descent]] is the recommended method for finding parameters $w,b$
# Checking [[Gradient Descent]] for convergence
- Make sure [[Gradient Descent]] is wroking correctly
	- Objective: $\underset{\vec{w},b}{min}\:J(\vec{w},b)$
- $J(\vec{w},b)$ should **decrease** after every iteration.
- [[Learning curve]]
- Automatic convergence test
	- Let $\varepsilon$ be $10^{-3}$
	- If $J(\vec{w},b)$ decreases by $\leq\varepsilon$ in one iteration, declare **convergence**. (found parameters $\vec{w},b$ to get close to global minimum)