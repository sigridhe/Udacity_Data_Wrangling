# Udacity_data_wrangling
udacity data wrangling project - @weratedogs

	January 21, 2019

Below is a summary of the wrangling process. 

Gather:

Three files are gathered via different methods:

    1. Since WeRateDogs Twitter archive csv. file is given by the project, I downloaded the file manually and then uploaded to project workspace. Then pandas is used to write data in the file to a data frame. 
    
    2. Project instruction also provides url address for image prediction file. I used python’s requests library to download the tsv. file, and then write data to a separate data frame.
    
    3. To get retweet counts and favorite counts of each twitter, first, I set up a Twitter’s development account, submitted application, and then the access to twitter API was granted immediately.      
    The tweet IDs in the WeRateDogs Twitter archive is used to query the Twitter API for each tweet's JSON data using Python Tweepy library, and then each tweet's JSON data(tweet ID, retweet count, and favorite count) is stored in tweet_json.txt file, with each tweet's JSON data written to its own line. Due to Twitter’s API rate limit (15 minute), the process ran about 25 minutes. 
    Then this .txt file is written into a pandas data frame. 


Assess:

After gathering above data, I assessed the three data frames by pandas library programmatically. I also opened them in excel to read the complete tweets. Below quality and tidiness issues are identified:
>Quality :
>>Tweets archive file:
1. Some tweets are retweets. We only need original ratings.
2. Some tweets are replies. We only need original ratings. 
3. Timestamp is a string object, not datetime object.
4. Source is a link, not category data type. 
5. Not all data in rating_denominator is 10. Some of them is wrong data, but some of them is valid based on the text content. 
6. Outliers in rating_numerator. 
7. Some rating numerators is float in text content, but rating_numerator type is int in dataframe. 
8. tweet_id is int, not string object.
>>Image prediction file:
1. tweet_id is int, not string object.
>>Retweet counts and favorite counts file:
1. tweet_id is int, not string object.
   
>Tidiness:
1. All three files describe one type of observational unit. 
2. Tweets archive file: columns retweeted_status_id, retweeted_status_user_id, retweeted_status_timestamp, in_reply_to_status_id, in_reply_to_user_id are not needed. 
3. Tweets archive file: columns ‘doggo','floofer', ‘pupper',' puppo' is one variable.


Clean:

First, a copy of original file is created for the cleaning process. I used pandas and numpy library to fix above identified issues one by one programmatically. For each issue, the cleaning process is: defining, coding and testing. 
