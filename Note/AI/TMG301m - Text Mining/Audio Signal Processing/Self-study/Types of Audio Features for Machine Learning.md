> Audio features are the characteristics of sound

# Audio feature categorisation
## Level of abstraction
- Low-level
	- Definition: Features that make sense for the machine and don't make sense for human (less statistical features that get extracted directly from audio)
	- Example: amplitude envelope, energy, spectral centroid, spectral flux, zero-crossing rate
- Mid-level
	- Definition: Features that start to make sense from a perceptual perspective
	- Example: pitch-and-beat-related descriptors, such as note onsets, flucctuation patterns, MFCCs
- High-level
	- Definition: Abstract features and these kind of like tend to map to musical construct that we can understand
	- Example: instrumentation, key, chords, melody, rhythm, tempo, lyrics, genre, mood
## Temporal scope
- Instantaneous (~50ms)
- Segment-level (seconds)
- Global 
## Music aspect
- Beat
- Timbre
- Pitch
- Harmony
- ...
## Signal domain 
- Time domain 
	- Definition: Features are extracted from a waveform
	- Example:
		- Amplitude envelope 
		- Root-mean square energy 
		- Zero crossing rate
- Frequency domain
	- Definition: Focus on frequency components of sound
	- Example: 
		- Band energy ratio 
		- Spectral centroid 
		- Spectral flux
	- Basic idea: take a signal from time domain representation, apply Fourier transform. Then we get a spectrum.
- Time-frequency representation
	- Definition:
	- Example:
		- Spectrogram
			- Time domain $\overset{STFT}{\rightarrow} Spectrogram$
		- Mel-spectrogram
		- Constant-Q transform
## ML approach
### Traditional [[Machine learning]]
- Amplitude envelope 
- Zero crossing rate
- Spectral flux
### [[Deep learning]]
- Root-mean square energy 
- Band energy ratio 
- Spectral centroid 
- Spectral spread
- MFCCs
# Type of intelligent audio systems 
![](https://i.imgur.com/piEwS60.png)