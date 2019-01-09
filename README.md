![](https://github.com/kahartman2/beautiful_coffee/blob/master/java.png)

#### Data Selection 

At first, we wanted to sort through wine data to create a model that could essentially do some of the work of sommeliers. After not finding data with which we were satisfied, we thought about looking into whiskey or beer. Still, we weren't satisfied. We quickly realized that coffee culture has been picking up, and as coffee aficionados, we realized this would be the perfect topic. Thanks to James LeDoux (https://github.com/jldbc/coffee-quality-database), we found a plethora of data regarding coffee quality scores and various features, most of which was sourced from the Coffee Quality Institute (https://database.coffeeinstitute.org/coffees/arabica). We also sourced price data from the International Coffee Organization (http://www.ico.org/new_historical.asp).

#### Overview of Features Used - what determines your coffee quality?

Over the past decade, coffee quality and small farm coffee beans have become a thing.  Much like wine and craft beer, coffee beans have a list of measures to determine the quality of the brew.  These measures include:

  -Taste Measurements: Aroma, Flavor, Aftertaste, Acidity, Body, Balance, Uniformity, and Sweetness
  -Geographical Measurements:  Altitude, Region, and Country
  -Other notable measurements:  Color, Quakers, Processing Methods, Variety, Defects, and Vintage

#### Key Cleaning Steps: 
  -Dropped any row missing more than four features that we could not fill in (ie. region) 
  -Analyzed column value counts and dropped columns with categorical data that had a large number of unique categories, which   we feared could lead to overfitting our model 
  -Merged price data with initial dataset based on harvest year and country. Ultimately, dropped this column due to missing     countries/years in price data 
  -Removed excess characters from moisture and defect columns to convert data types to floats
  -Created a year column using the grading date year. We initially wanted to use the harvest year data, but we had too many     missing values   
  -Used regex to clean altitude column. The initial altitude values are seen below. For data points with missing altitude, set    altitude equal to the regions average. In cases where the region was unique, we used the country average 

#### Model Selection: 
  -We chose to initial test our data using Random Forest, K-Nearest Neighbors (KNN), Support Vector Machines (SVM), and       XCGoost. After comparing the accuracy scores of the models using pipeline with grid search, we found that our best performing 
  model was SVM with the following parameters: Kernel = linear, gamma = .001, and C = 10. 

![](https://github.com/kahartman2/beautiful_coffee/blob/master/confusion_matrix2.png)

![](https://github.com/kahartman2/beautiful_coffee/blob/master/roc_curve2.png)
