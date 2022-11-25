# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Netflix vs DisneyPlus classification


### Problem statement

We are part of the marketing team for a tv/movie production company. Our company is interested to sign a contract with either Netflix or Disney+ to stream our shows on their platform. Before we make our decisions, we would like to see which platform suits our tv/movie genre the best. To get the sentiments of the users of the platform, we dive into their subreddit community to extract what the community have to say about these platforms. 

We will make use of natural language processing and classification models to classify reddit posts into either netflix or disneyplus. This will allow us to make use of the review of our tv/movies and run it through the classification model to see which platform is a better fit for our tv/movie. 

### Dataset description

The datasets are scraped from the following subreddits using Pushshift's API:

- [DisneyPlus Subreddit](https://www.reddit.com/r/DisneyPlus/)
- [Netflix Subreddit](https://www.reddit.com/r/netflix/)

The posts in the subreddits are scraped only when there are at least 30 words in the post.

The scraped datasets are then saved in: 

> 1. [`reddit_disneyplus.csv`](../dataset/reddit_disneyplus.csv)
> 2. [`reddit_netflix.csv`](../dataset/reddit_netflix.csv)

The data is as of 5 Nov ~2pm.

Duplicated posts are then removed from the dataset, leaving us with 9,800 unique posts for each subreddit. 

### Natural Language Processing Parsing

In order to classify posts, some initial data cleaning and NLP parsing were required before beginning to model using
1. Lemmatizing 
2. Stemming 
3. Count Vectorizers
4. TF- IDF (Term Frequency Inverse Document Frequency) Vectorizers

### The Modelling Process

We will be comparing two different classification algorithms: **Random Forest Classification** and **Logistic Regression**

Tweleve different classification models were tested using various parameter search methods with both type of vectorizer and lemmatizing/stemming to determine which combination of vectorizer, classification algorithm, and hyperparameters yielded the most accurate model.

Modelling Process: 

1. Generate the classification models. Within this process, we will be making use of:
    - train-test split
    - cross-validation / grid searching for hyperparameters


2. Evaluate our models
    - consider the evaluation metrics
    - consider the baseline score
    - how can the model be used for inference?

    
### Conclusions/Recommendations

**Conclusion:**

> From the top 20 words, other than the top 3 words: 'disney', 'netflix' and 'plus', which probably relates to disneyplus, netflix and disneyplus respectively, the remaining words seem to be quite generic. 

> The top 2 words is also ~4-5x more important than the 3rd/4th words. 

> This tells us that if our movie reviews do not have 'disney' or 'netflix' in them (which is highly likely since our shows are not on either platforms yet), our model will probably have a hard time classifying the reviews. This would then impact the accuracy of our model. 


**Recommendations:**

> Improvement to the model could be made by removing the words with high correlation to the subreddit such as 'disney', 'netflix', 'plus'.
