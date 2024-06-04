# Introduction
- Statistical language models used in NLP.
- Estimate the likelihood of a sequence of N words based on their frequency in data. 
- "N" represents the number of words grouped together. 
# [[#Unigrams (1-grams)]] and [[#Bigrams (2-grams)]]
## Unigrams (1-grams)
Unigrams are the *simplest form of N-Grams*, where each word or token in a text is *treated as a separate unit*, and its probability is *calculated independently of other words*. In other words, unigrams *don't take into account any context or relationship with surrounding words.*

## Bigrams (2-grams)
Bigrams are a type of N-Gram where *words are grouped into pairs*, and the *probability of a word depends on the previous word*. This introduces a basic level of context into the model. Bigram models *consider the likelihood of observing a word given the word that immediately precedes it.*
# Limitations
Using only unigrams and bigrams in language modeling has several limitations
- Lack of Context Beyond Adjacent Words
- Ignoring Long-Range Dependencies
- Limited Understanding of Nuanced Language Patterns
- Difficulty with Ambiguity
- Poor Performance on Tasks Requiring Deep Semantics
- Inadequate for Creative Text Generation
# Trigram and Higher N-Grams
Trigrams (3-grams) and higher N-Grams are extensions of the N-Gram language modeling concept. 

While bigrams consider pairs of adjacent words, trigrams consider sequences of three consecutive words, and higher N-Grams consider sequences of N words, where N is greater than 3.

These models aim to capture more intricate language patterns by considering a broader context within the text.
# Applications of N-Gram Language Model
- Speech Recognition
- Machine Translation
- Text Generation
- Language Modeling
- Spell Checking and Correction
- Information Retrieval
- Predictive Text Analytics
# Summary
- While N-Gram models offer simplicity and efficiency, they are best suited for tasks that require basic language understanding and context prediction. 
- For more advanced applications that demand nuanced understanding and generation of text, modern models like RNNs, LSTMs, and transformer-based models have proven to be more effective due to their ability to capture long-range dependencies and semantic relationships in language.
