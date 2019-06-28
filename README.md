<img width="1440" alt="title" src="https://user-images.githubusercontent.com/30739929/57937133-569a7700-7893-11e9-9a18-fcf16fb5e769.png">

This project takes a look at 311 Service Requests in New York City made on 3.11.2019, the start date of my Data Science bootcamp.  The features in this data set include:

<img width="1292" alt="features" src="https://user-images.githubusercontent.com/30739929/60364329-dbf56900-99b3-11e9-9cb6-851fab90750f.png">

Using classification models, I want to see if I can predict a positive or negative resolution outcome.  Resolution outcome is an engineered feature based on the contents of the resolution_description feature.  An example of a  negative (0) resolution was "The NYPD responded but upon arrival those responsible were gone."  An example of a positive (1) resolution was "The DOT responded to the complaint and took action to fix the condition."

<img width="1440" alt="target variable" src="https://user-images.githubusercontent.com/30739929/60364336-e1eb4a00-99b3-11e9-993e-a3d209a4e9da.png">

## EDA

I took a look at what the top service requests for New York City were:

<img width="1440" alt="top5_nyc" src="https://user-images.githubusercontent.com/30739929/60364627-ab61ff00-99b4-11e9-9d62-433f21217e7c.png">

I looked further to check if this was different per borough, and indeed they were.

<img width="1440" alt="top5_bq" src="https://user-images.githubusercontent.com/30739929/60364659-c0d72900-99b4-11e9-98c2-e6f38cba0006.png">
<img width="1440" alt="top5_mbsi" src="https://user-images.githubusercontent.com/30739929/60364972-9043bf00-99b5-11e9-93f1-95a52d1204f2.png">

I mapped out the positive and negative resolutions to see if there was a relationship with the boroughs

<img width="1440" alt="map_borough" src="https://user-images.githubusercontent.com/30739929/60364713-ebc17d00-99b4-11e9-8f13-991304af1f64.png">

![311_resolutions_borough](https://user-images.githubusercontent.com/30739929/57945816-dc74ed00-78a8-11e9-97e4-bc93cecd8393.png)

I then took a look at if another feature, complaint type, had a relationship.

<img width="1440" alt="rodent_complaints" src="https://user-images.githubusercontent.com/30739929/60365214-1829c900-99b6-11e9-9bdf-e2a17daa34e4.png">


I also looked at the different agencies.

<img width="1440" alt="nypd" src="https://user-images.githubusercontent.com/30739929/60364859-36db9000-99b5-11e9-8262-c4c1a722b77d.png">


<img width="1440" alt="agency" src="https://user-images.githubusercontent.com/30739929/60364883-48bd3300-99b5-11e9-8f49-36bae6914c25.png">

## Models
I used F1 Score as the metric to find the most accurate model.  The F1 Score considers both precision and recall of the test.  Precision is the number of correct positive results divided by the number of all positive results.  Recall is the number of correct positive results divided by the number of all results that should have been identified as positive.  The higher a F1 score is, the more accurate a test is.

<img width="1440" alt="logistic regression" src="https://user-images.githubusercontent.com/30739929/60365669-5ecbf300-99b7-11e9-8581-70b1731beb2f.png">

<img width="1440" alt="random_forest" src="https://user-images.githubusercontent.com/30739929/60365734-8de26480-99b7-11e9-8458-08ef9794db87.png">

<img width="1287" alt="k_nearest_neighbors" src="https://user-images.githubusercontent.com/30739929/60365749-976bcc80-99b7-11e9-86e3-cecba87977c0.png">

<img width="1440" alt="decision_tree" src="https://user-images.githubusercontent.com/30739929/60365757-9f2b7100-99b7-11e9-9657-1f66ab794535.png">

The decision tree first split on agency_Dept of Transportation because the resolution outcome handled by that agency was largely positive.  It then split on complaint_rodent because that had largely negative resolution outcomes.

<img width="1425" alt="xgboost" src="https://user-images.githubusercontent.com/30739929/60365771-a6eb1580-99b7-11e9-9185-49e121ef0aa2.png">

XGBoost found that the Department of Health and Mental Hygiene, followed by Dept of Buildings, then complaint_Rodent were the most important features.

## Best Model
The Logistic Regression model with Upsampling provided the highest F1-Score of 0.730.

## What I would do next
The fact that this project only looks at a single day of data greatly limits its scope.  The most frequent complaint of HEAT/HOT WATER is probably highly correlated with the month and winter season.  It might be a safe assumption to say that the number one complaint may be completely different if this data took a look at a day in the middle of summer.  Would the number one complaint be Noise?

Moving forward, I would like to see how the data would change by season.  I would also like to see if throughout the years, whether or not the frequency of complaint types change, perhaps due to the city addressing these problems or improving how they approach the needs of the city.  
