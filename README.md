# ind-aus-series-prediction
Predictions for the top scorer, top wicket taker, player who will hit the most 4's and 6's for the upcoming India-Australia ODI Series Feb 2019

**Initial dataset**
The data that was considered for the prediction was post 2011 ICC Cricet World Cup onwards. All the matches that featured India and Australia have been considered. The data was put together from varoius sources i.e. howstat.com, cricinfo statsguru API, and the cricinfo statistics

_File Name: "Dataset.xlsx"_
The final refined datasets used as an input for the code are:
- All matches data that featured India and Australia:
    columns: Team	Opponent,	Ground,	Result (Team)
- Squads for the upcoming odi series
    columns: Player Name,	Role,	Country,	Career Runs,	Career Balls Bowled
- Player Bowling Stats
    columns: Player,	Opponent,	Stadium,	Wickets
- Player Batting Stats
    columns: Player,	Opponent,	Stadium,	Runs,	4's,	6's
- Stadium Data
    columns: Ground,	City,	Country,	Matches,	RPW,	RPO,	Home Win %,	Away win %
- Current Team Rankings
    columns: Position,	Country,	Weighted Matches,	Points,	Rating
- Player Batting Rankings
    columns: Pos,	Player,	Country,	Rating
- Player Bowling Rankings
    columns: Pos,	Player,	Country,	Rating

File Name: "Ind-Aus Prediction Data.xlsx"
Along with this, a prediction (x-variables) dataset was created that holds the input variables regarding the upcoming matches which will be used as input for prediction:
- Player Level Prediction
    columns:ODI Number,	Ground,	Opponent,	Player
- Match Level Predictions
    columns: ODI Number,	Ground,	Opponent

Once the files were loaded, the first step was _exploratory data analysis_. Here, a number of steps were followed for each dataset.
- _Missing value treatment_
- _Univariate analysis_
   - For unordered categorical variables (Using Rank-Frequency Plots)
   - For quantitative variables (Using Box Plots)
   - Segmented unvariate analysis
- _Bivariate Analysis_
  This was done on continuous variables. A correlation matrix was plotted to identify the relationship between the variables in the dataset

Once the data cleaning and EDA was done, we go ahead with the _prediction models_
  - Since all the variables that we were considering had a corresponding unique numerical value, we didn't have to make use of any categorical variables as inputs for the model, hence one hot encoding was not necessary
  - The data was broken into test and train data and then the prediction model was applied on train data. We tested the performance metrics for each model using the test dataset, and then went on to using the ind-aus series data to generate the final predictions
  
**For the match level predictions:**
- Logistic regression was done on the match level data to identify - output (1- India wins, 0- Australia wins)
  Input variables: "Opponent Rating", "Average Stadium Runs per Wicket", " Average Stadium Runs per Over", "Stadium Home Team Win %", "Stadium Away Team win %"
- Output: India wins series 5:0

**For Predicting Highest Run Scorer:**
- Linear regression was done on batsmen level data
  Input variables: "Opponent Rating", "Average Stadium Runs per Wicket", " Average Stadium Runs per Over", "Stadium Home Team Win %", "Stadium Away Team win %", "Batsman ICC Rating"
- Output: Virat Kohli is the highest run scorer in the series

Breakdown of Top Run Scorers:
Player	
Virat Kohli (Capt)	249.0
Rohit Sharma (vc)	240.0
Shikhar Dhawan	211.0
MSD (wk)	195.0
Aaron Finch(c)	182.0

**For Predicting the most number of 4's and 6's**
- Linear Regression was done on batsmen level data
  Input variables: "Opponent Rating", "Average Stadium Runs per Wicket", " Average Stadium Runs per Over", "Stadium Home Team Win %", "Stadium Away Team win %", "Batsman ICC Rating"
- Output: Virat Kohli will hit the most 4's and 6's

**For Predicting the highest wicket-taker**
- Linear Regression was done on bowler level data
  Input variables: "Opponent Rating", "Average Stadium Runs per Wicket", " Average Stadium Runs per Over", "Stadium Home Team Win %", "Stadium Away Team win %", "Bowler ICC Rating"
- Output: Yuzvendra Chahal will be the highest wicket taker
