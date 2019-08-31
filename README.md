## Introduction

<p align="justify">  Data wrangling is a core skill that everyone who works with data should be familiar with since so much of the world's data isn't clean. We need to wrangle our data for good outcomes, otherwise there could be consequences. If we analyze, visualize, or model our data before we wrangle it, our consequences could be making mistakes, missing out on cool insights, and wasting time. So best practices say wrangle. Always. Through this project could made:</p>

- Data wrangling, which consists of:
1. Gathering data
2. Assessing data
3. Cleaning data
- Storing, analyzing, and visualizing our wrangled data
- Reporting on 
1. Our data wrangling efforts and 
2. Our data analyses and visualizations
 
<p align="justify"> The dataset that I will be wrangling (and analyzing and visualizing) is the tweet archive of Twitter user @dog_rates, also known as WeRateDogs. WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10. The numerators, though? Almost always greater than 10. 11/10, 12/10, 13/10, etc. Why? Because <a href="https://knowyourmeme.com/memes/theyre-good-dogs-brent">"they're good dogs Brent"</a>
. WeRateDogs has over 4 million followers and has received international media coverage.</p>

<p align="justify">  WeRateDogs downloaded their Twitter archive and sent it to Udacity via email exclusively for us to use in this project. This archive contains basic tweet data (tweet ID, timestamp, text, etc.) for all 5000+ of their tweets as they stood on August 1, 2017. More on this soon.</p>

## Files
 
#### I will provide a brief summary of the files below.

- **act_report.pdf** is a written report of the insights that I had found in my analysis of WeRateDogs tweets.
- **image_predictions.tsv** is a file that was provided by Udacity that has the dog breed predictions.
- **tweet_json.txt** is a json file containing all of the data available returned from twitter's api.
- **twitter_archive_enhanced.csv** is a csv file containing WeRateDogs tweet archive, but it contains a little more information.
- **twitter_archive_master_final.csv** is the clean data file that I wrote all the data to after wrangling. It was all the data that was used for the analysis.
- **wrangle_act.html** is the html file where I wrangled and analyzed all my data.
- **wrangle_act.ipynb** is the jupyter notebook where I wrangled and analyzed all my data.
- **wrangle_report.pdf** is a written report of my data wrangling efforts.

## Gathering

#### Gathering Data for this Project composed from three pieces of data as described below:

- <p align="justify">The WeRateDogs Twitter archive. We manually downloaded this file manually by clicking the following link: twitter_archive_enhanced.csv</p>
- <p align="justify">The tweet image predictions, i.e., what breed of dog (or other object, animal, etc.) is present in each tweet according to a neural network. This file (image_predictions.tsv) hosted on Udacity's servers and we downloaded it programmatically using python Requests library on the following <a href="https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv">"URL of the file"</a>.</p>
- <p align="justify">Each tweet's retweet count and favorite (i.e. "like") count and any additional data we found interesting. Using the tweet IDs in the WeRateDogs Twitter archive, we could query the Twitter API for each tweet's JSON data using Python's Tweepy library and store each tweet's entire set of JSON data in a file called tweet_json.txt file. Each tweet's JSON data stored in a line.</p>

## Gather: Summary

#### Gathering was the first step in the data wrangling process. We could finish the high-level gathering process:

1. Obtaining data
- Getting data from an existing file (twitter-archive-enhanced.csv) Reading from csv file using pandas
- Downloading a file from the internet (image-predictions.tsv) Downloading file using requests
- Querying an API (tweet_json.txt) Get JSON object of all the tweet_ids using Tweepy
2. Importing that data into our programming environment (Jupyter Notebook)

## Assessing

<p align="justify">After gathering each of the above pieces of data, assess them visually and programmatically for quality and tidiness issues was our next step. We could detect and document the following quality issues and tidiness issues.</p>

## Quality

**Completeness, Validity, Accuracy, Consistency => Has content issues archive dataset**

    in_reply_to_status_id, in_reply_to_user_id, retweeted_status_id, retweeted_status_user_id should be intergs instead of float
    retweeted_status_timestamp, timestamp should be datetime instead of object (string)
    The numerator and denominator columns have invalid values
    In several columns null objects are non-null (None to NaN)
    Name column have invalid names i.e 'None', 'a', 'an'
    We only want original ratings (no retweets) that have images
    We may want to change this columns type (in_reply_to_status_id, in_reply_to_user_id, retweeted_status_id, retweeted_status_user_id and tweet_id) to string because We don't want any operations on them images dataset
    Missing values from images dataset (2075 rows instead of 2356)
    Some tweet_ids have the same jpg_url
    Some tweets are have 2 different tweet_id one redirect to the other json_tweeets dataset
    This tweet_id (666020888022790149) duplicated 8 times

## Tidiness

**Untidy data => has structural issues**

    No need to all the informations in images dataset, (tweet_id and jpg_url what matters)
    Various stages of dogs in columns instead of rows archives dataset
    We may want to add a gender column from the text columns in archives dataset
    All tables should be part of one dataset

## Cleaning

<p align="justify">Cleaning our data is the third step in data wrangling. It is where we fixed the quality and tidiness issues that we identified in the assess step.</p>

<p align="justify">We used the two types of cleaning, the manual and programmatic even the manual not recommended but the issues were one-off occurrences. Our process was Define, Code and Test and we were always making a copy of the dataset even we made the copy in file to test the change before applying to the main dataset. We didn't spot all the quality and tidiness assessments at the assessing data section, so we have been iterating and revisiting assessing to add these assessments to our notes.</p>

## Conclusion

<p align="justify"> Data wrangling indeed is a core skill that everyone who works with data should be familiar with since so much of the world's data isn't clean. If we analyze, visualize, or model our data before we wrangle it, our consequences could be making mistakes, missing out on cool insights, and wasting time. We couldn't be able to make some of the visualization without wrangling (i.e dog gender partition) So best practices say wrangle. Always.</p>

