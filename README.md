# sportVU NBA Athlete Tracking

A working document looking at different physical metrics that can be derived from NBA plays using [SportVU](https://www.nbastuffer.com/analytics101/sportvu-data/) tracking data. 

### Dashboard Example

Below is a dashboard looking at the motion of the actual play along with calculated acceleration and running speed for the Detroit Pistons players. 

![](play.gif)  

### Data

SportVU in no longer used in the NBA, however a subset of games for the 2015/16 season can be found [here](https://github.com/linouk23/NBA-Player-Movements/tree/master/data/2016.NBA.Raw.SportVU.Game.Logs)

### Importing data

After downloading the games of interest to our working directory, I will import the data using the [sportvu_df()](https://rdrr.io/github/imadmali/NBAsportvu/man/sportvu_df.html) function. It also converts the data from json to a data frame. 

For this example I will use the Pistons vs Hawks game on Oct 27th, 2015 (id: 0021500001). Videohighlights available [here](https://www.youtube.com/watch?v=dNtmLm5D7dI). I randomly chose play id 388 consisting of a fast break for the Pistons resulting in a driving layup by Jodie Meeks.

To speed things up, I am only looking at this one play for this example but the calculations could easily be aggregated over time to look at demands over longer periods or for multiple games.

### Workflow

* Data import and variable selection
* Import game logs and play-by-play data using NBAstatR package
* Data cleaning, tidying and perform a join to the play-by-play data using NBAstatR.
* Create an animated visual of the play
* Distance, Acceleration and Running speed calculations
* Create various visuals of these metrics

*All code available [here](https://github.com/josedv82/sportVU_NBA_Tracking/blob/master/SportVU.Rmd)*

### To Do

* Look at peak demands for acceleration and speed for different periods of the game. Similar to this [study](https://pubmed.ncbi.nlm.nih.gov/26023738/)  
* Smoothing and resampling of data to minimise noise and help get more accurate calculations.
* Small shiny app that let users choose a game, filter by play and visualize all plots.

### Limitations

I am not super familiar with this data (only spent an afternoon on this), but some limitations I found were **1)** there are 25 data points per second, however there seems to be some noisy time intervals, which will affect the calculations of the above metrics. Maybe smoothing the time intervals and resampling afterwards may be required and **2)** the sportVU and play-by-play data do not align for all plays, meaning there is a mismatch in some cases or even some plays missing, which limits the ability to calculate demands for longer periods of time or across plays, quarters, etc...

### Some other examples of visuals

##### 1. Individual running speeds for the offensive part of the play

![](fastbreakspeed.PNG)

##### 2. Combined plot of raw acceleration and running speed for Jodie Meeks and the selected play.

![](combined.gif)

*Code for these images available [here](https://github.com/josedv82/sportVU_NBA_Tracking/blob/master/SportVU.Rmd)*

### Further Reading / acknowledgements

* Rajiv Shah's [github page](https://github.com/rajshah4) is a great resource and highly recommended.
* While I could not attend the conference, [Dean Little](https://twitter.com/DeanLittle) presented some [very interesting work](https://twitter.com/Bballphysio/status/1256376460593381376) in this area along with practical applications at IPS2020 conference.


