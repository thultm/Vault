# Why normalize input?
- If not normalize:
	- Weights can be vanished or exploded.
		- Vanished: ![[Drawing 2023-09-18 11.07.09.excalidraw]][[Derivative]] comes to zeros. (Vanishing gradient  < 1)
	- Exploding: [[Derivative]] large. (Exploding gradient > 1)
# Weights Intitialization 
- Zeros intitialization 
	- Has some significant drawbacks
	- Generally not recommended for deep neural networks 
	- The main issue is that it leads to symmetrics
- Random intitialization
	- 2 popular techniques:
		- Uniform intitialization 
		- Normal (Gaussian) Intitialization
- For the case of ReLU and its variants:
	- Setting the variance of the weight matrix proportional to $\frac{1}{n}$
	- Avoid vanishing
- He intitialization `W(l) = np.random.randn*sqrt(2 / n(l-1))`
- TanH [[Activation function]]