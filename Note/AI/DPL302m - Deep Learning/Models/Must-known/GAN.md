# Basics of GAN
- Adversarial: Conflict or opposition
- GAN are deep neural network architectures combines of 2 neural networks, competing one against the other (i.e why adversarial)
- GAN are neural networks that are trained in an adversarial manner to generate data mimicking some distribution.
- 2 classes of model in [[Machine learning]]
	- Discriminative model: It is the one that discriminates between 2 different classes of data. ([[Classification]] problems)
	- Generative model: A generative model $G$ to be trained on training data $X$ sampled from some true distribution $D$ is the one which given some standard random distribution $z$ produces a distribution $D'$ which is close to $D$ according to some closeness metric. Mathematically, $z\sim Z$ maps to a sample $G(Z) \sim D'$
- **Objective:** $D$ as close as possible to $D'$
- ![](https://i.imgur.com/3rk32Nq.png)
## Learning Mechanism 
### Training the Discriminator 
- Take inputs from real dataset and generator, then predict fake $(y = 0)$ or real $(y = 1)$
### Training the Generator 
- Keep $(w, b)$ of Discriminator fixed
## GAN training algorithm
_For_ each training iteration _do_
1. Train the Discriminator:
    1. Take a random mini-batch of real examples: _x_.
    2. Take a mini-batch of random noise vectors _z_ and generate a mini-batch of fake examples: $G(z) = x^{*}$.
    3. Compute the classification losses for $D(x)$ and $D(x^{*})$, and backpropagate the total error to update $\theta(D)$ to _minimize_ the classification loss.
2. Train the Generator:
    1. Take a mini-batch of random noise vectors $z$ and generate a mini-batch of fake examples: $G(z) = x^{*}$.
    2. Compute the classification loss for $D(x^{*})$, and backpropagate the loss to update $\theta(G)$to _maximize_ the classification loss.
_End for_
- The reason we allow updates only to the weights and biases of the network being trained is to isolate all changes to only the parameters that are under the network’s control. This ensures that each network gets relevant signals about the updates to make, without interference from the other’s updates. You can almost think of it as two players taking turns.
# Loss Function of GAN
![](https://i.imgur.com/0JrIF3k.png)
## Discriminator
- Role is to distinguish between actual data & fake data
## Generator 
- Role is to create data in such a way so that it can fool the discriminator
## Basic conventions to understand loss function
![](https://i.imgur.com/Kofhl8T.png)
- Loss function (Binary cross-entropy) $$L(\hat{y},y)=[y\log\hat{y}+(1-y)\log(1-\hat{y})]$$
  The label for the data coming from $p_{data}(x)$ is $y=1\;\&\; \hat{y}=D(x)$ so putting this we obtain equation $\hat{A}$: $$L(D(x),1)=\log(D(x))$$
  & for data coming from generator the label is $y=0\;\&\;\hat{y}=D(G(z))$ so in that case we obtain equation $B$: $$L(D(G(z)),0)=(1-0)\log(1-D(G(z)))=log(1-D(G(z)))$$
  and $$\begin{align}\hat{y}&=\text{reconstructed image} \\ y&=\text{original image}\end{align}$$
- Objective of the discriminator is to correctly classify fake vs the real dataset. For this A & B should be maximized. ![[Introduction and Back-Propagation 2023-10-10 15.30.23.excalidraw]] $$\max\log(D(x))+\log(1-D(G(z)))=D$$
- Object of the generator is to fool the discriminator ![[Introduction and Back-Propagation 2023-10-10 15.42.47.excalidraw]]
Objective of loss function: $$\begin{align}
&\underset{G}{\min}\underset{D}{\max}\{\log(D(x))+\log(1-D(G(z)))\}\newline
\overset{\text{Goodfellow 2014.}}{\rightarrow}&\underset{G}{\min}\underset{D}{\max}V(D,G) = \{{\text{E}}_{x\sim p_{data}(x)}[\log(D(x))]+{\text{E}}_{z\sim p_{Z}(z)}\log(1-D(G(z)))\}
\end{align}$$
## Explaination 
### Finding the best discriminator 
- Proposition: For $G$ fixed, the optimal discriminator $D$ is $$D_{G}^{*}(x)=\frac{p_{data}(x)}{p_{data}(x)+p_{g}(x)}$$
- Proof: The training criterion for the discriminator $D$, given any generator $G$ is to maximize equation $\hat{A}$
  Hence, the optimal discriminator for a given $G$ is denoted as $D_{G}^{*}=\arg\underset{D}{\max}V(D,G)$
  Note that $\text{E}_{p(x)}[x]=\int_{x}x\;p_{x}(x)dx\qquad(1)$
  $$\begin{align}D_{G}^{*}&=\arg\underset{D}{\max}\{{\text{E}}_{x\sim p_{data}(x)}[\log(D(x))]+{\text{E}}_{z\sim p_{Z}(z)}\log(1-D(G(z))\}\\&=\arg\underset{D}{\max}\{V(G,D)\}\qquad(2)\end{align}$$
  Applied (1) to (2) we get: 
  $$\begin{align}
  V(G,D)&=\int_{x}p_{data}(x)\log(D(x))dx+\int_{z}p_{z}(z)\log(1-D(G(z))dz\\
  \text{In paper it is further written as}\\
  &=\int_{x}p_{data}(x)\log(D(x))dx+\int_{x}p_{g}(x)\log(1-D(x)dx
  \end{align}$$
 ![[Introduction and Back-Propagation 2023-10-10 17.04.08.excalidraw]]
To show $\int_{z}p_{z}(z)\log(1-D(G(z))dz=\int_{x}p_{g}(x)\log(1-D(x)dx$![[Introduction and Back-Propagation 2023-10-10 17.28.27.excalidraw]]
So $$\begin{align}
  V(G,D)&=\int_{x}p_{data}(x)\log(D(x))dx+\int_{z}p_{z}(z)\log(1-D(G(z))dz\\
  \text{Can be written that}\\
  V(G,D)&=\int_{x}\left[ p_{data}(x)\log(D(x))dx+p_{g}(x)\log(1-D(x) \right]dx
  \end{align}$$
  The optimal $D^{*}$ for a given $G$ is obtained by maximizing $V(G,D)$. So, we will find maximum of the argument & choose the value at maximum value to be optimal value of D given G i.e $D_{G}^{*}$. So $$\begin{align}
  &\frac{d}{dD(x)}\left[p_{data}(x)\log(D(x)) + p_{g}(x)\log(1-D(x)) \right] = 0 \\
  &\Rightarrow \frac{p_{data}(x)}{D(x)}-\frac{p_{g}(x)}{1-D(x)} = 0 \qquad(4)\\
  &\Rightarrow D_{G}^{*}(x)=\frac{p_{data}(x)}{p_{data}(x)+p_{g}(x)}\qquad \text{(proved) (optimal value)}
  \end{align}$$
  Prove (4): To prove it is a maximum value, we differentiable (4) again $$\begin{align}
  &\frac{d}{dD(x)}\left[\frac{p_{data}(x)}{D(x)}-\frac{p_{g}(x)}{1-D(x)} \right] &< 0 \\
  &\frac{-p_{data}(x)}{(D(x))^{2}}-\frac{p_{g}(x)}{(1-D(x))^{2}} &< 0 \\
  &\text{Hence maximum value is achieved for D given G as}\\
  &D_{G}^{*}(x)=\frac{p_{data}(x)}{p_{data}(x)+p_{g}(x)} \qquad \text{optimized as well as maximum value}
  \end{align}$$
### Finding the best Generator 
The role of generator is reverse of that of $D$ i.e min. So the optimal $G$ that minimize the loss function occurs when $D=D_{G}^{*}$. So we get optimal $G^{*}$ as $$G^{*}=\arg\underset{G}{\min}V(D_{G}^{*},G)$$
At this points, we must show that the optimization problem stated in $\hat{A}$ has a unique solution $G^{*}$ & this solution satisfies $p_{g}=p_{data}$
Our optimal $$D_{G}^{*}=\frac{p_{data}(x)}{p_{data}(x)+p_{g}(x)}$$
So substituting optimal value of $D_{G}^{*}$ in $$\begin{align}
G^{*}&=\arg\underset{G}{\min}V(D_{G}^{*},G)\text{ we obtain}\\
&= \arg\underset{G}{\min}\Biggl[\int_{x}\biggl\{ p_{data}(x)\log\bigl(D_{G}^{*}(x)\bigr)+p_{g}(x)\log\bigl(1-D_{G}^{*}(x)\bigr) \biggr\}dx \Biggr] \\
&= \arg\underset{G}{\min}\Biggl[\int_{x}\biggl\{ p_{data}(x)\log\Bigl(\frac{p_{data}(x)}{p_{data}(x)+p_{g}(x)}\Bigr)+p_{g}(x)\log\Bigl(\frac{p_{g}(x)}{p_{data}(x)+p_{g}(x)}\Bigr) \biggr\}dx \Biggr]
\end{align}$$
Add & subtract $\log2\;p_{data}(x) \,\&\, \log2\;p_{g}(x)$ in above equation $$\begin{align}
G^{*}&= \int_{x}\biggl\{(\log2-\log2)p_{data}(x) + p_{data}(x)\log\Bigl(\frac{p_{data}(x)}{p_{data}(x) + p_{g}(x)}\Bigr)+(\log2-\log2)p_{g}(x) +p_{g}(x)\log\Bigl(\frac{p_{g}(x)}{p_{data}(x)+p_{g}(x)}\Bigr) \biggr\}dx \\
&= \int_{x}\biggl\{-\log2(p_{data}(x)+p_{g}(x)) + p_{data}(x)\biggl[\log2+\log\Bigl(\frac{p_{data}(x)}{p_{data}(x) + p_{g}(x)}\Bigr)\biggr]+p_{g}(x)\biggl[\log2+\log\Bigl(\frac{p_{g}(x)}{p_{data}(x)+p_{g}(x)}\Bigr)\biggr] \biggr\}dx\\
&= -\log2\int_{x}\biggl\{(p_{data}(x)+p_{g}(x))\biggr\}dx + \int_{x}\biggl\{p_{data}(x)\biggl[\log2+\log\Bigl(\frac{p_{data}(x)}{p_{data}(x) + p_{g}(x)}\Bigr)\biggr]\biggr\}dx+\int_{x}\biggl\{p_{g}(x)\biggl[\log2+\log\Bigl(\frac{p_{g}(x)}{p_{data}(x)+p_{g}(x)}\Bigr)\biggr] \biggr\}dx
\end{align}$$
Recall: $\int_{x}p_{x}dx=1\,\&\,\log A + \log B = \log AB$, so:$$\begin{align}
G^{*} &= -\log2(1 + 1) + \int_{x}\biggl\{p_{data}(x)\log\Bigl(\frac{p_{data}(x)}{\frac{p_{data}(x) + p_{g}(x)}{2}}\Bigr)\biggr\}dx + \int_{x}\biggl\{p_{g}(x)\log\Bigl(\frac{p_{g}(x)}{\frac{p_{data}(x) + p_{g}(x)}{2}}\Bigr)\biggr\}dx
\end{align}$$
\- Kullback–Leibler divergence
$$\begin{align}
G^{*} &= \arg \underset{G}{\min} \biggl\{ -\log4 + \text{KL} \Bigl[ p_{data}(x) || \frac{p_{data}(x) + p_{g}(x)}{2} \Bigr] + \text{KL} \Bigl[ p_{g}(x) || \frac{p_{data}(x) + p_{g}(x)}{2} \Bigr] \biggr\}
\end{align}$$
must be wondering no $G$ in RHS! But $p_{g}(x)$ is dependent on $G$ because $$p_{g}(x)=p_{z}(G^{-1}(x))\frac{dG^{-1}(x)}{dx}$$
\- Jensen-Shennon divergence $\text{JSD} = \frac{1}{2}\Bigl\{ \text{KL}(P||M) + \text{KL}(Q||M)\Bigr\}$ where $M = \frac{P + Q}{2}$
$$\begin{align}
G^{*} &= \arg \underset{G}{\min} \biggl\{ -\log4 + 2\cdot\text{JSD} \bigl( p_{data}(x) || p_{g}(x) \bigr) \biggr\}
\end{align}$$
To minimize $G^{*}$, $p_{g}(x)=p_{data}(x)$. That means $\text{JSD} = 0$.
So $\text{JSD} = 0 \Leftrightarrow p_{g}(x) = p_{data}(x)$ which minimizes the arguments & the value obtain is $-\log4$.
> Objective of $G$ is minimizes $\text{JSD}$

## Theorem
- The global minimum of the criterion $G^{*} = \arg \underset{G}{\min} V(D_{G}^{*},G)$ is achieved if & only if $p_{g}(x) = p_{data}(x)$. At that points $G^{*}$ is $-\log4$.
- Proof: The goal of GAN process is to have $p_{g}(x) = p_{data}(x)$. So substituting these values for optimal $D$ results in $D^{*}_{G} = \frac{p_{data}(x)}{p_{g}(x)+p_{data}(x)} = \frac{1}{2}$. Because substituting $D(x) = \frac{1}{2}$ we get 
  $$\begin{align}
  V(G,D)&=\int_{x}\Bigl[ p_{data}(x)\log(D(x))dx+p_{g}(x)\log(1-D(x)\Bigr]dx \\
  &= \int_{x}\left[ p_{data}(x)\log(\frac{1}{2})dx+p_{g}(x)\log(\frac{1}{2}) \right]dx \\
  &= -\log2 \int_{x}\left[ p_{data}(x)+p_{g}(x)\right]dx \\
  &= -2\log2 \\ &= -\log4
  \end{align}$$
So this value is a global minimum
# Optimization 
![[Introduction and Back-Propagation 2023-10-11 02.02.32.excalidraw]]
![[Introduction and Back-Propagation 2023-10-11 02.14.39.excalidraw]]
In the 2014 paper, Goodfellow et al. discuss the following advantages and disadvantages of GANs in more detail:

**Advantages:**

* **No Markov chains are needed:** GANs do not require Markov chains to generate samples, which can be slow and difficult to tune. Instead, GANs use backpropagation to train the generator and discriminator networks.
* **Only backpropagation is used to obtain gradients:** GANs only use backpropagation to obtain gradients, which is a well-understood and efficient technique. This makes GANs relatively easy to train, even for complex models.
* **No inference is needed during learning:** GANs do not require inference during learning, which can be computationally expensive. Instead, GANs use a game-theoretic approach to train the generator and discriminator networks.
* **A wide variety of functions can be incorporated into the model:** GANs can be used to generate a wide variety of data types, including images, text, and audio. This is because GANs can be incorporated with a variety of different neural network architectures.
* **Component of input not copied directly into generator’s parameters:** GANs are trained using a game-theoretic approach, where the generator and discriminator networks are constantly competing against each other. This means that the generator network is not updated directly with data examples, but only with gradients flowing through the discriminator. This can help to prevent the generator network from overfitting to the training data.
* **Ability to represent very sharp, even degenerate distributions:** GANs are able to represent very sharp, even degenerate distributions, which is something that other generative modeling approaches, such as Markov chain Monte Carlo (MCMC) methods, cannot do. This is because GANs are able to learn the underlying structure of the data, rather than just the density of the data.

**Disadvantages:**

* **No explicit representation of pg(x):** GANs do not have an explicit representation of the probability distribution of the data that they are generating. This can make it difficult to analyze and control the behavior of the GAN.
* **D must be synchronized well with G during training:** The discriminator network in a GAN must be synchronized well with the generator network during training. If the discriminator network gets too far ahead, then the generator network will not be able to learn how to generate realistic samples. This can lead to mode collapse, where the generator network gets stuck generating a small subset of the possible outputs.

Overal, the 2014 paper presents a very positive view of GANs. Goodfellow et al. highlight the many advantages of GANs, such as their computational efficiency, ability to generate a wide variety of data types, and ability to represent very sharp distributions. However, they also acknowledge the disadvantages of GANs, such as the lack of an explicit representation of pg(x) and the difficulty of synchronizing D and G during training.

It is important to note that GAN research has progressed significantly since the publication of the 2014 paper. Many of the disadvantages of GANs have been addressed or mitigated by new techniques. However, the 2014 paper is still a seminal work in the field of GANs, and it provides a valuable overview of the key advantages and disadvantages of this type of model.
# Limitations of GANs
## Vanishing Gradients

To understand vanishing gradients, it is helpful to first understand how backpropagation works. Backpropagation is a technique used to train neural networks. It works by calculating the gradient of the loss function with respect to the weights of the network. The gradient is then used to update the weights in order to minimize the loss function.

However, the gradient can become very small during backpropagation. This is because the gradient is multiplied by many small numbers, which can cause it to shrink exponentially. This is known as the vanishing gradients problem.

Vanishing gradients can be a problem for GANs because the generator and discriminator networks are constantly competing against each other. This competition can cause the gradient signal to become very weak, making it difficult for the generator to learn.

## Mode Collapse

Mode collapse occurs when the generator gets stuck in a mode where it only produces a small subset of the possible outputs. This can happen if the generator is not able to learn the entire distribution of the training data.

One possible explanation for mode collapse is that the generator is too weak to explore the entire space of possible outputs. Another possible explanation is that the discriminator is too powerful and is able to easily distinguish between real and fake data. This can make it difficult for the generator to learn how to produce outputs that are realistic enough to fool the discriminator.

## Difficulty in achieving Nash equilibrium

A Nash equilibrium is a situation in which no player can improve their payoff by unilaterally changing their strategy. In the context of GANs, a Nash equilibrium is a situation in which the generator and discriminator networks are both performing optimally.

However, it can be difficult to achieve a Nash equilibrium in GANs. This is because the generator and discriminator are constantly trying to outsmart each other. The generator is trying to produce outputs that are realistic enough to fool the discriminator, while the discriminator is trying to become better at distinguishing between real and fake data.

This competition can lead to oscillations in the training process, where the generator and discriminator networks are constantly taking turns getting better at their respective tasks. This can make it difficult for the training process to converge to a Nash equilibrium.

## Problems with counting, perspective, and global structure

GANs can sometimes have difficulty generating images that have accurate counting, perspective, and global structure. This is because GANs are trained to generate images that are pixel-wise similar to the training data, but they may not learn the underlying relationships between the pixels.

For example, a GAN might be able to generate an image of a cat that looks realistic at a pixel level, but the cat might have the wrong number of legs or the wrong perspective. This is because the GAN has not learned that cats typically have four legs and that they should be drawn from a certain perspective.

Researchers are actively working to address the limitations of GANs. One promising area of research is the development of new loss functions that are better suited for training GANs. Another area of research is the development of new training techniques that can help to stabilize the training process and prevent mode collapse.

Despite their limitations, GANs are still a powerful tool for generating realistic data. They have been used to create many impressive applications, such as generating realistic images and videos, creating new artistic styles, and translating languages.
