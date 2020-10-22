
### John Mahoney
### Data 512 A2
### October 22, 2020

# Bias in Data
This repository contains files for recreating exploratory data analysis of a corpus of data created and used by Nithum Thian and Lucas Dixon of Google Jigsaw working with Ellery Wulczyn at the Wikimedia Foundation. Their work was published under the title Ex Machina: [Personal Attacks Seen at Scale](https://arxiv.org/pdf/1610.08914.pdf) and was attempting to better understand personal attacks on online platforms. This work was used to create the [Perspective API](https://www.perspectiveapi.com/#/home) tool to help control toxic comment.


## Analysis Summary

#### Exploration of Toxicity Corpus

There is often a generational component in how people speak and this could affect whether someone perceives a comment as toxic or not.
The question(s) I asked is: Is the toxicity corpus age-ballanced with respect to the population, and if not is there some relation between age and liklihood to rate a comment as toxic? This could indicate an age bias.

![Toxicity vs Age](https://github.com/jfm888/data-512/blob/main/data-512-a2/data512_a2_approximate_annotator_age_vs_rate_marking_a_comment_as_toxic.png)

We see that younger annotaters are less likley than older annotaters to rate a comment as toxic.

We have also seen that the corpus is biased towards younger annotaters, which taken together with the above information would suggest the corpus toxicity is underrated do to the age bias. Furthermore, any models trianed on this corpus may underrepresent how toxic a comment is to the larger population.

#### Exploration of Aggression Corpus

In many cultures men are seen to be generally more aggressive than women. 

My question(s): is the Aggression corpus gender balanced, and if not is it related to how aggressive comments are scored? This could indicate a gender bias.

![Aggression vs Gender](https://github.com/jfm888/data-512/blob/main/data-512-a2/data512_a2_percent_of_annotater_scores_by_score_and_gender.png)

In the above plot we see that men annotaters tend to give lower aggressiveness scores than women annotaters which seems to represent a gender bias. The score of zero was omitted for clarity

We also saw that there are about twice as many men annotaters as women annotaters which compounds the bias.  It seems like the aggressiveness of the comments in the corpus is underrated due to the majority of men annotaters. If this is not corrected then any models trained on this corpus may also underrate how aggressive a comment is to a larger population.

#### Implications

The results of our exploratory data analysis lead us to strongly suspect that an annotator gender and age imbalance in the overall corpus could result in a bias where the level of toxicity and aggresiveness of comments could be underestimated. Any models trained on this corpus should be closely examined for age and gender bias.

## Data

The data raw data was initially taken from a public dump of English Wikipedia made available on January 13, 2016, of articles dating from 2004-2015. The data was originally 63 million comments and was randomly sampled to generate a new corpus of 160k comments, which was then given to [Crowdflower](https://visit.figure-eight.com/People-Powered-Data-Enrichment_T) for cleaning and annotating. The paper was published on the 22 February of 2017 along with the data sets.

Cloudflower labeled 160k discussion comments for the toxicity data and 100k comments for the aggression data from English Wikipedia with the assistance of 4053 annotators. For the toxicity data each comment was labeled by 10 annotators via Crowdflower on whether it is a toxic or healthy contribution (-2 to 2). For the aggressive data each comment was labeled by 10 annotators via Crowdflower on how aggressive it was (-3 to 3). T

notebook(data-512-a2.ipynb) contains instructions recreate the analysis of these two datasets(toxicity and aggression)

The actual data figshare datasets are not in the repository as they are too big for Github to host. However the data files can be downloaded using code in the included ipython notebook(data-512-a2.ipynb) the files can also be found here: [Aggression](https://figshare.com/articles/Wikipedia_Talk_Labels_Aggression/4267550) and [Toxicity](https://figshare.com/articles/Wikipedia_Talk_Labels_Toxicity/4563973)

The included CSV files are to help with recreating the png images seen below and in the notebook (also in the repo)


### Packages
The ipython notebook uses python 3 (https://www.python.org/download/releases/3.0/) and the folowing python packages:
  - [pandas 1.1.3](https://pandas.pydata.org/)
  - [numpy 1.19.0](https://numpy.org/)
  - [matplotlib 3.3.1](https://matplotlib.org/)
  - [seaborn 0.11.0](https://seaborn.pydata.org/)
  - [scipy 1.5.3](https://docs.scipy.org/doc/scipy/reference/tutorial/stats.html)

Please send questions about this project to John Mahoney jm888@uw.edu

Enjoy!
