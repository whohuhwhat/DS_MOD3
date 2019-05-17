<img width="1440" alt="title" src="https://user-images.githubusercontent.com/30739929/57937133-569a7700-7893-11e9-9a18-fcf16fb5e769.png">

This project takes a look at 311 Service Requests in New York City made on 3.11.2019, the start date of my Data Science bootcamp.  The features in this data set include:

<img width="1440" alt="features" src="https://user-images.githubusercontent.com/30739929/57944925-771ffc80-78a6-11e9-9b9b-e282e5a85cae.png">

Using classification models, I want to see if I can predict a positive or negative resolution outcome.  Resolution outcome is an engineered feature based on the contents of the resolution_description feature.  An example of  negative (0) resolution was "The NYPD responded but upon arrival those responsible were gone."  An example of a positive (1) resolution was "The DOT responded to the complaint and took action to fix the condition."

<img width="1440" alt="target variable" src="https://user-images.githubusercontent.com/30739929/57944926-771ffc80-78a6-11e9-941b-06a16e070800.png">

### EDA

I took a look at what the top service requests for New York City were:

<img width="1440" alt="top5_nyc" src="https://user-images.githubusercontent.com/30739929/57945375-b4d15500-78a7-11e9-935f-cc9f7ff7ca5c.png">

I looked further to check if this was different per borough, and indeed they were.

<img width="1440" alt="top5_bq" src="https://user-images.githubusercontent.com/30739929/57945561-332df700-78a8-11e9-9eaf-c32c9bf58d3a.png">
<img width="1440" alt="Manhattan, Bronx, Staten Island" src="https://user-images.githubusercontent.com/30739929/57945447-ea763e00-78a7-11e9-9ff4-e060f0659d9f.png">

I mapped out the positive and negative resolutions to see if there was a relationship with the boroughs

<img width="1440" alt="map_borough" src="https://user-images.githubusercontent.com/30739929/57945695-843deb00-78a8-11e9-8816-7d19ad54db58.png">
![311_resolutions_borough](https://user-images.githubusercontent.com/30739929/57945816-dc74ed00-78a8-11e9-97e4-bc93cecd8393.png)

I then took a look at if another feature, complaint type, had a relationship.

<img width="1440" alt="map_rodent" src="https://user-images.githubusercontent.com/30739929/57946106-8b192d80-78a9-11e9-9d3c-afdeb68f6e0c.png">

I also looked at the different agencies.

<img width="1440" alt="map_nypd
" src="https://user-images.githubusercontent.com/30739929/57946227-d2072300-78a9-11e9-8732-ba0a7117ccf3.png">

<img width="1440" alt="agency" src="https://user-images.githubusercontent.com/30739929/57946253-e21f0280-78a9-11e9-8f7a-cb4362a1999e.png">

### Models
<img width="1440" alt="Logistic Regression" src="https://user-images.githubusercontent.com/30739929/57946418-3de98b80-78aa-11e9-91ce-4d75e66d1dbd.png">

<img width="1440" alt="Random Forest" src="https://user-images.githubusercontent.com/30739929/57946428-417d1280-78aa-11e9-9b1e-9f6bc287c946.png">

<img width="1440" alt="knn" src="https://user-images.githubusercontent.com/30739929/57946514-72f5de00-78aa-11e9-8931-35d2f9fd0728.png">

<img width="1440" alt="Decision Tree" src="https://user-images.githubusercontent.com/30739929/57946456-55c10f80-78aa-11e9-90b5-a77f75db99f6.png">

The decision tree first split on agency_Dept of Transportation because the resolution outcome handled by that agency was largely positive.  It then split on complaint_rodent because that had largely negative resolution outcomes.

<img width="1440" alt="xgboost" src="https://user-images.githubusercontent.com/30739929/57946838-56a67100-78ab-11e9-9311-697a7a509c41.png">

XGBoost found that the Department of Health and Mental Hygiene, followed by Dept of Buildings, then complaint_Rodent were the most important features.

The Logistic Regression model with Upsampling provided the highest F1-Score of 0.730.
