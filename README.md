**Data**

11 countries’ text data from 5_domestic_filter_Ngram_stopwords_lemmatize folder.
Countries for training: Canada, US, Singapore, Philippines, New Zealand, Nigeria, Ireland, and Bangladesh.
Countries for testing: Australia, Kenya, United Kingdom.

**Processing**

• Remove named entities: for the column “article_text_Ngram” in each dataset, applied function “en_core_web_sm” in package spacy to remove named entities such as person’s name, country, places.
• Manually removed more named entities that were not removed from previous steps.
• Remove stop words: applied stopwords.words(‘english’) in package nltk to remove stop words, resulted in a new column “text_no_sw”.
• For each peaceful countries’ data, added a new column named “target”==1, and this column in each non-peaceful data equal to 0.
• Removed single letters and “#” through regular expression.

**Training**

<img width="746" alt="Screen Shot 2022-08-29 at 11 42 38 AM" src="https://user-images.githubusercontent.com/91220978/187240330-f749ea44-1dbd-408a-b360-c12f189e3f3f.png">


• Classified four country pairs regarding their demographic region similarity.
• For each pair, split data to training and testing set (80/20 ratio).
• Created TF-IDF features for each text in the training dataset.
• Trained three models on the training dataset: Logistic Regression, Random Forest, and XGB
-	Logistic Regression: Logistic function to classify the dependent variable (peace level)
-	Random Forest: Bagging (ensemble) of Decision Trees to predict the average of Decision Tress and minimize the variance and overfitting. The feature importance is the decrease in node impurity weighted by the probability of reaching that node.
-	XGB: Extreme Gradient Boosting of Decision Trees with iteration through residuals of previous model to minimize bias and underfitting
![image](https://user-images.githubusercontent.com/91220978/188536096-e9ef9f8e-43e2-4f50-b209-3b6d81d985a0.png)

• Combine eight countries’ dataset together and trained the same process.
• Loaded the top 200 features and their importance of each model.
• Compared the performance of the three models and five dataset choices.
• Used trained models to predict Australia, Kenya, United Kingdom, and other single countries’ dataset and compared their performance.

**Results**

The Canada/US pair showed higher accuracy score for predicting non-peaceful countries’ data, and the New Zealand/ Nigeria pair and Ireland/Bangladesh pair showed higher score for predicting peaceful countries’ data. However, the Singapore/Philippines pair tended to predict each text to be peaceful whether it was from peaceful countries or not. Moreover, the combination of eight countries showed higher score for predicting Australia’s data (accuracy = 0.85 Logistic Regression, accuracy = 0.93 Random Forest) and United Kingdom’s data (accuracy = 0.82 Logistic Regression, accuracy = 0.90 Random Forest). The score for Kenya is lower (accuracy = 0.60 Logistic Regression, accuracy = 0.46 Random Forest). Overall, the five choices for country pairs had higher score for predicting peaceful countries’ data than predicting non-peaceful countries’ data. 

**Exploration**

Since Random Forest had higher accuracy overall, we chose the top 200 important words and their feature importance of each trained pairs and joined their peaceful level (1 or 0). The Word Cloud showed the appearances of these words.

<img width="745" alt="Screen Shot 2022-08-29 at 11 45 51 AM" src="https://user-images.githubusercontent.com/91220978/187241023-dbb02da2-8691-4e5a-88f4-c6af350b6643.png">

<img width="742" alt="Screen Shot 2022-08-29 at 11 46 46 AM" src="https://user-images.githubusercontent.com/91220978/187241200-b8e317ab-3cba-4044-bca8-74e62bfd1b5d.png">

The following two WordCLouds are from the training process of eight countries toghther.

<img width="847" alt="Screen Shot 2022-09-07 at 3 22 54 PM" src="https://user-images.githubusercontent.com/91220978/188960332-9abc7648-88f3-4e59-9d94-1f449fa48e0a.png">

<img width="841" alt="Screen Shot 2022-09-07 at 3 23 13 PM" src="https://user-images.githubusercontent.com/91220978/188960385-ff940400-a23b-482a-8e4b-f5ba0def1e7f.png">


