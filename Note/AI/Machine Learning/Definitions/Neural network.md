# Neurons and the brain
## Neural networks 
- Origins: Algorithms that try to mimic the brain 
- Used in the 1980's and early 1990's
- Fell out of favor in the late 1990's
- Resurgence from around 2005
- Speech ---> images ---> text (NLP) ---> ...
-  How neurons work: ![[Pasted image 20230826160415.png]]
![[Pasted image 20230826160554.png]]
![[Pasted image 20230826160833.png]]
# Demand prediction 
![[Pasted image 20230826161310.png]]
- $x$: price 
- $a$: stands for activation (refers to how much a neuron is sending a high output to other neurons downstream from it)
![[Pasted image 20230826161637.png]]
- $\text{layer:}$ is a grouping of neurons which take input the same or similar features and that in turn outputs a few numbers together
- $\text{input layer:}$ a vectors of features 
- $\text{hidden layer}$: is a layer in between input layers and output layers, where artificial neurons take in a set of weighted inputs and produce an output through an [[Activation function]].
> The way a neural network is implemented in practice each neuron in a certain layer say this layer in the middle will have access to every feature to every every value from the previous layer from the input layer
## Multiple hidden layers 
![[Pasted image 20230826164157.png]]
# Example 
## Recognizing images
![[Pasted image 20230826164532.png]]
![[Pasted image 20230826164752.png]]
# Neural network model 
## Neural network layer
![[Pasted image 20230903164826.png]]
![[Pasted image 20230903165231.png]]
![[Pasted image 20230903165331.png]]
## More complex neural network 
![[Pasted image 20230903173230.png]]
- Activation value of layer $l$,unit(neuron) $j$: $$a_{j}^{[l]}=g(\vec{w}_{j}^{l}\cdot \vec{a}^{[l-1]}+b_{j}^{[l]})$$
	- $\vec{a}^{[l-1]}$: output of layer $l-1$ (previous layer)
	- $\vec{w}_{j}^{l},b^{[l]}_{j}$: Parameters $w\;\&\;b$  of layer $l$, unit $j$
	- $g$: sigmoid function ([[Activation function]])
## Inference: making predictions (forward propagation)
### Forward propagation 
> Is the process that propagate the activations of the neurons to make these computations in the forward direction from left to right.

## Inference in code
![[Pasted image 20230906213343.png]]
```python
x = np.array([[200.0, 17.0]])
layer_1 = Dense(units=3, activation='sigmoid')    # 3 hidden units using sigmoid function, Dense is the name of the layer
a1 = layer_1(x)    # Compute the layer_1
> a1 = [0.2, 0.7, 0.3].T

layer_2 = Dense(units=1, activation='sigmoid')
a2 = layer_2(a1)
> a2 = [0.8]
```
### Model for digit [[Classification|classification]]
![[Pasted image 20230906214003.png]]
```python
x = np.array([[0.0,...245,...240....0]])
layer_1 = Dense(units=25, activation='sigmoid')
a1 = layer_1(x)
layer_2 = Dense(units=15, activation='sigmoid')
a2 = layer_2(a1)
layer_3 = Dense(units=1, activation='sigmoid')
a3 = layer_2(a2)

if a3 >= 0.5:
	yhat = 1
else:
	yhat = 0
```
# Neural network implementation in Python
## Forward prop in a single layer
- Remember: 
	- Activation value of layer $l$,unit(neuron) $j$: $$a_{j}^{[l]}=g(\vec{w}_{j}^{l}\cdot \vec{a}^{[l-1]}+b_{j}^{[l]})$$
	- [[Logistic regression#Sigmoid function|Sigmoid function]]: $$g(z)=\frac{1}{1+e^{-z}}\quad 0<g(z)<1$$
```python
x = np.array([200, 17])

# Calculate a_{1}^{1}
w_1 = np.array([1, 2])
b1_1 = np.array([-1])
z1_1 = np.dot(w1_1, x) + b
a1_1 = sigmoid(z1_1)

w1_2 = np.array([-3,4])
b1_2 = np.array([1])
z1_2 = np.dot(w1_2,x) + b
a1_2 = sigmoid(z1_2)

w1_3 = np.array([5,-6])
b1_3 = np.array([2])
z1_3 = np.dot(w1_3,x) + b
a1_3 = sigmoid(z1_3)

a1 = np.array([a1_1, a1_2, a1_3])
```
## General implementation of forward propagation 
### Forward prop in NumPy
- Using previous input 
```python
W = np.array([[1, -3, 5],
			 [2, 4, -6]])
b = np.array([-1, 1, 2])
a_in = np.array([-2, 4])
```
- Define Dense function
```python
def dense(a_in,W,b,g):
	units = W.shape[1]    # units=3 because W.shape = [2,3]
	a_out = np.zeros(units)    # Initialize a_out
	for j in range(units):
		w = W[:,j]    # Pull out the j column of a matrix
		z = np.dot(w,a_in) + b[j]
		a_out[j] = g(z)
	return a_out
```
- Define Sequential
```python
def sequential(x):
	a1 = dense(x, W1, b1)
	a2 = dense(x, W2, b2)
	a3 = dense(x, W3, b3)
	a4 = dense(x, W4, b4)
	f_x = a4
	return f_x
```