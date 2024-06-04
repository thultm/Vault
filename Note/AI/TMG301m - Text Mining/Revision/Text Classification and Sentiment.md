# Text [[Classification]]
> [[#Text classification]] is the task of *categorizing* or *assigning predefined labels or categories* to text documents based on their content. 

***Goal:*** *Develop* algorithms or models that can *automatically determine the most appropriate category for a given piece of text*, enabling *efficient organization and analysis* of large volumes of textual data.
- Relevance of Text Classification 
	- Spam Detection
	- Sentiment Analysis
	- Topic Categorization
	- Language Identification
	- News Categorization 
	- Document Classification
# Navie Bayes to Text Classification
> Naive Bayes is a powerful and widely used algorithm for [[#text classification]]. It's based on the Bayes' theorem, which *calculates the probability of a certain event occurring based on prior knowledge of related events.*

In the context of text classification, Naive Bayes assumes that the presence of a particular word in a document is independent of the presence of other words. This is a simplification, as words in a text often have contextual relationships. However, despite this "naive" assumption, the algorithm often works well in practice, especially for tasks like spam detection and sentiment analysis.
# Navie Bayes Algorithm
![](https://i.imgur.com/lH7WhxD.png)
# Sentiment Analysis
- Also known as ***opinion mining***
- Is the process of analyzing a piece of text to determine the ***sentiment, emotion, or attitude*** expressed within it. 
- **Goal:** to *identify* whether the text conveys a positive, negative, or neutral sentiment, and sometimes to further *classify emotions* like joy, anger, sadness, etc.
- Importance of [[#Sentiment Analysis]]
	- Understanding Public Opinion
	- Customer Feedback Analysis
	- Social Media Monitoring
	- Brand Management
	- Market Research
	- Political and Social Analysis
	- Crisis Management
	- Investor Relations
	- Product Launch and Campaign Evaluation
# Navie Bayes to [[#Sentiment Analysis|SA]]
- Training the Naive Bayes Model
	- Data Preparation:
		- Gather a labeled dataset containing text samples along with their sentiment labels.
		- These labels could be binary (positive/negative) or include additional sentiment categories.
	- Feature Extraction:
		- Features are typically words or terms.
		- Each word becomes a feature
		- The presence or absence of a word in a text is a binary feature.
		- Preprocesing text
	- Creating the Training Data: 
		- From the labeled dataset, the algorithm calculates the frequency of each word in each sentiment category. 
		- This information forms the basis of the probabilities needed for classification.

# Evaluation Metrics
- Accuracy: 
	- Measures the proportion of *correctly classified instances out of the total instances.* While it's a straightforward metric, it *might be misleading in cases of imbalanced datasets where one class dominates.*
	- Formula: $$\text{Accuracy} = \frac{TP + TN}{TN +TP + FP + FN}$$
- Precision: 
	- Precision quantifies the *ratio of correctly predicted positive instances to all instances predicted as positive.* It indicates the *model's ability to avoid false positives.*
	- Formula: $$\text{Precision} = \frac{TP}{TP + FP}$$
- Recall (Sensitivity or True Positive Rate): 
	- Recall calculates the *ratio of correctly predicted positive instances to all actual positive instances.* It shows the *model's effectiveness in capturing all positive instances.*
	- Formula: $$\text{Recall} = \frac{TP}{TP + FN}$$
- F1-Score: 
	- The F1-score is the *harmonic mean of precision and recall.* It *balances both metrics and is especially useful when class distribution is imbalanced.*
	- Formula: $$\begin{align}\text{F1-Score} &= \frac{2\cdot \text{Precision}\cdot\text{Recall}}{\text{Precision}+\text{Recall}}\\ &=\frac{2TP}{2TP+FP+FN}\end{align}$$
- Confusion Matrix: 
	- A confusion matrix is *a tabular representation of the model's predictions compared to the actual labels.* It provides *insight into true positives, true negatives, false positives, and false negatives.*
