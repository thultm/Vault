# Case Normalization
> Case normalization involves converting text to a consistent case, usually lowercase or uppercase. This *ensures uniformity in text analysis regardless of the original case.*

Example:
	Original: "Hello World"
	Case Normalized (Lowercase): "hello world"
	Case Normalized (Uppercase): "HELLO WORLD"
# Punctuation and Special Character Removal
> Removing punctuation and special characters from text helps *eliminate noise that might interfere with analysis.* This is especially useful for tasks like sentiment analysis or keyword extraction.

Example:
	Original: "Wow! What an amazing day!!! :)"
	After Removal: "Wow What an amazing day"
# Whitespace and Line Break Handling
> Handling whitespace and line breaks *ensures consistent spacing and structure.* Extra whitespace and line breaks can cause inconsistency in text data.
# [[#Stemming]] and [[#Lemmatization]]
Example:

Sentence: "Running shoes are better for runners."
    Stemming (Porter Stemmer):
        "run": running, runners
        "shoe": shoes
        "better": better
    Lemmatization:
        "run": running, runners
        "shoe": shoes
        "be": better
## Stemming
> Stemming *involves removing prefixes, suffixes, and inflections from words to obtain their root form.* The *resulting stems might not always be actual words.*
## Lemmatization 
> Lemmatization, on the other hand, involves *transforming words to their dictionary or base form (lemma (cơ sở)), which is a valid word.* Lemmatization *considers word context and part-of-speech information for accuracy.*

# Stop Word Removal
> Stop words are *common words that are frequently used in a language but generally do not carry significant meaning on their own.* These words are *often removed from text data* during preprocessing to *improve the quality of text analysis and reduce computational load.*

Examples
- Articles: "a", "an", "the"
- Prepositions: "in", "on", "under", "with"
- Pronouns: "I", "you", "he", "she", "it"
- Conjunctions: "and", "but", "or"
- Common verbs: "is", "are", "am", "was", "were"

