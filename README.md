# spotify-stream-trend
 ML Project Fall 2021.

## Data
The 'data' folder consists of 

1. /8countries 

- Preprocessed data for 8 countries. 

2. /9countries 

- top200_9countries.csv 

-- Removed unwanted columns ('Unnamed: 0','artist_x', 'artist_y', 'explicit', 'type', 'chart', 'album', 'id')

-- Concatenated title + region = title 

-- Split date => year and month. 

-- Added top200 count (across full data) - based on title (which has region). 

-- Calculated trend_rank_score for a song based on region (title), up till each individual date (sorted data by AO of title, date).


top200_9countries_processed2.csv 

-- Reduced dataset to most recent unique songs (by region). 

-- Merged trend_rank_score into this. 

-- Binned streams by different regions. 


3. /ie 

- Full data (meta + audio features + charts) for Ireland. 


## Time Series Analysis
'EDA+TimeSeries.ipynb'contains the code for the following:
- Data Extraction
- Data Preprocessing
- Data Augmentation(inclusion of features top200_count and trend_rank_score)
- Categorical Feature Encoding
- Time-Series Models: ARIMA(Auto Regressive Integrated Moving Average) and LSTM RNN(Long Short Term Memory Recurrent Neural Networks)

The timeseries models were run on "acousticness" features of the Rank #1 song in the Canadian top200 charts, sampled in 30-day intervals. We have also provided the flexibility to enable the user to run the models for different combination of inputs: Rank, Feature and Country.

We have observed that the ARIMA model performed better to forecast acousticness on our Canadian dataset (univariate) than its LSTM counterparts (vanilla, multivariate and mulilayer).


## Classification

'Classification_models.ipynb' contains the code to classify a song for a particular region on a given month and a given year into one of the stream bins (1,2,3,4). 

Where 1 signifies that the song for a particular region will have streams in the range (minimum streams, 25 percentile of streams), 2 signifies that the song will have song will have streams in the range (25 percentile, 50 percentile of the streams), 3 signifies that the song will have streams in the range (50 percentile, 75 percentile of the streams) and 4 signifies that the song will have streams in the range (75 percentile, maximum streams).

The different classification models implemented are: Decison trees, K Nearest Neighbours, Random forest and Multi Layer Perceptron. 

Multilayer Perceptron gave the best performance amongst all the classification models with a weighted-f1 score of `0.712`.
