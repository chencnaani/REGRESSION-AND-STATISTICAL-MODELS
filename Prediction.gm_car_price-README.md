# *Regression-and-Statistical-Models*  

### Assignment given throughout the course


**Prediction of car price**

###### Background: 
In this task I was asked to build a model that would predict the price of the car given the following data:
  Price, Mileage, Make, Model, Trim, Type, Cylinder, Liter, Doors, Cruise, Sound, Leather.

I used various automated methods to find the most accurate model.




Required Libraries:
library(GGally)
library(MASS)
library(olsrr)

## Split to train and test
head(data)
      Price Mileage  Make   Model     Trim  Type Cylinder Liter Doors Cruise
 1 17314.10    8221 Buick Century Sedan 4D Sedan        6   3.1     4      1
 2 17542.04    9135 Buick Century Sedan 4D Sedan        6   3.1     4      1
 3 16218.85   13196 Buick Century Sedan 4D Sedan        6   3.1     4      1
 4 16336.91   16342 Buick Century Sedan 4D Sedan        6   3.1     4      1
 5 16339.17   19832 Buick Century Sedan 4D Sedan        6   3.1     4      1
 6 15709.05   22236 Buick Century Sedan 4D Sedan        6   3.1     4      1
   Sound Leather
 1     1       1
 2     1       0
 3     1       0
 4     0       0
 5     0       1
 6     1       0


## descriptive stats for continuous variables
*price*
resembles chi-square: many cars with low price, few with high price

 $n
 [1] 804
 
 $sumry
    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    8639   14273   18025   21343   26717   70755 
 
 $std
 [1] 9884.853
 
 $range
 [1] 62116.54
 
 $iqr
 [1] 12444.24
 
 $quant
        1%        5%       10%       15%       20%       25%       30%       35% 
  9654.414 11099.581 12109.914 12719.037 13508.657 14273.074 15058.614 15748.221 
       40%       45%       50%       55%       60%       65%       70%       75% 
 16407.638 17162.617 18024.995 19200.322 20537.898 21877.969 23423.405 26717.317 
       80%       85%       90%       95%       99% 
 29257.826 31321.155 35291.577 39864.709 55529.975


![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/1.png)


*Mileage*

 $n
 [1] 804
 
 $sumry
    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
     266   14624   20914   19832   25213   50387 
 
 $std
 [1] 8196.32
 
 $range
 [1] 50121
 
 $iqr
 [1] 10589.5
 
 $quant
       1%       5%      10%      15%      20%      25%      30%      35% 
  1178.33  4848.90  7901.60 10555.00 12783.40 14623.50 16625.10 17874.45 
      40%      45%      50%      55%      60%      65%      70%      75% 
 18946.80 19839.35 20913.50 21583.90 22381.60 23132.55 24078.40 25213.00 
      80%      85%      90%      95%      99% 
 25896.80 27185.05 28657.50 32606.40 38955.24
 
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/2.png)


*Liter* 
not realy continuos, you'll see later it behaves better as categorical
 $n
 [1] 804
 
 $sumry
    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
   1.600   2.200   2.800   3.037   3.800   6.000 
 
 $std
 [1] 1.105562
 
 $range
 [1] 4.4
 
 $iqr
 [1] 1.6
 
 $quant
  1%  5% 10% 15% 20% 25% 30% 35% 40% 45% 50% 55% 60% 65% 70% 75% 80% 85% 90% 95% 
 1.6 1.6 1.8 2.0 2.2 2.2 2.2 2.2 2.2 2.3 2.8 3.5 3.5 3.6 3.8 3.8 3.8 3.8 4.6 4.6 
 99% 
 6.0
 
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/3.png)

## correlations between Y and continuous variables and Scatterplots
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/4.png)

## Frequency table for categorical variables
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/5.png)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/6.png)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/7.png)
Sedan is by far most common
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/8.png)
Sedan 4D is by far most common
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/9.png)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/10.png)
We can still see the bimodal distribution around 2.2 and 3.8
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/11.png)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/12.png)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/13.png)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/14.png)

## cross tables - partial solution
almost always we have both
heat_map(data$Cruise, data$Sound)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/15.png)

almost always we have both
heat_map(data$Cruise, data$Leather)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/16.png)

almost always we have both
heat_map(data$Sound, data$Leather) 
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/17.png)

more liter mostly means 4 doors
heat_map(data$Liter, data$Doors) 
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/18.png)

very correlated!
heat_map(data$Liter, data$Cylinder)  
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/19.png)


## Boxplots of Y and the continuous X variables by value of each categorical variable - partial solution
evenly distributed (in this case all will be)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/gm_cars/20.png)


I used "stepAIC" - where the minimum model is:

'Price ~ 1'

The full model is:

'Price ~ Mileage + Make + Model + Trim + Type + Cylinder + Liter + Doors + Cruise + Sound + Leather'

The results of each test are-

forward-
  Step: AIC = 9379.66
  
'Price ~ Model + Mileage + Trim + Leather + Sound'

backwards-
Step: AIC = 9379.66

  Price ~ Mileage + Model + Trim + Sound + Leather

stepwise-
Step: AIC = 9379.66

  Price ~ Model + Trim + Mileage + Leather + Sound


  All methods gave the same model, so we just pull the metrics for this model

Quality indicators of the chosen model:


                          Model
                          
 R Square             0.9978704
 
 Adjusted R Square    0.9955939
 
 Mallow's Cp        -81.4574659
 
 AIC               1941.7014529
 
 BIC               2120.6320479
 
