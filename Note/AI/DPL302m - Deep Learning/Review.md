# Chapter 1: Introduction to [[Deep learning]]
## 1.1 What is a [[Neural network]]?
- A neural network is a type of machine learning algorithm that is inspired by the structure and function of the human brain.
- Consists of `interconnected nodes`, called `neurons`, that are organized into layers:
	1. The `input layer` receives input data 
	2. The `output layer` produces the output of the model. 
	3. The `intermediate layers`, known as `hidden layers`, perform computations on the input data and progressively extract higher-level features.
- Adjusting `the connections` and `weights` between the neurons $\overset{\text{neural network}}{\rightarrow}$ can be trained to *recognize patterns* and *make predictions* on new data.
- Commonly used in image recognition, speech recognition, natural language processing, and other complex tasks where traditional algorithms may struggle.
- Neural networks are *made up of neurons*, which *take input, compute a function, and produce output.* 
- A single neuron can implement a simple function.
- In contrast, a larger neural network can be formed by stacking many neurons together.
## 1.2 [[Supervised Learning]] with [[Neural network]]
### 1.2.1 Structured data vs. Unstructured data
- ***Structured data*** refers to data that is organized in a pre-defined manner, typically in tables with rows and columns, where each data point has a well-defined meaning.
	- Example: Data found in relational databases, spreadsheets, and transaction logs. 
	- Often processed using traditional data processing tools, such as SQL.
- ***Unstructured data*** refers to data that does not have a pre-defined structure or format. 
	- Example: Text documents, images, audio and video files, social media posts, and email messages. 
	- Often processed using [[machine learning]] algorithms that can extract patterns and meaning from the data.

| **Structured data** 	| **Unstructured data** 	|
|:---:	|:---:	|
| Organized and has a pre-defined format 	| Often disorganized and lacks a pre-defined format. 	|
| Often processed using traditional data processing tools 	| Processed using machine learning algorithms. 	|
## 1.3 Why is [[Deep Learning]] taking off?
- Increasing availability of data %%As the amount of data increased, traditional learning algorithms, such as support vector machines or logistic regression, were unable to keep up.%%
- The development of [[Neural network|neural networks]] that can take advantage of that data. %%Neural networks, on the other hand, were able to take advantage of the vast amount of data to achieve better performance.%%
- Scale drives deep learning progress ![](https://i.imgur.com/HYPJf7t.png)
# Chapter 2: Basics of [[Neural network]] Programming
## 2.1 Binary Classification
- A type of [[machine learning]] problem where the goal is to [[Classification|classify]] input data into one of two categories or classes.
- [[Logistic regression]] is an algorithm used to solve the [[#2.1 Binary Classification|binary classification]] problems. 
## 2.2 Notation of Neural Network
![](https://i.imgur.com/IQHkBio.png)
## 2.3 [[Logistic Regression]]
## 2.4 [[Gradient Descent]]
> Is an optimization algorithm used to minimize a [[Cost function]] by iteratively adjusting the values of the parameters of a model.
- Commonly used in [[machine learning]] to update the [[weights]] and [[biases]] of a [[Neural network]] during training. 
- Idea: Calculate the [[Gradient]] of the cost function with respect to each parameter, which gives us the direction and magnitude of the steepest ascent.
- Take small steps in the opposite direction of the [[Gradient]] to descend the [[Cost function]], towards a local minimum. 
- The size of each step is determined by the [[learning rate]], which is a [[Hyperparameter]] of the algorithm.
	- If the [[learning rate]] is too small, the algorithm may take a long time to [[converge]] to the minimum.
	- While if it is too large, it may overshoot the minimum and fail to [[converge]]. 
- There are different variations of [[gradient descent]], such as [[batch gradient descent]], [[stochastic gradient descent]], and [[mini-batch gradient descent]], which differ in how the gradients are calculated and how the steps are updated.
## 2.5 [[Derivative|Derivatives]]
> Derivatives are a fundamental concept in [[calculus]], and they represent the rate at which one quantity changes with respect to another.
- The formal definition of the [[derivative]] involves taking the limit as the change in a goes to zero. 
- The slope or derivative of a function represents how much the output changes for a given change in the input.
- The slope can be different at different points on the function.
