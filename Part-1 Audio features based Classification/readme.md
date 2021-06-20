# Audio features analysis

## Predicting perceived moods through analyzing audio features.

- A Kaggle dataset containing audio features (danceability, loudness, speechiness, acousticness, liveness)  of 2000+ top Spotify songs is used to build a model.
- The k-mean clustering method is used to allocate tracks with similar feature values to clusters.
- From the dataset, 5 optimal clusters were formed.
- An SVM model and a confusion matrix is then used to classify the perceived moods that are associated with the different clusters.
- The mood labels used to classify the five different clusters are romantic, nostalgic, artsy, sad, chill (taken from this music mood classification study).

![image](https://user-images.githubusercontent.com/62847225/122662691-92127880-d1b2-11eb-9552-fc060275bd00.png)

