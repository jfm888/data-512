
### John Mahoney
### Data 512 A2
### October 22, 2020

# Bias in Data
This repository contains files for recreating exploratory data analysis of a corpus of data created and used by Nithum Thian and Lucas Dixon of Google Jigsaw working with Ellery Wulczyn at the Wikimedia Foundation. Their work was published under the title Ex Machina: [Personal Attacks Seen at Scale](https://arxiv.org/pdf/1610.08914.pdf) and was attempting to better understand personal attacks on online platforms. This work was used to create the [Perspective API](https://www.perspectiveapi.com/#/home) tool to help control toxic comment.


## Analysis Summary

#### Exploration of Toxicity Corpus

There is often a generational component in how people speak and this could affect whether someone perceives a comment as toxic or not.
The question(s) I asked is: Is the toxicity corpus age-ballanced with respect to the population, and if not is there some relation between age and liklihood to rate a comment as toxic? This could indicate an age bias.

![Toxicity vs Age](https://github.com/jfm888/data-512/blob/main/data-512-a2/data512_a2_approximate_annotator_age_vs_rate_marking_a_comment_as_toxic%20(1).png)

We see that younger annotaters are less likley than older annotaters to rate a comment as toxic.

We have also seen in ur ipythion notebook analysis that the corpus is biased towards younger annotaters, which taken together with the above information would suggest the corpus toxicity is underrated do to the age bias. Furthermore, any models trianed on this corpus may underrepresent how toxic a comment is to the larger population.

#### Exploration of Aggression Corpus

In many cultures men are seen to be generally more aggressive than women. 

My question(s): is the Aggression corpus gender balanced, and if not is it related to how aggressive comments are scored? This could indicate a gender bias.

![Aggression vs Gender](https://github.com/jfm888/data-512/blob/main/data-512-a2/data512_a2_percent_of_annotater_scores_by_score_and_gender%20(1).png)

In the above plot we see that men annotaters tend to give lower aggressiveness scores than women annotaters which seems to represent a gender bias. The score of zero was omitted for clarity

Our ipythion notebook analysis shows that there are about twice as many men annotaters as women annotaters which compounds the bias.  It seems like the aggressiveness of the comments in the corpus is underrated due to the majority of men annotaters. If this is not corrected then any models trained on this corpus may also underrate how aggressive a comment is to a larger population.

#### Implications

The results of our exploratory data analysis lead us to strongly suspect that an annotator gender and age imbalance in the overall corpus could result in a bias where the level of toxicity and aggresiveness of comments could be underestimated. Any models trained on this corpus should be closely examined for age and gender bias.

## Data

The data raw data was initially taken from a public dump of English Wikipedia made available on January 13, 2016, of articles dating from 2004-2015. The data was originally 63 million comments and was randomly sampled to generate a new corpus of 160k comments, which was then given to [Crowdflower](https://visit.figure-eight.com/People-Powered-Data-Enrichment_T) for cleaning and annotating. The paper was published on the 22 February of 2017 along with the data sets.

Cloudflower labeled 160k discussion comments for the toxicity data and 100k comments for the aggression data from English Wikipedia with the assistance of 4053 annotators. For the toxicity data each comment was labeled by 10 annotators via Crowdflower on whether it is a toxic or healthy contribution (-2 to 2). For the aggressive data each comment was labeled by 10 annotators via Crowdflower on how aggressive it was (-3 to 3). T

notebook(data-512-a2.ipynb) contains instructions recreate the analysis of these two datasets(toxicity and aggression)

The actual data figshare datasets are not in the repository as they are too big for Github to host. However the data files can be downloaded using code in the included ipython notebook(data-512-a2.ipynb) the files can also be found here: [Aggression](https://figshare.com/articles/Wikipedia_Talk_Labels_Aggression/4267550) and [Toxicity](https://figshare.com/articles/Wikipedia_Talk_Labels_Toxicity/4563973)

The included CSV files are to help with recreating the png images seen below and in the notebook (also in the repo)

#### Data Schema

Data description and schema was taken from [WikiMedia](https://meta.wikimedia.org/wiki/Research:Detox/Data_Release)

The schema for toxicity_annotations.tsv
rev_id: MediaWiki revision id of the edit that added the comment to a talk page (i.e. discussion).
worker_id: Anonymized crowd-worker id.
toxicity_score: Categorical variable ranging from very toxic (-2), to neutral (0), to very healthy (2).
toxicity: Indicator variable for whether the worker thought the comment is toxic. The annotation takes on the value 1 if the worker considered the comment toxic (i.e worker gave a toxicity_score less than 0) and value 0 if the worker considered the comment neutral or healthy (i.e worker gave a toxicity_score greater or equal to 0). Takes on values in {0, 1}.

Schema for aggression_annotations.tsv
rev_id: MediaWiki revision id of the edit that added the comment to a talk page (i.e. discussion).
worker_id: Anonymized crowd-worker id.
aggression_score: Categorical variable ranging from very aggressive (-2), to neutral (0), to very friendly (2).
aggression: Indicator variable for whether the worker thought the comment has an aggressive tone . The annotation takes on the value 1 if the worker considered the comment aggressive (i.e worker gave an aggression_score less than 0) and value 0 if the worker considered the comment neutral or friendly (i.e worker gave an aggression_score greater or equal to 0). Takes on values in {0, 1}.

Schema for {toxicity/aggression}_worker_demographics.tsv
This information was obtained by an optional demographic survey administered after the labelling task, and fields are blank if the worker did not answer parts of the survey.
worker_id: Anonymized crowd-worker id.
gender: The gender of the crowd-worker. Takes a value in {'male', 'female', and 'other'}.
english_first_language: Does the crowd-worker describe English as their first language. Takes a value in {0, 1}.
age_group: The age group of the crowd-worker. Takes on values in {'Under 18', '18-30', '30-45', '45-60', 'Over 60'}.
education: The highest education level obtained by the crowd-worker. Takes on values in {'none', 'some', 'hs', 'bachelors', 'masters', 'doctorate', 'professional'}. Here 'none' means no schooling, some means 'some schooling', 'hs' means high school completion, and the remaining terms indicate completion of the corresponding degree type.

Schema for {aggression/toxicity}_annotated_comments.tsv
The comment text and metadata for comments with attack/aggression/toxicity labels generated by crowd-workers. The actual labels are in the corresponding {aggression/toxicity}_annotations.tsv since each comment was labeled multiple times.

rev_id: MediaWiki revision id of the edit that added the comment to a talk page (i.e. discussion).
comment: Comment text. Consists of the concatenation of content added during a revision/edit of a talk page. MediaWiki markup and HTML have been stripped out. To simplify tsv parsing, \n has been mapped to NEWLINE_TOKEN, \t has been mapped to TAB_TOKEN and " has been mapped to `.
year: The year the comment was posted in.
logged_in: Indicator for whether the user who made the comment was logged in. Takes on values in {0, 1}.
ns: Namespace of the discussion page the comment was made in. Takes on values in {user, article}.
sample: Indicates whether the comment came via random sampling of all comments, or whether it came from random sampling of the 5 comments around a block event for violating WP:npa or WP:HA. Takes on values in {random, blocked}.
split: For model building in our paper we split comments into train, dev and test sets. Takes on values in {train, dev, test}.

## Packages
The ipython notebook uses python 3 (https://www.python.org/download/releases/3.0/) and the folowing python packages:
  - [pandas 1.1.3](https://pandas.pydata.org/)
  - [numpy 1.19.0](https://numpy.org/)
  - [matplotlib 3.3.1](https://matplotlib.org/)
  - [seaborn 0.11.0](https://seaborn.pydata.org/)
  - [scipy 1.5.3](https://docs.scipy.org/doc/scipy/reference/tutorial/stats.html)

Please send questions about this project to John Mahoney jm888@uw.edu

Enjoy!
