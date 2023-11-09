
# Project 3 - Netflix and Disney+ Reddit Webscraping

by Liyena Putri Yusoff


## Background

In the past year, Netflix stock price has been decreasing due to shortage of in-demand films which have been the drive for viewership and subscriptions (abcnews, 2023). Due to the fallout of Hollywood actors and writer's strike, there has been fewer original shows produced by Netflix on top of lower subscription sign ups as compared to the previous years. 

## Problem Statement

As the marketing team at Netflix, our primary objective is to boost website traffic and increase the number of sign-ups for our streaming service. To achieve this, we aim to develop a machine learning classifier to analyze Netflix and Disney+ Reddit posts, distinguishing between discussions related to Netflix and Disney+. The model will identify unique words and phrases associated specifically with Netflix, allowing us to understand what sets us apart in public perception.

## Goal

The goal of the project is to utilize the unique words and insights for the company's marketing campaigns to amplify our unique selling points, thereby driving more traffic to our website and increasing subscriber sign-ups and viewership.

## Stakeholders

1. Netflix Marketing Team
2. Netflix Content Team

## Success metrics
* F1-score

## Summary
This is a supervised learning NLP project involving classification models. The F1 scores is used as evaluation. The best performing model that was found is the Logistic Regression, giving a F1 score of 91.8%. 

### Notebooks
* [Data_Cleaning_EDA.ipynb](Data_Cleaning.ipynb)
* [EDA.ipynb](EDA.ipynb)
* [Pre_processing_2.ipynb](pre_processing_2.ipynb)

### Datasets
The [`Netflix_reddit_submissions.csv`](datasets/Netflix_reddit_submissions.csv) and [`DisneyPlus_reddit_submissions.csv`](datasets/DisneyPlus_reddit_submissions.csv) consists of posts from the respective subreddits.

### Data Dictionary

|Column|Type|Description|
|---|---|---|
|readable_time|datetime|the date and time the post was posted|
|subreddit|integer|boolean, 1 for netflix, 0 for disney+|
|title|object|the title of the post|
|selftext|object|the content of the post|
|text|object|combined title and selftext|
|proc_text|object|processed text|
|proc_text_lem|object|lemmatized processed text|
|char_length|integer|character length of each post|
|word_count|integer|word count of each post|
|day|object|the day the post was posted|
|time|integer|the time the post was posted, 0 to 23|

### Key Data Cleaning Steps
1. Webscraping
2. Remove duplicates
3. Get readable time
3. Assigned binary values to categorize Netflix and Disney+ data

### Illustrations

![Top 30 Unigrams](images/top_30_unigrams.png)

![Top Netflix Words](images/top_words_netflix.png)

![Top DisneyPlus Words](images/top_words_dp.png)

### Pre-processing and Modelling
* Vectorized words using Count Vectorizer and TF-IDF Vectorizer

The models include:
* Logistic Regression
* Naive Bayes Classifier
* Random Forest Classifier
* AdaBoost Classifier

### Evaluation of Models
* F1-score

| Vectorizer  | Model         | F1-score (train)  | F1-score (test)  | Time |
|-------------|---------------|-------------------|------------------|----------|
| Cvec     | Random Forest  (baseline)  | 0.871 |  0.872 | 266.45s |
| TF-IDF   | Random Forest    | 0.920  | 0.895  | 959.11s |
| Cvec     | Naive Bayes      |    0.934   |  0.907 | 58.02s |
| TF-IDF   | Naive Bayes  |    0.948    |  0.902  | 74.26s |
| Cvec     | Logistic Regression      |  0.940    |   0.910  | 11.86s |
| **TF-IDF** | **Logistic Regression** |  0.954 |  **0.918**  | **11.47s** |
| Cvec     | Adaboost    | 0.975 |  0.913 | 77.43s|
| TF-IDF   | Adaboost    | 0.944  | 0.923 | 73.25s |

### Business recommendations

1. **Boost Marketing**

Using the words that we have gotten from the model, we could optimize the 'People also ask' section and optimize image SEO on search engines that could redirect those words from Disney+ to the shows on Netflix. 

2. **Expand Original Productions**

To counter the response from the cancellation of expensive productions, the team can channel the fanbase of these cancelled productions to other productions that have some similarities or by producing new original series or movies. This could be paired with the insights and that we have gotten from the model to also attract viewers from our competitors. This accentuates the brand's uniqueness of producing original titles.

3. **Boost Non-English productions**

Having a bigger diversity or titles and productions from different countries than Disney+, we could push forward the titles of other languages that are associated with the words that we can find from the Disney+, introducing new shows to each user.

### Conclusion

Our goal was to create a robust binary classifier that is able to distinguish between posts associated with Netflix and Disney+.

Our classifier model has yielded impressive results with an F1 score of 0.918. This achievement not only enhances Netflix's ability to attract higher traffic but also augments the quality of content we offer to subscribers, improving user experience.
