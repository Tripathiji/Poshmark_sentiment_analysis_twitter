# Poshmark_sentiment_analysis_twitter
This is a python script designed to estimate the public sentiment towards Poshmark by analyzing tweets.

Sentiment analysis by parsing the tweets fetched from Twitter using Python. Sentiment Analysis is the process of ‘computationally’ determining whether a piece of writing is positive, negative or neutral. It’s also known as opinion mining, deriving the opinion or attitude of a speaker.

DEPENDENCIES:
- tweepy
- textblob
- install NLTK corpora by running this in command : python -m textblob.download_corpora

Register for API access on apps.twitter.com to receive keys and access tokens

Create a TwitterClient class. This class contains all the methods to interact with Twitter API and parsing tweets. We use __init__ function to handle the authentication of API client.
In get_tweets function, we use: fetched_tweets = self.api.search(q = query, count = count) to call the Twitter API to fetch tweets.
In get_tweet_sentiment we use textblob module. analysis = TextBlob(self.clean_tweet(tweet)) TextBlob is actually a high level library built over top of NLTK library. First we call clean_tweet method to remove links, special characters, etc. from the tweet using some simple regex. Then, as we pass tweet to create a TextBlob object, following processing is done over text by textblob library:
Tokenize the tweet ,i.e split words from body of text. Do POS( part of speech) tagging of the tokens and select only significant features/tokens like adjectives, adverbs, etc. 

Pass the tokens to a sentiment classifier which classifies the tweet sentiment as positive, negative or neutral by assigning it a polarity between -1.0 to 1.0 .
Here is how sentiment classifier is created:

TextBlob uses a Movies Reviews dataset in which reviews have already been labelled as positive or negative.
Positive and negative features are extracted from each positive and negative review respectively.
Training data now consists of labelled positive and negative features. This data is trained on a Naive Bayes Classifier.
Then, we use sentiment.polarity method of TextBlob class to get the polarity of tweet between -1 to 1.
Then, we classify polarity as:

if analysis.sentiment.polarity > 0:
       return 'positive'
elif analysis.sentiment.polarity == 0:
       return 'neutral'
else:
       return 'negative'
Finally, parsed tweets are returned. Then, we can do various type of statistical analysis on the tweets. For example, in above program, we tried to find the percentage of positive, negative and neutral tweets about a query.

References:

http://www.ijcaonline.org/research/volume125/number3/dandrea-2015-ijca-905866.pdf
https://textblob.readthedocs.io/en/dev/quickstart.html#sentiment-analysis
textblob.readthedocs.io/en/dev/_modules/textblob/en/sentiments.html  
https://www.geeksforgeeks.org/twitter-sentiment-analysis-using-python/
