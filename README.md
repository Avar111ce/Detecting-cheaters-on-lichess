# Detecting-cheaters-on-lichess
The program analyzes a player's chess games for different periods of time and checks if he cheated in one of them

## Requirements

To use the program you need python version 3.8 and below. The **first block of the ipynb-file** contains commands for setting up the virtual environment and downloading the necessary libraries

To work with the program you need **API token with lichess**. You can get it by going to site settings -> API access tokens -> New personal API access token, then select all the checkboxes and get a personal access token. It should be used in the function argent. https://lichess.org/account/oauth/token 

The access token is needed to use the function that downloads games, analyzes them with the engine, counts the loss of centipedes, accuracy and number of yawns, errors and inaccuracies:


## Instructions

```analyze_player_performance(username, engine_path='/usr/games/stockfish', token='yor_token',  end_date=None, days=365, perf_type="blitz", depth=20)```

The function returns a Dataframe that represents the metrics described above for each batch
Other arguments:

username - the nickname of the player on lichess

engine_path - the path where the engine is installed

end_date - a string with the date in the format '%Y-%Y-%m-%d'. End date of the time period

days - duration of the time period

perf_type - batch type ('blitz', 'bullet', 'rapid')

depth - depth of analysis by the engine

**While working with the program you should use this function 2 times to get 2 sets of batches to compare them later**

Then the ``plot_all_metrics(players_stats)`` function builds histograms of all the metrics described above for the specified dataframe.

The ```normality_check(data)`` function checks the data for normality

The ```detecting_cheaters(data1, data2)`` function tests the hypothesis of equality of mean values if the data of both samples are normal

The function ```detecting_cheaters_if_distributions_are_not_normal(data1, data2)`` tests the hypothesis of equality of mean values, if the data are not normal.


**Batch analysis by the engine is long, there are 2 csv files attached to the repository with the uploaded and raasculated data**

## Running files

ipynb:

git clone https://github.com/Avar111ce/Detecting-cheaters-on-lichess.git

pip install -r requirements.txt

jupyter notebook Detecting_cheaters_on_lichess.ipynb


py:

git clone https://github.com/Avar111ce/Detecting-cheaters-on-lichess.git

pip install -r requirements.txt

python detecting_cheaters_on_lichess.py

