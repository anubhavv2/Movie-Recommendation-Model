# Movie-Recommendation-Model

## Objective
This project aims to build a movie recommendation system that suggests movies based on user input. The system utilizes similarity scores to match user preferences with the closest movies in the dataset.

## Recommendation System
The recommendation system is based on calculating similarity scores between movies. It matches the user input with the closest movie title and recommends similar movies based on these scores.

## Steps

### Import Libraries

pandas, 
 numpy, 
 matplotlib.pyplot,
  seaborn,
 imblearn,


### Import Dataset

### 4. Feature Selection
Selecting five features for movie recommendation.
'Movie_Genre','Movie_Keywords','Movie_Tagline','Movie_Cast','Movie_Director'


### Feature Engineering
Combining selected features into a single feature text.


### 6. Text Conversion to Tokens
Using TF-IDF Vectorizer to convert text features into tokens.

### 7. Similarity Score Calculation
Using cosine similarity to calculate similarity scores between movies.

### 8. Movie Recommendation
Getting movie name input from the user and finding close matches.
```python
import difflib
fav_movie_name = input('Enter your favourite movie name: ')
all_movies_title_list = df['Movie_Title'].tolist()
Movie_recom = difflib.get_close_matches(fav_movie_name, all_movies_title_list)
close_match = Movie_recom[0]
index_of_close_match_movie = df[df.Movie_Title == close_match]['Movie_ID'].values[0]
recom_score = list(enumerate(similarity_score[index_of_close_match_movie]))
```

### 9. Sorting Movies Based on Recommendation Score
```python
sorted_similar_movies = sorted(recom_score, key=lambda x: x[1], reverse=True)
print('Top 30 Movies Suggested for you : \n')
i = 1
for movie in sorted_similar_movies:
    index = movie[0]
    title_from_index = df[df.index == index]['Movie_Title'].values[0]
    if i < 31:
        print(i, '.', title_from_index)
        i += 1
```

### 10. Top 10 Movie Recommendations
```python
movie_name = input('Enter your favourite movie name: ')
list_of_all_titles = df['Movie_Title'].tolist()
find_close_match = difflib.get_close_matches(movie_name, list_of_all_titles)
close_match = find_close_match[0]
index_of_movie = df[df.Movie_Title == close_match]['Movie_ID'].values[0]
recom_score = list(enumerate(similarity_score[index_of_movie]))
sorted_similar_movies = sorted(recom_score, key=lambda x: x[1], reverse=True)

print('Top 10 Movies Suggested for you : \n')
i = 1
for movie in sorted_similar_movies:
    index = movie[0]
    title_from_index = df[df.index == index]['Movie_Title'].values[0]
    if i < 11:
        print(i, '.', title_from_index)
        i += 1
```

## Conclusion
The model provides movie recommendations based on the closest match to the user's favorite movie, using a combination of genres, keywords, taglines, cast, and director information.
