# Introduction
## Overview of importance of text preprocessing in text mining
- Text preprocessing involves transforming text prior to analysis through techniques like tokenization, removal of stop words, stemming/lemmatization, etc. These decisions can significantly impact results.
- Preprocessing aims to increase statistical power by reducing data dimensionality/sparsity, but it can also remove useful information or introduce errors if done improperly.
- Decisions made during preprocessing affect whether text mining captures the content and/or style of language in texts. This impacts the ability to address different types of research questions.
- Preprocessing is important because it determines what linguistic features are extracted during open vocabulary text mining, where there are no predefined dictionaries. It can also impact measurement precision in closed vocabulary text mining.
- Poor or inconsistent preprocessing practices are common issues in past text mining research. However, preprocessing recommendations have been conflicting.
- If not conducted appropriately, preprocessing has the potential to inadvertently alter results, reducing reliability and validity, similar to "researcher degrees of freedom".
- The paper aims to resolve inconsistent recommendations by providing empirically grounded guidelines based on reviews of computational linguistics and organizational research literature.
- The goal is to improve understanding of preprocessing effects, enhance validity, and promote transparency and replicability in text mining research. Preprocessing is often overlooked but strongly impacts analysis and results.
## Conflicting recommendations in past research
- Stemming - Researchers have provided four distinct recommendations:
    - Always stem except on short documents
    - Only stem in small corpora
    - Only stem if it does not reduce classification/prediction accuracy
    - Cautiously consider stemming only after conducting topic modeling
- Spelling correction - Some recommend correcting misspellings to standardize text and reduce noise, while others note individual spelling differences could predict traits.
- Stop words - Some recommend removing extremely common words, while others note these words are key for assessing unique communicative style.
- Preprocessing for closed vs. open vocabulary text mining - Past methodological articles described the general text mining process but recommendations were inconsistent for closed vs. open vocabulary techniques.
- Reporting of preprocessing - The vast majority of closed vocabulary studies do not report any preprocessing conducted, despite some tools recommending it. However, open vocabulary requires explicit specification of all preprocessing decisions.
- Consideration of research questions and data characteristics - Prior recommendations provided little guidance on how preprocessing should account for factors like question type, content vs. style focus, corpus size, document length, etc.
So in summary, the paper notes there have been conflicting views on specific techniques as well as inconsistent integration of important contextual factors like research needs and data properties into preprocessing recommendations.
## Goals of current paper to resolve recommendations and provide guidelines
- Conduct two complementary reviews of computational linguistics and organizational text mining research to advance understanding of whether organizational research follows best practices.
- Derive preprocessing best practices from the computational linguistics literature review. Then critically review preprocessing practices in organizational research.
- Provide empirically grounded text preprocessing decision-making recommendations that account for:
    - Whether open or closed vocabulary text mining is being conducted
    - The research question under investigation
    - Characteristics of the dataset, including corpus size and average document length
- Resolve the conflicting preprocessing recommendations seen in past research.
- Improve current text preprocessing practices based on the reviews and conceptual/empirical considerations discussed.
- Provide recommendations for both conducting text mining preprocessing and reporting text mining research to promote transparency and reproducibility.
- The goal of the recommendations is to enhance the validity of text mining results, researchers' understanding of preprocessing effects, and the overall transparency and replicability of text mining research.
# Conceptual Considerations for Preprocessing
## Closed vs open vocabulary text mining
### Closed vocabulary text mining:
- Uses a priori dictionaries containing lists of conceptually related words and phrases
- Counts occurrences of words/phrases in these dictionaries to analyze language and extract features
- More deductive approach where features are predefined by dictionaries
- Examples include LIWC dictionaries for linguistic and psychological constructs
- Can be used for manual coding, dictionaries developed for organizational constructs
### Open vocabulary text mining:
- Has no predefined dictionaries, so uses any n-grams (phrases of length n) as potential features
- More inductive approach where textual features are not specified in advance
- Commonly used for machine learning applications like classification/prediction
- Useful for contexts with nonstandard language like misspellings or emoticons
- What is captured depends entirely on preprocessing decisions since they affect what words/phrases remain in the text
### Differences that impact preprocessing:
- Preprocessing can impact validity for both by altering word matches between text and dictionaries (closed) or removing words entirely (open)
- Open vocabulary requires explicit specification of all preprocessing since it determines featured extraction
So in summary, closed vocabulary uses predefined dictionaries while open vocabulary induce features from text, and this fundamental difference impacts how preprocessing affects validity and what must be reported.
## Capturing content vs style of language
- Content words (nouns, verbs, adjectives) convey the topic or what is being communicated. They tend to differ based on the situation.
- Function words (pronouns, prepositions, articles) convey linguistic style or how the communication is delivered. They tend to be consistent indicators of individual differences.
- Content words are more important for understanding state-like, context-dependent variables from text like topics predictive of future outcomes.
- Function words are more important for understanding trait-like, stable individual differences that can be inferred from language patterns, like personality.
- Some preprocessing techniques like stop word removal reduce the ability to capture style represented by function words.
- Techniques like spelling correction could alter content word validity if corrections introduce errors.
- The research question should dictate whether the focus is on content, style, or both to guide preprocessing.
- If the goal is trait-like variables, idiosyncrasies in language use may be informative.
- But when not trait-focused, standardizing via techniques like spelling correction can improve measurement precision.
- Preprocessing decisions should be aligned with whether the research aims to extract content- or style-based linguistic features.
## Importance of research question
- The research question should dictate whether text mining focuses on capturing content words, function words, or both.
- Content words are more relevant for state-like, context-dependent variables like predictive topics, while function words focus more on trait-like individual differences.
- Preprocessing aims to increase statistical power, but it can remove useful information if not aligned with the research question.
- The research question determines if closed vocabulary (requires predefined dictionaries) or open vocabulary (uses any textual features) is more appropriate.
- Closed and open vocabulary text mining have different preprocessing needs due to their deductive vs inductive approaches.
- Preprocessing that standardizes language may reduce validity if the goal relates to trait-like differences expressed through style/idioms.
- Considerations like focusing on topics vs traits should guide decisions like correcting misspellings.
- Preprocessing recommendations vary based on whether text mining aims to extract thematic content or linguistic patterns.
- The research question is important context for selecting optimal text mining techniques and preprocessing methods.
## Considerations of corpus size and average document length
- Corpus size - The size of the corpus impacts decisions like whether to stem words. Stemming may be preferable in smaller corpora to reduce data sparsity, but it risks conflating meanings in larger corpora.
- Average document length - Shorter texts provide less context for techniques like topic modeling. Preprocessing should account for whether documents contain sufficient semantic content.
- Some techniques are more appropriate for larger/longer documents while others are better for smaller/shorter texts.
- For instance, in short texts like tweets, representing style may require preserving misspellings rather than correcting for their semantic content.
- Data characteristics like volume and granularity affect statistical power and validity.
- Preprocessing recommendations that disregard corpus/document properties may not generalize.
- Techniques should consider whether the goal is within-document relationships or aggregate patterns across many short texts.
In summary, the paper emphasizes that optimal preprocessing depends on not just research questions but also corpus/document scale, to maximize information retention for different analysis needs.
# Specific Preprocessing Techniques
## Lowercase conversion
- Lowercase conversion standardizes text by normalizing capitalization differences. This can reduce noise for features based on word forms.
- However, capitalization contains stylistic information, so its removal may alter the ability to capture traits from language use/style.
- For example, emphasis expressed through capitalization could indicate psychological states.
- Lowercasing is commonly recommended but its justification depends on the research question and whether style/content are priorities.
- If the goals focus on within-document semantics, lowercasing likely has little effect since capitalization distinction is reduced within pieces of text.
- But if extracting stylistic patterns across texts, lowercasing could remove valid information about individual variation in writing conventions.
- Recommendations should consider capitalization in the context of the targeted construct (state-based content vs trait-based style).
## Handling negation
- Negation is an important linguistic construct that reverses the meaning or polarity of sentences.
- However, it is often overlooked in text mining and preprocessing. Simply counting words can misrepresent the true sentiment or semantic meaning of negated text.
- Negation should be explicitly addressed through techniques like:
    - Negation scope detection - Identifying the extent of a negation's influence over subsequent words.
    - Negation handling - Reversing the polarity or meaning of words under the scope of a negation.
- Negation is especially important for tasks like sentiment analysis where correct handling can significantly impact accuracy.
    
- Prior organizational research has neglected negation, which can limit the validity and reliability of results from affect detection or other semantic analyses.
- Proper negation handling becomes even more critical as natural language understanding systems aim to capture deep semantics beyond simple word counts.
- The paper recommends assessing how research objectives and dataset characteristics relate to negation, then applying targeted techniques to appropriately account for its effects.
## Spelling correction and abbreviation expansion
- Spelling correction standardizes language but runs the risk of introducing errors if corrections are incorrect.
- Individual differences in spelling ability could contain meaningful stylistic information. Correcting these introduces validity issues if style is the focus.
- Abbreviation expansion reduces sparsity but expansion decisions require subjective judgment that could alter meaning.
- Both techniques prioritize content words, but their appropriateness depends on whether the goal is to understand semantics or infer stylistic/trait information.
- If the research focuses on traits conveyed through language patterns/idioms, idiosyncratic spelling or abbreviations may be informative indicators.
- But for objectives centered on topics or prediction of states, standardization through correction/expansion could enhance measurement precision.
- The ideal approach considers how the data and goals relate to normalization vs preservation of nonstandard language variations.
- These techniques warrant careful reflection on whether variance introduced by individual linguistic styles is meaningful to retaining validity.
## Removing nonalphabetic characters
- Removing numbers, punctuation, etc. aims to simplify text to just words for analysis.
- However, nonalphabetic characters may carry meaningful information, such as emphasis through capitalization or emotion through emoticons.
- Their removal could diminish the ability to capture aspects of writing style or psychological/emotional states from language.
- Numbers in particular are often deeply tied to semantic meaning (e.g. dates, times, ages). Removing them may degrade validity.
- The research goals should dictate whether stylistic markers or contextual semantic cues are priorities over simplification.
- For tasks focused on aggregate topic patterns, character filtering is less problematic than for analyses of individual language use.
- The paper recommends carefully considering what non-lexical elements may inform the research question before implementing this technique.
- Transparency in reporting any such modifications improves reproducibility and understanding of valid inferences from the results.
## Stop word removal
- Stop words are highly frequent function words like articles, pronouns, prepositions that contribute little to content semantics.
- Removing stop words aims to reduce noise and sparsity to focus analyses on meaningful content words.
- However, function words also provide information about linguistic style that can reveal traits/individual differences.
- For example, personal pronouns indicate social or psychological aspects of language.
- Stop word removal should be conditioned on whether the goal is understanding content vs. inferring stylistic patterns/traits.
- It is more suitable when focusing on aggregate topic patterns rather than individual language behaviors.
- If traits are of interest, alternates like frequency cuts versus complete lists could retain some function word signal.
- The decision also depends on whether analyses target within-text context vs. cross-text comparisons.
- Transparency about lists/criteria is important for reproducibility and generalizability.
## Stemming and lemmatizing
- Stemming and lemmatizing group inflected word forms under a common stem or lemma to reduce feature sparseness.
- This can increase statistical power for tasks like classification on smaller corpora.
- However, grouping may conflate semantically distinct words in deeper analysis or larger datasets.
- Morphological variations also provide stylistic signals that can convey traits if those are the focus.
- Lemmatization tends to have fewer conflations than stemming since it output the base word form rather than stem.
- The degree of preferred standardization depends on corpus scale, research question, and whether topics vs. styles are priorities.
- When traits are relevant, retaining morphological richness improves validity over aggressive standardization.
- No single recommendation applies; researchers must assess how target constructs relate to invariant vs. variant features.
- Transparency in reporting stemming/lemmatizing decisions aids understanding limitations of linguistic inferences.
## Effects and recommendations for each technique
### Lowercasing:
- Effects - Removes stylistic signals from capitalization
- Recommendation - Consider capitalization's role based on focus on content vs style
### Negation handling:
- Effects - Impacts sentiment, meaning if unaddressed
- Recommendation - Explicitly handle based on objectives like sentiment analysis
### Spelling correction:
- Effects - May alter meaning or introduce errors if corrections are wrong
- Recommendation - Reflect on whether variation conveys valuable traits
### Abbreviation expansion:
- Effects - Requires subjective judgments that could alter semantics
- Recommendation - Consider appropriateness based on focus on topics vs language patterns
### Character filtering:
- Effects - Removes potentially meaningful stylistic or emotional cues
- Recommendation - Retain if non-lexical elements inform research question
### Stopword removal:
- Effects - Removes traits conveyed by function words
- Recommendation - Use alternates like frequencies if styles of interest
### Stemming/lemmatization:
- Effects - May conflate meanings in larger data or deeper analysis
- Recommendation - Reflect dataset scale and whether topics or traits priority
# Reviews of Computational Linguistics and Organizational Research
## Derive best practices from computational linguistics research
- Carefully align preprocessing techniques with the specific research questions and targeted linguistic constructs. What aspects of language (content, style, etc.) are most relevant to analyze?
- Consider corpus/document characteristics like size, granularity, text length when determining appropriate preprocessing approaches. Techniques have different impacts based on data properties.
- Explicitly address important linguistic phenomena like negation that can significantly alter meaning if not handled properly. Apply validated techniques from NLP.
- Thoughtfully assess whether non-standard language variations (spelling, capitalization, punctuation etc.) could inform research goals before standardizing.
- Techniques like stopword removal require justification if individual language behaviors/traits are relevant. Frequency cutoffs are safer alternatives.
- Stemming and lemmatization risk conflating meanings - balance benefits based on dataset scale and focus on topics vs. styles.
- Report preprocessing details transparently to enable technique evaluation and reproducibility across studies.
- Periodically review new developments in computational linguistics to incorporate best practices as the field advances methodologies.
The overarching goal is maximizing information retention through valid preprocessing aligned with research needs and characteristics of the textual data being analyzed.
## Critically analyze practices in organizational research
- Assess whether studies sufficiently justify their choice of techniques based on the research questions/focus (e.g. content vs style) and data characteristics.
- Evaluate if important linguistic phenomena like negation are addressed or whether their effects could impact results/interpretations.
- Determine whether non-standard variations in the data like capitalization or abbreviations that may signal traits are standardized without reason.
- Analyze whether stopword or idiomatic/function word removal could remove information relevant to analyzing individual differences if traits are a focus.
- Critique whether stemming/lemmatization decisions could conflate meanings given the granularity and scale of texts analyzed.
- Examine the transparency of preprocessing details reported - are the techniques applied unambiguous and reproducible?
- Compare descriptions of methods to current best practices in computational linguistics to assess alignment.
- Consider whether studies acknowledge limitations their choices may impose on inference types that can be validly made.
- As a field, reflect on consistency in meeting validation standards as new methods and understanding develop over time.
The goal would be a constructive analysis highlighting areas for organizational research to better integrate computational linguistics knowledge.
## Advance understanding of whether organizational research follows best practices
- By systematically examining multiple past studies' reported methodologies against best practices, trends can be identified in how well aligned the field has been historically.
- Findings from the analysis could be aggregated to assess overall adherence vs. opportunities for improvement across the research domain.
- Studies that closely followed validation standards from computational linguistics can be highlighted as exemplars for the field.
- Studies that did not sufficiently justify techniques or address important constructs like negation can serve as cautionary examples.
- The analysis results could be published to increase awareness within organizational research of how preprocessing practices have measured up to standards over time.
- Research groups may be able to self-evaluate their own past work using the framework developed in the analysis.
- Having a collective understanding of the field's methodological strengths and weaknesses better positions it to progressively strengthen validity moving forward.
- The enhanced transparency also benefits practitioners interpreting and applying such research in practice.
So in summary, a systematic critical review can advance the shared learning for the community around best practices compliance.
# Recommendations for Text Preprocessing
## Provide empirically grounded recommendations based on reviews
- Develop systematic review methodology
    - Keywords, inclusion/exclusion criteria
    - Data extraction and analysis templates
- Conduct review of past decade of research
    - Categorize studies by questions, data, techniques
    - Assess adherence to reporting guidelines
- Publish review findings
    - Highlight best/limiting practices
    - Opportunity areas for field to strengthen
- Propose minimum reporting standards
    - Based on Figure 1 criteria
    - Enforceable via publication guidelines
- Suggest benchmarking of techniques
    - Effect sizes tests of analytical choices
    - Demonstrate evidentiary impacts
- Recommend independent replications
    - Verify published findings/methods
    - Continually advance scientific rigor
- Establish evaluation framework
    - Rubric to measure future studies
    - Incentivize continuous progress
The systematic, evidence-based approach aims to professionlize practices over time.
## Account for type of text mining, research question, and data characteristics
- Topic modeling/content analysis
    - Explicitly justify number of topics based on data/goals
    - Pilot alternate topic specifications
- Sentiment/emotion analysis
    - Preserve variations that could signal constructs of interest
    - Evaluate impact of standardization
- Author attribution/profiling
    - Retain stylistic elements unless proven non-diagnostic
    - Consider personalized vocabularies
- Predictive modeling
    - Systematically compare preprocessing workflows
    - Demonstrate choice validity over alternatives
- Variation/comparative analyses
    - Prioritize conservative techniques to avoid conflation
    - Replicate analyses with flexible specifications
- Smaller/noisier datasets
    - Favor lightweight preprocessing
    - Pilot effects of heavier techniques
- Qualitative comparison/synthesis
    - Clearly define codes of interest regarding language
    - Evaluate risk of information loss from normalization
The recommendations aim to ensure approach matches data and goals per the guidelines.
## Guidelines presented in Figure 1
- Research Questions
    - Explicitly link techniques to questions/constructs of interest
    - Pilot sensitivity to alternative valid specifications
- Type of Text Analysis
    - Justify choices for topic models vs. other methods  
    - Align weights/parameters to data characteristics
- Corpus Characteristics
    - Favor lightweight preprocessing for smaller datasets  
    - Evaluate risks of information loss for specific analyses
- Preprocessing Techniques
    - Retain meaningful variations unless proven non-diagnostic  
    - Compare impact of standardization across pipelines
- Validation Strategies
    - Systematically compare modeling performance of techniques  
    - Demonstrate validity over alternatives for research context
- Limitations
    - Acknowledge assumptions and generalization constraints  
    - Suggest avenues to address limitations over time
- Reproducibility
    - Disclose preprocessing details to facilitate reproduction  
    - Promote sharing of annotated datasets and tools
![Figure 1](https://i.imgur.com/0QHR5Nf.png)
# Recommendations for Reporting Text Mining Research
## Promote transparency and replicability
- Datasets
    - Make datasets openly available where possible
    - Provide data dictionaries/codebooks
- Preprocessing Methods
    - Fully document all techniques and parameters
    - Consider representing as modular, parameterized pipelines
- Computations
    - Provide computational reproducibility sections
    - Release code/notebooks for all analyses
- Analytic Details
    - Describe hyperparameter tuning or model selection
    - Note all model specifications
- Validation Measures
    - Report all evaluation metrics calcuations
    - Replicate on validation/test partitions
- Limitations
    - Fully acknowledge analytic, dataset and method limitations
    - Suggest validation of claims under other conditions
- Artifacts
    - Archive artifacts in online repositories
    - Release tools that reproduce or build on the work
- Independent Evaluation
    - Encourage community review and extension
    - Conduct collaborative reproducible research projects
These changes would strengthen the scientific rigor and utility of published research.
![](https://i.imgur.com/y3Gsubq.png)
# Conclusion
## Summary of contributions to understanding effects of preprocessing
- Highlighted Preprocessing Decisions as Impactful
    - Decisions often underreported or unjustified despite potential to influence results
- Proposed Framework for Evaluating Choices
    - Figure 1 conceptually links choices with questions, data, validation strategies
- Emphasized Lack of One-Size-Fits-All Approach
    - Techniques must be tailored empirically based on specific study characteristics
- Advocated for Increased Transparency
    - About decisions to facilitate reproducibility and evaluation of findings
- Suggested Comparative Experimentation
    - Applying different valid techniques to demonstrate sensitivity of outcomes
- Proposed Guidelines for Systematic Reporting
    - Of preprocessing to enhance accountability and consistency in practices
- Brought Attention to Underreported Implications
    - Of computational choices, advancing methodology by emphasizing empiricism
The key contributions were conceptual tools for evaluating choices, transparency and accountable reporting standards to improve reproducibility and validity.
## Limitations and opportunities for future research
- Limitations
    - Focused primarily on text analysis applications
    - Did not quantitatively assess impact of all preprocessing techniques
    - Guidance proposed as framework requiring further validation
- Future Research
    - Evaluate effects of preprocessing choices across other data types
    - Conduct sensitivity analyses comparing technique impacts systematically
    - Develop shared benchmark datasets covering a range of research needs
    - Build reusable pipelines and annotation tools enabling research
    - Promote collaborative projects exemplifying reporting standards
    - Quantify adherence to proposed guidelines in literature over time
    - Continuously update reviews to strengthen evidenced standards
    - Propose new techniques with validity justified prior to adoption
Building on identified limitations, continued empirical work can advance understanding of preprocesing impacts and sustain progress towards best practices. Generalizability and rigor remain areas for future improvement.