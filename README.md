# Predicting Housing Prices in King County, WA

The goal of this project was to create a model that would build 95% confidence intervals for housing prices in King County, WA. Our dataset is modified from the original <a href="https://www.kaggle.com/harlfoxem/housesalesprediction">available</a> on kaggle.

The columns that we used to build our regression model were:

Response: 
* **price** - The sale price of the house (in dollars)

Predictors:
* **sqft_living**: The amount of living space, in square feet.
* **sqft_lot**: Used in conjunction with sqft_living to create a Floor Area Ratio.
* **sqft_lot15**: The square footage of the land lots of the nearest 15 neighbors
* **waterfront**: Indicates whether the house is on the waterfront (1) or not (0).
* **bathrooms**: The number of bathrooms, including partial bathrooms that do not have specific fixtures (i.e. a bathroom with a sink and toilet only is .5)
* **bedrooms**: The number of bedrooms
* **floors**: The number of floors, where 1/2 indicates a partially-finished floor or a loft
* **zipcode**: The house's zipcode

We also used the <a href="https://developer.mapquest.com/">MapQuest API</a> to retrieve city information, based on the columns **lat** and **long**.

This repository contains the following files:
* **MappingFunctions.ipynb** - Contains lat/long scatterplots using hues to display patterns in various predictors.
* **EDA.ipynb** - Contains visualizations and numerical summaries from our initial exploratory data analysis.
* **Regression.ipynb** - Contains functions for transforming the data, including taking the log and one-hotting, in addition to performing the actual regression analysis.
* **predicting-housing-prices.pdf** - The slides from our final presentation on July 7, 2020.

The data folder contains the following files:
* **kc_house_data_original.csv** - The original, unmodified dataset.
* **updated_housing_data.csv** - A modified version of the original csv which contains new columns for ratios and city information.

Through our analysis, we were able to construct 95% confidence intervals for housing prices. Approximately 94% of the data was for houses that sold for less than $1,000,000 (in 2014-2015), and approximately 99% of the data was for houses that sold for less than $2,000,000, so the model's accuracy decreases for more expensive houses due to lack of available training data.

We built the model by splitting the dataset into 80% training and 20% testing. After a lot of tinkering and trial and error, we got residuals that we were happy with:

![Residual plot](https://github.com/HeeebsInc/Project2Flatiron/blob/master/Images/Screen%20Shot%202020-07-10%20at%209.51.07%20AM.png?raw=true)

Once we knew we were looking at a solid set of columns as predictors, we retrained the model on the entire dataset and used it to predict prices of houses on Zillow.
