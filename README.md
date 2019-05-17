<img width="1440" alt="The 311 on 3.11" src="https://user-images.githubusercontent.com/30739929/57596573-5dcf2700-7519-11e9-89ab-aaeda757fa90.png">

How well can we predict a positive or negative outcome resolution based on the following features.

Features:  
  * Agency 
  * Borough
  * Location (Latitude & Longitude)
  * Created Date
  * Closed Date
  * Complaint Type
  * Descriptor
  * Resolution Description → Resolution Outcome
  
       Positive or Negative?

The Resolution Outcome is based on the contents of the resolution description.  An example of a positive resolution is "The NYPD responded to the complaint and took action to fix the condition.  An example of a negative resolution is "The Police Department responded and upon arrival those responsible for the condition were gone."

There are a total of 1000 311 Service Requests made on 3.11.2019.  Using the criteria above, there is
a total of 614 positive outcomes and a total of 386 negative outcomes.

![pos_vs_neg_outcomes](https://user-images.githubusercontent.com/30739929/57596883-f31eeb00-751a-11e9-9dbd-9f83a165c8f9.png)

## Exploratory Data Analysis
Top 311 complaints for New York City:

![top_complaints_NYC](https://user-images.githubusercontent.com/30739929/57596956-44c77580-751b-11e9-8dd0-54acccf9651c.png)

Broken down further by borough:

![top_complaints_bronx](https://user-images.githubusercontent.com/30739929/57596992-66286180-751b-11e9-881a-427d16f2b887.png)
![top_complaints_brooklyn](https://user-images.githubusercontent.com/30739929/57596996-6a547f00-751b-11e9-8681-dad186483f79.png)
![top_complaints_manhattan](https://user-images.githubusercontent.com/30739929/57597003-6de80600-751b-11e9-80b8-8539cd2c8306.png)
![top_complaints_queens](https://user-images.githubusercontent.com/30739929/57597009-72acba00-751b-11e9-954a-2f34c6aa480e.png)
![top_complaints_staten](https://user-images.githubusercontent.com/30739929/57597012-750f1400-751b-11e9-87e8-0d96a01b175a.png)

#### Positive vs Negative Resolutions by Borough:
![311_resolutions_borough](https://user-images.githubusercontent.com/30739929/57597082-d20aca00-751b-11e9-85eb-ba926d67f95b.png)
![311_resolutions_borough_stacked](https://user-images.githubusercontent.com/30739929/57597083-d46d2400-751b-11e9-97fd-5885fc23f897.png)


#### Positive vs Negative Resolutions by Agency:
![311_resolutions_agency](https://user-images.githubusercontent.com/30739929/57597112-067e8600-751c-11e9-86e3-d1b36d7f04ac.png)

#### Folium Heatmaps
Complaints of HEAT/HOT WATER

<img width="481" alt="map_heat" src="https://user-images.githubusercontent.com/30739929/57597514-a852a280-751d-11e9-9f78-8c173c74c1c9.png">

Complaints of Noise - Residential

<img width="484" alt="map_noise" src="https://user-images.githubusercontent.com/30739929/57597515-a852a280-751d-11e9-85c8-ec25a7310740.png">

Complaints of Rodents

<img width="585" alt="map_rodents" src="https://user-images.githubusercontent.com/30739929/57597516-a852a280-751d-11e9-8d65-1599100bfb65.png">

## Models Used
Using the F1 Score to find our most accurate model:

Random Forests: The best parameters were
{'max_depth': 5,
 'max_features': 0.25,
 'min_samples_leaf': 0.03,
 'n_estimators': 200} and returned a F1 Score of 0.521
 
 KNN: A KNN model with a k:3 returned a F1 Score of 0.660

Decision Tree:  A Decision Tree with the following parameters {'max_depth': 12, 'max_features': 41} returned a F1 score of 0.616

![decision tree](https://user-images.githubusercontent.com/30739929/57598894-f8803380-7522-11e9-9cf9-147425fe7836.png)

XGBoost

![xg_feature_01](https://user-images.githubusercontent.com/30739929/57598913-0df55d80-7523-11e9-9d57-617567b5f648.png)

XGBoost with GridSearch

![xg_feature_02](https://user-images.githubusercontent.com/30739929/57598914-0df55d80-7523-11e9-8231-3db467818ff5.png)
