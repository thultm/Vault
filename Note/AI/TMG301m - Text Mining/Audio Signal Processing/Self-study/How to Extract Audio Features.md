# Time-domain feature pipeline
![](https://i.imgur.com/rjELdfy.png)
## Frames 
- Perceivable audio chunk
- Power of 2 num. samples
- Typical values: 256 - 8192
- Duration of a frame: $$d_{f} = \frac{1}{s_{r}} \cdot K$$
  where $s_{r}:$ sampling rate and $K:$ frame size
- Why framing before extract feature: Duration 1 sample << Ear's time resolution (10ms).
# Frequency-domain feature pipeline
![](https://i.imgur.com/nAFwiPN.png)
![](https://i.imgur.com/0liDR3K.png)
# Spectral leakage
- Processed signal isn't an integer number of periods
- Endpoints are discontinuous
- Discontinuities appear as high-frequency components not present in the original signal
- How to solve: Using [[#Windowing]] 
## Windowing 
- Apply windowing function to each frame 
- Eliminates samples at both ends of a frame 
- Generates a periodic signal
### Hann window
- Formula: $$w(k) = 0.5 \cdot (1-\cos{(\frac{2\pi k}{K-1}}), \: k=1...K$$![](https://i.imgur.com/hu1CdxQ.png)
- Convert from [[#Hann window]] to original signal: $$s_{w}(k) = s(k) \cdot w(k), \, 1...K$$![](https://i.imgur.com/6LMkjbb.png)
$\Rightarrow$ Lose signal at endpoints because we just removed it through the application of a windowing function
$\Rightarrow$ [[#Overlapping frames]]
## Non-overlapping frames
![](https://i.imgur.com/2eZfJst.png)
## Overlapping frames
![Overlapping frames](https://i.imgur.com/zpdsdas.png)
![](https://i.imgur.com/2bGiwqR.png)
- Hop length: the amount of samples we shift to the right every time we take a new sample
  ![](https://i.imgur.com/dL14nt1.png)
