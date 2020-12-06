# *Regression-and-Statistical-Models*  

### Assignment given throughout the course


**Predicts which Titanic passengers will survive **

###### Background: 
In this section I got data on the passengers of the Titanic ship that include the following data:

survival -> Survival 0 = No, 1 = Yes

pclass-> Ticket class 1 = 1st, 2 = 2nd, 3 = 3rd

sex-> Sex

Age -> Age in years

sibsp -> # of siblings / spouses

parch-> # of parents / children

ticket -> Ticket number

fare-> Passenger fare

cabin-> Cabin number

embarked -> Port of Embarkation

And I will engage in logistical regression and build a model that predicts which Titanic passengers will be rescued.


Required Libraries:
library(dummies) 

library(dplyr)

library(bestglm)

library(tidyverse)

library(MASS)

library(data.table)

library(olsrr)

library(Hmisc)

library(GGally)

library(RCurl)

library(ggplot2)

## Split to train and test


## Summary
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot.jpg)

### 'Survived'

$n

[1] 606

$sumry

Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 

0.0000  0.0000  0.0000  0.4076  1.0000  1.0000 

$std

[1] 0.4917923

$range

[1] 1

$iqr

[1] 1

$quant

1%  5% 10% 15% 20% 25% 30% 35% 40% 45% 50% 55% 60% 65% 70% 75% 80% 85% 90% 95% 99% 

0   0   0   0   0   0   0   0   0   0   0   0   1   1   1   1   1   1   1   1   1 


### 'Age'

$n
[1] 606

$sumry
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
   0.42   21.00   28.00   29.92   38.00   80.00 

$std
[1] 14.49714

$range
[1] 79.58

$iqr
[1] 17

$quant
   1%    5%   10%   15%   20%   25%   30%   35%   40%   45%   50%   55%   60%   65%   70%   75%   80%   85%   90%   95%   99% 
 1.00  4.00 14.25 17.00 19.00 21.00 22.00 24.00 25.00 27.00 28.00 30.00 32.00 34.00 36.00 38.00 42.00 45.00 50.00 56.75 69.80 

### 'SibSp'

$n
[1] 606

$sumry
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
 0.0000  0.0000  0.0000  0.5132  1.0000  5.0000 

$std
[1] 0.9067191

$range
[1] 5

$iqr
[1] 1

$quant
 1%  5% 10% 15% 20% 25% 30% 35% 40% 45% 50% 55% 60% 65% 70% 75% 80% 85% 90% 95% 99% 
  0   0   0   0   0   0   0   0   0   0   0   0   0   1   1   1   1   1   1   2   4 


### 'Parch'

$n
[1] 606

$sumry
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
 0.0000  0.0000  0.0000  0.4158  1.0000  6.0000 

$std
[1] 0.8304215

$range
[1] 6

$iqr
[1] 1

$quant
 1%  5% 10% 15% 20% 25% 30% 35% 40% 45% 50% 55% 60% 65% 70% 75% 80% 85% 90% 95% 99% 
  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   1   1   1   2   2   4 

### 'Fare'

$n
[1] 606

$sumry
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
   0.00    8.05   15.90   35.43   34.38  512.33 

$std
[1] 54.39026

$range
[1] 512.3292

$iqr
[1] 26.325

$quant
        1%         5%        10%        15%        20%        25%        30%        35%        40%        45%        50% 
  4.061875   7.229200   7.750000   7.854200   7.925000   8.050000   9.220850  10.500000  13.000000  13.000000  15.900000 
       55%        60%        65%        70%        75%        80%        85%        90%        95%        99% 
 20.562500  26.000000  26.550000  29.125000  34.375000  49.504200  65.400000  80.929150 120.000000 261.632290 



![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot2.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot3.jpg)


![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot4.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot5.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot6.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot7.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot8.jpg)



![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot9.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot10.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot11.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot12.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot13.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot14.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot15.jpg)


![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot16.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot17.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot18.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot19.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot20.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot21.jpg)

The chances of survival by age vary depending on the sex: men have a high chance of survival at the ages of 14-40 and women at the ages of 18-30.
Pclass Embarked have high correlation with the explained variable. Particularly Class 1 passengers have a particularly high chance of surviving compared to Class 3 where the chances are very low.

There are coordinated variables - age and gender, ticket price and department.

I used "stepAIC" - where the minimum model is:

'Survived ~ Age'

The full model is:

'Survived~ Age + SibSp + Parch + Fare + Sex + Embarked +Pclass'

The results of each test are-

forward- Step: AIC: 572.39

'Survived ~ Age + Sex + Pclass + SibSp'

backwards- Step: AIC=572.39

Survived ~ Age + Sex + Pclass + SibSp

both- Step: AIC=821.98

Survived ~ Age

The best model seems to be-
Survived ~ Age + Sex + Pclass + SibSp


![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot22.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot23.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot24.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot25.jpg)


![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot26.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot27.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot28.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot29.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot30.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot31.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/Titanic/rplot32.jpg)


With the results of the residue analysis, it seems that the model needs to be manipulated in order to make it more accurate.

The additional models offered-
model_1 <-glm (Survived ~ class1 + class2 + Male + SibSp + Parch + SibSp * Parch + Age + class1 * Age + class2 * Age, family = binomial (link = 'logit'), data = train_b)

AIC = 556,477


model_2 <- glm (Survived ~ class1 + class2 + Male + SibSp + Parch + SibSp * Parch + Age + class1 * Male + class2 * Male,
family = binomial (link = 'logit'), data = train_b)

AIC = 525.7151


model_3 <-glm (Survived ~ class1 + class2 + Male + SibSp + Parch + SibSp * Parch + Age + class1 * Parch + class2 * Parch, family = binomial (link = 'logit'), data = train_b)

AIC = 545.6214


model_4 <-glm (Survived ~ class1 + class2 + Male + SibSp + Parch + SibSp * Parch + Age + Age ^ 2, family = binomial (link = 'logit'), data = train_b)

AIC = 553.1103

Residues There seems to be a problem in adjusting the residues and therefore we will perform transformations to the variables.

SibSp * Parch
class1 * Male
class2 * Male

And after testing the percentage accuracy of the model according to the test data it seems that there is an accuracy of 0.8796296 for model 2
