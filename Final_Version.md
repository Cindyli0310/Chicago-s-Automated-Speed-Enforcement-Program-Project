
# Project Overview

The topic for the individual project is the City of Chicago’s Automated Speed Enforcement Program, and the project is to transform Speed Camera Violations in Chicago dataset into visualizations. The project is divided into three parts  Data Exploration, First Version, Revised Version.  

The revised versions of your individual projects document your individual mastery of the course. The revised version of your dashboard should substantially improve the first versions based on the roadmap developed during the first version and include:

* The final version of your data product.
* A documentation of your data product.
* The final version should make use of advanced and interactive features of Tableau.

# Dataset Information

## Speed Camera Violations Dataset  

This dataset reflects the daily volume of violations that have occurred in Children's Safety Zones for each speed camera. The data reflects violations that occurred from July 1, 2014 until present, but not including the most recent 14 days. This data may change due to occasional time lags between the capturing of a potential violation and the processing and determination of a violation. The most recent 14 days are not shown due to revised data being submitted to the City of Chicago. The reported violations are those that have been collected by the camera and radar system and reviewed by two separate City contractors.

The City ordinance establishing the Children’s Safety Zone program substantially narrows the hours and locations of automated speed enforcement that are allowed under state law, and provides for the following 
* The enforcement hours will be limited from 7 a.m. to 7 p.m. in safety zones around schools on school days (Monday through Friday)
* The enforcement hours around parks will be limited to only those hours parks are open (typically 6 a.m. to 11 p.m., 7 days a week) with a 30 mph speed limit

Here is the preview of the Speed Camera Violations Dataset:
![](images/Speeding.png) 

## Speed Camera Violations with Crime Dataset  

This dataset reflects reported incidents of crime (with the exception of murders where data exists for each victim) that occurred in the City of Chicago from 2015 to 2018. Data is extracted from the Chicago Police Department's CLEAR (Citizen Law Enforcement Analysis and Reporting) system. The dataset is merged Year of 2015-2018's crime datasets orginally comes from Chicago Data Portal website. Each case number represents total number of crime by each wards.

Here is the preview of the Speed Camera Violations with Crime Dataset
![](images/crime.png) 


# Finding Analysis 

## Finding 1   
The graph clearly show that daily average speed violation number decreases year by year.  
![](revised_images/Finding_1_New.png)  

### Data wrangling steps   
**Step 1**  I conceptually think that with speed camera installation, drivers behavior will change, and the violation numbers will change by time. So I checked the relatioship between violation numbers and each year.  

**Step 2**  Year 2014 and 2019 are not complete year, instead of using total number of violation by year, I choose to use daily average violation as row.  

**Step 3**  I used line chart to represent the data first. However, even it clearly shows the trend, it is hard to compare different year's violation numbers. So I changed the graph to bar chart, and it much clearly to show trend and each year's difference. The following line graph is what I have tried first to explore the finding
![](images/Finding_1_line_graph.png) 


### Analysis   
The reason may come from Chicago speed camera in differenct safety zone. The speed camera is changing driver's behavior in these locations. On the other hand, with less violation numbers,accident injury by automobiles will decrease in these area. So government expense on ambulance, hospital expense will be less.  

However, an article named 'CHICAGO’S LATEST MONEY GRAB  300 SPEED CAMERAS COULD GENERATE UP TO $4.3 BILLION IN FINES FROM LOCAL MOTORISTS' in illinois policy website,violation tickets fine is a major money collection for government. So less violations will cause less ticket fines and decrease government income. 

## Finding 2   
Violation number is affected by seasonality issue. The higheset violation number by each month usually happened in May or October for each year, and August is always the low point between May and October.  

![](revised_images/Finding_2_New.png)


### Data wrangling steps   
**Step 1**  After found yearly violation trend is decreasing, I also want to check whether month has effect on violation numbers.  

**Step 2** Because year 2014 and 2019 are not complete data, I filter the data only include whole calendar year from 2015-2018.

**Step 3** I tried line graph to find the relationship between violation numbers and month. However, the result was very disappointed. It looks like one particular month has higher violation numbers than others, however, it is hard to tell the seasonality relationship with violation numbers. 
![](images/Finding_2_line_graph.png) 

**Step 4** And then I used bar chart to make the plot and sort by sum violation number descending. However, the relationship is not obvious and the graph looks a little bit messy. It only can figure out May is the highest violation month from 2015-2017, but Octorber became the highest violation number on 2018. 
![](images/Finding_2_bar_graph.png) 

**Step 5** And then I realized finding a trend Line by sorting violation number maybe not a good idea. So I changed back to line chart. But this time, I divided the data by each year, and because I want to compare whether seasonality issue happened on each year and has similar trend. After I check it, the result is very clear. 

### Analysis   
After did some reasearches, there are two possible reasons to cause this happened.

First, based on the 'Average Weather in Chicago report on Weather Spark', Chicago's weather temperature become warmer on May, get hotter on July and August, become warmer again on October. When the weather get better, the road situation getting better. For example, there will be less snowing or raining. People have higher opportunity to drive faster. Moreover, because the speed cameras are located on school and park zone, more people will hang out to play when weather getting better. The opportunity to get speed violation increase.  

Second, one potential reason to cause August has low point is that majority schools have summer break during July and August, there will be less children and parents in children safety zone during these time. On the other hand, because Auguest is still pretty hot in Chicago, less people will visit park comparing to better warm weather months.  

In order to sovle the high violation issue, I would suggust Chicago government to double the fine during warm weather month. With higher fine, people will be more careful to pass children safety zone and decrease automobile injuries. 

![](images/Chicago_weather.png)


### Finding 3   
In each ward, number of crimes is not positively correlated to the number of speeding violations. In wards with low crime numbers, the number of speeding violations seem to be randomly distributed. In wards with high crime numbers, the number of crimes and number of speeding violations seem to be negatively correlated.  

![](revised_images/Finding_3_New.png)


### Data wrangling steps   
**Step 1**  Besides time trend with violation numbers relationship, I also want to know whether the violations are affected by neiborhood enviornments. The first variable comes to my mind is income. However, I only find Year of 2017's Chicago average income. Because the data is not representable, I drop this idea.  

**Step 2**  I download Year 2015-2018 Chicago crime dataset on Chicago data portal. Choosing year 2015-2018 because it is the complete academic year and it is more representable.

**Step 3**  I use Python to merge 2015-2018 Chicago crime dataset with speed camera violation dataset by Wards.  

**Step 4**  In the new merged dataset in Tableau, each case number represents total number of crime by each wards.

![](images/merge_1.png) 

![](images/merge_2.png)

**Step 5**  I used bar chart to make the plot first. However, many bars overlap together, the graph looks really messy. 
![](revised_images/Finding_3_1.png) 


**Step 6**  On PM Study Circle website, it illustrates "scatter plot shows the relationship between two variables. It is the best method to show you a non-linear pattern. The range of data flow, i.e. maximum and minimum value, can be easily determined." And I want to find whether violation numbers are correlated with crime numbers, I realized that scatter plot is a better choice. As a result, I got an unexpected finding.  

### Analysis   
The result is really unexpected. One possible reason is that, there are more police officers on duty in high crime wards. Many drivers, being aware of this situation, tent to pay more attention to their speed when driving through these regions.

The finding is very useful. Some people might have sugguested that high crime number regions need more speed cameras. This finding suggests the opposite. 

# Road-map with future features/enhancements 

1. The date range of data is very limited - we have only three full calendar years. For example, if data from more years is available, I should be able to build better visualizations to demonstrate my findings such as time trend with violation numbers.  


2. By collecting more dimentions of the data - for example the age and gender of the drivers, the model and registration place of the vehicles, the illumination condition, the locations of the speed signs - I will be able to find more insights on the cause of speed violations, and give more suggestions to the audience.  


# Tableau Public Link  
https://public.tableau.com/profile/xinran.li7719#!/vizhome/Final_version_1/Dashboard1


# References  

1. "Children's Safety Zone Program & Automated Speed Enforcement." chicago.gov, www.chicago.gov/city/en/depts/cdot/supp_info/children_s_safetyzoneporgramautomaticspeedenforcement.html. 

2. "Average Weather in Chicago." Weather Spark, 
https://weatherspark.com/y/14091/Average-Weather-in-Chicago-Illinois-United-States-Year-Round#Sections-Temperature

3. "CHICAGO'S LATEST MONEY GRAB: 300 SPEED CAMERAS COULD GENERATE UP TO $4.3 BILLION IN FINES FROM LOCAL MOTORISTS." illinoispolicy, 21 Aug. 2013, www.illinoispolicy.org/chicagos-latest-money-grab-300-speed-cameras-could-generate-up-to-4-3-billion-in-fines-from-local-motorists/. 

4. Usmani, Fahad. "What is a Scatter Diagram (Correlation Chart)?" PM Study Circle, 23 July 2018, https://pmstudycircle.com/2014/08/what-is-a-scatter-diagram-correlation-chart/

# Revision History

## Documentation part
* Adding final version requirement explanation in Project Overview part
* Adding some exploration graphs analysis and reasons in data wrangling step
* Adding screen shots for Speeding Violation dataset and Crime dataset

## Visualization part

### 1 - Dashboard:

* In the first version, I use 'Tiled' format in Dashboard design. It is hard to adjust each graph's shape, location, and size. However, I change to 'Floating' design this time, it is much eaisier to adjust the graph and make the dashboard has a better outlook.

### 2 - Findings:  

Finding 1:
* Add trend line, checking P-value and R-square and write the result in caption
* Rewrite columns name to make sure it easy to understand

Finding 2:
* Adding average line for each year. The average line help shows clearer which months have higher violation numbers and which months have lower violation numbers. 
* Rewrite columns name to make sure it easy to understand

Finding 3:
* Clustering the data by each Ward's crime number, because it can help understand which Ward are high crime Wards.
* Rewrite columns name to make sure it easy to understand


```python

```
