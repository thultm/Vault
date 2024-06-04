# Why "Evaluate"?
- Trade-off between efficiency and 
# Evaluate corpus
- Good dataset
# Logging
- Capture user interactions
- Which document is first choice in each query (relevant)
- Time of user in the webpage
# Effectiveness metrices
$$Recall = \frac{|A\cap B|}{|A|}$$
$$Precision = \frac{|A\cap B|}{|B|}$$
where $A:$ relevant set of documents for query, $B:$ set of retrieved documents
- The proportion of non-relevant documents that are retrieved (related to false negative errors): $$Fallout = \frac{|\overline{\rm A}B|}{|\overline{\rm A}|}$$
- Mean average precision (MAP) $$GMAP = \exp \frac{1}{n} \sum\limits_{k=1}^{k=n}AP_{k}$$