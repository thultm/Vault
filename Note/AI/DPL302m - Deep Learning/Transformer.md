# Preprocesing data
- Number of characters
- Average word length 
- Frequent word removal
- Rare words removal Spelling correction 
- Tokenization 
- Stemming 
- Lemmatization 
# Word Embedding
## CBOW
- From n-1
## Skip-gram
- From 1-n
## Word2Vec
- Including its word and semantic
- Usually uses 768 dimensions
## Seq2Seq
$\Rightarrow$ Bottleneck (lose information)
### Encoder 
> Nén lại dưới dạng 1 vector. [[#Encoder]] dùng để học vector biểu của câu với mong muốn rằng vector này mang thông tin hoàn hảo của câu đó.
## Decoder
> [[#Decoder]] thực hiện chức năng chuyển vector biểu diễn kia thành ngôn ngữ đích.
# Attention 
- Flexible hidden state
- Tất cả các từ trước đó đều tham gia vào việc dự đoán $\rightarrow$ softmax and return `Atention score`
- Start at token `<START>` and end at token `<END>`
# Transformer architecture
## High-level 
- 2 phần:
	- [[#Encoder]]
	- [[#Decoder]]
	- ![](https://i.imgur.com/GNQ8zTw.png)