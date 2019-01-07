# Movie Recommendation System Using Graph Database neo4j 
###Final Project for CSCI E-89 Deep Learning Harvard University 

# Problem Statement:  
The goal is to develop the model which will allow us to find movie recommendation based on user’s previous experience. I’ll use neo4J graph database as a tool. I will use 2 datasets: MovieLens, which contains ratings and tag applications applied toward movies by users, and TMDB 5000 Movie Dataset, which contains, among other, credits data for movies.

# Dataset Description: 

1.	MovieLens (Small) contains 100,000 ratings and 3,600 tag applications applied to 9,000 movies by 600 users. Last updated 9/2018. Size: 1 MB.
https://grouplens.org/datasets/movielens/
2.	TMDB 5000 Movie Dataset contains 2 csv files: one with detailed information about the movie (budget, genres, original language and so forth), the second one – contains movies credits – actors, directors, producers. Only csv file with credentials will be used. Size of the compressed tmdb_5000_credits.csv file: 7.64 MB.
https://www.kaggle.com/tmdb/tmdb-movie-metadata

# Overview of Technologies Used:
neo4j is a graph-based database; Cypher is declarative graph query language; Python (via Jupiter notebook) was used only for preparing data. 

# Conclusions 

I used neo4j graph database and declarative graph query language Cypher to create a model for movie recommendation system using previous user experience. As a data source, I choose 2 separate databases – MovieLens, which contains ratings and tag applications applied to movies by users and TMDB 5000 Movie Dataset, which gave me access to movies actors, directors. Data from 2 datasets were united using links.csv file which contains both “internal” movie id (used thought MovieLens files) and “foreign” id which refers to movie id in TMDB 5000 Movie Dataset.

Neo4j fits perfectly for this task. We constantly have to use connections between entities, like find movies likes by user1 which also are liked by other users, and then find movies that other users liked, but user1 hasn’t seen. Had we user traditional relational database, we’d end up with a large number of joints, which are very expensive for RDBMS. With a graph database, on the other hand, we have fast access to both data (user, movie, genre) and relationships between them. As all relationships are easily and quickly acceptable, it allows us to process queries very fast, enabling using the model for real-time recommendation engines. 

Most queries used in this work took about 200-500 ms to process. The longest query took ~60000 ms, in RDBMS it would require ~10 joints and would take much longer. 

Another advantage of using a graph database for this model is that it’s easy to visualize the connections and paths that led us to a particular result, and by doing so, to understand the underlying patter better.

Graph query language Cypher is very easy to learn but very powerful. It allows a user to write moderately complex queries even without prior knowledge of this language. I, for example, have never used it before, except during one homework in this course, yet, I thoroughly enjoyed working with it. 

I used different models – both Content-Based, Collaborative Filtering and combination of them. It’s hard to evaluate the performance of such models. We would have to propose movies to a user, and then to see whether he or she liked them. We would need “access” to a real user to do so.

It would be interesting to use other features to expand our model, like user demographic information, social relationships; more consistent tags that describe the movies, as well as more information about movies itself, like to know the movie sequences (we wouldn’t want to recommend user to watch episode #8 long sequence, if he had never watched any previous, even if his friends like it, rather, it would be better to recommend him to watch from the beginning).

As I discovered, the problem of creating a model for a recommendation engine, in particular, for movies recommendation system, can be successfully and easily solved using a graph database. 

# References: 

Code and technical info:

https://neo4j.com/

https://anaconda.org/anaconda/anaconda-navigator

https://www.python.org/

http://jupyter.org/

http://guides.neo4j.com/sandbox/recommendations

https://neo4j.com/developer/movie-database/#_import_instructions

https://neo4j.com/graphgist/competency-management-a-matter-of-filtering-and-recommendation-engines#competences

https://github.com/citruz/movies4j

https://neo4j.com/blog/real-time-recommendation-engine-data-science/

https://en.wikipedia.org/wiki/Jaccard_index

https://en.wikipedia.org/wiki/Pearson_correlation_coefficient

Data source:

https://www.kaggle.com/tmdb/tmdb-movie-metadata

https://www.themoviedb.org/ 

https://grouplens.org/datasets/movielens/

F. Maxwell Harper and Joseph A. Konstan. 2015. The MovieLens Datasets: History and Context. ACM Transactions on Interactive Intelligent Systems (TiiS) 5, 4: 19:1–19:19. 
https://doi.org/10.1145/2827872
