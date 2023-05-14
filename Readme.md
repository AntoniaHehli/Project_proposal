# Proposal for Semester Project

**Patterns & Trends in Environmental Data / Computational Movement
Analysis Geo 880**

| Semester:      | FS23                                     |
|:---------------|:---------------------------------------- |
| **Data:**      | Posmo Data for different transportation modes  |
| **Title:**     | Estimating carbon dioxide emissions from movement trajectories |
| **Student 1:** | Laura Haus                               |
| **Student 2:** | Antonia Hehli                            |

## Abstract 
<!-- (50-60 words) -->
Climate change is present everywhere in our lives. Heavy rainfalls, and more frequent and severe droughts are only one possible result of the ongoing climate change. The Paris Agreement has the goal to keep the increase in global average temperature below 2°C above pre-industrial levels and therefore, amongst others, a reduction in carbon emission is required. One emission factor that individuals can control is the choice of our transportation mode as for example cars are responsible for approximately 12% of total EU emissions of carbon dioxide. In our project, we analyze the average carbon emissions and how they reconcile with the climate objectives.

## Research Questions
<!-- (50-60 words) -->
In our paper we adress the following research questions: Considering various factors such as transportation mode, distance travelled, velocity or slope, what are the average weekly carbon emissions per individual? Furthermore, using these values as a benchmark, is it possible to achieve climate objectives?

## Results / products
<!-- What do you expect, anticipate? -->
Our goal is to have a weekly average value of carbon dioxide emission per person. We decided to analyse the emissions per week as there would be too much variance when assessing it daily. Although there are some uncertainties in these values, we believe that we can make a statement about the achievement of the climate objectives if we take the obtained values as a benchmark.

## Data
<!-- What data will you use? Will you require additional context data? Where do you get this data from? Do you already have all the data? -->
We will use our own Posmo tracking data as well as the tracking data from the pool. To calculate the slope, we need a digital elevation model to be able to determine the elevation of each location and afterwards derive the slope. For that we will use the swissALTI3D provided by swisstopo. This dataset can be downloaded for various extents.
Furthermore, we need data about the average emissions of different transport modes considering factors such as velocity or slope. Therefore, we will collect data provided on various governmental web sites or in research papers.
At last, we need the emission values for transportation which are favourable for reaching the climate goals. As the Sustainable Development Goals do not provide specific target values which are needed to tackle climate change we probably have to use target values stated from federal, cantonal, regional or city governments to see whether the objectives are met.  

## Analytical concepts
<!-- Which analytical concepts will you use? What conceptual movement spaces and respective modelling approaches of trajectories will you be using? What additional spatial analysis methods will you be using? -->
For our analyses, we need the distance, as well as the concept of speed and acceleration. We need to segment the trajectories based on velocity as emissions depend on it. We should also determine sequences that consists of high acceleration and deacceleration within a short period of time as these emit more carbon than driving at a constant speed. Furthermore, we use a digital elevation model to extract the height information of a certain location. Based on that we can determine the slope and thus whether one was driving up- or downhill, which also has an influence on the emissions.

## R concepts
<!-- Which R concepts, functions, packages will you mainly use. What additional spatial analysis methods will you be using? -->
Before starting our analysis, we need to filter outliers as well as static points using a certain threshold value.  
As we need to determine speed and acceleration, we need to calculate the distance between each subsequent fix of the same transportation mode. This can be done using the lead() function from the dplyr package. The distance divided by the time difference, which can also be calculated with the same function, results in the speed. To segment the trajectories, we segment them by speed. The acceleration is the change in speed over time. All these calculation will be done using functions from the dplyr package.
To be able to assign the elevation values to each fix, we need to extract raster values at the respective locations. Raster analysis in R can be done using the package terra for example. The slope is then calculated using the elevation of the start and the end point and determining the difference. The height difference divided by the distance travelled multiplied by 100 is the slope in percentage. If we need the angle also in degrees, we use the arctan of the result obtained before and get the angle of elevation. This can also be done using the dplyr package. 

## Risk analysis
<!-- What could be the biggest challenges/problems you might face? What is your plan B? -->
Theoretical challenges may be finding robust reference values for carbon dioxide emission depending on speed, slope and acceleration. There are many different websites from governments providing various values. Furthermore, it could be difficult to find a overall emission values which allow to address climate change. Another challenge is that we have to deal with twofold uncertainties: Once from the GPS data themselves, but also from the methodology applied. We have to consider this in the interpretation of our results. 
If we cannot find robust values for the emissions, we need to make estimations about the plausibility of the values found. Thereby, it is important that we try to focus on Swiss or EU values, as in the US the percentage use of SUVs is probably higher than in Switzerland.

## Questions? 
<!-- Which questions would you like to discuss at the coaching session? -->
