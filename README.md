# Predicting Positive Sentinment with Multinomial Bayes'

**Author**: [Benjamin Jaron](mailto:bmjaron@gmail.com)

# Table of Contents
* [Overview](#I.Overview)
* [Data](#II.Data)
* [EDA](#III.EDA)
* [Modeling](#IV.Modeling)
* [Conclusions](#V.Conclusions)

# I. Overview

Our client is SXSW and we've been tasked with building a model that helps them classify positive tweets. Our data for this project is 8,721 tweets from the conference. Many of these tweets have an emotion associated with them. 

Tweets differ greatly from traditional text documents, as they are often in short-hand and have specific Twitter words that don't provide much meaning to the overall tweet. Additionally, there are usernames and online abbreviation containing special symbols and numbers. In order to account for this we made heavy use of regular expresions to remove this and leave as many pure words as possible. We also tokenized, stemmed and lemmatized, in addition to removing Twitter and SXSW specific words. 

A characteristic of our data was that it was imbalanced. Positive tweets (our target) accounted for only about 30% of the data. As such, we created 2 classes, positive and non-positive tweets, and randomly undersample the majority class in order to train on a balanced dataset. 

Our final model was a multinomial naive Bayes' model. Our metric that we scored this model on was recall, as we found it imperative to correctly identify as many positive tweets as possible. This would provide the SXSW with the ability to build off that positive sentiment. Our model had a 73% recall score, which means that we can identify 73% of all positive tweets.

# II. Data 

We have a data set that contains 8,721 entries. Each entry is a tweet that contains text, to which product or brand the tweet is directed, and if there is a discernable emotion from the tweet.

# III. EDA 

# IV. Modeling

## A. Overview (and a word about our scoring metric)

The model that we used was a multinomial naive Bayes' classifier, and we were able to achieve a recall score of 73%. 

We felt that recall, which is the ratio of predicted positives to true positives, was the most approriate method to score our model. This is our business problem is to provide SXSW a model to identify as many positive tweets as possible, which will in turn enable them to fortify their strengths.

## B. Method to determine best model

# V. Conclusions 

