# AI_and_ML_Course

## AI and machine learning course final portfolio project

## Introduction
The purpose of this project is to create a model that can predict type of a sensor within a Building Management control System (BMS) based on the shorthand name given to that point in the BMS.  This is a multi-class text classification problem where the predictors will be elements of text from within the datapoint name.  This can include both shorthand text and acronyms.  This is primarily for the use of VitalView and similar BMS analytics systems where a user must manually set the sensor type during setup and commissioning.  The main goal is to reduce amount of manual input required during setup and commissioning and to reduce associated human error. 

## Data
The original dataset was obtained from Vital Energi's VitalView system. This is a live system used to assess the performance building Management Systems (BMS) and the heating, ventilation, and air conditioning systems they control. It contains customer specific contract and building names.  The initial code in the notebook removes any customer or contract specific details to anonymise the dataset.  Only the redacted dataset has been provided with this code.
During the development it was noted that the original dataset has a large imbalance in sample numbers between categories.  Several approaches have been used to account for this, however it is recommended that further samples for the minority categories be exported from VitalView prior to further modelling.

## Model
I initially started with a Random Forest (RF) model using a custom tokenizer with a custom dictionary to extract useful information from the 'datapoint' category into a Bag-Of-Words.  This had limited success due to the imbalance in the original dataset, after further testing I moved to Support Vector Machines (SVM) model and replaced the BoW with binary vectors again based on the custom dictionary.

## Hyperparameter Optimisation
Hyperparameters for the initial RF and final SVM models were optimised using a simple grid search.  For the RF I focused on the number of estimators, max-depth, minimum samples per split, and minimum samples per leaf using the following grid:
'n_estimators': [20, 40, 80, 100, 200]
'max_depth': [None, 2, 5, 10, 20]
'min_samples_split': [5, 10, 20, 30]
'min_samples_leaf': [5, 10, 20, 30, 40, 50]
For the SVM I used the regularisation parameter 'C' and linear and rbf kernal types:
'C': [0.1, 1, 10]
'kernel': ['linear', 'rbf']

## Results
The initial RF was affected by the imbalance in the original dataset achieving a prediction accuracy of 31%.
I tried oversampling the balance the dataset and re-trained the same model, this produced improved accuracy of 62%, however when looking at the performance per category it was clear that the oversampled minority categories were overfitting, and the remaining categories performed poorly, so the overall accuracy was not representative of the actual performance.
I also tried to retrain the model using the majority categories only, this provided a marginal improvement on the original model with accuracy of 37.8%
The fourth RF model used the binary vector tokenizer instead of the BoW with a dedicated training set created from a fixed number of 50 samples randomly selected from each category.  This produced much better results with overall accuracy of 60.1% and reduced overfitting some of the minority classes.
The final SVM model reused the same binary tokenizer but achieved and accuracy of 87.8%.  This is largely as SVM are better at dealing with spare binary vectors.
