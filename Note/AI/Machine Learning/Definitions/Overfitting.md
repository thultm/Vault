# The problem of [[Overfitting]]
- [[Underfitting|Underfit]] 
	- Does not fit the [[Training set]] well 
	- High [[Bias]]
```desmos-graph
bottom = -0.5
left = -0.5
top = 15
---
y=x+1
(1,3),(2.5,9.75),(2,7),(3,13)|cross
```
<br>
- [[Generalization]]
	- Fit [[Training set]] pretty well 
```desmos-graph
bottom = -0.5
left = -0.5
top = 15
---
y=x+x^2+1
(1,3),(2.5,9.75),(2,7),(3,13)|cross
```
<br>
- [[Overfitting|Overfit]]
- Fits the [[Training set]] extremely well
- High [[Variance]]
```desmos-graph
bottom = -0.5
left = -0.5
right = 20
top = 20
---
y=\frac{1}{4}*x^4-\frac{16}{6}*x^3+\frac{17}{2}*x^2-12x+25
(1,229/12),(2.5,3115/192),(2,53/3),(3,55/4),(6,7),(6.3,13.797025)|cross
```
# Addressing [[Overfitting]] 
- Collect more data
- Select features to include/exclude 
- [[Feature selection]]
- Reduce size of parameters 
	- [[Regularization]] 