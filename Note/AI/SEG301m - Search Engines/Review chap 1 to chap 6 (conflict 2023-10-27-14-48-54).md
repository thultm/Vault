# Chapter 1: Information Retrieval and Search Engines
## 1.1 Information Retrieval
![](https://i.imgur.com/ObQFMwU.png)

> [[#1.1 Information Retrieval|Information Retrieval]] is a field concerned with the structure, analysis, organization, storage, searching, and retrieval of information.

\- Salton, 1968
- Search for information on the Web **almost all the time** 
- Need to improve search by coming up with easier and faster ways to find the right information 
- **Who do it:** computer scientists, software engineers, information scientists, search engine optimizers 
$\Rightarrow$ **[[#1.1 Information Retrieval|Information Retrieval]]**
$\Rightarrow$ **Core task:** *understanding and modeling how people compare texts, and designing computer algorithms to accurately perform this comparison!*
## 1.2 Search engines
> The practical application of [[#1.1 Information Retrieval|information retrieval]] techniques to large-scale text collections

- Examples: 
	- Web search engine
	- Desktop search engine 
	- Enterprise search engine
- The big issue of [[#1.1 Information Retrieval|IR]] and [[#1.2 Search engines|SE]] ![](https://i.imgur.com/8gQofbi.png)
## 1.3 Search engineers
- Primarily people trained in computer science, mostly with a systems or database background 
- Few of them have training in [[#1.1 Information Retrieval|information retrieval]]
- The majority of [[#1.2 Search engines|SE]]![](https://i.imgur.com/gnShWfy.png)
## 1.4 Web Search
![](https://i.imgur.com/QysIh7g.png)
## 1.5 Other Search Applications
- Desktop search engines:
	- Index and search files stored locally on a computer or local network
	- Require understanding of file formats, metadata, creation times, etc.
	- Used to find documents and files on a single machine or small network
- Enterprise search engines:
	- Index and search documents across an entire organization or business
	- Manage retention (lưu trữ) and compliance of emails, files, and other communications
	- Used to find business information across multiple systems and locations
	- Aid in satisfying regulatory requirements for data retention
	- Provide organization-wide content management and collaboration
## 1.6 Other Information Retrieval Appplications
- Document routing, filtering, and selective dissemination
- Text clustering and categorization
- Summarization systems: reduce documents to a few key paragraphs, sentences, or phrases describing their content
- Information extraction systems: identify named entities, such as places and dates, and combine this information into structured records that describe relationships between these entities
- Topic detection and tracking systems: identify events in streams of news articles and similar information sources, tracking these events as they evolve
- Expert search systems: identify members of organizations who are experts in a specified area 
- Question answering systems: integrate information from multiple sources to provide concise answers to specific questions
- Multimedia information retrieval systems

![](https://i.imgur.com/dx1HPRK.png)

# Chapter 2: Architecture of a Search Engine
## 2.1 Basic IR System Architecture
![[Review chap 1 to chap 6 2023-10-27 02.16.27.excalidraw]]
- Primary goals of [[#1.2 Search engines|SE]]
	- Effectiveness (quality): retrieve the most relevant set of documents possible for a query
	- Efficiency (speed): process queries from users as quickly as possible 
- Search engine has two major components 
	- Indexing process ![](https://i.imgur.com/vCGvjgL.png)
	- Query process ![](https://i.imgur.com/6ofPMel.png)

## 2.2 Building blocks: 
### Text acquisition
- Task: identify and make available the documents that will be searched 
#### Crawler 
- General web crawler 
	- Follow the links on web pages to discover and download new pages 
	- Efficiently find huge numbers of web pages (coverage) and keep them up-to-date (freshness)  
	- Single site crawlers for site search  
	- Topical or focused crawlers for vertical search 
- Document crawlers for enterprise and desktop search 
	- Follow links and scan directories
#### Feeds
- Mechanism for accessing a real-time stream of documents
	- News feed is a constant stream of news stories and updates 
- A search engine acquires new documents from a feed simply by monitoring it
	- RSS is a common standard used for web feeds for content such as news, blogs, or video
#### Conversion
- Convert documents into a consistent text plus metadata format 
	- HTML, XML, PDF, Word, … $\rightarrow$ XML 
- Convert text encoding for different languages 
	- 8-bit ASCII code represents 256 characters, Chinese have many more than 256 characters $\rightarrow$ cannot by represented 8-bit ASCII 
	- Unicode (16-bit words) represent most of the world’s languages
#### Document data store 
- Database used to manage large numbers of documents and the structured data that is associated with them 
- Stores text, metadata and other related content (links or anchor text) for documents 
- Provides very fast access to document contents for search engine components 
- Can use a relational database system to store documents and metadata 
	- Use a simpler, more efficient storage system is used because of huge numbers of documents
### Text transformation
#### Parser 
> Processing the sequence of text tokens in the document to recognize structural elements e.g., titles, links, headings, etc. 
- Tokenizer recognizes “words” in the text 
	- Must consider issues like capitalization, hyphens, apostrophes, non-alpha characters, separators 
- Markup languages such as HTML, XML often used to specify structure 
	- Tags used to specify document elements: E.g. <h/2> Overview <h/2> 
	- Document parser uses syntax of markup language (or other formatting) to identify structure
#### Stopping 
> Remove common words e.g., “and”, “or”, “the”, “in” 
- Some impact on efficiency and effectiveness 
- Can be a problem for some queries 
#### Stemming 
> Group words derived from a common stem e.g., “computer”, “computers”, “computing”, “compute” 
- Usually effective, but not for all queries 
- Benefits vary for different languages
#### Link extraction and analysis 
> Makes use of links and anchor text in web pages 
- Link analysis identifies popularity and community information 
	- e.g., PageRank, Hubs & Authorities 
- Anchor text can significantly enhance the representation of pages pointed to by links 
- Significant impact on web search 
	- Less importance in other applications
#### Information Extraction 
> Identify classes of index terms that are important for some applications e.g., named entity recognizers identify classes such as people, locations, companies, dates, etc. 
#### Classifier
> Identifies class-related metadata for documents 
- i.e., assigns labels to documents (identifying documents as spam, and identifying the non-content parts of documents, such as advertising)
- e.g., topics (“sports”, “politics”, or “business”), reading levels, sentiment, genre 
- Use depends on application
### Index Creation
#### Document Statistics 
> Gathers counts and positions of words and other features 
- Ranking algorithm uses to compute doc scores 
#### Weighting 
> Computes weights for index terms 
- Used in ranking algorithm e.g., TF-IDF weight 
	- Combination of *term frequency* in document and *inverse document frequency* in the collection
#### Inversion 
> Core of indexing process 
- Converts document-term information to term-document for indexing
	- Difficult for very large numbers of documents 
- Format of inverted file is designed for fast query processing 
	- Must also handle updates 
	- Compression used for efficiency
#### Index Distribution 
> Distributes indexes across multiple computers and/or multiple sites on a network 
- Essential for fast query processing with large numbers of documents 
- Many variations 
	- Document distribution, term distribution, replication 
- P2P and distributed [[#1.1 Information Retrieval|IR]] involve search across multiple sites
### User Interaction 
#### Query input 
> Provides interface and parser for query language 
- Most web queries are very simple (few operators), other applications may use forms 
- Query language used to describe more complex queries and results of query transformation 
	- e.g., Boolean queries, Indri and Galago query languages 
	- Similar to SQL language used in database applications 
	- [[#1.1 Information Retrieval|IR]] query languages also allow content and structure specifications, but focus on content
#### Query transformation 
> Improves initial query, both before and after initial search 
- Includes text transformation techniques used for documents (e.g. tokenization, stopping) 
- Spell checking and query suggestion provide alternatives to original query 
- Query expansion and relevance feedback modify the original query with additional terms
#### Results output 
> Constructs the display of ranked documents for a query 
- Generates snippets to show how queries match documents 
- Highlights important words and passages 
- Retrieves appropriate advertising in many applications 
- May provide clustering and other visualization tools
### Ranking 
#### Scoring 
- Calculates scores for documents using a ranking algorithm 
- Core component of search engine 
- Basic form of score is $\sum\limits_{i}q_{i}d_{i}:$ $q_{i}$ and $d_{i}$ are query and document term weights for term $i$
- Many variations of ranking algorithms and retrieval models
#### Performance optimization 
> Designing ranking algorithms for efficient processing 
- Term-at-a time vs. document-at-a-time processing 
- Safe vs. unsafe optimizations 
#### Distribution 
> Processing queries in a distributed environment 
- Query broker distributes queries and assembles results 
- Caching is a form of distributed searching
### Evaluation
#### Logging 
> Logging user queries and interaction is crucial for improving search effectiveness and efficiency 
- Query *logs* and *click-through* data or dwell time used for query suggestion, spell checking, query caching, ranking, advertising search, and other components 
#### Ranking analysis 
> Measuring and tuning ranking effectiveness 
#### Performance analysis 
> Measuring and tuning system efficiency
# Chapter 3: Crawls and Feeds
## 3.1 What to search?
- Everything you possibly can!
- Every document answers at least one question
- The best documents answer many more

The number of questions it can answer increases $\rightarrow$ Not easy to find the best documents to show to the user
## 3.2 Crawling the Web
## 3.3 Crawling documents and emails
## 3.4 Documents feeds
## 3.5 Conversion problem: character encodings
## 3.6 Storing documents
## 3.7 Delete duplicates
## 3.8 Remove noise
