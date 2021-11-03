### Investigating the evolution in opinions regarding vaccines and mask use.

Ignasi Sols

#### Question/need:

* What is the framing question of your analysis, or the purpose of the model/system you plan to build? 

I aim to identify the different groups of Twitter users that currently tweet about vaccines and mask use on Twitter, and to investigate the evolution of opinions of their members when comparing with their tweets in 2020 (early in the pandemic). Therefore, I plan to investigate two snapshots of time (mid-2020 and fall-2021, the exact periods to be determined). For each 2021 Twitter user included, I plan to identify to which 2020 cluster she/he was assigned to. I aim to better understand the different groups of people in favor or opposed to vaccines and masks, and understand where were their members at the start of the pandemic (in which twitter user clusters).

* Who benefits from exploring this question or building this model/system?
A better understanding of the different subgroups of people in favor or opposed to vaccination and masks might be useful for public health officials as well as journalists. A more granular and nuanced analysis and understanding of the public opinion regarding masks and vaccination might be more useful than a pure binary classification that might feed more polarization.

#### Data Description:
I plan to use the Twitter API to identify tweets from a snapshot of time in the fall of 2021 regarding vaccines and mask use, and then investigate the tweets that these users had back in 2020, at the start of the pandemic. I plan to download 10000+ tweets from each time period.

#### Tools:

I plan to use Spacy for pre-processing: clean, tokenize, remove stop words, stem/lemmatize if needed and vectorize the tweets. Then, I will perform dimensionality reduction and topic modeling, with the aim of finally identifying clusters of twitter users at both periods of time. 
Once this information is available, I would like to obtain insights regarding which cluster groups in 2020 are the origin of the current clusters, and perhaps assessing polarization (by investigating if there is a tendency for users to be closer in euclidian distance when comparing 2020 with 2021). 


#### MVP Goal:

* The MVP for this project would be to perform topic modeling on tweets regarding vaccines and mask from 2020.