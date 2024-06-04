> Mô hình Transformer là một trong những mô hình học sâu nổi bật nhất hiện nay, được giới thiệu lần đầu tiên trong bài báo `Attention is All You Need` bởi Vaswani et al. vào năm 2017.
# Architecture
![](https://i.imgur.com/H0w7GSU.png)
## Encoder-Decoder Structure
#### Encoding Component
![](https://i.imgur.com/G9A7RnU.png)
- Mỗi lớp encoder bao gồm:
	- [[#Multi-Head Attention|Multi-Head Self Attention]] layer. → Giúp encoder xem xét các từ trong input và encode thành 1 từ cụ thể.
	- [[#Feed-Forward Network]].
	- [[#Layer Normalization and Residual Connections]].
- Đầu ra của lớp trước trở thành đầu vào của lớp sau.
- Các encoder xếp chồng lên nhau thành 1 stack.
- Trong paper, xếp chồng 6 encoder lên nhau.
- Same structure, different [[weights]].
#### Decoding Component
![](https://i.imgur.com/ZupoKEH.png)
- Mỗi lớp decoder bao gồm:
	- Masked Multi-Head Self-Attention (để tránh việc từ hiện tại nhìn thấy các từ tương lai trong đầu ra).
	- Multi-Head Self-Attention (với đầu vào từ encoder).
	- Feed-Forward Network.
	- Residual Connections và Layer Normalization.
- Cấu trúc giống [[#Encoding Component]].
### Self-Attention
> Phép toán cơ bản nhất trong [[Transformer]] là [[#self-attention]]. [[#Self-attention]] cho phép mỗi từ trong câu "chú ý" đến các từ khác trong cùng câu để tạo ra một biểu diễn có ngữ cảnh đầy đủ hơn.

![*As we are encoding the word "it" in encoder #5 (the top encoder in the stack), part of the attention mechanism was focusing on "The Animal", and baked a part of its representation into the encoding of "it".*](https://i.imgur.com/ycwB8r0.png)
#### Công thức Self-Attention
Giả sử chúng ta có một tập hợp các vector đầu vào $$X=\left[x_{1},x_{2},\ldots,x_{n}\right]\text{ với }x_{i}\in\mathbb{R}^{d}$$
$X\in\mathbb{R}^{n\times d}\text{ là ma trận biểu diễn các từ đầu vào với }n\text{ là số từ và }d\text{ là kích thước vector của từ}.$
![*Each word is embedded into a vector of size 512. We'll represent those vectors with these simple boxes.*](https://i.imgur.com/WIBR2IP.png)
- Embedding chỉ xảy ra ở lớp encoder hoặc decoder đầu tiên.
- Đều nhận 1 list các vector có size là 512, theo paper. Size của list các vector này là 1 [[Hyperparameter|hyperparameter]] - *thông thường sẽ là độ dài của câu dài nhất trong dataset.*
- Ở lớp encoder cuối cùng thì input là embedding của từ đó, các lớp encoder khác thì là đầu ra của encoder ngay trước.
- Sau khi embedding các từ trong câu đầu vào, đưa qua từng lớp trong 2 layer của encoder đầu tiên.
  ![*The word at each position passes through a self-attention process. Then, they each pass through a feed-forward neural network -- the exact same network with each vector flowing through it separately.*](https://i.imgur.com/S9fK9lm.png)
- Có sự phụ thuộc giữa các từ trong lớp [[#Self-Attention|self-attention]].

##### 1. Tính toán các vector truy vấn (Query), khóa (Key) và giá trị (Value)
![*Multiplying x1 by the WQ weight matrix produces q1, the "query" vector associated with that word. We end up creating a "query", a "key", and a "value" projection of each word in the input sentence.*](https://i.imgur.com/rOOIorW.png)

![*Every row in the X matrix corresponds to a word in the input sentence. We again see the difference in size of the embedding vector (512, or 4 boxes in the figure), and the q/k/v vectors (64, or 3 boxes in the figure)*](https://i.imgur.com/NliMXTv.png)
- $Q=XW_Q$
- $K=XW_K$
- $V=XW_V$
Trong đó $W_Q,W_K,W_V\in\mathbb{R}^{d\times d_k}$ là các ma trận trọng số được học.

- Các vector mới này có chiều nhỏ hơn chiều của embedding vector.
- Trong paper, chiều của các vector này là 64 trong khi các vector embedding và encoder input/output là 512.
- *Thực ra không cần phải nhỏ hơn, đây là một lựa chọn dành cho kiến trúc [[Note/AI/DPL302m - Deep Learning/Models/Must-known/Transformer|Transformer]] để cho việc tính toán của [[#Multi-Head Attention]] hầu như không đổi.*
> **_`Query`, `Key`, `Value` vectors là gì?_**
> _Là những khái niệm trừu tượng có ích cho việc tính toán và dễ hiểu cho cơ chế attention._
##### 2. Tính toán điểm tương tự (Attention scores)
> Điểm tương tự được tính bằng tích vô hướng giữa các vector truy vấn và khóa, sau đó được chia cho căn bậc hai của $d_{k}$ để điều chỉnh độ lớn của các giá trị. $$ \mathrm{scores}=\frac{QK^T}{\sqrt{d_k}}$$
![](https://i.imgur.com/CTBCLXx.png)
- Để tính toán điểm tương tự cho từ `Thinking`, đầu tiên ta chấm điểm của từng từ ở trong câu đầu vào so với từ này.
- Điểm được tính bằng cách lấy tích vô hướng của `query vector` với `key vector` của từ tương ứng ta đang chấm điểm.
- Điểm này để xác định mức độ cần tập trung vào các phần khác trong câu đầu vào khi ta encode 1 từ ở 1 vị trí nhất định nào đó là bao nhiêu.
![](https://i.imgur.com/uu0eHmd.png)
- Mặc định $d_{k}=64$ trong paper.
- Có thể thay đổi $d_{k}$ là 1 giá trị khác.
→ ***Having more stable gradients.***
##### 3. Áp dụng softmax để chuẩn hóa các điểm tương tự
![](https://i.imgur.com/Pv02BBH.png)
- Softmax chuyển đổi các điểm số thành xác suất, làm cho tổng của các trọng số bằng 1.
$$ \text{Attention weights}=\text{softmax(scores)}$$
- Xác định mức độ quan trọng của mỗi từ sẽ được thể hiện ở vị trí này → Đương nhiên từ ở vị trí này sẽ có [[Softmax Layer|softmax]] score cao nhất nhưng đôi khi việc chú ý đến 1 từ khác có liên quan đến từ hiện tại sẽ rất hữu ích.
→ ***Keep intact the values of the word(s) we want to focus on, and drown-out irrelevant words***
##### 4. Tính toán giá trị có trọng số (Weighted sum of values)
![](https://i.imgur.com/wZlrE9N.png)
- Kết quả là sự kết hợp có trọng số của các vector giá trị.
$$\text{Output}=\text{Attention weights}\cdot V$$
### Transformer Encoder
> Bao gồm một chuỗi các lớp mã hóa (encoding layers) để biến đổi đầu vào thành một biểu diễn trung gian.
#### Multi-Head Attention
> Để tăng cường khả năng của [[#self-attention]], [[Transformer]] sử dụng [[#multi-head self-attention]], trong đó [[#self-attention]] được tính toán nhiều lần với các trọng số khác nhau và kết quả được nối lại với nhau.

![](https://i.imgur.com/xuDf70y.png)
Giả sử có $h$ heads:
- Các đầu vào được chia thành $h$ phần, và mỗi phần có kích thước $d_{k}=\frac{d}{h}$​.
- Tính toán self-attention cho mỗi phần. $$ \mathrm{head}_i=\mathrm{SelfAttention}(XW_Q^i,XW_K^i,XW_V^i)$$
- Nối các kết quả lại với nhau và nhân với một ma trận trọng số cuối cùng $W_O$: $$ \text{MultiHead}(Q,K,V)=\text{Concat}(\text{head}_1,\text{head}_2,...,\text{head}_h)W_O$$
	Trong đó $W_O\in\mathbb{R}^{hd_k\times d}$.

Lợi ích của [[#Multi-Head Attention]]:
- Mở rộng khả năng tập trung vào các vị trí khác nhau của mô hình.
- Cung cấp cho attention layer nhiều `không gian con biểu diễn (representation subspaces)`.
	- Multiple sets of Query/Key/Value weight matrices, each of these sets is randomly initialized → After training, each set is used to project the input embeddings (or vectors from lower encoders/decoders) into a different representation subspace.
	![*With multi-headed attention, we maintain separate Q/K/V weight matrices for each head resulting in different Q/K/V matrices. As we did before, we multiply X by the WQ/WK/WV matrices to produce Q/K/V matrices.*](https://i.imgur.com/6FAYONt.png)
	- If we do the same self-attention calculation we outlined above, just eight different times with different weight matrices, we end up with eight different Z matrices.
	![](https://i.imgur.com/RSKLSFN.png)
	- [[#Feed-Forward Network]] is not expecting eight matrices – it’s expecting a single matrix (a vector for each word) → concat the matrices then multiply them by an additional weights matrix $W^{O}$.
	![](https://i.imgur.com/KUvuDnJ.png)

##### Scaled Dot-Product Attention
![](https://i.imgur.com/YA0XkZB.png)
#### Feed-Forward Network
Sau mỗi lớp self-attention, đầu ra được đưa qua một mạng nơ-ron truyền thẳng (Feed-Forward Neural Network) độc lập cho từng vị trí:
$$\mathrm{FFN}(x)=\max(0,xW_1+b_1)W_2+b_2$$
- $W_1\in\mathbb{R}^{d\times d_{ff}},W_2\in\mathbb{R}^{d_{ff}\times d}$​ là các ma trận trọng số.
- $b_1\in\mathbb{R}^{d_{ff}}\text{ và }b_2\in\mathbb{R}^d$ là các vector bias.
- $\max(0,x)$ là hàm [[ReLU]].
#### Layer Normalization and Residual Connections
##### Residual Connections
> Để dễ dàng học và tránh mất mát thông tin, mỗi đầu ra của self-attention và FFN đều được thêm vào đầu vào ban đầu (skip connection).
$$\begin{align} \mathrm{Output}_{\mathrm{SA}}=\text{LayerNorm}(x+\text{SelfAttention}(x))\\\mathrm{Output}_{\mathrm{FFN}}=\text{LayerNorm}(\text{Output}_{\mathrm{SA}}+\text{FFN}(\text{Output}_{\mathrm{SA}}))\end{align}$$
##### Layer Normalization
![](https://i.imgur.com/TX8Hab0.png)
> Sau mỗi phép toán cộng, đầu ra được chuẩn hóa để cải thiện quá trình học: $$ \mathrm{LayerNorm}(x)=\frac{x-\mu}\sigma\cdot\gamma+\beta $$
Trong đó $\mu$ và $\sigma$ là giá trị trung bình và độ lệch chuẩn của $x, \gamma$ và $\beta$ là các tham số học được.
$$\begin{align} \mu_{c}=\frac{1}{N\times H\times W}\sum_{i=1}^{N}\sum_{j=1}^{H}\sum_{k=1}^{W}F_{ijk}\ \\
\sigma_{c}=\sqrt{\frac{1}{N\times H\times W}\sum_{i=1}^{N}\sum_{j=1}^{H}\sum_{k=1}^{W}\left(F_{ijk}-\mu_{c}\right)^{2}}\end{align}$$
### Transformer Decoder
#### Encoder-Decoder Attention
## Positional Encoding
Vì mô hình Transformer không có cấu trúc tuần tự như RNN, cần thêm thông tin về vị trí của các từ trong câu bằng cách sử dụng positional encoding:
$$\begin{align}PE_{(pos,2i)}=\sin\left(\frac{pos}{10000^{2i/d}}\right)\\PE_{(pos,2i+1)}=\cos\left(\frac{pos}{10000^{2i/d}}\right)\end{align}$$
Trong đó $pos$ là vị trí và $i$ là chiều. Các giá trị này được thêm vào đầu vào của mỗi lớp encoder và decoder để giữ thông tin về thứ tự từ.
![](https://i.imgur.com/uEhqQFb.png)
### Sinusoidal Positional Encoding
### Learned Positional Encoding
![](https://i.imgur.com/tbqRJs9.png)

# Training
## Unsupervised Pre-training
### Masked Language Modeling
### Next Sentence Prediction

## Fine-tuning
### Task-Specific Fine-tuning
### Domain-Specific Fine-tuning
# Applications
## Natural Language Processing

### Machine Translation

### Text Summarization

### Question Answering
## Computer Vision
### Image Classification
### Object Detection
### Image Segmentation
## Multimodal Learning
### Vision-Language Models
### Speech Recognition
# Variants
## Bidirectional Encoder Representations from Transformers (BERT)
### BERT Base
### BERT Large
## Generative Pre-trained Transformer (GPT)
### GPT-2
### GPT-3
## Transformer-XL
## XLNet
# Performance Optimization
## Attention Optimization
### Sparse Attention
### Efficient Attention
## Model Compression
### Knowledge Distillation
### Weight Pruning
# Limitations and Challenges
## Long-Range Dependency Modeling
## Computational Complexity
## Interpretability