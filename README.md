# Building a Soccer Recommendation Model for Transfermarket Seasons
_Author_: Peter Garcia


## Table of Contents
1. [Problem Statement](#Problem-Statement)
2. [Background Information](#Background-Information)
3. [Project Files](#Project-Files)
4. [Executive Summary](#Executive-Summary)
5. [Visualizations](#Visualizations)
    1. [Player Activity](#Player-Activity)
    2. [Incomplete Passes](#Incomplete-Passes)
6. [Conclusion and Recomendations](#Conclusions-and-Recommendations)
7. [Limitations](#Limitations)




## Problem Statement
As team weaknesses are discovered, what players can fill the roles that are needed? I will be using unsupervised clustering algorithms to recommend players, with similar playing styles, to supplement a team's overall weaknesses. Player movement heatmap images and team movement heathamps images will be our main source of data.  

Due to limited time constraints, this project focus on generating images of player movement through the course of a season. The dataset created will be used for the next phase of this project. The data was not ready available in the format that is needed to build our model. We will be taking open data from Statsbomb to generate our own dataset of images to process.



## Background Information
Currently, signing a new soccer player is based a lot on name recognition, goal scoring percentile, and sometimes just hype. Building a team around world class players is what everyone wants but sometimes, even world class players have to adjust to a new position if their natural position is already filled by another superstar. The likes of Messi, Suarez, and Griezmann are all superstars but have difficulty building chemistry in the attacking third of the pitch. This is partly because Griezman needs to adapt to a wider position than he was used to naturally playing at his former club. At his former club, Griezman would be the focal point of attack and now at Barcelona, he's not. Instead he is playing on the wing or as a striker when Luis Suarez is injured. 

This isn't just limited to Griezman but other soccer players as well. Hirving Lozano is currently Napoli's most expensive signing at $\$46.5$ million dollars. Pundits in Italy have been harsh critics about this transfer since he hasn't been able to make an impact like he did at his former club. We can also look at Neymar's record \$263 million transfer fee to PSG. He hasn't been able to make an impact on his team's performance overall. Neymar's case might be a bit different because there are problems unrelated to his football abilities that have hindered his performance but the point is the same. 

How can we, as a club manager or owner know that a player will be a great addition to their team? Just because players have great talent doesn't necessarily make them the perfect fit. 

In Barcelona's case, if someone else who was naturally playing as a Left Winger would come in to replace Neymar, there wouldn't be a need to put so much pressure on Griezman to quickly adapt to a new role this isn't his natural role. He can still do the job well but he isn't as efficient as he was at his former club. It is frustrating to see a player like Griezman valued at $135 million not produce the results that are expected of him, from a club manager's perspective. Equally important, the player feels frustrated in not being about to produce similar results and will take longer to adaptat. The longer the adaptation period, the more impatient the fans, pundits, club owners, and even the player themself will get. The player's need for time to adapt to a new role, and the manager's need to see positive results as soon as possible are a difficult balance. 


## Project Files

[Statsbomb Open Data](https://github.com/statsbomb/open-data)
[Player Activity Heatmap](https://github.com/PeterGarcia95/Soccer_Analytics/tree/master/Player_Heatmaps)
[Player GIFs](https://github.com/PeterGarcia95/Soccer_Analytics/tree/master/Player_GIFs)
[Incomplete Passes Heatmap](https://github.com/PeterGarcia95/Soccer_Analytics/tree/master/Passes_Heatmaps)

## Executive Summary
Statsbomb has a public repo that is periodically updated with public event data for particular soccer matches that they release. The data I was working with initially consisted of 2.27 million rows once it was aggregated together. This was a lot of data to handle given the time constraints and data cleaning that needed to happen before even analyzing data. Upon reevaluation, I decided to focus on Barcelona's team since approximately 875k rows were pertaining to Barcelona games.

Data cleaning consisted of unpacking information stored as python dictionary equivalents within the json files. Some data contained nested dictionaries and data wrangling became much of the time consuming portion of the project. Functions were created in order to automate the process. However, the overall cleaning process was limited to Barcelona data due to the limited processing power of my computer and time constraints. Additionally, we narrowed down to the basic test cases for each Starting-XI players in a given Barcelona match. This serves as a proof of concept and the process becomes smoother when scaling up to larger quantities of matches per player and overall data. 

In the end, GIFs were created in order for us to see player activity density every 5 minutes per game. When scaling to include the activity density for a player across a whole season, the "natural" position of that player will be revealed. This is because one game is not enough of a sample size to determine a player's natural position. A player can be playing a different position in the next game due to another player's injury or a tactical experiment. Over the course of the season, we are able to determine what postions were played effectivly and consistently based on heatmap image intensity. 


## Visualizations
Visualizations are divided by the sections below. 


### Player Activity

Below are the GIF representations of three of Barcelona's most influential players: Neymar(has since moved to PSG), Luis Suarez, and Lionel Messi. 

Note: If they were subbed out at any point in time, the heatmap will appear empty after the time lapse. GIFs were made to reflect player activity every 5 minutes.

![Lionel%20Andr%C3%A9s%20Messi%20Cuccittini.gif](attachment:Lionel%20Andr%C3%A9s%20Messi%20Cuccittini.gif)![Neymar%20da%20Silva%20Santos%20Junior.gif](attachment:Neymar%20da%20Silva%20Santos%20Junior.gif)![Luis%20Alberto%20Su%C3%A1rez%20D%C3%ADaz.gif](attachment:Luis%20Alberto%20Su%C3%A1rez%20D%C3%ADaz.gif)

### Incomplete Passes
While we did not have enough time to do the same time lapse for incomplete passes. Instead, I have plotted all the places where passes were incomplete for each half. This can be due to the ball going out of bounds, a player not receiving a pass, or a player from the opposite team intercepting that pass. 

The first heatmap map shows where incomplete passes took place during the 2nd half of the game while the second heatmap shows where incomplete passes occurred during the first half.


![Incomplete_2.png](attachment:Incomplete_2.png)![Incomplete_1.png](attachment:Incomplete_1.png)



## Conclusions and Recommendations
Using machine learning, we can aim to reduce the time it takes for players to adapt to their new teammates. Thought we did not have time to actually implement a model, we did establish the precursors needed four our model and began a pipline to gather data and clean data. Using a player recommendation system to effectively supplement weaknesses identified in a team throughout a season, will decrease the adaptation period. 

Below are is the summary of our analysis and next steps to implementing our machine learning model:

- Heatmaps and GIFs were only done for one particular match as a test case but we can create an heatmap of a specific player that accounts for the player's movement throughout an entire season. This will give us a better understanding of where players are more inclinded to move and play and allow us analyze their effectiveness in their preferred position. 

- Similarly, we can also identify areas where a team as a whole is lacking. Useful heat maps include but are not limited to: locations of incomplete or intercepted passes,locations where goals were conceeded or scored, or even the adjustment to a new formation when a substitute comes on. Once we have a team profile, we can the team's most effective formation throughout the season and identify weakness they are experiencing. 

- Combining these two phases, we can create a player recommender systems to recomend players that are effective in their natural positions on the field. We can run a neural network and feed it player heatmaps in addition to the relevant team heatmaps in order to provide optimal formations and transfer market targets. 

- Lastly, we can attempt to estimate the time it will take for a player to adjust to a team's playing style if they are currently in another league. This will require a more in depth analysis and might even be a project on its own after the above steps are complete.  


## Limitations
Note: This project relies heavily on data. I decided to focus on Barcelona because the majority of the data in Statsbomb's open data pertains to Barcelona. If we were to scale this to other teams, we would need data for each specific team every mid-season in order to start making predictions. Alternatively, we can scale our problem down and use the concepts here to process live data during a match and make necessary modifications during halftime break.

