# Intuition 
- Decompose a complex sound into its frequency components
- From time to frequency domain ![](https://i.imgur.com/6n4ufrH.png)
- Compare signal with sinusoids of various frequencies
- For each frequency we get a magnitude and a phase
- High magnitude indicates high similarity between the signal and a sinusoid
- Sine wave: $$\sin(2\pi\cdot(ft-\phi))$$
```python
# Create a sinusoid 
f = 523 
phase = 0

sin = 0.5 * np.sin(2 * np.pi * (f * t - phase))

plt.figure(figsize=(10,8))
plt.plot(t[10000:14000], sin[10000:140000], color='r')

plt.xlabel('Time(s)')
plt.ylabel('Amplitude')

plt.show()
```
