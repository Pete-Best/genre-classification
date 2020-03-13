##### Peter Eusebio, Lola Johnston, Brea Beals, Jerry Sha, Roy Xie
##### Winter 2020

#### GitHub repository: https://github.com/Pete-Best/genre-classification
------------------------------------------------------------------------------------------------------------------------------
## Files in the repository:

`DM_Project_Holdout_Predictions.ipynb`: This file uses `lyrics.csv`, with songs, artist, genres, and lyrics. The dataset is sampled, cleaned, and pre-processed just as our original dataset was. We then run our gradient boost model, `gbtune.sav` on the data to explore the predictive nature of our models. 

`Genres_EDA.ipynb`: This notebook details the Exploratory Data Analysis of `songdata.csv`

`Model Evaluation-1.ipynb`:  This notebook evaluates models that were previously developed.

`Models_LJ_Clean.ipynb`: This notebook contains ridge classification modeling

`Models_PE.ipynb`:  This notebook uses logistic regression, random forest, and gradient boosting

`README.md`: The readme file.

`RidgeBalanced.sav`: this is the trained ridge classifier

`balance_DM_Project_Data_Cleaning_Pre_Split_Doc2Vec.ipynb`: Jupyter Notebook file cleaning songdata.csv, extracting features, preparing it for modeling, and balancing on the rock genre label.

`gb_pred_balance.pkl`: these are predictions from gradient boosting on rock balanced X test for evaluation

`gbtune.sav`: this is the tuned gradient boosting classifier

`genre collection.ipynb`: Jupyter Notebook calling Spotify API to search for each artist name from songdata.csv and extract all genre tags corresponding to the first search result for that name

`genres.pkl`: output of genre collection.ipynb, list of genre tags for each artist

`holdoutresponse.pkl`:This pkl contains the response data generated from running `gbtune` on the holdout dataset.

`response_balanced_rock_doc2vec_test.pkl`: The pkl contains the genres of each song in the train set.

`response_balanced_rock_doc2vec_train.pkl`: The pkl contains the genres of each song in the test set.

`response_doc2vec_holdout.pkl`: Response data from the holdout data 

`DM_Project_Holdout_Predictions.ipynb`: this notebook processes the holdout data and evaluates model performance predicting holdout genre with holdout lyrics

`response_doc2vec_train.pkl`: this contains the train genres for a set of songs on an unbalanced dataset

`response_doc2vec_test.pkl`: this contains the test genres for a set of songs on an  unbalanced dataset

`rf_pred_balance.pkl`: this is the output of random forest using rock balanced data

`rfmulti.sav`: this is the trained random forest classifier

`ridge_y_pred.sav`: this is the output of the ridge classifier using rock balanced data

`songdata.csv`: Original data with artist, song name, link, and lyrics for each song  
`veclyrics_balanced_rock_doc2vec_test.pkl`: test array of processed lyrics with rock column balanced

`veclyrics_balanced_rock_doc2vec_train.pkl`: train array of processed lyrics with rock column balanced

`veclyrics_doc2vec_holdout.pkl`: explanatory data from holdout set 

`y_pred_prob_gb.pkl`: probability output from gradient boosting for evaluation notebook

`y_pred_prob_rf.pkl`: probability output from random forest for evaluation notebook

------------------------------------------------------------------------------------------------------------------------------

## Methodology

**Section 1: Pulling Genre Date From Spotify**

Jupyter Notebook calls Spotify API to search for each artist name from songdata.csv and extract all genre tags corresponding to the first search result for that name

**Section 2 EDA**

 * Explored different aspects of the dataset including: 
 * Songs in each genre
 * Top artists in each genre
 * Most frequently used words in each genre
 * Profanity usage in each genre
 * Multi-label artists and single-label artists
 * Sentiment analysis
 
**Section 3: Cleaning and Pre-Processing** 

 * Attempted to mitigate the imbalance in our labels by using random undersampling to bring labels closer to an even split
 * Basic cleaning including deleted all round brackets, square brackets, and text within square brackets, and line breaks
 * Removed non-english songs. Found the probability of a song being English and removed all songs with a probability lower than 0.5
 * Lemmatized and preprocessed the text data using gensim simple_preprocess as well as tokenization
 * Removed stop words from "tokens" using the package stopwords from ntlk
 * Ran a doc2vec model to extract numeric feature from words

**Section 4: Creating Models** 

Models are trained in the following files:
`Models_LJ_Clean.ipynb`
`Models_PE.ipynb`

**Section 5: Comparing and Selecting Model** 

We selected several metrics for model evaluation and created a function that would take our model predictions and run the full suite of evaluations for each. The metrics used are:
 * classification report
 * confusion matrix
 * ROC curve
 * Matthews Correlation Coefficient
 
Some additional metrics we experimented with but did not present include Hamming Loss (for evaluating partially correct predictions in multilabel predictions) and Jaccard Similarity.

**Section 6: Validating on New Dataset** 

 * Downloaded dataset from https://www.kaggle.com/gyani95/380000-lyrics-from-metrolyrics and randomly subsetted 1% of the data for use in running our models and evaluating since the dataset was so large
 * Cleaned, pre-processed, lemmatized and tokenized in the same way the original dataset was prepared
 * This dataset was too messy to run langdetect correctly, so instead we removed all rows containing several different commonly used words in other languages as a way of detecting non-english songs. Explored any remaining row that did not contain the word “the” to confirm
 * Removed all songs with less than 15 words as they were likely to be some form of “instrumental” song with no lyrics. 
 * Removed stopwords and ran doc2vec and continued preparation the same way we did on the original data
 * Ran `gbtune.sav` on the predictors to generate response data `holdoutresponse.pkl` and evaluated the predictions as compared to the true labels
