# Analog signal 
- Continuous values for time ![](https://i.imgur.com/WjTF47D.png)
- Continuous value for amplititude
# Digital signal
- Sequence of discrete values 
- Data points can only take on a finite number of values 
# Analog to digital conversion
- Pulse-code modulation
## Sampling 
![](https://i.imgur.com/pZFwBL0.png)
- Each period sample at a point
- Locating samples: $$t_{n} = n \cdot T$$
  $n:$ sample number
  $T$: period
- Sampling rate: a feature we can play around it to obtain different types of audio. Basically a frequency measures in hertz indicates the kind of number of sample that we have for each second of our digital signal $$s_{r} = \frac{1}{T}$$ ![](https://i.imgur.com/M2IxU4u.png)
- Why sampling rate = 44100Hz: 
	- Nyquist frequency: upper bound frequency that we can have in a digital signal that's not going to recreate any artifacts$$f_{N} = \frac{s_{r}}{2}$$
	- Aliasing
## Quantization
- Resolution = num. of bits
- Bit depth
- CD resolution = 16 bits
## Memory for 1' of sound 
- Sampling rate = 44100 Hz
- Bit depth = 16 bits
# Dynamic range 
- Difference between largest/smallest signal a system can record
## Signal-to-quantization-noise ratio
- Relationship between max signal strength and quantization error
- Correlates with dynamic range
- Note: $$SQNR \approx 6.02 \cdot Q$$
  where $Q$ is bit depth
- Example: $$SQNR(16) \approx 96dB$$
# How do we record and reproduce sound?
- Record: Start with a mechanical wave from sound recorder $\rightarrow$ ADC $\rightarrow$ Digital signal
- Reproduce: Digital signal $\rightarrow$ DAC $\rightarrow$ Electrical signal