# IMDb_vs_metacritic
An exploratory analysis into the differences between the two movie rating websites.

Business Understanding:
I use both of the movie ratings sites when researching which films to watch. I have a preconception that metacritic favours certain types of movies so I would like to see if the data backs this up.

The questions I would like to answer to solve this are: 
Part I: How generous are IMDb and metacritic with their ratings?
Part II: Do release years affect the scoring on the two websites?
Part III: Do movie genres change the scoring across the two websites?

These are investigated in the movies_eda.ipnyb workbook and further explainations are found on my medium article here: https://medium.com/@jacobveerapen/imdb-vs-metacritic-fe9b23c41fb5

Data Understanding:
I took the data from two different sources. For IMDb I was able to get data from them directly at https://www.imdb.com/interfaces/
I used the two datasets title.basics and title.ratings

To get the metacritic ratings I used a kaggle project linked here: https://www.kaggle.com/
https://storage.googleapis.com/kagglesdsdata/datasets/457220/861700/metacritic_movies.csv?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=gcp-kaggle-com%40kaggle-161607.iam.gserviceaccount.com%2F20220805%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20220805T132542Z&X-Goog-Expires=259200&X-Goog-SignedHeaders=host&X-Goog-Signature=1f5accc9ddb844d4c152c26a7211f58ba6dd05b526821986a0fefaa397848feb6a61a66d6f470c2317e8317c175d6d6accf7b8ef1579cb7bd35d3c1d845c906037259dffcb56c3c7d8ae24c050db2f3f25b76bef70be68808c1ab0801e2dd7fa51ed4882abc9c5d8f788f3538826e60a7c4594b0e5b6ea849035f554eb5ec38023ec5b3ce58dcbf63119592dc6f8b1071a951bfb216f5178e305cf5f2438ac0c205e4be16f7a0de664fb3c15b0be16af12a922e876b2b670967a4404e3666bbf73c3642a30948539e273e5b780717dec326e622cf5fadf09b9ad88ad37ab7f14873a141ee11b879bcc84b62142b692e594cc419ff168f8c6a7482f3c52416e09

Preparing Data: 
The two IMDb datsets both have different information in them but they share a common film ID called 'tconst' so I joined the two datsets using that column.
Another issue is that the datasets did not exclusively have data on movies (there was info on TV shows as well) so I dropped those.
I also chose to filter out films that had very few votes to minimise the effect of rare movies that IMDb filter out from their rankings themselves.
The final thing I removed was films that I did not have ratings from both websites for as the purpose of this analysis is to compare the two websites opinions on the same films.
For parts II and III in this analysis I have decided to track the metric ScoreDiff = (IMDb-metascore)
This is an easy metric to understand as positive values suggest IMDb had higher ratings and negative values indicate higher metascores.

For the purpose of this analysis I have decided against using any ML models. 


Libraries Used:
Seaborn 0.11.2
Pandas 1.4.3
os
matplotlib 3.5.2
numpy 1.23.1

Files:
movies_eda.ipynb - This file is the workbook that I used to conduct the analysis
metacritic_movies.csv - This file contains the metacritic data
title.basics.tsv & title.ratings.tsv - These files contain the IMDb data
The rest of the files in the directory are the graphs, exported for the purpose of adding to my medium article


My key takeaways from this analysis were these:

- IMDb Scores tend to be higher than metacritic scores, so don’t be put off by a slightly lower rating on metacritic.
- metacritic tend to favour older movies particularly those from the 1970s so if thats your thing, metacritic might be your best bet for movie recommendations.
- There are differences in terms of how different genres perform on the two platforms but that is going to need some more investigation as there are so many genres out there.
