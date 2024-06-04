$$STFT(t, f) = ∫[x(n) * w(n - t)] * e^{(-j2\pi ft)}dn$$
Where:

- $STFT(t, f)$ is the complex-valued spectrogram representation at time $t$ and frequency $f$.
- $x(n)$ is the audio signal.
- $w(n - t)$ is a window function (e.g., Hamming or Hanning window) centered at time index $t$.
- $f$ is the frequency index.
- $\int$ denotes the integral over the window length.

# Number of STFT features
The number of Short-Time Fourier Transform (STFT) features depends on several factors, including the properties of the audio signal and the parameters you choose for the STFT analysis. To calculate the number of STFT features, you need to consider the following parameters:

1. Window Size (N): The window size, often denoted as "N," determines the length of each time frame in the STFT analysis. A larger window captures more time information but has less frequency resolution, while a smaller window captures more frequency information but has less time resolution. The number of samples in each window defines the dimensionality of your STFT features.
    
2. Hop Size (H): The hop size, often denoted as "H," represents the step size between consecutive analysis windows. A smaller hop size results in more frequent analysis frames and, therefore, more features. The hop size directly affects the number of features you obtain.
    
3. Signal Length (L): The length of the audio signal, denoted as "L," determines the total number of frames analyzed. The signal length divided by the hop size, rounded up to the nearest integer, gives you the number of analysis frames.
    

Now, to calculate the number of STFT features:

$$\text{Number of Features} = (\frac{L}{H}) * (\frac{N}{2} + 1)$$

Where:

- "L" is the signal length.
- "H" is the hop size.
- "N" is the window size.
- "(N / 2 + 1)" represents the number of unique frequency bins in the STFT. The "+1" accounts for the zero frequency component (DC component).

This formula accounts for the fact that the STFT typically provides a complex-valued representation of the signal, but often, you might work with just the magnitude or power of the STFT coefficients. In that case, you will have $\frac{N}{2} + 1$ features for each frame.

Keep in mind that the actual number of features can vary depending on the settings you choose for N, H, and the length of your audio signal. Experimenting with different window sizes and hop sizes allows you to balance time and frequency resolution to best suit your specific signal analysis needs.
# How CChroma works 
1. Short-Time Fourier Transform (STFT): The first step in chroma feature extraction is to compute the Short-Time Fourier Transform (STFT) of the audio signal. The STFT is a way to analyze the frequency content of the audio signal over short, overlapping time windows. It is computed as follows for a given frame at time index t:

$$\text{Number of Features} = (\frac{L}{H}) * (\frac{N}{2} + 1)$$

Where:

- "L" is the signal length.
- "H" is the hop size.
- "N" is the window size.
- "(N / 2 + 1)" represents the number of unique frequency bins in the STFT. The "+1" accounts for the zero frequency component (DC component).
2. Chroma Filter Bank: The chroma filter bank is a set of 12 bandpass filters, each corresponding to one of the 12 pitch classes (C, C#, D, D#, E, F, F#, G, G#, A, A#, B). These filters are designed to capture the energy of each pitch class. To define the filters, you can set the center frequencies of each filter according to the corresponding pitch class frequencies. For example, the center frequencies for the C Major scale would be:
    
    - C: 261.63 Hz
    - C#: 277.18 Hz
    - D: 293.66 Hz
    - D#: 311.13 Hz
    - E: 329.63 Hz
    - F: 349.23 Hz
    - F#: 369.99 Hz
    - G: 392.00 Hz
    - G#: 415.30 Hz
    - A: 440.00 Hz
    - A#: 466.16 Hz
    - B: 493.88 Hz
3. Filter Convolution: For each time frame in the spectrogram, you apply the chroma filter bank to obtain the chroma values. To do this, you convolve each filter in the filter bank with the magnitude spectrum of the STFT. The result of the convolution is a 12-dimensional vector representing the energy of each pitch class for that frame.
    
    $$Chroma_{i(t)} = \int[S(|f|) * H_i(|f|)] df$$
    
    Where:
    
    - Chroma_i(t) is the energy of the i-th pitch class for the frame at time t.
    - S(|f|) is the magnitude spectrum of the STFT.
    - H_i(|f|) is the frequency response of the i-th filter in the chroma filter bank.
4. Normalization: To make the chroma vectors independent of the overall loudness or energy of the audio signal, you can apply L2 normalization to each chroma vector. This ensures that the vector represents the distribution of pitch classes, regardless of the signal's volume.
    
    Chroma_i(t) = Chroma_i(t) / √(Σ(Chroma_j(t)^2))
    

In summary, chroma feature extraction involves the computation of the STFT, convolution with a chroma filter bank, and normalization. This process results in chroma vectors that represent the distribution of pitch classes in short-time frames of the audio signal, making them suitable for various music analysis tasks.