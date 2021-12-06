# spotify-top-viral
 ML Project Fall 2021.

## Data
The 'data' folder consists of 


top200_processed1.csv 

1. Removed unwanted columns ('Unnamed: 0','artist_x', 'artist_y', 'explicit', 'type', 'chart', 'album', 'id')
2. Concatenated title + region = title 
3. Split date => year and month. 
4. Added top200 count (across full data) - based on title (which has region). 
5. Calculated trend_rank_score for a song based on region (title), up till each individual date (sorted data by AO of title, date).

top200_processed2.csv 

1. Reduced dataset to most recent unique songs (by region). 
2. Merged trend_rank_score into this. 
3. Binned streams by different regions. 

## Time Series Analysis

## Classification

'Classification_models.ipynb' contains the code to classify a song for a particular region on a given month and a given year into one of the stream bins (1,2,3,4). 

Where 1 signifies that the song for a particular region will have streams in the range (minimum streams, 25 percentile of streams), 2 signifies that the song will have song will have streams in the range (25 percentile, 50 percentile of the streams), 3 signifies that the song will have streams in the range (50 percentile, 75 percentile of the streams) and 4 signifies that the song will have streams in the range (75 percentile, maximum streams).

The different classification models implemented are: Decison trees, K Nearest Neighbours, Random forest and Multi Layer Perceptron. 

Multilayer Perceptron gave the best performance amongst all the classification models with a weighted-f1 score of 0.712.