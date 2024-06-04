# Data in Tensorflow
![[Pasted image 20230906214438.png]]
## Why double square bracket
![[Pasted image 20230906214720.png]]
```python
# 1-D array (no rows or columns)
x = np.array([200,17])
# 2-D array
x = np.array([[0,1],
			 [1,2]])
```
# Activation vector
![[Pasted image 20230906234857.png]]
```python
x = np.array([[200.0, 17.0]])
layer_1 = Dense(units=3, activation='sigmoid')
a1 = layer_1(x)
print(a1)
> tf.Tensor([[0.2 0.7 0.3]], shape=(1,3), dtype=float32)    # Tensor is a data type that the the tensorflow team had created in order to store and carry out computations on matrices efficiently
a1.numpy()
> array([[1.4661001, 1.125196, 3.2159438]], dtype=float32)
```
# Building a [[Neural network|neural network]]
```python
x = np.array([[200.0, 17],
			 [120.0, 5.0],
			 [425.0, 20.0],
			 [212.0, 18.0]])
y = np.array([1,0,0,1])

# Create layers
layer_1 = Dense(units=3, activation='sigmoid')
layer_2 = Dense(units=1, activation='sigmoid')

# String 2 layers together
model = Sequential([layer_1, layer_2])

# Train model
model.compile(...)
model.fit(x,y)

# Predict
model.predict(x_new)
```
