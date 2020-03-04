


##### A FINAL PROJECT SUBMITTED TO THE UNIVERSITY OF CHICAGO IN PARTIAL FULFILLMENT OF THE REQUIREMENTS FOR THE COURSE OF MSCA 31008.3 DATA MINING PRINCIPLES

##### Peter Eusebio, Lola Johnston, Brea Beals, Jerry Sha, Roy Xie
##### Winter 2020

#### GitHub private repository: https://github.com/Pete-Best/genre-classification


## 1. Executive summary

## 2. Files in the repository

`README.md`: The readme file.

`DM_Project_Data_Cleaning.ipynb`: Jupyter Notebook file cleaning songdata.csv, extracting features, and preparing it for modeling  

`songdata.csv`: Original data with artist, song name, link, and lyrics for each song  

`genre collection.ipynb`: Jupyter Notebook pulling genres from spotify INSERT PETER'S DESCRIPTION 

`genres.pkl`:

`songs_wv_model`:


FINISH THIS LATER

## 3. Metadata for (INSERT FINAL FILE NAME HERE):
 - artist: Artist name
 - song: Name of song
 - link: Link to a webpage with the song (for reference). This is to be concatenated with http://www.lyricsfreak.com to form a real URL.
 - text: Lyrics of song (Songs with a probability of being non-english lower than 0.50  have been removed. Text within square brackets have been removed and line breaks have been removed)
 - genres: Genre of artist as pulled from Spotify
 - rock: Does the genre list contain the substring: “rock”?  (0 if the substring is not present in genre, 1 if it present)
 - singer-songwriter: Does the genre list contain the substring: “singer-songwriter”? (0 if the substring is not present in genre, 1 if it present)
 - pop: Does the genre list contain the substring: “pop”? (0 if the substring is not present in genre, 1 if it present)
 - metal: Does the genre list contain the substring: “metal”? (0 if the substring is not present in genre, 1 if it present)
 - folk: Does the genre list contain the substring: “folk”? (0 if the substring is not present in genre, 1 if it present)
 - country: Does the genre list contain the substring: “country”? (0 if the substring is not present in genre, 1 if it present)
 - hip hop/rap: Does the genre list contain the substring: “hip hop” or "rap"? (0 if the substring is not present in genre, 1 if it present)
 - text_preprocessed: Text has been lemmatized and preprocessed (different inflected forms of a word grouped together, lowercased)
 - tokens: Tokenized version of text_preprocessed with stop-word removed (Stop-words taken from nltk stopwords.words('english'))
 - stem_str: Un-tokenized version of stem_str
 

## 4. Methodology

**Section 4.1: Pulling Genre Date From Spotify**

**Section 4.2: Cleaning and Pre-Processing** 

1. Deleted all round brackets, square brackets, and text within square brackets, and line breaks
2. Removed non-english songs. Found the probability of a song being English and removed all songs with a probability lower than 0.5
3. Lemmatized and preprocessed the text data using gensim simple_preprocess and saved under "text_preprocessed"
4. Tokenized the data and saved under "tokens"
5. Removed stop words from "tokens" using the package stopwords from ntlk
6. Ran a word2vec model to explore relationships between words
7. Applied Count Vectorizer() to transform "tokens" into vectors

**Section 4.2: Creating Models** 

**Section 4.3: Comparing and Selecting Model** 

**Section 4.3: Validating on New Dataset** 



