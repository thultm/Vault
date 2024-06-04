# Definition
>Unsupervised learning is a [[Machine learning]] paradigm where the algorithm learns patterns and structures in data without explicit labels or predefined categories.
- Find something interesting in **unlabeled** data.
- Data only comes with input $x$ but not output labels $y$. Algorithm has to find **structure** in the data.
- Uses for 
- [[Dimensionality reduction]]
- [[Clustering]]
- Example
	- Organize computing clusters
	- Social network analysis
	- Market segmentation
	- Astronomical data analysis
- Cocktail party problem algorithm
	- $$$x_i = \begin{bmatrix} x_{1i} \\ x_{2i} \\ \vdots \\ x_{mi} \end{bmatrix} C = \sum_{i=1}^{n} x_i x_{i^T A}=\text{repmat}(C, m, 1) \cdot x [W, S, V] = \text{svd}(A \cdot x^T)$$