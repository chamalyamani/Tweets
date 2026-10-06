# Tweets — Sentiment Analysis

## Description

This project is an introduction to Natural Language Processing (NLP) through sentiment analysis of tweets.

The objective is to classify tweets into three sentiment classes:

- Negative
- Neutral
- Positive

The project explores different text preprocessing techniques, text vectorization methods, similarity analysis, and machine learning algorithms.

## Project Objectives

The project covers:

- Data preparation and preprocessing
- 18 different preprocessing approaches
- Text vectorization using:
  - Count Bag-of-Words
  - Binary Bag-of-Words
  - TF-IDF
- Cosine similarity to find the top-10 most similar tweet pairs
- Sentiment classification using different machine learning algorithms
- Hyperparameter optimization with GridSearchCV
- Model evaluation using Accuracy, AUC and Macro F1-score
- Word2Vec text vectorization as a bonus

## Dataset

The dataset contains 3,865 tweets divided into three sentiment classes:

- Negative
- Neutral
- Positive

The dataset is split into:

- 80% training data
- 20% test data

The split is stratified to preserve the distribution of the sentiment classes.

## Preprocessing

18 versions of the dataset are generated using different combinations of:

- Lowercasing
- Punctuation removal
- Stopword removal
- Stemming
- Lemmatization
- Bigrams
- Trigrams

The resulting datasets are stored in:

`Data/preprocessed_data/`

## Text Vectorization

Three main vectorization approaches are evaluated:

### Count Bag-of-Words

Represents each tweet using the number of occurrences of each word.

### Binary Bag-of-Words

Represents whether a word is present or absent in a tweet.

### TF-IDF

Weights words according to their importance within the dataset.

## Cosine Similarity

Cosine similarity is used to identify the top-10 most similar tweet pairs.

The analysis is performed for all 18 preprocessing datasets and for the three vectorization methods.

## Machine Learning

Three classification algorithms are evaluated:

- Logistic Regression
- Linear SVM
- Multinomial Naive Bayes

GridSearchCV with 5-fold cross-validation is used to select the best hyperparameters.

## Results

The best configurations obtained on the test dataset are:

| Algorithm | Dataset | Vectorization | Hyperparameter | Accuracy | AUC | Macro F1 |
|---|---|---|---|---:|---:|---:|
| Logistic Regression | D1 | Binary BOW | C = 1.0 | 0.909444 | 0.978937 | 0.907302 |
| Linear SVM | D10 | Binary BOW | C = 0.1 | 0.906856 | 0.978091 | 0.905396 |
| Naive Bayes | D8 | TF-IDF | alpha = 2.0 | 0.895213 | 0.975582 | 0.891044 |

The best overall configuration is **Logistic Regression with D1 Binary BOW**, achieving an accuracy of **0.909444** and an AUC of **0.978937**.

## Bonus — Word2Vec

Word2Vec is used as an alternative text representation.

The Word2Vec model is trained on the training data and combined with Logistic Regression.

Current results:

| Metric | Score |
|---|---:|
| Best C | 100 |
| Accuracy | 0.829237 |
| AUC | 0.935146 |
| Macro F1 | 0.825668 |

## Project Structure

```text
Tweets/
├── Data/
│   ├── processedNegative.csv
│   ├── processedPositive.csv
│   ├── processedNeutral.csv
│   └── preprocessed_data/
│       ├── D1_Original.csv
│       ├── ...
│       └── D18_*.csv
├── notebooks/
│   └── tweets.ipynb
├── .gitignore
├── README.md
└── requirements.txt

```
## Installation
Clone the repository and create a virtual environment:
- git clone <repository-url>
- cd Tweets

Create and activate the virtual environment:
- python3 -m venv venv
- source venv/bin/activate

Install the dependencies:
- pip install -r requirements.txt

## Running the Project
Start Jupyter Notebook:
- jupyter notebook
Then open:
- notebooks/tweets.ipynb
Run the notebook cells in order.

## Technologies

- Python
- Pandas
- NumPy
- NLTK
- Scikit-learn
- Gensim
- Matplotlib
- Jupyter Notebook
