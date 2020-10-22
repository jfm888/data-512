
### John Mahoney
### Data 512 A2
### October 22, 2020

# Bias in Data


This repository contains files for recreating exploratory data analysis of a corpus of data created and used by Nithum Thian and Lucas Dixon of Google Jigsaw working with Ellery Wulczyn at the Wikimedia Foundation. Their work was published under the title Ex Machina: [Personal Attacks Seen at Scale] (https://arxiv.org/pdf/1610.08914.pdf) and was attempting to better understand personal attacks on online platforms. This work was used to create the [Perspective API] (https://www.perspectiveapi.com/#/home) tool to help control toxic comment. The data was initially taken from a public dump of English Wikipedia made available on January 13, 2016, of articles dating from 2004-2015. The data was originally 63 million comments and was randomly sampled to generate a new corpus of 160k comments, which was then given to [Crowdflower](https://visit.figure-eight.com/People-Powered-Data-Enrichment_T) for cleaning and annotating. The paper was published on the 22 February of 2017 along with the data sets.

Cloudflower labeled 160k discussion comments from English Wikipedia with the assistance of 4053 annotators. Each comment was labeled by 10 annotators via Crowdflower on whether it is a toxic or healthy contribution. The commenters were given a questionnaire (Image 1) and asked to rate how likely a comment was to make them leave the discussion. The authors used ten annotators as they saw little benefit from increasing the number past ten.

notebook(data-512-a1.ipynb) contains instructions to produce a visualiztion showing english wikipedia traffic by pageview count and legacy pagecount data gathered from the wikipedia api (https://wikimedia.org/api/rest_v1/#/Legacy_data/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end). 

The pageviews counts were filtered to only show traffic from users.

The included one CSV and five JSON files exist to help with repoducabliity; the notebook will generate these files when run using the wikipedia api.

There is a png of the visualization to show expected output of the notebook.

The API set up code in the notebook is borrowed with permission from a notebook: (https://public.paws.wmcloud.org/User:Jtmorgan/data512_a1_example.ipynb) by Brandon Martin-Anderson (bmander@uw.edu)

The ipython notebook uses python 3 (https://www.python.org/download/releases/3.0/) and the folowing python packages:
  - json 3.9 (https://docs.python.org/3/library/json.html)
  - requests 2.24.0 (https://pypi.org/project/requests/)
  - pandas 1.1.3 (https://pandas.pydata.org/)
  - numpy 1.19.0 (https://numpy.org/)
  - matplotlib 3.3.1 (https://matplotlib.org/)

All other work is original

Please send questions about this project to John Mahoney jm888@uw.edu

Enjoy!
