# Amplitude envelope (AE)
- Max amplitude value of all samples in a frame $$AE_{t} = \underset{k = t \cdot K}{\overset{(t+1) \cdot K -1}{\max}}s(k)$$
  where $AE_{t}$: Amplitude envelope at frame $t$, $s(k):$ Amplitude of *k*th, $K:$ frame size 
- Give rough idea of loudness
- Sensitive to outliers
- Onset detection, music genre [[Classification|classification]] 
# Root-mean-square energy (RMS)
- RMS of all samples in a frame $$RMS_{t} = \sqrt{\frac{1}{K} \cdot \sum\limits_{k=1\cdot K}^{(t+1)\cdot K-1} s(k)^{2}}$$
  where $s(k)^{2}:$ Energy of *k*th sample, $\sum\limits_{k=1\cdot K}^{(t+1)\cdot K-1} s(k)^{2}$: Sum of energy for all samples in frame $t$, $\frac{1}{K} \cdot \sum\limits_{k=1\cdot K}^{(t+1)\cdot K-1} s(k)^{2}:$ Mean of sum of energy
- Indicator of loudness 
- Less sensitive to outliers than [[#Amplitude envelope (AE)]]
- Audio segmentation, music genre [[Classification|classification]] 
# Zero-crossing rate (ZCR)
- Number of times a signal crossess the horizontal axis $$ZCR_{t} = \frac{1}{2} \cdot \sum\limits_{k = t \cdot K}^{(t+1) \cdot K-1} \mid sgn(s(k)) - sgn(s(k+1)) \mid$$
  where $sgn:$ sign function
  - $s(k) > 0 \rightarrow +1$
  - $s(k) < 0 \rightarrow -1$
  - $s(k) = 0 \rightarrow 0$
- Recognition of percussive vs pitched sounds
- Monophonic pitch estimation 
- Voice/unvoiced decision for speech signals