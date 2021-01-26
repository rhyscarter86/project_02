# Predicting Salaries for Players in the English Premier League (EPL)

This effort combines web-scraping of English Premier League (EPL) player data with linear regression tools and techniques to create a predictor for current player salary.

## Description, Data Used, Overall Outcome

Data from [sofifa.com](https://sofifa.com/) includes detailed information on all ~650 EPL players' speed, general skills, offensive abilities and defensive abilities. These capabilities are captured across ~30 attributes in the player's profile, which provide a comprehensive view of their abilities. *These data points were used in a series of linear regression models, with the final iteration achieving an R^2 value of ~0.88 and a Mean Absolute Error (MAE) of ~€599K.* 

## Features and Target

* **Target:** Salary (or Annual Wage)
* **Features Used:** Position (dummy variables for forward, midfield, goalkeeper. Defender variable dropped), age, overall rating, short passing, reactions, long passing, show power, ball control, volleys, stamina, overall rating inverse, overall rating squared, reactions squared, forward shot (combo of forward dummy variable and shot power)

## Tools & Techniques Used

#### *For Web-Scraping:*
* Beautiful Soup 

#### *For Regression:*
* Scikit-Learn
* Simple Linear Regression
* Multi-variate Linear Regression (without Cross-Validation_)
* LASSO Linear Regression (Ridge code present, but not used in final build)

## Analysis Limitations

* **Collinearity of Model Features:** There was a heavy emphasis on Overall Rating as a strong predictor of salary by itself. Simple Linear regression with this attribute had an R^2 of ~.60 and MAE of ~€990K. 
* **Interpretabilty of Model Features:** The final model, with the various transformations to Overall Rating, had a high R^2, but it was a mix of + and - values. Although potentially predictive, actually explaining what elements of the model were driving said predictions requires further investigation, and potentially a new model which addresses the strong collinearity of Overall Rating with the other features (e.g. removing it all together). 

## Possible Impacts & Future Efforts

Although the current model does not have strongly interpretable features, it still appears to be useful in making predictions, which may be acceptable given the future use case intended. That is, can players from other leagues, with similar skills/attributes to those of players in the EPL, have their salary predicted *if they were to play in the EPL.* If so, that predicted salary could then be compared with their current salary, and create a way to identify player 'steals' for the club, or give players themselves a way to show their value to clubs. 

#### *Future Efforts:*
Ingest data from the league directly below the EPL, the English Championship. Build a pipeline of data from other leagues and establish the mechanism to compare players worldwide with the English leagues-based model. 