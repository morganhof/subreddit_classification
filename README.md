# **PROJECT 3**: Morgan Hofmann  


# Problem Statement  
*This is a binary classification problem that predicts whether a Reddit post originated from the Dogs Subreddit or the Parenting Subreddit using natural language processing. I'd like to determine how similar the woes and wows of dog-ownership and child-rearing are, with the goal of building a model that categorizes these two Subreddit posts within 90% accuracy.*  
    
  
# File Directory  
* README.md   
* 01_code_pushshift_dogs.ipynb
* 01_code_pushshift_parenting.ipynb
* 02_eda_and_cleaning.ipynb
* 03_modeling_and_viz
* data_collection  
    * dogs.csv  
    * parenting.csv
* data_clean  
    * subreddits_cleaned.csv 
* presentation_dogs_v_parenting.pdf

  
# Data and Data Dictionary  
Data Sources:  
* [`dogs.csv`](./data_collection/dogs.csv): Dogs subreddit data used for modeling the data  
* [`parenting.csv`](./data_collection/parenting.csv): Parenting subreddit data used for modeling the data 
    
The above data sources were scraped from the Pushshift API: https://github.com/pushshift/api  
Reference the code I used to scrape the APIs by looking at these two files: *01_code_pushshift_dogs.ipynb* and *01_code_pushshift_parenting.ipynb*

The full datasets include all sorts of information regarding these two different subreddit posts. The untouched data includes 70-74 features per subreddit and 3,600 posts per subreddit. The cleaned version of the datasets is much smaller, containing 10 features and 6,170 observations in total, combining both subreddits. This cleaned dataset is 54% Dogs subbreddit observations and 46% Parenting subreddit observations.
  

**Features contained in the subreddits_cleaned.csv**:  

|Feature|Type|Dataset|Description|  
|---|---|---|---|  
|author|string|subreddits_cleaned.csv|Creator of the subreddit post|   
|topic|string|subreddits_cleaned.csv|Topic of the subreddit post|   
|title|string|subreddits_cleaned.csv|Title curated by the author for the subreddit post|   
|text|string|subreddits_cleaned.csv|Content of the post|   
|num_comments|int|subreddits_cleaned.csv|Number of comments on the subreddit post|   
|is_dogs|int|subreddits_cleaned.csv|Categorizes subreddits: Dogs=1, Parenting=0|  
|title_length|int|subreddits_cleaned.csv|Number of characters in the title|  
|title_word_count|int|subreddits_cleaned.csv|Number of words in the title|  
|text_length|int|subreddits_cleaned.csv|Number of characters in the subreddit post|  
|text_word_count|int|subreddits_cleaned.csv|Number of wrods in the subreddit post|  
   
  
# Executive Summary  
*I divided my data into a training set and testing set, using Text as the single feature to help me predict whether the subreddit post belongs to Dogs or Parenting. Since I wanted to predict whether a Reddit post originated from the Dogs subreddit or the Parenting subreddit, I figured I'd start with the single most important feature and build onto my model if I needed to.*  
  
*I executed 3 models total. The first model was my baseline model, which performed with an accuracy of 54.05%, and a balanced accuracy of 50%, meaning my baseline model will predict the true subreddit half of the time, assuming the data set is split 50/50. For my next model, I made a pipe and used gridsearchCV with various parameters to transform Text and used a Naive Bayes model to predict the subreddit. The model that performed the best filtered out common english words, contained unigrams and bigrams, and removed any words that was in more than 70% of the observations - this model performed with an accuracy of 97.67%. I created another model using a pipe and gridsearchCV with various parameters to transform Text and used a Logistic Regression model to predict the subreddit. This model didn't perform as well as the prior model - it performed with an accuracy score of 96.37%. So, my best model was the Naive Bayes model.*
  
    
# Conclusions and Recommendations  
*My goal was to build a model that categorizes Dogs & Parenting subreddit posts within 90% accuracy. Our model was able to accurately filter 97.67% of the subreddit posts, meaning that about 98 times out of 100, this Naive Bayes model will accurately predict which one it is. This leaves about 2.33% of subreddit posts for further analysis. I would love to do additional research to discover which texts were miscategorized and see if it’s due to similar language, or lack of language, or something else. Looking into the data further would help me determine how similar the woes and wows of dog-ownership and child-rearing are.*  
  
*A recent study posted in Scientific American showcases data that suggests that humans nurture their pets like they do human children **(3)**. However, we can see by the high accuracy rate of my model, that we use different language in Subreddits when we talk about parenting human kids or dogs. There is language that is similar enough to cause our model to incorrectly categorize some Dogs & Parenting subreddit posts. I think looking into those miscategorized posts and repeating this study on new data is prudent.*

  
# Sources
**(1):** https://www.reddit.com/r/dogs/
  
**(2):** https://www.reddit.com/r/Parenting/ 
  
**(3):** https://www.scientificamerican.com/article/dog-and-cat-moms-and-dads-really-are-parenting-their-pets/
