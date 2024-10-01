# Tweet-Retweet-Predictor

## Project Overview

This project aims to predict the number of retweets for a given tweet using various machine learning models. By analyzing key features such as text length, time-related factors, and user information, the project identifies which aspects most influence the likelihood of a tweet being retweeted.

## Table of Contents

- [Introduction](#introduction)
- [Feature Selection and Extraction](#feature-selection-and-extraction)
- [Models Used](#models-used)
- [Results](#results)
- [Future Improvements](#future-improvements)

## Introduction

Retweet prediction is important in understanding content engagement on social media platforms. This project explores different models, including gradient boosting, regression trees, random forests, and neural networks, to predict the number of retweets based on various features extracted from the tweet and user data.

## Feature Selection and Extraction

1. **Time-related Features**:  
   - Tweets are categorized by the day of the week and hour of the day. We observed more retweets from 6 AM to 9 PM and fewer from 10 PM to 5 AM.
  
2. **Text Length**:  
   - Tweets were categorized into three length categories:  
     - Short: 0-45 characters  
     - Medium: 45-80 characters  
     - Long: 80+ characters

3. **Followers-Friends Ratio**:  
   - The ratio of followers to friends is a strong predictor of retweets. Z-score normalization was applied to scale this feature.
  
4. **Word Embedding**:  
   - Text was vectorized using the `doc2vec` library and combined with other features such as followers count, friends count, and text length to form the final feature set.

5. **Correlation Matrix and Feature Importance**:  
   - Feature importance was calculated using the Extra Tree Classifier, highlighting that `favorites_count`, `followers_count`, and `friends_count` were the top features influencing retweets.

## Models Used

Five machine learning models were evaluated:

1. **Gradient Boosting**  
   - Sequentially fits decision trees to reduce overall error.
  
2. **Linear Regression**  
   - Used for baseline comparison, but performed the worst among the models.

3. **Regression Trees**  
   - Optimized with a `max_depth` of 8 to prevent overfitting.

4. **Random Forests**  
   - Used a `n_estimators` of 5 for the best performance.

5. **Neural Networks**  
   - A 3-layer neural network (4, 5, and 1 hidden nodes) using ReLU activation was implemented but was computationally expensive.

## Results

The models were compared using **Mean Absolute Error (MAE)** on the training dataset:

| Model             | MAE  |
|-------------------|------|
| Gradient Boosting  | 7.18 |
| Linear Regression  | 10.71|
| Regression Tree    | 7.70 |
| Random Forest      | 7.82 |
| Neural Networks    | 7.61 |

Gradient Boosting had the best performance with the lowest MAE. We selected this model to predict retweets on the evaluation dataset due to its accuracy and reasonable computational time.

## Future Improvements

1. **Increase Vector Size**:  
   - Expanding the vector size for text embeddings using `doc2vec` could improve accuracy.

2. **Hyperparameter Tuning**:  
   - Implement grid search or random search for better hyperparameter tuning of the models.
