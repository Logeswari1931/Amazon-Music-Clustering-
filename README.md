Amazon Music Clustering Project

**Overview**

This project performs clustering on a dataset of songs from artists associated with a single genre. The goal is to group songs based on audio features such as danceability, energy, loudness, and more, using K-Means clustering after dimensionality reduction with PCA. The analysis identifies patterns in the data, such as "Chill Acoustic" tracks, "Party" tracks, and rap/spoken-word content.
The dataset appears to be sourced from Spotify-like features (e.g., danceability, valence) but is labeled for Amazon music clustering.

**Dataset**

File: single_genre_artists.csv
Columns:
id_songs: Song ID
name_song: Song name
popularity_songs: Song popularity
duration_ms: Song duration in milliseconds
explicit: Explicit content flag (0/1)
id_artists: Artist ID
release_date: Release date
danceability: Danceability score (0-1)
energy: Energy score (0-1)
key: Musical key
loudness: Loudness in dB
mode: Modality (major/minor)
speechiness: Speechiness score (0-1)
acousticness: Acousticness score (0-1)
instrumentalness: Instrumentalness score (0-1)
liveness: Liveness score (0-1)
valence: Valence score (0-1)
tempo: Tempo in BPM
time_signature: Time signature
followers: Artist followers
genres: Artist genres (as list)
name_artists: Artist name
popularity_artists: Artist popularity

**Size**: 95,837 rows (songs)
**Source**: Not specified in the notebook; assumed to be a custom or public dataset (e.g., from Spotify API).

The clustering focuses on the following features: danceability, energy, loudness, speechiness, acousticness, instrumentalness, liveness, valence, tempo, duration_ms.

**Requirements**

Python 3.x
Libraries:
pandas
seaborn
matplotlib
scikit-learn (for StandardScaler, PCA, KMeans, silhouette_score)

**Install dependencies using:**

textpip install pandas seaborn matplotlib scikit-learn

**Usage**

**Run the Notebook:**
Open Amazon.ipynb in Jupyter Notebook or JupyterLab.
Ensure the dataset single_genre_artists.csv is in the specified path (e.g., C:/Amazon music clustering/single_genre_artists.csv). Update the path if necessary.
Execute cells sequentially.

**Key Steps in the Notebook:**
Load and display the dataset.
Select features for clustering.
Scale the data using StandardScaler.
Apply PCA for dimensionality reduction (2 components).
Perform K-Means clustering (3 clusters).
Evaluate with Silhouette Score.
Assign clusters to the DataFrame.
Visualize clusters using a scatter plot of PCA components.
Compute and print cluster summaries (mean feature values).
Save the clustered DataFrame to clustered_data.csv.

**Output Files:**
clustered_data.csv: The original dataset with an added cluster column.


**Results and Insights**

Number of Clusters: 3 (determined via elbow method and silhouette score in the notebook).
Cluster Interpretations (based on mean feature values):
Cluster 0: Low energy, high acousticness – "Chill Acoustic" tracks.
Cluster 1: High danceability, high energy, high tempo, high valence – "Party" tracks.
Cluster 2: High danceability, medium energy, high speechiness, high liveness – Rap songs, live recordings, or spoken-word content.

Visualization: A scatter plot of PCA components colored by cluster is generated.
Cluster Summary (example output):textdanceability    energy   loudness  speechiness  acousticness  \
cluster                                                                 
0            0.486242  0.311018 -13.208988     0.060103      0.749539   
1            0.627309  0.693465  -7.608616     0.075061      0.258713   
2            0.664254  0.466617 -13.364383     0.829908      0.585922   

         instrumentalness  liveness   valence       tempo    duration_ms  
cluster                                                                   
0                0.168760  0.182065  0.413047  111.933323  223500.904818  
1                0.050681  0.199854  0.666324  124.905464  226568.204680  
2                0.001384  0.435498  0.584036  100.387090   97522.338234

**Limitations**

The dataset path is hardcoded; make it relative or configurable for portability.
Clustering assumes 3 clusters; experiment with different numbers for better results.
No hyperparameter tuning (e.g., for K-Means or PCA components) is shown.
Insights are preliminary and based on mean values; further analysis (e.g., genre correlations) could enhance understanding.
