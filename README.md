<<<<<<< HEAD
<h1>House Rent Data Analysis</h1>

***AIM:* Build a model that can predict the rent of a house based on various parameters like region,sqfeet etc..,**



The file ***[modelling](https://drive.google.com/file/d/1cwnobVY24B8wRpac9dakS7s1wyT3SQ35/view?usp=sharing)*** contains the detail code and description.

The data is available in the link ***["housing_train.csv"](https://drive.google.com/file/d/1zSNcBFId3nzbWBJoBfM7dvxDVUKTiGGU/view?usp=sharing)*** file.

The data has 265190 rows and 22 columns.

The columns are: 

```
id                           int64
url                         object
region                      object
region_url                  object
price                        int64
type                        object
sqfeet                       int64
beds                         int64
baths                      float64
cats_allowed                 int64
dogs_allowed                 int64
smoking_allowed              int64
wheelchair_access            int64
electric_vehicle_charge      int64
comes_furnished              int64
laundry_options             object
parking_options             object
image_url                   object
description                 object
lat                        float64
long                       float64
state                       object
```



The data has columns which have null values. The columns are [laundry_options , parking_options , description, lat , long ,state]

The null values are filled by ***Random Imputation***.



**Text Analysis** is also performed on **description** column to get an idea on the user necessary trends.

![](https://github.com/Anusha-raju/House-Rent-Data-Analysis/blob/main/word_cloud.png)

**Observations**: Most users basically need a pet friendly home, apartment type, fitness center, swimming pool, washer dryer facility.





**Spatial Analysis** was performed to get a clear idea of where exactly houses are situated.

![](https://github.com/Anusha-raju/House-Rent-Data-Analysis/blob/main/spatial_analysis.png)

Other necessary **EDA (Exploratory Data Analysis)** is done for insightfull information.





Outliers are detected (using Boxplot and Q-Q plot) and are imputed using Statistical Techniques.



**Price distribution analysis is done , following observations are received:**

- The price is not varying significantly with dogs/cats allowed or not.

  ![](https://github.com/Anusha-raju/House-Rent-Data-Analysis/blob/main/dogs_or_cats_price_distribution.png)

- The price is not varying significantly with furnished/not furnished homes.

  ![](https://github.com/Anusha-raju/House-Rent-Data-Analysis/blob/main/furnished_price_distribution.png)

- The price is varying significantly with whether the homes are equipped with electric vehicle charger.

  ![](https://github.com/Anusha-raju/House-Rent-Data-Analysis/blob/main/price_distribution_electric_vehicle_charge.png)



***Analysis of relationship between AREA and PRICE is done.***

![newplot](https://github.com/Anusha-raju/House-Rent-Data-Analysis/blob/main/newplot.png)

- Complex relationship between Price & sqfeet, meaning Linear Regression algorithm won't perform good



Categorical features are either ***Frequency encoded [regions,state]*** or ***Label encoded [laundry_options, Parking_options, type]***.





Once the data is cleaned it is then model to various regression algorithms.



<h3>Modelling:</h3>

The following r2 scores were obtained.



- as discussed before linear regression won't perform well.
- Random forest is the better choice among all these.

```
LinearRegression
-1.8723470523082515


RandomForest
0.7398024100272547


Decision Tree
0.6355353092447944


KNN
0.6645825998003583
```



***Hyperparameter optimization is done using RandomizedSearchCV***



- The following are the best parameters obtained

```
{'n_estimators': 833,
 'min_samples_split': 5,
 'max_features': 'sqrt',
 'max_depth': 17}
```



- The r2 score of RandomForest Regressor after optimization is:

```
0.7629514608107044

```