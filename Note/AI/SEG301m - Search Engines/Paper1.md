# Abstract 
- The paper presents a survey of modeling and simulation approaches in information retrieval, discussing methods, challenges, models, components, and applications.
- It also highlights the use of AI applications in the legal field.
# Introduction
- The expansion of data in recent years has posed challenges for researchers to extract pertinent information in less time, leading to the need for innovative approaches in information retrieval.
- Information retrieval involves retrieving important data from repositories that contain structured, semi-structured, unstructured, and heterogeneous data.
- Despite significant developments in search understanding and technology, the question of whether the information retrieval stem truly retrieves relevant documents remains .
- Gerard Salton, a pioneer in information retrieval, defined information retrieval as the structure, analysis, storage, search, and retrieval of information.
- The paper is divided into three sections: an overview of the information retrieval system, the information search process including text processing, query processing methods, ranking algorithms, and retrieval models, and a presentation of existing related works.
# Background 
## Information Retrieval Notion
- Information retrieval is a common process where users search for information using search phrases, and systems like Google have been designed to make this process easier.
- Information retrieval involves representing, storing, and searching large collections of data to extract knowledge and provide relevant results to users based on their queries.
## Information Retrieval Components 
- The components of a basic web information retrieval (IR) system include crawling, indexing, query representation, ranking, and user feedback.
- Crawling involves seeking and retrieving documents for the search engine, while indexing creates a document index. Query representation allows users to write queries and retrieve relevant information, and ranking presents relevant documents to the user. User feedback can be provided to the search engine.
- ![](https://i.imgur.com/4M3MiIF.png)
## Information Retrieval Challenges
- The main challenge in information retrieval is the mismatch between the user's and the author's vocabulary, as well as limitations in the user's ability to explain their information needs and uncertainties in languages.
## Information retrieval applications 
- Information retrieval (IR) systems are used to manage large amounts of data and are employed in various applications such as media search, search engines, and digital libraries.
- Media search includes image retrieval, blog search, news search, speech retrieval, music retrieval, and video retrieval.
- Search engines are practical implementations of information retrieval techniques and include web search engines, federated search, desktop search, mobile search, enterprise search, web search, and social search. Digital libraries store collections digitally and can be accessed through computer networks. Other applications include genomic information retrieval, IR in software engineering, geographic IR, vertical search, and legal information retrieval.
## Processing Text
- Extremely significant and crucial 
- Preprocessing is the initial phase in text mining and involves parsing, tokenizing, removing stop words, stemming, and feature extraction.
- Is also used in **text mining** and **natural language processing** tasks, such as sentiment analysis (phân tích quan điểm), topic modeling, and named entity recognition
- ![](https://i.imgur.com/vNVub1R.png)
### Document parsing 
-  Is the process of identifying the content and structure of text documents, which may be written in different languages, character sets, or formats. 
- It involves breaking down a document into distinct components to form unitary documents.
- By parsing documents, researchers can gain insights into the structure and content of textual data, facilitating subsequent analysis and interpretation.
### Tokenizing 
- Tokenizing involves creating words from a series of letters in a document, breaking it down into words, phrases, or symbols .
- The purpose of tokenization is to prepare the text for further analysis and extraction of relevant information .
- Different languages pose different challenges in tokenization. Space-bound languages like English and French, where words are separated by white space, are relatively easier to tokenize. Non-segmented languages like Chinese and Thai, where words do not have obvious boundaries, present more difficulties in tokenization.
### Stop words
- **Stop words** are common words that are often considered insignificant or redundant in the context of text analysis.
- These words are typically removed during text processing to improve the efficiency and accuracy of information retrieval and natural language processing tasks.
- Some examples of stop words include articles (e.g., "the", "a", "an"), prepositions (e.g., "to", "in", "at"), and conjunctions (e.g., "and", "but", "or").
- Example: $$\text{The most apparent information retrieval applications are search  
engines}\rightarrow\text{most apparent information  
retrieval applications search engines}$$
### Stemming
- Stemming is a word-level modification technique that groups words with a common stem to eliminate multiple suffixes, minimize the number of words, and save memory space and time.
- For example, terms like "present," "presentation," "presented," and "presenting" can be stemmed to the term "present".
- By reducing words to their common stem, stemming allows for better matching of similar words and helps in identifying patterns and relationships within the text.
### Feature Extraction 
- Feature extraction is a technique used to remove unnecessary characteristics from a dataset, improving accuracy in text classification.
- The feature extraction algorithm is based on the vector space model, representing sentences as dots in an N-dimensional space.
- The TF-IDF weighted scheme is a method for extracting features, separating terms into unique and non-unique words based on their importance to the document's topic. Here is the mathematical formula how to calculate it: $$W_{i,j}=tf_{i,j}*\log(\frac{|N|}{df_{i}})$$
	- $W_{i,j}$​ represents the weight of term $i$ in document $j$.
	- $tf_{i,j}$​ represents the frequency of term i in document j.
	- $∣N∣$ represents the total number of documents in the collection.
	- $df_{i}$ represents the number of documents in the collection that contain term $i$.
### Information Retrieval models
- Information retrieval models are frameworks or approaches used to represent and process textual data in order to retrieve relevant information from a collection of documents.
- Some commonly used information retrieval models include:
    - Boolean Model: This model uses Boolean operators (AND, OR, NOT) to retrieve documents that match a user's query.
    - Vector Space Model: This model represents documents and queries as vectors in a high-dimensional space, where the similarity between documents and queries is measured using cosine similarity.
    - Probabilistic Model: This model calculates the probability of a document being relevant to a query based on statistical analysis of the document collection.
- These models provide the foundation for various information retrieval tasks such as document classification, search engines, and recommendation systems.
- Each model has its own strengths and weaknesses, and the choice of model depends on the specific requirements of the information retrieval task.
### Evaluation 
- IR systems are evaluated based on their ability to return relevant documents and the accuracy and precision of these retrieved documents.
- Two common criteria for evaluating the quality of an IR system are precision and recall.
- Precision is a measure of the accuracy of the search results in information retrieval.
	- Formula: $$Precision=\frac{|\text{Relevant documents}\cap\text{Retrieved documents}|}{|\text{Retrieved documents}|}$$
	- Precision is important in information retrieval because it helps to ensure that the search results are relevant and useful to the user.
	- A high precision value indicates that the search results are highly relevant, while a low precision value indicates that the search results are less relevant.
- Recall measures the proportion of documents related to the query that have been found.
	- Formula: $$Recall=\frac{|\text{Relevant documents}\cap\text{Retrieved documents}|}{|\text{Relevant documents}|}$$
- These measures help calculate the F-measure, which combines precision and recall to provide a comprehensive evaluation metric for IR systems .
- F-measure is  is a measure of the accuracy of a binary classification model.
	- Formula: $$F-measure = 2 * \frac{precision * recall} {precision + recall}$$
	-  It ranges from 0 to 1, with 1 being the best possible value.
- By considering precision, recall, and F-measure, the effectiveness of an IR system in retrieving relevant information can be assessed
# Related Work
- The research on information retrieval has primarily focused on statistical methods, such as the vector space method and similarity metrics.
- Vector similarities can be achieved by strengthening binary features on vectors, and distance between vectors determines word similarity.
- Query expansion is a method to improve search systems by automatically expanding original searches based on user feedback or query restructuring.
- Word embedding techniques, like word2vec, and non-parametric approaches, like K-nearest neighbor, are frequently used in information retrieval.
- The Naïve Bayes classifier technique, based on the Bayes theorem, is the most commonly used text categorization method.
- ![](https://i.imgur.com/bFg79OQ.png)
# Legal Information System 
- A legal information system refers to the use of technology, particularly artificial intelligence (AI), to handle time-consuming activities and provide efficient and accurate legal services.
- AI companies are continuously working on improving technology to enhance legal practices by automating various tasks and processes.
- AI applications in the legal field include tools such as Alexsei, Blue J Legal, Knomos, CaseText, FastCase, Judicata, LexisNexis, CaseMine, and MikeLegal, which are used in different countries like Canada, the United States, and India.
- These applications assist lawyers and clients in legal research, case analysis, document review, contract management, and other legal activities, thereby increasing efficiency and accuracy in the legal industry.
# Conclusion
- This paper provides a comprehensive overview of information retrieval, including pre-processing techniques and a comparison of different approaches such as KNN, SVM, Naïve Bayes, and Rocchio Algorithm, with a focus on future research.