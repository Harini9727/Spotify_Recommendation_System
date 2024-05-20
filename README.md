# Spotify_Recommendation_System

Implemented content-based recommender system that will use the K-Nearest-Neighbor (KNN) strategy to recommend items of interest to a user. A content-based recommender can be viewed as a type of IR system that, instead of an explicit user-specified query, uses a learned user profile to recommend similar items. As in other IR systems, the items to be recommended as well as the user's profile are represented as vectors over a set of features. Features may be textual tokens (when items are documents), but they can also be other types of "content" features that represent the characteristics of the items.

For this project, I used a preprocessed data set from Spotify where various songs (1421 of them) are represented in terms of different musical and acoustic features. Lets assume that, for each user, the system maintains a list of songs liked or played by the user in the past (e.g., a playlist). A user's profile will be represented as the aggregate vector representation of the songs in the user's playlist. The main task for the system is to match the user's profile with representations of the available songs and recommend the top k songs most similar to that profile. The necessary data files are:

- readme.txt -- this file provides a more detailed description of each file.
- Spotify_Metadata.csv
- Spotify_Numeric.csv
- Spotify_Users.txt

The  tasks for this project are the following:

Implement function knn(item, Data, K) that given the vector representation of an item (in this case a song), the Data matrix representing song features (from the file: "Spotify_Numeric.csv"), and the number of neighbors "K", will return the indices of the K most similar songs to "item" in decreasing order of similarity, along with the corresponding similarity values.

our implementation  used cosine similarity function to find the K nearest-neighbors.Used the information contained in the file "Spotify_Metadata.csv" to include information about the recommended songs in thr output (such song name, artist, song mood(s), etc.). For example, given an item represented as the following feature vector:
    item = [0.1, 0.5, 0.2, 0.5, 0.0, 0.5, 0.0, 0.8, 1.0, 0.2, 0.5, 0.5, 0.3]
the knn function might produce an output similar to this example. Demonstrated  knn function by producing the top 10 most similar songs the an item with the following feature vector:
    item = [0.8, 0.1, 0.7, 0.0, 0.5, 0.1, 0.5, 0.2, 0.0, 1.0, 0.1, 0.2, 0.7]
a function recommend(userID, Data, K)  generates a list of top K recommendations for a given user, given the user's previously recorded playlist. The function first looks up the user's playlist and computes a centroid (mean) vector of songs (by features) as the representation of the user's preference/music taste.  Note the userID is 0-based. 

Playlists of 20 users are shown in the file Spotify_Users.txt, where each line is a playlist of the user (indicated by song IDs).
Then the function calls knn() to generate the K most similar songs to the mean vector of the playlist as recommendations for the user.  For example, given a user playlist:

playlist = [1133, 1136, 1150, 1157, 1164, 1261, 1279, 1360]
and K = 10, the function might generate an output similar to this example.
THEN the FINAL recommendations returned from this function must be EXCLUDING the songs that were in the user's original playlist -- we want to recommend something the user has not listened before.
created the Data matrix (from the file: "Spotify_Numeric.csv").  

Finally shows the results for K = 20 for user 3 (4th row in the "Spotify_Users.txt") and for user 19 (20th row in the same file).
