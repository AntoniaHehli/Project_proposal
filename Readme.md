# Proposal for Semester Project

**Patterns & Trends in Environmental Data / Computational Movement
Analysis Geo 880**

| Semester:      | FS23                                     |
|:---------------|:---------------------------------------- |
| **Data:**      | Different transportation modes derived from movement trajectories |
| **Title:**     | Estimating carbon dioxide emissions from movement trajectories |
| **Student 1:** | Laura Haus                               |
| **Student 2:** | Antonia Hehli                            |

## Abstract 
<!-- (50-60 words) -->
Climate change is present everywhere in our lives. Heavy rainfalls, and more frequent and severe droughts are only one possible result of the ongoing climate change. The Paris Agreement has the goal to keep the increase in global average temperature below 2°C above pre-industrial levels and therefore, amongst others, a redution in carbon emission is required. One emission factor that we as individual people can control is our transportation mode as for example cars are responsible for approximately 12% of total EU emissions of carbon dioxide. In our project, we analyze our average carbon emissions.

## Research Questions
<!-- (50-60 words) -->
Under consideration of various factors such as transportation mode, distance travelled, speed, and sloped which was determined using a digital elevation model, what is the average carbon emissions per individual and week? Furthermore, using these values as a benchmark, is it possible to achieve climate objectives?

## Results / products
<!-- What do you expect, anticipate? -->
Our goal is to have an average value of carbon dioxide emission per person and week. Although there are some uncertainties in these values, we believe that we can make a statement about the achievement of the climate objective if we take the obtained values as a benchmark.

## Data
<!-- What data will you use? Will you require additional context data? Where do you get this data from? Do you already have all the data? -->
We will use our own tracking data as well as other people’s tracking data from the pool. To calculate the slope, we need a digital elevation model to be able to determine the elevation of each location and afterwards derive the slope. For that we will use the elevation model provided by swisstopo called swissALTI3D. This dataset can be downloaded for various extents from the swisstopo web page.

## Analytical concepts
<!-- Which analytical concepts will you use? What conceptual movement spaces and respective modelling approaches of trajectories will you be using? What additional spatial analysis methods will you be using? -->
For our analyses, we need the distance, as well as the concept of speed and acceleration. We need to segment the trajectories based on speed as emissions vary depending on this parameter. We should also determine sequences that consists of high acceleration and of strong deacceleration within a short period of time as these emit more carbon than driving at a constant speed. Further, we use a digital elevation model to extract the height information of a certain location. With that we can determine the slope, whether one was driving up- or downhill, which also has an influence on the emissions.

## R concepts
<!-- Which R concepts, functions, packages will you mainly use. What additional spatial analysis methods will you be using? -->
Before starting our analysis, we have to filter out outliers as well as static points using a certain threshold value.  
As we need to determine speed and acceleration, we need to calculate the distance between each subsequent fix of the same transportation mode. This can be done using the lead() function from the dplyr package. The distance divided by the time difference, which can also be calculated with the same function, results in the speed. To segment the trajectories, we segment them by speed. The acceleration is the change in speed over time. All these calculation will be done using functions from the dplyr package.
To be able to assign the elevation values to each fix, we need to extract raster values at the respective locations. Raster analysis in R can be done using the package terra for example. 
The slope is then calculate using the elevation of the start point of one segment as well as the elevation of the end point and calculating the difference. The height difference divided by the distance travelled multiplied by 100 is the slope in percentage. If we need the angle also in degrees, we use the arctan of the result obtained before and get the angle of elevation. This can also be done using the dplyr package. 

## Risk analysis
<!-- What could be the biggest challenges/problems you might face? What is your plan B? -->
Theoretical challenges may be to find good reference values for carbon dioxide emission depending on speed, slope and acceleration. There are many different values that can be found. Another challenge is that we have to deal with twofold uncertainties: Once from the GPS data themselves, but also from the methodology applied. We should not forget that in the interpretation of our results.

## Questions? 
<!-- Which questions would you like to discuss at the coaching session? -->
