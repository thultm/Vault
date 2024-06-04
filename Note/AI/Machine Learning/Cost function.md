> Help to find the best possible straight line for dataset.
## How to choose $w,b$
![[LR - Choose theta]]
> Idea: Choose $w,b$ so that $\hat{y}^{(i)}$  is close to $y^{(i)}$ for our training examples $(x,y)$
- It means we need to minimize $w,b$ in [[Sum of the Squared Error]] ([[Sum of the Squared Error|SSE]]) $$\frac{1}{2m}\sum\limits_{i=1}^{m} (\hat{y}^{(i)}-y^{(i)})^{2}$$
	- $\hat{y}^{(i)}=f_{w,b}(x^{(i)})$: the prediction of the house price
	- $y^{(i)}$: the actual of the house price
	- $m$: the number of training examples
	- The function is the difference between the prediction and the actual of the house price
> The objective is minimize the [[#Cost Function|cost function]]  (also call squared error function)
$$ \DeclareMathOperator*{\minimize}{minimize}
\minimize\limits_{w,b} J(w,b)=\frac{1}{2m}\sum\limits_{i=1}^{m} (f_{w,b}(x^{(i)})-y^{(i)})^{2}$$
## [[#Cost function]] intuition
$$h_{w}(x)=wx; \quad b=0$$
![[Pasted image 20230821150124.png]]
$$ \DeclareMathOperator*{\minimize}{minimize}
\minimize\limits_{w} J(w)=\frac{1}{2m}\sum\limits_{i=1}^{m} (f_{w,b}(x^{(i)})-y^{(i)})^{2}$$
![[Pasted image 20230821150354.png]]
![[Pasted image 20230821150455.png]]
## Visualize the [[Cost function]] 
![[Pasted image 20230821173422.png]]
 - Countour plot in the topographical map are basically horizontal slice of landscape. It shows all the points that are at the same height for different heights.
![[Pasted image 20230821173926.png]]