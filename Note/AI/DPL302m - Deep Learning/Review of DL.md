- Khi nào sử dụng DL:
	- Có hơn 10k data 
	- "Complex"
	- Unstructured data 
	- Need absolute "best" model
- When not use:
	- Don't have large dataset
	- Perform sufficiently well with traditional ML methods 
	- Data is structured and you possess the proper domain knowledge 
	- When your model should be explainable
- [[Neural network]] include:
	- Different connection leads to different structure
FCFN: 1 connect all
Deep = Many hidden layers
AlexNet (2012): 8 layers, error 16.4%
VGG (2014): 19 layers, 7.3% error
GoogleNet (2014): 22 layers, 6.7% error
ResNet(2015) (Skip connection): 152 layers, 3.57%
Taipei101: 101 layers
- Matrix Operation: Try to vectorization 
- Practical Aspects of DL
	- Weight Intitialization: Effect to performance
	- Diagnose [[Note/Note/AI/DPL302m - Deep Learning/Bias and Variance|Bias and Variance]] issues
		- Bias: difference between predictions and true values 
		- Variance: 
	- When to use [[Note/Note/AI/Machine Learning/Regularization|Regularization]]: dropout or L2 [[Note/Note/AI/Machine Learning/Regularization|Regularization]]
	- Vanishing and Exploding Gradient 
		- Vanishing: Avoid by using [[Note/Note/AI/DPL302m - Deep Learning/Batch Normalization|Batch Normalization]], Normalize
		- Exploding:
	- Mismatch train/test distribution data:
		- Combine algorithms 
		- Combine features 
- Optimization
- [[Note/Note/AI/DPL302m - Deep Learning/Tuning Hyperparameters|Tuning Hyperparameters]] 
- When large data, using 95% train, 3% val, 2% test