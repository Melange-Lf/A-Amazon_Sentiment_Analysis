# Amazon_Sentiment_Analysis

This project was made with purpose of getting familar with word embeddings and natural language processing using rnn based architecture...

The model is an RNN utilizing LSTM cells, trained on a dataset containing  650000 amazon product reviews and their rescpective star scores.  
The Dataset is completely balanced with regards to each star score

Note: while the model will be trained to predict the star score for an input review, we can still use it for sentiment analysis.

For sentiment analysis to one three states (negative/neutral/positive), we can overwrite the predict method of the model as follows:

analysis which node of the softmax layer has the highest probabilty-  
- 1: negative sentiment
- 3: netrual sentiment
- 5: postive sentiment
- 2: GOTO max(1, 3)*
- 4: GOTO max(3, 5)*

    * In case of intermediate score values like 2 and 4, the model looks at the softmax probabilites of the adjacent sentiment scores,  
    depending on which adjacent score is higher, it assigns sentiment accordingly.

The model outputs a score between positive/neutral/negative.

Dataset taken from:  https://drive.google.com/drive/folders/0Bz8a_Dbh9Qhbfll6bVpmNUtUcFdjYmF2SEpmZUZUcVNiMUw1TWN6RDV3a0JHT3kxLVhVR2M?resourcekey=0-TLwzfR2O-D2aPitmn5o9VQ  
Embeddings taken from: https://nlp.stanford.edu/projects/glove/

## Files/Folders

The project contains the following files/folders:

- `Senti.ipynb`: Contains the entire pipeline of the project
- `senti_saved_non_bi`: Contains the trained model to be loaded with `tf.keras.models.load_model('senti_saved_non_bi')`
- `logs_bi`: Contains the logs while training the model on the dataset
- `requirements.txt`: Dependencies to be installed for running the scripts
- `Word_Vec`: Contains the Embeddings used in the model
- `amazon_review_full_csv`: Contains the dataset which was used to train and test the model

## Prerequisites

The required libaries can be installed using the requirements file

Currenlty the Prerequisites include:

- Numpy
- scipy
- ipython


```bash
pip install -r requirements.txt
```

## Usage

For now, the entire pipeline is available in `Senti.ipynb`  
The notebook itself is devided into the following points:  
- Imports
- Word Embeddings loading
- Preprocessing input data
- Model creation
- Model Analysis
- Predictions on custom inputs


The pipeline isn't farctured into seperate components so as to make it easier to understand the entire process.  
In the future, the script can be divided into smaller files:  
- utility functions
- model definition
- loading embeddings and dataset
- training and saving model
- model analysis
