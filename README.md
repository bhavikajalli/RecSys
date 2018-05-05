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
I have then calculated the cosine similarity scores(using the user ratings as columns) and obtained the similarities between items’ consumption histories. Now by looking for the closest neighbours, the next movies can be recommended.

Here is a small snapshot of top 10 recommendations for the first five movies according to the recommender.

<a href="url"><img src="https://github.com/bhavikajalli/RecSys/blob/master/images/recommendations_10.png" align="center" width="760" ></a>

### User Based Collaborative Filtering

SImilarly as above, I have next calculated the user similarity. the method I have used is pairwise cosine distances with the user ratings as rows.

### Evaluation 
By considering the top k users who are most similar to the input user, we can predict that a user's rating for item i is given by the weighted sum of the top k user's ratings for item i where the weighting is the cosine similarity between the each user and the input user u.
I have then used RMSE(root-mean-square error) to calculate the mean-squared error between the actual user ratings and the predicted user ratings. The RMSE was 6.51. This low value could be because the ratings matrix is very sparse. The users have not always rated a movie that they have seen.

Since, real world data is sparse in nature. I now plan to use a Model based method using SVD to perform Collaborative filtering. 


