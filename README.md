







# Identifying conversation themes regarding covid-19 vaccines on Twitter 

Ignasi Sols

## **Abstract**

The framing question of my analysis is to be able to identify the distinct Twitter conversation topics regarding covid-19 vaccines. The aim is to provide a service to the Associated Press, such that they can readily understand the current status of the conversation on social media regarding vaccines. For this, I have scrapped 10,000 tweets in English with the query 'covid vaccine' from the most recent day available at the time of starting the analyses: November 7th. Then, I have applied NLP and unsupervised learning methods as matrix factorization, NMF, and k-means clustering to understand the data. I have identified 5 conversation topics, and with them, 7 conversation clusters. 


## **Design**

I have chosen the scrap Tweets with the query 'covid vaccine' for November 7th, 2021, with the python package 'snscrape'. The resulting DataFrame had 10,000 rows and six columns: DateTime, Tweet ID, Text (the tweet content), User ID, Username, and language (as a result of the filter applied, it was 'English' for all rows). There are assumptions and risks: as all tweets are from the same day - our algorithm could be too much influenced by events that happened only on that day and might not generalize to other days. Also, given that all tweets are in English, this limits the scope of the project.  


## **Data**

 The current data set does not include re-tweets (https://github.com/JustAnotherArchivist/snscrape/issues/163). But, I also checked that all the 'Text' cells were unique, which they were. That said, further down the pipeline analysis, I identified some strikingly similar tweets, but not the same. As mentioned in the 'algorithm' section, I reduced the number of features (words/terms) to 1,000 when doing matrix factorization. Then, I further reduced the dimensionality to 5 principal components (or topics). 


## **Algorithm**

I first applied NLP to the tweets corpus with the Spacy package. I used the most accurate version, 'en_core_web_lg'. For each tweet, I converted all the letters into lower case, I excluded characters identified by Spacy as 'punctuation', or stop words. I removed Dates and verbs as well. Then, I lemmatized the words that survived the filtered and exclude those that were hashtags, or mentions, or numbers, and removed extra spaces, tabs, and line breaks, as well as URL links, and removed white spaces at the start or end of the resulting words. The resulting words were joined into a single string of words. 

The next step was to apply matrix factorization by running the TfidfVectorizer function, with the following parameters: min_df = 5, max_df = 0.5, and max_features = 1000. In fact, the tweet preprocessing mentioned above took place at this matric factorization step and not before. As a result, a doc_term sparse matrix was generated with dimensions (10000,1000). This was the first step in dimensionality reduction, as we restricted the computation to only output 1,000 features (terms).
Next, I did topic modeling. The choice was NMF, given that tweets are short text. I run the algorithm with different numbers of topics, and I chose five topics as the best option. I could identify five topics: (1) India-related, (2) Sesame Street Bird getting vaccinated, (3) Vaccine mandates, (4) Kids vaccine shots, and (5) Discussion about the unvaccinated. This 5th topic was the one that more tweets were assigned to, and in fact it was the worst defined topic.
Next, I run k-means clustering with n_clusters = 7 and n_init = 10. I used the yellowbrick package, in particular 'KElbowVisualizer' to apply the elbow method for k-means to find the optimal number of clusters for my data. The recommendation was 7. The silhouette score method from KElbowVisualizer recommended 2 clusters, but at that was a very small number of clusters, I decided to run k-means clustering with n_clusters = 7. 
As a result, I had 7 clusters, but only six were easily interpretable. Interestingly, one of the clusters that showed a clear combination of topics ('about_unvaccinated' and 'kids_shots') actually showed a combination of both topics when checking the most representative tweets for that cluster. But, overall, the 'about_unvaccinated' group showed smaller scores across clusters. Unfortunately, it was the topic most assigned to documents. 
I proceeded to run CorEx instead of NMF, and I anchored 6 topics. While it identified more topics, and accurately, the cluster with more tweet counts was the one that was not assigned to any particular topic.


## **Tools**

Numpy and Pandas for data wrangling and computing, snscrape for scrapping tweets, Spacy for NLP pre-processing, sklearn for machine learning unsupervised models.

































