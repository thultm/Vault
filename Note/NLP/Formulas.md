1. Given a set of unigram and bigram probabilities, what is the probability of the following sequence '\<s> do Sam I like' according to the bigram language model? 
   $P(do|<s>) = 2/11, P(do|Sam) = 1/11, P(Sam|<s>) = 4/11, P(Sam|do) = 1/8, P(I|Sam) = 4/11, P(Sam|I) = 2/9, P(I|do) = 2/8, P(I|like) = 2/7, P(like|I) = 3/11, P(do) = 3/8, P(Sam) = 2/11, P(I) = 4/11, P(like) = 5/11$
   > ***Probability of the following sequence:*** $$P(<s> \text{do Sam I like}) = P(do|<s>) \times P(Sam|do) \times P(I|Sam) \times P(like|I)$$
2. Suppose a language model assigns the following conditional n-gram probabilities to a 3-word test set: 1/4, 1/2, 1/4. Then $P(test-set) = \frac{1}{4} \times \frac{1}{2} \times \frac{1}{4} = 0.03125$. What is the perplexity?
   > ***Perplexity:*** $$P P=2^{-{\frac{1}{N}}\sum_{i=1}^{N}\log_{2}P(w_{i})}$$
3. Assume a corpus with 350 tokens in it. We have 20 word types in that corpus (V = 20). The frequency (unigram count) of word types "short" and "fork" are 25 and 15 respectively. Which of the following is the probability of "short" (PMLE("short"))?
   > ***Probability of a word:*** $$P M L E('\operatorname{short}')={\frac{\mathrm{Frequency~of~}\mathrm{'short'}}{\mathrm{Total~number~of~tokens}}}$$
4. Assume a corpus with 350 tokens in it. We have 20 word types in that corpus (V = 20). The frequency (unigram count) of word types "short" and "fork" are 25 and 15 respectively. If we are using the Laplace smoothing, which of the following is PLaplace("fork")?
   > ***Probability of a word using the Laplace smoothing:*** $$P L a p l a c e(\mathrm{'fork'})={\frac{\mathrm{Frequency~of~}\mathrm{'fork'}+1}{\mathrm{Total~number~of~tokens}+V}}$$
5. Assume that there are 10000 documents in a collection. Out of these, 50 documents contain the terms "difficult task". If "difficult task" appears 3 times in a particular document, what is the TFIDF value of the terms for that document?
   > ${\begin{array}{l}{{\mathrm{Given:}}}\\ {\bullet\,{\mathrm{Total~number~of~documents~(D)}}\,=\,10000}\\ {\bullet\,{\mathrm{Number~of~documents~containing~difficult~task'}}\,(d)\,=\,50}\\ {\bullet\,{\mathrm{Term~frequency~of~'difficult~task'}}\,{\mathrm{in~the~document~(t)}=3}}\end{array}}.$
   > The IDF is calculated as follows: $$\begin{array}{l c r}{I D F=\ln\left({\cfrac{D}{d}}\right)}\\ {I D F=\ln\left({\cfrac{10000}{50}}\right)}\\ {I D F=\ln(200)}\end{array}$$
   > The TF-IDF value is then: $$TF-IDF=TF \times IDF$$
6. Zipf's Law:
   > $$f(k;s,N)={\frac{1/k^{s}}{\sum_{n=1}^{N}(1/n^{s})}}$$
   > $$\begin{array}{l}{{\mathrm{where:~}}}\\ {{\mathrm{*~}\ f{\mathrm{~is~the~frequency~of~the~word,}}}}\\ {{\mathrm{*~}\ k\ \mathrm{is~the~rank~of~the~word~in~the~frequency~table,}}}\\ {{\mathrm{*~}\ s\ \mathrm{is~the~value~usually~close~to~1~(often~it~is~set~to~1),}}}\\ {{\mathrm{*~}\ N\ \mathrm{is~the~number~of~elements~in~the~frequency~distribution.}}}\end{array}$$
