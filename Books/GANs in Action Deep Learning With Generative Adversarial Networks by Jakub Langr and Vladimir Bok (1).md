
[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/50/1:96)) on 2023-10-06 at 05:17:40 UTC:
> The training of a traditional neural network is an optimization problem.

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/62/1:97)) on 2023-10-06 at 05:18:33 UTC:
> GAN training can be better described as a game, rather than optimization

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/66/1:18)) on 2023-10-06 at 05:19:04 UTC:
> GAN training ends when the two networks reach Nash equilibrium

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/70[ch03fig03]/1:0)) on 2023-10-06 at 05:20:16 UTC:
> Figure 3.3. Player 1 (left) seeks to minimize V by tuning θ1. Player 2 (middle) seeks to minimize –V (maximize V) by tuning θ2. The saddle-shaped mesh (right) shows the combined loss in the parameter space V(θ1, θ2). The dotted line shows the convergence to Nash equilibrium at the center of the saddle. (Source: Goodfellow, 2019, www.iangoodfellow.com/slides/2019-05-07.pdf.)

Setup of a two-player zero-sum game and the process of reaching Nash equilibrium

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/78/1:0)) on 2023-10-06 at 05:22:04 UTC:
> Training GANs successfully requires trial and error

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/82/1:66)) on 2023-10-06 at 05:23:22 UTC:
> Generator (G) takes in a random noise vector z and produces a fake example x*

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/82/1:168)) on 2023-10-06 at 05:23:33 UTC:
> Discriminator (D) is presented either with a real example x or with a fake example x*; for each input, it outputs a value between 0 and 1 indicating the probability that the input is real

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/92/2[iddle1082]:4)) on 2023-10-06 at 05:23:47 UTC:
> Discriminator’s goal is to be as accurate as possible

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/92/2[iddle1082]:156)) on 2023-10-06 at 05:24:34 UTC:
> For fake examples x*, D(x*) strives to be as close as possible to 0

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/94/1:192)) on 2023-10-06 at 05:24:20 UTC:
> Generator strives to produce fake examples x* such that D(x*) is as close to 1 as possible.

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/106[ch03table01]/1:0)) on 2023-10-06 at 05:25:01 UTC:
> Table 3.1. Confusion matrix of Discriminator outcomes

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/110/2[iddle1070]:44)) on 2023-10-06 at 05:25:23 UTC:
> Discriminator is trying to maximize true positive and true negative classifications or, equivalently, minimize false positive and false negative classifications

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/110/2[iddle1070]:232)) on 2023-10-06 at 05:25:32 UTC:
> Generator’s goal is to maximize the Discriminator’s false positive classifications

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/110/2[iddle1070]:460)) on 2023-10-06 at 05:26:12 UTC:
> Generator is not concerned with how well the Discriminator classifies the real examples; it cares only about the Discriminator’s classifications of the fake data samples

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/112[ch03lev1sec3]/2[ch03lev1sec3__title]:5)) on 2023-10-06 at 05:26:44 UTC:
> GAN TRAINING ALGORITHM

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/122/1:208)) on 2023-10-06 at 05:28:36 UTC:
> The reason we allow updates only to the weights and biases of the network being trained is to isolate all changes to only the parameters that are under the network’s control

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/122/1:541)) on 2023-10-06 at 05:28:55 UTC:
> can almost think of it as two players taking turns

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/198/1:238)) on 2023-10-06 at 05:36:20 UTC:
> The greater the cross-entropy loss, the further away our predictions are from the true labels.

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/198/2/1:0)) on 2023-10-06 at 05:36:11 UTC:
> Binary cross-entropy is a measure of the difference between computed probabilities and actual probabilities for predictions with only two possible classes

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/200/1:242)) on 2023-10-06 at 05:36:45 UTC:
> Adam has become the go-to optimizer for most GAN implementations thanks to its often superior performance

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/214/1:194)) on 2023-10-06 at 05:37:28 UTC:
> Discriminator is trained to assign fake labels to the fake images and real labels to real images

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/214/1:297)) on 2023-10-06 at 05:37:41 UTC:
> Generator is trained such that the Discriminator assigns real labels to the fake examples it produces.

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/242/1:71)) on 2023-10-06 at 05:38:39 UTC:
> each mini-batch must be small enough to fit inside the processing memory

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/242/1:297)) on 2023-10-06 at 05:38:54 UTC:
> the more iterations we have, the longer the training process takes

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/244/1:48)) on 2023-10-06 at 05:39:10 UTC:
> monitor the training loss and set the iteration number around the point when the loss plateaus

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/30/2/4/2[sbo-rt-content]/280[ch03lev1sec6]/2[ch03lev1sec6__title]:0)) on 2023-10-06 at 05:40:28 UTC:
> SUMMARY

Summary of chap 3

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/12/2/1:0)) on 2023-10-06 at 05:41:05 UTC:
> Deep Convolutional GAN, or DCGAN

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/22/1:117)) on 2023-10-06 at 05:41:37 UTC:
> ConvNet are arranged in three dimensions (width × height × depth)

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/22/1:210)) on 2023-10-06 at 05:41:44 UTC:
> performed by sliding one or more filters over the input layer

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/22/1:266)) on 2023-10-06 at 05:42:01 UTC:
> Each filter has a relatively small receptive field (width × height) but always extends through the entire depth of the input volume.

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/24/1:45)) on 2023-10-06 at 05:42:35 UTC:
> each filter outputs a single activation value: the dot product between the input values and the filter entries

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/24/1:179)) on 2023-10-06 at 05:42:43 UTC:
> results in a two-dimensional activation map for each filter

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/24/1:297)) on 2023-10-06 at 05:43:00 UTC:
> then stacked on top of one another to produce a three-dimensional output layer; the output depth is equal to the number of filters used.

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/28/1:13)) on 2023-10-06 at 05:43:12 UTC:
> filter parameters are shared by all the input values to the given filter

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/28/1:190)) on 2023-10-06 at 05:43:27 UTC:
> efficiently learn visual features and shapes

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/28/1:387)) on 2023-10-06 at 05:43:35 UTC:
> reduces the number of trainable parameters

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/28/1:445)) on 2023-10-06 at 05:43:59 UTC:
> decreases the risk of overfitting and allows this technique to scale up to higher-resolution images without a corresponding exponential increase in trainable parameters

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/68/2[iddle1034]:0)) on 2023-10-06 at 05:46:31 UTC:
> Introduced in 2016 by Alec Radford, Luke Metz, and Soumith Chintala

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/72/1:250)) on 2023-10-06 at 05:47:20 UTC:
> LAPGAN, which uses a cascade of convolutional networks within a Laplacian pyramid, with a separate ConvNet being trained at each level using the GAN framework

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/72/1:509)) on 2023-10-06 at 05:47:51 UTC:
> LAPGAN has been largely relegated to the dustbin of history

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/78/1:87)) on 2023-10-06 at 05:49:00 UTC:
> allowed ConvNets to scale up to the full GAN framework without the need to modify the underlying GAN architecture and without reducing GAN to a subroutine of a more complex model framework, like LAPGAN

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/78/1:357)) on 2023-10-06 at 05:49:13 UTC:
> batch normalization

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/78/1:399)) on 2023-10-06 at 05:49:22 UTC:
> stabilize the training process by normalizing inputs at each layer where it is applied

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/94/1:65)) on 2023-10-06 at 06:44:01 UTC:
> makes comparisons between features with vastly different scales easier and, by extension, makes the training process less sensitive to the scale of the features.

Normalization advantages

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/98/1:4)) on 2023-10-06 at 06:44:42 UTC:
> insight behind batch normalization is that normalizing inputs alone may not go far enough when dealing with deep neural networks with many layers

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/98/1:557)) on 2023-10-06 at 06:45:23 UTC:
> Batch normalization solves it by scaling values in each mini-batch by the mean and variance of that mini-batch.

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/98/2/1:0)) on 2023-10-06 at 06:45:11 UTC:
> covariate shift

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/104/1:108)) on 2023-10-06 at 06:46:35 UTC:
> normalized value  is computed as shown in equation 4.2

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/122/1:0)) on 2023-10-06 at 06:48:36 UTC:
> Batch normalization limits the amount by which updating the parameters in the previous layers can affect the distribution of inputs received by the current layer

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/122/1:177)) on 2023-10-06 at 06:48:48 UTC:
> decreases any unwanted interdependence between parameters across layers, which helps speed up the network training process and increase its robustness, especially when it comes to network parameter initialization.

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/158/1:457)) on 2023-10-06 at 06:50:46 UTC:
> ake a vector and up-size it to an image

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/160/1:41)) on 2023-10-06 at 06:51:26 UTC:
> regular convolution is typically used to reduce input width and height while increasing its depth

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/160/1:140)) on 2023-10-06 at 06:51:38 UTC:
> Transposed convolution goes in the reverse direction: it is used to increase the width and height while reducing depth

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/160/2/1:0)) on 2023-10-06 at 06:50:57 UTC:
> transposed convolution

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/166/1:4)) on 2023-10-06 at 06:53:19 UTC:
> Generator starts with a noise vector z

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/166/1:43)) on 2023-10-06 at 06:53:28 UTC:
> Using a fully connected layer, we reshape the vector into a three-dimensional hidden layer with a small base (width × height) and large depth

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/166/1:195)) on 2023-10-06 at 06:53:59 UTC:
> Using transposed convolutions, the input is progressively reshaped such that its base grows while its depth decreases until we reach the final layer with the shape of the image we are seeking to synthesize

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/166/1:424)) on 2023-10-06 at 06:56:11 UTC:
> After each transposed convolution layer, we apply batch normalization and the Leaky ReLU activation function

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/166/1:524)) on 2023-10-06 at 06:56:19 UTC:
> At the final layer, we do not apply batch normalization and, instead of ReLU, we use the tanh activation function.

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/186/1:53)) on 2023-10-06 at 06:58:29 UTC:
> one that takes in an image and outputs a prediction vector: in this case, a binary classification indicating whether the input image was deemed to be real rather than fake.

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/270/1:72)) on 2023-10-06 at 07:01:33 UTC:
> Discriminator and Generator can be represented by any differentiable function

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/32/2/4/2[sbo-rt-content]/274[ch04lev1sec6]/2[ch04lev1sec6__title]:0)) on 2023-10-06 at 07:02:21 UTC:
> SUMMARY

Summary of DCGAN (Chap 4)

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/36/2/4/2[sbo-rt-content]/18/1:15)) on 2023-10-06 at 07:20:08 UTC:
> “How to Train Your DRAGAN” are a testament to both the incredible capacity of machine learning researchers to make bad jokes and the difficulty of training Generative Adversarial Networks well

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/36/2/4/2[sbo-rt-content]/46/2/1:42)) on 2023-10-06 at 07:24:51 UTC:
> derive from Maximum Likelihood

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/36/2/4/2[sbo-rt-content]/48/1:68)) on 2023-10-06 at 07:26:41 UTC:
> key idea is that we are moving away from explicit and tractable, into the territory of implicit approaches toward training

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/36/2/4/2[sbo-rt-content]/60/2[iddle1407]:232)) on 2023-10-06 at 07:29:53 UTC:
> nonapproximate version of maximum likelihood maximization

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/36/2/4/2[sbo-rt-content]/60/2[iddle1407]:300)) on 2023-10-06 at 07:30:24 UTC:
> we would know that the image either is or is not in this set, so no likelihood is involved

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/36/2/4/2[sbo-rt-content]/60/2[iddle1407]:410)) on 2023-10-06 at 07:30:07 UTC:
> in practice, this solution is never really possible.

---

[Highlighted](calibre://view-book/Calibre/2/EPUB?open_at=epubcfi(/36/2/4/2[sbo-rt-content]/64/1:500)) on 2023-10-06 at 08:13:53 UTC:
>  GANs tend to be quite sensitive to hyperparameters

---
