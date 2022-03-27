# PhazeRo-Interview-Solutions

#   SENTIMENT ANALYSIS USING NAIVE BAYES


## STAGES INVOLVED :

* Loading DataSet
Preprocessing
Feature Engineering
Model selection 
Tuning and Validation
Metrics

Loading Dataset :

  We are using the IMDB dataset which contains reviews on movies and corresponding  sentiment either in positive or negative. 

Reviews :    (str) Data
Sentiment : (str) Target

Preprocessing :

Initially to process the data we load  the data from respective folders which is encoded in utf8
Using the function get_data() which loads all data to the list and adds 1 for positive label and 0 for negative label data for every review record.
In Order to process the given sentence we need to preprocess certain special characters which add redundancy to the text using the function clean_text() .
We use regular expressions to filter out  the special characters and numerical data to clean the text.


Feature Engineering :

The  data containing the text is then splitted word by word and for every unique word a unique id which is the length of the dictionary is assigned for achieving the n-dimensions of the given corpus for building the feature matrix . This functionality is achieved for train and test data and the final dictionary of all unique words in the corpus are stored as key-value pairs using get_matrix_of_x(). The  dictionary is used for creating a feature matrix with the number of rows the same as the train and test data and the dimensions with the number of unique words in the corpus dictionary. The terms count are then updated for every word occurrence in that particular review . This technique in traditional machine learning is called Bag-of-Words.


Model Selection :

For training the feature matrix with the matrix data as X with n-dimensions where n is the number of unique word-counts . For training we are using the Multinomial Naive Bayes algorithm from sklearn package. The formulation of Multinomial NaiveBayes can be driven as 


The multinomial naive Bayes classifier becomes a linear classifier when expressed in log-space


Where   and  ….(source : wikipedia)

Tuning and Validation:

Since the Multinomial NaiveBayes has a tunable parameter alpha which initially is set to 1 . We select a range of five values from 0.01 to 10 with a multiplicative step size of 10.
For every parameter selection the model is initialized and is validated using k-fold cross validation with k=10 . At the end of every validation , the mean accuracy percentage is calculated and stored. Finally we select the model with the maximum mean average accuracy for final training of the data.

Metrics:

Finally the accuracy is calculated using the best config from the validated data. We calculate the accuracy by comparing the predicted values with the ground truth.







