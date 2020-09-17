# Recommendation-System

***Recommendation System***

I wanted too see if I could extract meaningful results out of the Movielens 100k dataset. For the first iteration I used a colloborative filtering approach and built a KNN model that would recommend 10 movies based on the ratings of the 10 closest movies. Although this method gave decent results, the recommendations are based purely off distance in the user-movie similarity matrix and this approach doesn't work well for large datasets and for datasets with lots of missing values. 

To overcome these issues during the second iteration I used a content based approach powered by singular value decomposition  or SVD for short. Using the SVD approach its possible to a user profile for each user in the dataset and compare it against user profiles to determine user preferences which is more robust than a distance based approach. SVD uses matrix factorization which breaks down N items into K factors. For example, the reduction 25000 movies into 64 latent factors where each factor is a linear combination of movies that can be assigned to a user’s profile. A factor can mean something such as “Action movies with Tom Cruise” and another might be “Movies that have a sequel”. The key is that recommending based on factors is more reliable than just using movie similarities, maybe a user hasn’t seen “The Hangover” but the user might have seen other movies that are related to “The Hangover” via other factors and those can be used in the recommendation process. These factors are always there in our data but they aren’t discovered until we start reducing which is when they start to emerge and hence the “latency”. Using this method I was able to create a recommender whose results are more catered towards the user and can also predict ratings for the recommendations.

Ex: Recommendations for user 610

First lets take a look at user 610's current preferences for movies

![User 610 Ratings](https://github.com/aayush4249/Recommendation-System/blob/master/Images/Ratings.jpg)


We get the idea that they enjoy genre's such as comedies, children's movies, etc.
Now lets have the recommendation system predict movies and their forecasted ratings.


![Recommender results](https://github.com/aayush4249/Recommendation-System/blob/master/Images/Predictions.jpg)


Interesting results, lets take a deeper dive and compare one of the predictions against the user's preferences.

![Comparison](https://github.com/aayush4249/Recommendation-System/blob/master/Images/Similarity.jpg)

So here we can see that the recommended movie Wallace & Gromit: The Wrong Trousers has the children and comedy genres associated with it, both of which the user enjoys. This tells us that the SVD model recognizes the children and comedy tags as factors and uses them in the recommendation process.
