<img width="468" alt="image" src="https://github.com/Chedvihas/IPL_pred/assets/62206587/958f7888-b589-42ac-b8f4-d84a7d466ae0">


IPL Data Analysis

# Objective

Right now, the hot topic online is the Indian Premier League (IPL). The
aim is to observe the performances and statistics of the players and
teams at different phases of the game from which we can interpret some
interesting results and can reveal useful information about the
performances, areas of improvement, etc. Building models which can
predict the first innings score at a given instance and winning
probability of the second batting team at an instance.

# Data Scraping

The ball by ball data of all IPL matches till now has been scraped from
the site [<u>ESPN Cricinfo</u>](https://www.espncricinfo.com/). Every
match has a commentary section which consists of detailed ball by ball
data where that data is requested from a site in which all the data is
present in the JSON format.

The JSON data consists of ball by ball data which includes current
score, current overs, details of current batsmen and current bowlers,
etc.

# Data Cleaning and Preprocessing

We have eliminated redundancies from the dataset like same team names
with different spellings or teams whose names have changed.

We have added some required columns like

-   Striker_SR : Consists of career strike rate of the batsman on
    strike.

-   Non_Striker_SR : Consists of career strike rate of the non-striker.

-   runs_in_last3 : Runs scored in the last 3 overs.

-   wickets_in_last3 : Wickets in the last 3 overs.

-   Total : Total score of the team.

-   Winner : Winner of that match.

-   out_ind : True/False depending whether a wicket has fallen in that
    ball.

# Analysis and Visualization

From the available data, we can analyse different fields of the game by
obtaining the statistics from which we can interpret some useful and
interesting results. These visualisations can be helpful for the teams
and players to understand the areas of improvement and to plan new
strategies against opponents.

## Performance of teams in death overs

> We have analysed the performance of teams in death overs by comparing
> the average number of runs scored per over by teams vs the average
> number of runs given per over by that team in the death overs. We have
> used a grouped bar plot to visualize this data. Each teams’ average
> runs scored per over vs average runs given per over are plotted side
> by side as a group to show a better visualization of all the teams’
> performances.
>
<img width="468" alt="image" src="https://github.com/Chedvihas/IPL_pred/assets/62206587/d09ec850-2f0a-4edb-aeb1-2b810a1f3617">

>
> Scoring runs at the death can be a game-changer because it can shift
> the momentum towards the batting team. From the above statistics we
> can observe that some of the successful teams like MI, CSK have
> comparatively more run rate at the death while batting.

## Performance of players in death overs 

> Performance of individual players is important for teams’ success. So
> we have also plotted bar graphs showing the batsmen with highest
> strike rate at the death and bowlers who are economical at the
<img width="179" alt="image" src="https://github.com/Chedvihas/IPL_pred/assets/62206587/32f1b869-bf38-4d6f-9e69-41d0a0f2e19e"> <img width="185" alt="image" src="https://github.com/Chedvihas/IPL_pred/assets/62206587/09d79e4e-51ae-4283-8050-d2d271c3e255">


>
> Above data shows the strike rates and economies of the players at the
> death in 2020. Two players from RCB, AB de Villiers and Chris Morris,
> are at the top of both the lists. However, Hardik Pandya and Kieron
> Pollard, the key power-hitters for MI and Jasprit Bumrah, the death
> bowling specialist were some of the most important reasons for the
> success of MI at the death with both bat and ball.

## Contribution of batsmen to the runs scored by the team in the year 2020

> For a team to perform well in the whole season, all the players need
> to contribute for the team. Only one or two players cannot win all the
> matches for the team. We have plotted pie charts for all teams showing
> the percentage of runs scored by each batsman for his team.

<img width="203" alt="image" src="https://github.com/Chedvihas/IPL_pred/assets/62206587/ce9b7463-9f1a-42a3-994c-a7b289e29605"> <img width="187" alt="image" src="https://github.com/Chedvihas/IPL_pred/assets/62206587/1aa673f9-322b-48a6-9cb6-dc976eab6178">




> In some teams like MI, six players have scored more than 10% of the
> team's runs, which means almost all the batsmen have contributed good
> enough for the team. Whereas in some teams like KXIP, only four
> players have scored more than 10% of the team’s runs out of which only
> two players have scored around 50% of the runs. This shows the
> dependency of the team on only two of its batsmen which is a bad sign
> for any team.

## Comparison of players' strike rate in different phases 

> We have made a grouped bar plot which compares the strike rates of
> players at each phase of the game i.e., power play, 7-10 overs, 11-15
> overs and death overs. We can observe how the players’ strike rates
> change as the innings progresses.
>
<img width="447" alt="image" src="https://github.com/Chedvihas/IPL_pred/assets/62206587/b4142d2d-4f9d-4e41-8168-c28689cbebac">


## Leading wicket takers in powerplay<img src="media/image9.png" style="width:2.58333in;height:1.78396in" />

> Bowlers striking early in the innings will be useful to restrict the
> opponent with low score. Here are the leading wicket takers in
> power-plays in the year 2020. Trent Boult from MI has been very
> successful at picking early wickets in the power-play which is another
> reason for MI’s success in 2020.

# Preparing the data for Modelling

-   We have used 9 features for our models considering the basic
    features like current over, current score, current wickets.

-   Also, we have considered some important features like career strike
    rates of the current Batsmen. This is because the batsmen with
    higher strike rates can help the team to reach the high total.

-   Other important features we have used are runs and wickets in the
    last 3 overs. This can indicate the momentum of the game.

-   At first, we used the total score of our team as Y-Data. But, in
    this way the model didn’t give expected results for outliers.

-   Later instead of using score as Y-Data, we have used the run-rate at
    which the team has scored in the next overs.

-   In this way RMS error has decreased and also worked well for the
    outliers.

# Building models

## Predicting the first innings score

-   We tried using multiple Linear regression and Random forest
    regression to predict the first innings score.

-   X data has the features as said above and Y-Data has the run-rate at
    which the team has scored in the next overs.

-   Finally we have chosen random forest regression since it gave a
    lesser RMS error of 1.7 where as Linear Regression gave 2.97

-   The model inputs all the data at that instance and outputs the final
    score by calculating from the predicted run-rate.

## Winning probability of the second batting team

-   We tried using different classifiers like logistic regression, naive
    bayes and SVM to predict the winner and find the winning
    probabilities.

-   X-Data has one extra feature along with the previous features called
    the rem_runs which has the data of the runs required to reach the
    target at that instance and the Y-Data has binary values 0 and 1
    which represents whether the team has won or not.

-   We have majorly worked on logistic regression and finally chose it
    since it gave a lesser RMS error of 0.46 and also performed well on
    custom inputs.

# Challenges Faced

The main challenge faced was to scrape ball by ball data of all the
matches where we used to get bad gateway errors while scraping more
data. We had to make few changes to the code while scraping data for
some seasons due to some irregularities in the data.

# Final Results

The main objective of the project is to analyse the data to interpret
the results and make some conclusions regarding the performances of
teams and players, which we have done in the above sections. Also, we
have developed a [<u>web app</u>](https://ipl-predictor1.herokuapp.com/)
for our score predicting and winning predicting models using flask and
deployed it on heroku.

<img width="230" alt="image" src="https://github.com/Chedvihas/IPL_pred/assets/62206587/655770b6-9b77-45f4-995b-d31ff1ae204a"> <img width="228" alt="image" src="https://github.com/Chedvihas/IPL_pred/assets/62206587/dc1360a0-e6ac-4ccf-a90c-9ef4bc329ebc">



We need to fill in the data of the current situation of the match as
shown in the above image. To predict the first innings score, we need to
provide the current over, current score, current wickets, names of
striker and non-striker, current scores of striker and non-striker, runs
and wickets in the last 3 overs. The page displays the range of
projected scores which the team is expected to score. To predict the
winner, we need to provide the runs remaining along with the above
mentioned data. The page displays the winning percentage of the chasing
team in that situation.

<img width="229" alt="image" src="https://github.com/Chedvihas/IPL_pred/assets/62206587/6bef0dfc-e4d4-4e8f-bed6-7888af34857a"> <img width="228" alt="image" src="https://github.com/Chedvihas/IPL_pred/assets/62206587/97f71fef-e650-4636-ae02-741e9ed8e935">


# Areas of Improvement

1.  Much more analysis can be made if we could extract information like

    1.  Nature of the pitch (hard, grassy, etc).

    2.  Ball pitching (full length, short length, pitched outside off,
        etc)

    3.  Speed of the delivery

    4.  Bowler type (off spinner, leg spinner, fast bowler, medium
        pacer, etc)

    5.  Whether the bowler and batsman are right handed or left handed

2.  Models can be improved by considering the features like

    1.  Batsmen who are yet to come

    2.  Bowlers in the opponent team

    3.  Performance of batsmen in that season (runs, average,
        strike-rate, etc)

    4.  Performance of bowlers in that season (wickets, economy, etc)

    5.  Nature of the pitch
