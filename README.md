# Recommendation System: Demographic Filtering
Offers users with similar demographic background the similar movies that are popular and well-rated regardless of the genre or any other factors. Therefore, since it does not consider the individual taste of each person, it provides a simple result but easy to be implemented.

As we understood, demographic filtering is one of the simplest Recommender System that only offers the users the best rated and most popular movies. However, although it might be simple, we still need the appropriate formula to calculate the best rated movies because some movies have 9.0 rating but only have 5 votes, so it is not fair for the rest of the movies that are rated slightly lower but with much more votes.

The best formula to calculate movie rating is provided by IMDB, which is articulated clearly here. It basically taking number of votes, minimum number of votes required to be considered, mean of votes, and average rating into account and ended up with a formula as follow:

![image](https://user-images.githubusercontent.com/86812576/172283374-4c7d03e7-d892-4a80-becf-faad6e7186b6.png)

Where:

- W = Weighted Rating
- v = number of votes for the movie
- m = minimum number of votes necessary to be considered
- R = average number of the movie’s rating
- C = the mean vote from overall data

Therefore, we need to determine each of those elements in order to obtain W. Number of votes (v) and average number of votes (R) have already been provided in the dataset, therefore, we do not need to calculate further for those variables. Next, we need to find out C, which is the mean of the overall votes that can be determined through the following function:

# Import Package
- import **pandas as pd**

# Import Dataset
The data used is movie data. The data consists of 45130 rows and 26 columns.

# Simple Demographic Filtering: Filter -> Score -> Sort
# Step 1: Filter
Here I will add a filter, to make it a little more focused, because if no filtering is done, the recommendation results will be a little messy, and assign it to a new variable.

![Screenshot 2022-06-07 100628](https://user-images.githubusercontent.com/86812576/172287165-c7c4e28c-b681-4f15-a80b-1e4b00b13836.png)

Where, I only filtered against the 'Animation' genre with movie durations between 60 to 150 minutes which aired between 2000 and 2019, and brought up the 20 best movies.

# Step 2: Score
I just use 'vote_average' as score.

# Step 3: Sort
In this step what is done is only sorting by 'vote_average' (score). And I only show the important columns, starting from 'title', 'genres', 'runtime', 'vote_average', 'vote_count', and 'release_year' to make it easier to read.

![Screenshot 2022-06-07 102957](https://user-images.githubusercontent.com/86812576/172289766-ab22733a-b87f-4b18-826e-954861aef1e6.png)


# Improve with IMDB's formula as Scoring
Now I will improve the scoring by using the formula created by IMDB to calculate movie rating. Why is this done? if we look at the results of the movie recommendations, then there are several movies that get high ratings, but only 5 people voted. The formula is as described above.

The result of using IMDB formula is as follows.

![Screenshot 2022-06-07 105329](https://user-images.githubusercontent.com/86812576/172292489-9f450a12-1fdd-4102-b836-b462a6dc657b.png)

Can be seen in the table above, that the results are more focused. The 'vote_count' is already more, the 'vote_average' is not very high, and everything looks reliable. This is what demographics recommend.
