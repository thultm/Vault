- ![[Pasted image 20230826152504.png]]To reduce [[Overfitting]]
- Reduce the size of parameters $w_{j}$
- [[Regularization]] lets you keep all of your features but  it just prevents the features from having a overly large effect which is what sometimes can cause [[Overfitting]]
# [[Cost function]] with [[Regularization]]
![[Drawing 2023-08-25 20.33.40.excalidraw]]
- If choose $\lambda$ is large, the model will [[Underfitting|underfit]] 
- If choose $\lambda$ small, the model will [[Overfitting|overfit]] 
# Regularized [[Linear regression]] 
[[Gradient Descent]]: repeat {
	  $$w_{j}=w_{j}-\alpha\Bigr[\frac{1}{m}\sum\limits_{i=1}^{m}[(f_{\vec{w},b}(x^{(i)}-y^{(i)})x_{j}^{(i)}]+\frac{\lambda}{m}w_{j}\Bigr]$$
	  $$b=b-\alpha\Bigr[\frac{1}{m}\sum\limits_{i=1}^{m}[(f_{\vec{w},b}(x^{(i)}-y^{(i)})x_{j}^{(i)}]+\frac{\lambda}{m}w_{j}\Bigr]$$
} simultaneous update 
![[Pasted image 20230826152513.png]]
# Regularized [[Logistic regression]]
[[Gradient Descent]]: repeat {
$$w_{j}=w_{j}-\alpha\Bigr[\frac{1}{m}\sum\limits_{i=1}^{m}[(f_{\vec{w},b}(x^{(i)})-y^{(i)})x_{j}^{(i)}]+\frac{\lambda}{m}w_{j}\Bigr]$$
$$b=b-\alpha\Bigr[\frac{1}{m}\sum\limits_{i=1}^{m}(f_{\vec{w},b}(x^{(i)})-y^{(i)})\Bigr]$$
} simultaneous update
![[Drawing 2023-08-26 15.27.26.excalidraw]]
# Dropout [[Regularization]]
- Is a powerful [[Regularization]] technique that can help prevent [[Overfitting]] in neural networks.
- The basic idea is randomly selected neurons are ignored during training. They are “dropped-out” randomly. This means that their contribution to the activation of downstream neurons is temporally removed on the forward pass and any weight updates are not applied to the neuron on the backward pass.
## Why does drop-out work?
- Dropout $\rightarrow$ Less performance (meaning high bias) $\rightarrow$ Down dropout ratio
# Other [[Regularization]] methods
- Data augmentation (solving high variance)
- Early stopping 
	- Stop at the right time
	- Avoid [[Overfitting]]
	- Can using with L2 [[Regularization]] 