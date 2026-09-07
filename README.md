# Sentiment Analysis of Twitter Data

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge\&logo=python\&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/pandas-150458?style=for-the-badge\&logo=pandas\&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge\&logo=scikit-learn\&logoColor=white)
![NLTK](https://img.shields.io/badge/NLTK-306998?style=for-the-badge\&logo=nltk\&logoColor=white)

## Project Overview

This project implements a machine learning-based sentiment analysis system for Twitter data. The system analyzes the textual content of tweets and classifies them into **negative** or **positive** sentiment categories.

The project uses the **Sentiment140 dataset**, containing approximately 1.6 million tweets, to train and evaluate a Decision Tree classification model. Natural Language Processing (NLP) techniques are applied to clean and transform the raw tweet text before converting it into numerical features using **TF-IDF**.

The trained model can then be used to predict the sentiment of new, unseen tweets.

## Dataset

The project uses the **Sentiment140 dataset**, which contains 1.6 million tweets collected from Twitter.

Each record contains information such as:

* Sentiment label
* Tweet ID
* Tweet date
* Query
* User
* Tweet text

For this project, the **tweet text** and **sentiment label** are primarily used. The original sentiment labels are `0` for negative and `4` for positive, with the positive label converted to `2` during preprocessing.

## Key Steps

### 1. Data Loading

The dataset is loaded into a Pandas DataFrame. The required columns are selected and the data is inspected for missing or invalid values.

### 2. Data Preprocessing

Raw tweets contain URLs, usernames, punctuation, numbers, and other unnecessary elements. The text is cleaned using several NLP techniques:

* Handling missing values
* Converting text to lowercase
* Removing non-alphabetic characters
* Tokenizing text
* Removing English stopwords
* Applying stemming using the **Porter Stemmer**

These steps help reduce noise and prepare the tweets for machine learning.

### 3. Feature Extraction

Machine learning models cannot directly process raw text. The cleaned tweets are converted into numerical feature vectors using **TF-IDF (Term Frequency-Inverse Document Frequency)**.

TF-IDF assigns higher importance to words that are relevant to individual tweets while reducing the importance of very common words.

### 4. Model Training

A **Decision Tree Classifier** from Scikit-learn is trained using the TF-IDF feature vectors and corresponding sentiment labels.

The dataset is divided into training and testing sets to evaluate how well the model performs on unseen data.

### 5. Model Evaluation

The trained model is evaluated using accuracy scores on both the training and test datasets. This helps measure the model's learning performance and its ability to generalize to new tweets.

### 6. Model Persistence

The trained Decision Tree model and TF-IDF vectorizer are saved using Python's `pickle` module.

This allows the trained components to be loaded later without retraining the model from scratch.

### 7. Sentiment Prediction

After loading the saved model and vectorizer, users can provide new tweets as input. The tweet is processed using the same preprocessing pipeline and passed to the trained model to predict whether the sentiment is **positive** or **negative**.

## Technologies Used

* **Python** – Core programming language
* **Pandas** – Data loading and manipulation
* **NumPy** – Numerical operations
* **NLTK** – Natural Language Processing and text preprocessing
* **Scikit-learn** – TF-IDF feature extraction and machine learning
* **Pickle** – Model and vectorizer persistence

## Project Workflow

```text
Twitter Dataset
      ↓
Data Loading
      ↓
Data Cleaning
      ↓
Text Preprocessing
      ↓
Tokenization + Stopword Removal
      ↓
Stemming
      ↓
TF-IDF Feature Extraction
      ↓
Train/Test Split
      ↓
Decision Tree Classifier
      ↓
Model Evaluation
      ↓
Save Model & Vectorizer
      ↓
Predict Sentiment of New Tweets
```

## Example

**Input:**

```text
"I absolutely love this product! It is amazing."
```

**Predicted Sentiment:**

```text
Positive
```

**Input:**

```text
"This is the worst experience I have ever had."
```

**Predicted Sentiment:**

```text
Negative
```

## Applications

This type of sentiment analysis system can be used for:

* Monitoring customer opinions
* Analyzing social media trends
* Brand reputation analysis
* Product and service feedback
* Customer experience analysis
* Social media opinion mining

## Future Improvements

The project can be further improved by:

* Experimenting with Logistic Regression, SVM, Random Forest, or deep learning models
* Using word embeddings such as Word2Vec or GloVe
* Applying advanced NLP models such as BERT
* Improving tweet-specific preprocessing
* Adding precision, recall, and F1-score evaluation
* Developing a web interface for real-time sentiment prediction

## Conclusion

This project demonstrates a complete NLP and machine learning pipeline, starting from raw Twitter data and ending with sentiment prediction. It provides practical experience with text preprocessing, TF-IDF feature extraction, model training, evaluation, and model persistence using Python.
