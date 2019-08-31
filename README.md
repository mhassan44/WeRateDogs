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

### Gather: Summary

#### Gathering was the first step in the data wrangling process. We could finish the high-level gathering process:

1. Obtaining data
- Getting data from an existing file (twitter-archive-enhanced.csv) Reading from csv file using pandas
- Downloading a file from the internet (image-predictions.tsv) Downloading file using requests
- Querying an API (tweet_json.txt) Get JSON object of all the tweet_ids using Tweepy
2. Importing that data into our programming environment (Jupyter Notebook)

## Assessing

<p align="justify">After gathering each of the above pieces of data, assess them visually and programmatically for quality and tidiness issues was our next step. We could detect and document the following quality issues and tidiness issues.</p>

### A- Quality Issues

**Completeness, Validity, Accuracy, Consistency => Has content issues archive dataset**

**1. archive_copy**

- Missing values for dog stage (incomplete data for doggo, floofer, pupper, puppo).
- Replace 'None' with 'NaN' for all dog stages.
- Rating numerators and rating denominators values are incorrect.
- Remove entries that are retweets and expanded URLs are unnecessary
- tweet_id is numeric. Should be string.
- Change tweet_archive timestampe from object type to datetime type.

**2. image_predictions_copy**

- Remove entries where p1_dog, p2_dog, and p3_dog are all "False".
- Values for p1, p2, and p3 sometimes capitalized but not always .
- tweet_id is numeric. Should be string.

**3. tweet_data_copy**

- tweet_id is numeric. Should be string.

### B- Tidiness Issues

**Untidy data => has structural issues**

   
- Doggo, floofer, pupper, puppo are one variable spread across different columns in archive_copy.
- rating_numerator and rating_denominator can be combined into one column in archive_copy.
- Combine data frames by tweet_id.


## Cleaning

<p align="justify">Cleaning our data is the third step in data wrangling. It is where we fixed the quality and tidiness issues that we identified in the assess step.</p>

<p align="justify">We used the two types of cleaning, the manual and programmatic even the manual not recommended but the issues were one-off occurrences. Our process was Define, Code and Test and we were always making a copy of the dataset even we made the copy in file to test the change before applying to the main dataset. We didn't spot all the quality and tidiness assessments at the assessing data section, so we have been iterating and revisiting assessing to add these assessments to our notes.</p>


## Insights Summary

- <p align="justify">The mean for rating is 1.127;the 3 most common ratings are 1.2,1.0,1.1, and rating frequency becomes smaller as the rating becomes extreme.</p>
- <p align="justify">Posts with extreme ratings get more favorites and retweets.Posts with rating 1.4 gets the highest favorite counts and retweet 
- <p align="justify">Favorites and retweets counts are highly positively correlated. For about every 4 favorites there is 1 retweet. Most of the data falls below 40000 favorites and 10000 retweets.</p>
- <p align="justify">Favorites and retweets are the gradually increase over time.</p>
- <p align="justify">Among the 4 dog stages, pupper has the biggest frequency, but pupper also gets the lowest favorite counts and retweet counts and rating.</p>


## Conclusion

<p align="justify"> Data wrangling indeed is a core skill that everyone who works with data should be familiar with since so much of the world's data isn't clean. If we analyze, visualize, or model our data before we wrangle it, our consequences could be making mistakes, missing out on cool insights, and wasting time. We couldn't be able to make some of the visualization without wrangling (i.e dog gender partition) So best practices say wrangle. Always.</p>

