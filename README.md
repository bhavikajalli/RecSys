# RecSys
Collaborative Filtering using the Movie Lens 1 MB dataset
- Item Based Collaborative Filtering
- User Based Collaborative Filtering

### Dataset
I am using the MovieLens 100k Dataset at https://grouplens.org/datasets/movielens/100k/. Please read the README for details.
I have created three dataframes from the dataset. The Ratings dataframe contains the users and their ratings for the movies. The users dataframe contains user demographic information and the Movies dataframe contains the item descriptions.

### Content Based Reommendation
Using the Movies dataframe I will calculate which movie is the closest to the others.(Still needs to be implemented)

### Item Based Collaborative Filtering
In item based collaborative filtering similarities between items are calculated from rating-matrix. And based upon these similarities, user’s preference for an item not rated by him/her is calculated. I have used the Ratings dataframe and pivoted in the following way.
```
movies_train = ratings_train.pivot(index='user_id', columns='movie_id', values='rating')
```
I have then calculated the cosine similarity scores and obtained the similarities between items’ consumption histories. Now by looking for the closest neighbours, the next movies can be recommended.

Here is a small snapshot of top 10 recommendations for the first five movies according to the recommender.

<a href="url"><img src="https://github.com/bhavikajalli/RecSys/blob/master/images/recommendations_10.png" align="center" width="640" ></a>

### User Based Collaborative Filtering
