# Spam_Detection # 

# Dataset Overview
It contains a collection of more than 5 thousand SMS phone messages and Detects Spam Messages.

The first column is a "label" saying whether the given message is a normal message (commonly known as "ham") or "spam". The second column is the "message" itself.


# Exploratory Data Analysis.
- Went over the length of "spam" and "ham" messages.
  - Which revealed "spam messages tend to have more characters".
    
- Looked into "spam" and "ham" messages ratio.
  - Which revealed "There at 13.4 % spam messages and 86.6% ham messages".


# Data Pre-processing. 
- Removing non-alphabetical characters with an empty space with the help of re.sub
- Lower case the messages.
- Removing the stopwords.
- Performing Lemmatization on the messages.
- Appending all the processed Messages to a corpus list.

# TF-IDF Vectorization. 
It helps to down-weight common words while uweighting up rare or more informative words.

- High TF-IDF Score: Indicates that a term is important in a specific document and rare across the entire corpus, making it a strong indicator of the document's content.

- Low TF-IDF Score: Indicates that a term is either too common in many documents or not informative for the document’s content.

# Training Machine learning model {Multinomial Naive Bayes}.
- Splitting dataset into X_dense (dependent variable) means it hold our TF-IDF values for each sentences and y_1 (independent variable or target) means it 0 ("ham" regular message) and 1 ("spam" spam messages).
- Splitting the X_dense and y_1 into test and train.

# Evaluating Model.
- Looking at realistic implementation of this model. We want our model to classify spam messages "spam" such that they land in spam folder and not into regular inbox. On the other hand we want our model to classify regular "ham" messages such that they comes to our normal inbox feed.
- Accuracy
- Precision
- Recall
- F1-score
- Printing Confusion Matrix (OUR POSITIVE HERE IS SPAM MESSAGE)
  - True Positive: Actual spam message -> Model Predicted spam message.
  - True Negative: Actual regular message - > Model Predicted regular message.
  - False Negative: Actual spam message -> Model Predicted regular message.
  - False Positive: Actual regular message -> Model Predicted spam message.

# Hyperparameter Tuning.
- From my Evaluation I was able to notice that my model misses out to classify some spam messages to be "spam" which is why we see a 79% of recall. Which means some of the spam messages are shown as regular messages (ham) and comes to our normal inbox instead of landing into spam folder.

- To improve recall we will do grid_search to find alpha value which handles the zero probabilities.
  
- For Multinomial Naive Bayes:
alpha (Laplace smoothing parameter): A smoothing parameter to handle zero probabilities. Typically, values between 0 and 1 are used.


# FINAL MODEL 
- With help of grid_search I was able to find 0.01 value for alpha. After that I created a new model and printed the metrics.
- Accuracy: 0.979372197309417
- Precision: 0.92
- Recall: 0.9261744966442953
- F1-score: 0.9230769230769231
