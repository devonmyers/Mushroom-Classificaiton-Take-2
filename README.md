# Mushroom-Classificaiton-Take-2

A secondary exploration into classification of mushrooms as poisonous or edible based on the UCI mushroom dataset.  This attempt explores four different types of classification, namely decision trees, multinomial naive Bayes, categorical naive Bayes, and K-nearest neighbors.  Moreover, we also explore imposing different topological structures onto the mushroom dataset to convert the nominal features to numeric data and the effect of the differnt topological structures therein.  
First, the two different topological structures imposed on the dataset are sklearn's LabelEncoder class, and then binary dummy variables.  The LabelEncoder class takes a nominal variable with C categories and converts each categorical entry for that varaible to an integer between 0 and C-1.  On the other hand, binary dummy variables takes a nominal variable with C categories and creates C-1 binary variables (possible values are 0 when that category is absent and 1 when it is present) where each of the newly created variables correspond to one category of the original nominal variable.  For purely nominal variables, the LabelEncoder class makes less sense intuitively.  This is because LabelEncoder makes the dataset have charactersitcs of an ordinal variable.  Thus, the a priori expectation is that models trained on dummy variables would have better classification performance.
Eight models in total were trained in this experiment,  One for each of the four classificaiton methods for LabelEncoder data, and one for the four classificaiton methods for dummy variable data.  Model performance was evaluated by computing the F1 score and model testing was done by using 5-fold cross validation. Note that F1 score is akin to measuring accuracy of the model and is a float between 0.0 (worst performance) and 1.0 (best performance).  For both forms of naive Bayes, models had better performance on dummy variable data, but had F1 scores below 0.96.  The decision trees models had equally good performance on both forms of data, with an F1 score of 0.9998 in each case.  The K-nearest neighbors model had a perfect F1 score of 1.0 for dummy variable data, and had an F1 score of 0.9944 on LabelEncoder data.  
So, the best performing model is the K-nearest negihbors model using dummy variable data.  Generalization of this model was estimated by using a previously held-out validation set and computing the F1 score of the model when the validation data was presented to the model.  This F1 score was again a perfect 1.0, which is an indicator that K-nearest neighbors might be the best model for predicting the edibility of mushrooms.
