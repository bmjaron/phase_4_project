![readme1](https://github.com/bmjaron/phase_4_project/assets/115658357/2a140028-a99f-4670-a83f-98a1af42d331)

# Predicting Positive Sentinment with Multinomial Bayes'

**Author**: [Benjamin Jaron](mailto:bmjaron@gmail.com)

# Table of Contents
* [Repository Structure](#I.Repository Structure)
* [Overview](#II.Overview)
* [Data and EDA](#III.Data and EDA)
* [Text Cleaning](#IV. Text Cleaning)
* [Modeling](#V.Modeling)
* [Conclusions](#VI.Conclusions)

# I. Repository Structure

Aside from this README file, our repository contains a data set of 8,721 tweets, a .gitignore file, and a Jupyter notebook. It also contains the slide deck for our non-technical presentation. 

# II. Overview

Our client is SXSW and we've been tasked with building a model that helps them classify positive tweets. Our data for this project is 8,721 tweets from the conference. Many of these tweets have an emotion associated with them. 

Tweets differ greatly from traditional text documents, as they are often in short-hand and have specific Twitter words that don't provide much meaning to the overall tweet. Additionally, there are usernames and online abbreviation containing special symbols and numbers. In order to account for this we made heavy use of regular expresions to remove this and leave as many pure words as possible. We also tokenized, stemmed and lemmatized, in addition to removing Twitter and SXSW specific words. 

A characteristic of our data was that it was imbalanced. Positive tweets (our target) accounted for only about 30% of the data. As such, we created 2 classes, positive and non-positive tweets, and randomly undersample the majority class in order to train on a balanced dataset. 

Our final model was a multinomial naive Bayes' model. Our metric that we scored this model on was recall, as we found it imperative to correctly identify as many positive tweets as possible. This would provide the SXSW with the ability to build off that positive sentiment. Our model had a 73% recall score, which means that we can identify 73% of all positive tweets.

# II. Data and EDA

We have a data set that contains 8,721 entries. Each entry is a tweet that contains text, to which product or brand the tweet is directed, and if there is a discernable emotion from the tweet.

![readme2](https://github.com/bmjaron/phase_4_project/assets/115658357/da4868bb-ba86-4de6-b03e-ead0084451b1)

We see that we have a data imbalance, with most tweets not being of the positive target. We account for this in our modeling section by undersampling the majority class.

![readme3](https://github.com/bmjaron/phase_4_project/assets/115658357/4379d382-00c1-4323-8d89-77889c6437d9)

After all stopwords were removed, the above represents the most common words to appear in the corpus. Below we show the most common unique positive and unique non-positive words.



# III. Text Cleaning

In order to properly process our tweets, we used a relatively conventional cleaning and tokenization process using NLTK's built-in functions. We first all tweets of special characters and punctuation using regular expression. We then used NLTK's tokenizer. We also stemmed and lemmatized, and removed all English and business-problem specific stopwords.

# IV. Modeling

## A. Overview (and a word about our scoring metric)

The model that we used was a multinomial naive Bayes' classifier, and we were able to achieve a recall score of 73%. 

We felt that recall, which is the ratio of predicted positives to true positives, was the most approriate method to score our model. This is our business problem is to provide SXSW a model to identify as many positive tweets as possible, which will in turn enable them to fortify their strengths.

## B. Validation method and vectorization

In order to validate our model, we divided the data into 3 sets: training, testing and a holdout. The models were trained on the training set, and each iteration was tested on the testing set. We ran the final model on the unseen holdout set.

An important element of our modeling process was converting our text data into features for modeling. We utilized both count vectorizers and the TF-IDF vectorizer.

## C. Multinomial naive Bayes' 

Our final model was a multinomial naive Bayes' model. The naive Bayes' model is specifically apt for text classification problems, and it was our best model. We attempted both count and TF-IDF vectors, and found that the model trained on features produced with the count vectorizer was the highest scoring. 

The model had a recall score of 73% when ran on the holdout set. Below is a confusion matrix of our results. 

![readme4](https://github.com/bmjaron/phase_4_project/assets/115658357/5ac84648-b0b6-421d-90e4-e8de67b4c4fe)


# V. Conclusions 

Our final recommendation is that SXSW use our model in order to predict positive tweets. In turn this will help them classify each potential positive tweet, and use its contents to identify and fortify existing strengths of the conference.
