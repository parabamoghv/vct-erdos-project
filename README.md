## 2023 Valorant Champions Tour
Erdos Institute Project

**Team members**
Ahram Lim, Yuqing(Frank) Lin, Alex Elchesen, Amogh Parab

**Stakeholders**
Riot Games, Valorant Teams, Online Betting, Broadcasters

### Project Description

Valorant is a first-person tactical hero shooter video team game created by Riot Games. Throughout the year professional Valorant teams participate in various tournaments to claim the title of Valorant Champions. We want to create a model that predicts the results of 2023 Valorant championship matches using the regular season data. Also, we want to figure out which aspects of the game matter the most in such models.

## getting started

To get started with this repository, we need to set up a reproducible environment. The tool we will use here is Poetry. In a new conda environment (we will use Python 3.10), install Poetry as

```
pip install poetry
poetry install
```

This will install the dependencies of the project into your virtual environment. Now we need to fetch the data from Kaggle. You will first need to get an API authentication token from your Kaggle account (**DO NOT COMMIT THIS TOKEN INTO THE REPO**). Follow https://www.kaggle.com/docs/api#getting-started-installation-&-authentication in order to create an API token and store the generated `kaggle.json` into the recommended location in your filesystem.

Once you have your API token in place, run

```
kaggle datasets download -d ryanluong1/valorant-champion-tour-2021-2023-data -p data/
unzip data/valorant-champion-tour-2021-2023-data.zip -d data/
rm data/valorant-champion-tour-2021-2023-data.zip
```

Now you have the VCT dataset ready to go!

## Data processing
### Overview
We have a vast collection of data from professional tournaments played over the years 2021 to 2023. The data includes results, economy data, individual player and team statistics, and team compositions; at the levels of both individual rounds and an entire game (which usually lasts 13 to 24 rounds). We collected this data from Kaggle.com.

For this project, we only used tournaments held in 2023.  The data was spread over various files with varying amounts of overlapping and missing data relative to each other.  We put substantial effort into unifying the data into a single dataframe while preserving key features. We indexed our data by games, with around 160 features per game after feature engineering. 

###
Main data files we used are: maps_scores.csv, overview.csv, players_stats.csv, eco_rounds.csv, kills.csv, scores.csv.  Since there is no data giving each game outcome, we used maps scores to extract each game outcome and combine it with other data.  For example, players_stats.csv has data about individual players' performance on each match, but it doesn't have match outcomes.

Similarly, eco_rounds.csv and kills.csv have no match outcomes, so we needed to combined them with maps_scores.csv and scores.csv in order to

1. study how individual rounds are related to overall match outcomes
2. define eco_rating, special_kills_rating with economy, special kills per rounds and match outcomes

You can find more details in the following notebooks.

vct_2023_eco_rating_using_prob.ipynb
vct_2023_kills_vs_scores.ipynb
vct_2023_special_kills_rating.ipynb

After manufacturing our own ratings, eco_rating and special_kills_rating, we need to save them for use in another notebook.

First, run these two notebooks, "vct_2023_eco_rating_using_prob" and "vct_2023_special_kills_rating.ipynb".
It will create three csv files in "../data/vct_2023/", one is for eco_rating and special_kills the other two.

