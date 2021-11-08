### Investigating the opinions on Twitter regarding vaccines and mask use.

Ignasi Sols Balcells

I aim to identify the different groups of Twitter users that currently tweet about vaccines and mask use on Twitter. 

To start exploring this goal, I have used the package 'snscrape' to scrap 1000 tweets published on 2021-11-03, labeled by this package as being written in English, with the query 'COVID Vaccine'. I scrapped several tweet fields, but for the current analyses, I only used the 'text' field. 

I have used Spacy for pre-processing (removing stop words, punctuations, lemmatization, white spaces, URL, numbers), resulting in a bag of words per each tweet. In parallel, by leveraging Spacy's objects, I analyzed named entities: I removed stop words from the named entities, (but not numbers), lemmatize each component, and then added the result the bag-of-words with underscores if the resulting named entity had more than one word. If the named entity was already in the bag of words as a result of the first pre-processing, I did not add it again. 

The above preprocessing was then wrapped in a function and passed to sklearn' CountVectorizer, resulting in a document-term matrix (dimensions 1000 documents x 4551 terms). Then, I applied matrix vectorization (NMF), with n_topics = 5 as a parameter. 

These are the 30 most important terms for the five topics:

<img src="https://github.com/ignasisols/metis_NLP_unsupervisedML/blob/main/topics_MVP.png" width="600px" />


In the next days, I plan to scale my analysis to a million tweets, using TfidfVectorizer instead of CountVectorizer and reducing the number of terms in the document-term matrix to 1000 (when calling TfidfVectorizer). I also plan to run k-means clustering to identify different clusters of users and plot the different clusters in 2D. 







