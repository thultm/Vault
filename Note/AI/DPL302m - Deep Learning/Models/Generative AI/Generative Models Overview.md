# Generative Models
| Discriminative models                                | Generative models                |
| ---------------------------------------------------- | -------------------------------- |
| Take a set of features $X$ to categorize classes $Y$ | $\text{Noise, } Y \rightarrow X$ |
| $P(Y\|X)$                                            | $P(X\|Y)$                        |

| Variational Autoencoders                                 | GANs                                                                                                          |
| -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Encoder $\rightarrow$ Latent Space $\rightarrow$ Decoder | $\text{Random Noise} \rightarrow \text{Generator} \rightarrow \text{Compete} \leftarrow \text{Discriminator}$ |
## Summary 
- Geneative models learn to produce realistic examples 
- Discriminative models distinguish between classes
# Real Life GANs
## Applications
- Face Genaration
	- 2014: Black and white 
	- 2018: Colored photo-realistic 
- StyleGAN2
- GANs for Image Translation 
	- From one domain to another ([[CycleGAN]] transform a horse to a zebra and vice versa)
	- Drawing doodles to pictures ([[GauGAN]])
- GANs for 3D Objects ([[3D-GAN]])
## Summary 
- GANs' performance is rapidly improving 
- Huge opportunity to work in this space!
- **Major companies** are using them
# Intuition Behind GANs
| Generator                                       | Discriminator                                    |
| ----------------------------------------------- | ------------------------------------------------ |
| - Learns to make ***fakes*** that look **real** | - Learns to distinguish **real** from ***fake*** |
