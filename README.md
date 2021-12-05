# spotify-top-viral
 ML Project Fall 2021.



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
