#  Predicting the mood of a song based on its lyrics

## For achieving this aim, I have used Bidirectional LSTMs with GloVe(Global Vectors) embedding for the words in the lyrics. 

The model is basically subdivided into 5 parts - 

1. Data Acquisition - This part of my model was created in order to gather the lyrics of the songs for training purpose. I have used the MoodLyrics Dataset as the ground-truth dataset for my model. It contains a dataframe of 2595 songs, each assigned one particular emotion out  of Angry, happy, sad and relaxed . The dataset however does not contain the lyrics itself. For getting the lyrics of each of the song in the dataset, I used the LyricsGenius library which is built upon the LyricsGenius API. This way I was able to scrape the lyrics of each of the songs.

2. Data Cleaning and Preprocessing - In this step, I worked on cleaning the lyrics I had gotten and transforming it into a format that my classifier would understand more easily as well as remove unwanted noise. So, by using the re and nltk library, I first removed all the punctuations, then all the numbers that appeared in the lyrics, followed by removing the stop words. Stopwords in NLP terms - is a collection of words which add almost no meaning to the context of the corpus. Eg- a, the, at, etc.

3. Creating the corpus and glove embedding of the corpus - In this step, I started out with tokenizing the cleaned up version of the lyrics that I had. Tokenization refers to the process of mapping every unique word to a unique integer(token) and represent the sentence(lyrics here) using the sequence of those tokens. I further used the Keras library for tokenizing and then post pad each lyrics to a constant length of 1000 so that each lyrics would be of a constant length for our classifier to match the input length of our model. 
I have then used the 100d version of the 6 billion embedding version of GloVe to represent each word in each lyrics by a 100 dimensional vector. This finally prepares the input for our model - ( 1000 × 100 ) for each lyrics.

4. Training- Here, I first split my data into training and validation sets - 80 - 20 %. The output column of emotions was one-hot encoded into 4 different columns, something which is a must for any multi-class classification problem. This allows the model to infer that it has 4 different classes to map the input. 
The model that I have created consists of 4 layers. One- the embedding layer. Second - a dropout layer. Third - A Bidirectional LSTM layer consisting of 100 hidden units and Fourth - the Output layer. 
The optimizer that I have used is the Adam classifier. The learning rate was experimentally adjusted to 0.0006 which gave the best results. The loss function used is the - categorical cross- entropy loss function and the metrics we have used is Accuracy. 
Our model upon 20 epochs and 64 batch size gives a training accuracy of 90.64% and a validation accuracy of 84% - which is extremely good given that the paper had talked about the training accuracy of 91%. We are actually very close.

5. Using the model to predict the mood of songs acquired from Spotify - This step is all about using the data we get from the user to make predictions. This will involve a mix of nearly all the steps that were mentioned above. We'll have to get the songs' lyrics, clean that, tokenize the lyrics  and use that to pass into the model and get the desired output which will give us the emotion.

![image](https://user-images.githubusercontent.com/62847225/122662865-fd107f00-d1b3-11eb-9a90-dee58d4b700b.png)


