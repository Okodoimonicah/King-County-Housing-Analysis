KING COUNTY HOUSE PRICES PREDICTION MODEL

![image](https://user-images.githubusercontent.com/60213013/193290028-41c2c18d-fbd8-4ca1-a17b-496530ac701f.png)

OVERVIEW:

King County is located in the U.S. state of Washington. It is the most populous county in Washington, and the 13th-most populous in the United States. The county seat is Seattle, also the state's most populous city.

BUSINESS UNDERSTANDING:

A real estate agent of a company in Seattle wants to know which factors significantly impact the prices of a house in King County. 
This will aid in strategizing on the best criteria to take in order to maximize on profit. 
I have been given the task by the company to come up with a model that will be used to predict property prices in King County and obtain significant recommendations on steps that they should take for the business to be successful.


BUSINESS OBJECTIVES:

i) To understand factors that are most predictive of price.

ii) which house features will give the best deals.

iii) Obtain a model that will be of use when predicting the price of a property.

DATA STRUCTURE AND DATA UNDERSTANDING:

The dataset contains over 20,000 records of homes sold with 20 features.
The data contains a numeric, discrete and categorical data.

COLUMN DISCRIPTION

* id - Unique identifier for a house
* date - Date house was sold
* price - Sale price (prediction target)
* bedrooms - Number of bedrooms
* bathrooms - Number of bathrooms
* sqft_living - Square footage of living space in the home
* sqft_lot - Square footage of the lot
* floors - Number of floors (levels) in house
* sqft_above - Square footage of house apart from basement
* sqft_basement - Square footage of the basement
* yr_built - Year when house was built
* yr_renovated - Year when house was renovated
* zipcode - ZIP Code used by the United States Postal Service
* lat - Latitude coordinate
* long - Longitude coordinate
* sqft_living15 - The square footage of interior housing living space for the nearest 15 neighbors
* sqft_lot15 - The square footage of the land lots of the nearest 15 neighborsaterfront - Whether the house is on a waterfront
* view - Quality of view from house
* condition - How good the overall condition of the house is. Related to maintenance of house.
* grade - Overall grade of the house. Related to the construction and design of the house.

DATA PREPARATION:

we drop columns that won't be used for this analysis, cleaned the data by removing outliers.

Our target variable is for this task is price.

Checking the correlation of the features with price, we see that:
     sqft_living, sqft_above, sqft_living15 and bathrooms have a high correlation with price.
     
     VISUALIZATIONS:  CHECKING FOR LINEAR RELATION BETWEEN THE DEPENDENT VARIABLE(PRICE) AND INDEPENDENT VARIABLES
     
   ![image](https://user-images.githubusercontent.com/60213013/193332926-7f2292c9-ad7e-4c5f-9ff7-73d32c8a7afd.png)
 
 
 Comparing price against sqft_living, we see a linear relationship between the two. An increase in sqft_living increases the price of a home.
 
 using a apir plot to visualize all the independent variables against price, we have:
 
 ![image](https://user-images.githubusercontent.com/60213013/193333379-ccebeffc-e578-4395-abfc-6029ad54233f.png)

sqft_living15, sqft_living, sqft_ab0ve, sqft_above and bathrooms have a linear relationship with price.

distribution of price is quite skewed and we correct this by removing outliers.

MODELING:

Target variable = Price

independent variables = sqft_living, sqft_above, grade, sqft_living15

1. LINEAR REGRESSION:

use linear regression analysis to predict house price based on sqft_living. 
USing StatsModels to create a simple linear regression, we obtain:

 price = -5.045e+04 + 284.3280sqft_living
 Rsquared = 49.7%
 tstatistics, pvalue < 0.05
 
 visualizing the model:
 
 
 ![image](https://user-images.githubusercontent.com/60213013/193336069-0235b582-8ef1-4af4-8ec0-da61a24437ba.png)
 
 49.7% variation in price can be explained by the Square footage of living space in the home
 
 An rsquared of 49.7% is a low variation and indicates the Square footage of living space in the home is not explaining much variation of the price.
 
 we solve this by doing a multiple linear regression, adding more variables to our model to increase variability.
 
 plotting the regression line:
 
 
 ![image](https://user-images.githubusercontent.com/60213013/193338021-122a9c12-09a9-42ee-89fb-63743723032b.png)
 
 2. MULTIPLE LINEAR REGRESSION
 
 
 Using grade column, categorical data for multiple linear regression, we first perform one-hot encoding convert it to numerical counterparts.
 
Drop the first column when performing one-hot coding to avoid dummy variable trap.

list of independent variables for the model = ['sqft_living', 'sqft_above', 'grade']


creating a multiple linear regression model that includes categorical variables

rsquared = 59.4%
fstatistics, pvalue < 0.05

The model explains 59.4% variation in price.
All of the p-values round to 0
when all predictors are 0, the price value would be about 5.954e+05
with each increase in 1 sqft_living, we see an associated price increase of 220.1353 and with each inctrease in 1 sqft_above, we see an associated price decrease of -93.6898
For a house with an overall grade of 11(Excellent) we see an increase of 2.844e+05 in price of the house, an increase of 8.757e+05 in house price for grade 12(luxury) and 2.036e+06 on grade_13 Mansion.
for the company to maximize on profit, the houses should be of a high overall grade of the house. Related to the construction and design of the house.
 
 
 model fit
 
 ![image](https://user-images.githubusercontent.com/60213013/193342308-e19dcb71-57dc-4a05-8ae7-d88bb783bb32.png)
 
Visualizing true (blue) vs. predicted (red) values, with the predictor, sqft_living along the x-axis.









 
 
 
