# The importance of tuning hyperparameters
![[Pasted image 20230925112054.png]]
1. [[Learning rate]]: Higher 
2. Loss function: High 
3. Layer size: High
4. Weight intitialization: Medium
5. Layer params (e.g., kernel size): Medium
6. Optimizer choice: Low (Why not affected too much: Because Adam is improved from RMSProp and GD + Momentumn)
# [[Tuning Hyperparameters]] methods
- `GridSearch`
	- Take too much time
- `RandomSearch` (recommended for [[Deep learning]])
	- Picking randomly
	- Rich exploration of a wide range of hyperparameters
- `Coarse-to-fine sampling scheme` 
	- Starting with a coarse sampling to fine sampling of a wide range of hyperparameters 
# Appropriate scale for hyperparameters 
- Units/layers: Sampling uniformly at random 
- [[Learning rate]]: $10^{-4} - 10^{-0}$
- 