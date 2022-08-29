** ** Data
11 countries’ text data from 5_domestic_filter_Ngram_stopwords_lemmatize folder.
Countries for training: Canada, US, Singapore, Philippines, New Zealand, Nigeria, Ireland, and Bangladesh.
Countries for testing: Australia, Kenya, United Kingdom.

** ** Processing
• Remove named entities: for the column “article_text_Ngram” in each dataset, applied function “en_core_web_sm” in package spacy to remove named entities such as person’s name, country, places.
• Manually removed more named entities that were not removed from previous steps.
• Remove stop words: applied stopwords.words(‘english’) in package nltk to remove stop words, resulted in a new column “text_no_sw”.
• For each peaceful countries’ data, added a new column named “target”==1, and this column in each non-peaceful data equal to 0.
• Removed single letters and “#” through regular expression.

** ** Training

Peaceful Country	Non-Peaceful Country
Canada	US
Singapore	Philippines
New Zealand	Nigeria
Ireland	Bangladesh

• Classified four country pairs regarding their demographic region similarity.
• For each pair, split data to training and testing set (80/20 ratio).
• Created TF-IDF features for each text in the training dataset.
• Trained three models on the training dataset: Logistic Regression, Random Forest, and XGB
• Combine eight countries’ dataset together and trained the same process.
• Loaded the top 200 features and their importance of each model.
• Compared the performance of the three models and five dataset choices.
• Used trained models to predict Australia, Kenya, United Kingdom, and other single countries’ dataset and compared their performance.

** ** Results
The Canada/US pair showed higher accuracy score for predicting non-peaceful countries’ data, and the New Zealand/ Nigeria pair and Ireland/Bangladesh pair showed higher score for predicting peaceful countries’ data. However, the Singapore/Philippines pair tended to predict each text to be peaceful whether it was from peaceful countries or not. Moreover, the combination of eight countries showed higher score for predicting Australia’s data (accuracy = 0.85 Logistic Regression, accuracy = 0.93 Random Forest) and United Kingdom’s data (accuracy = 0.82 Logistic Regression, accuracy = 0.90 Random Forest). The score for Kenya is lower (accuracy = 0.60 Logistic Regression, accuracy = 0.46 Random Forest). Overall, the five choices for country pairs had higher score for predicting peaceful countries’ data than predicting non-peaceful countries’ data. 

** ** Exploration
Since Random Forest had higher accuracy overall, we chose the top 200 important words and their feature importance of each trained pairs and joined their peaceful level (1 or 0). The Word Cloud showed the appearances of these words.


