# Sigmoid 
   - **Equation :** $$A = \frac{1}{1 + e^{-x}}$$
   - **Nature :** Non-linear
   - **Value Range :** 0 to 1
   - **Uses :** Usually used in output layer of a binary classification
   - **Graph :**
```desmos-graph
top = 1.1
bottom = -0.1
right = 3
left = -3
---
y=\frac{1}{1+e^{-x}}|0<y<1
```
# Tanh function 
   - **Equation :** $$A = \frac{e^{2x}-1}{e^{2x}+1}$$
- **Value Range :** -1 to +1
- **Nature :** non-linear
- **Uses :** Usually used in hidden layers of a neural network as it’s values lies between **-1 to 1** hence the mean for the hidden layer comes out be 0 or very close to it, hence helps in _centering the data_ by bringing mean close to 0. This makes learning for the next layer much easier.
- **Graph :**
```desmos-graph
top = 1.1
bottom = -1.1
right = 3
left = -3
---
y=\frac{e^{x}-e^{-x}}{e^{x}+e^{-x}}|-1<y<1
```
# ReLU function
- It Stands for _Rectified linear unit_. It is the most widely used activation function. Chiefly implemented in _hidden layers_ of Neural network.
- **Equation :** $$\begin{align*} A(x) &= \max(0,x) \\ &= \left\{ \begin{array}{ll} x & \text{if } x \ge 0 \\ 0 & \text{if } x < 0 \end{array} \right. \end{align*}$$
- - **Value Range :** \[0, inf)
- **Nature :** non-linear, which means we can easily backpropagate the errors and have multiple layers of neurons being activated by the ReLU function.
- **Uses :** ReLu is less computationally expensive than tanh and sigmoid because it involves simpler mathematical operations. At a time only a few neurons are activated making the network sparse making it efficient and easy for computation.
- **Graph :**
```desmos-graph
top = 1.1
bottom = -1.1
right = 3
left = -3
---
y = x | x > 0 | BLUE
y = 0 | x <= 0 | BLUE
```
# Softmax Function
The softmax function is also a type of sigmoid function but is handy when we are trying to handle multi- class classification problems.

- **Equation :** $$A(x_{i})=\frac{e^{x_{i}}}{\sum\limits_{j=1}^{n}e^{x_{j}}}$$
- **Nature :** non-linear
- **Uses :-** Usually used when trying to handle multiple classes. the softmax function was commonly found in the output layer of image classification problems.The softmax function would squeeze the outputs for each class between 0 and 1 and would also divide by the sum of the outputs. 
- **Output:-** The softmax function is ideally used in the output layer of the classifier where we are actually trying to attain the probabilities to define the class of each input.
- The basic rule of thumb is if you really don’t know what activation function to use, then simply use _RELU_ as it is a general activation function in hidden layers and is used in most cases these days.
- If your output is for binary classification then, _sigmoid function_ is very natural choice for output layer.
- If your output is for multi-class classification then, Softmax is very useful to predict the probabilities of each classes.
# How to choose [[Activation function]]
![[Pasted image 20230908170205.png]]