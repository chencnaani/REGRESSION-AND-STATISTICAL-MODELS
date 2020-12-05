# *Regression-and-Statistical-Models*  

### Assignment given throughout the course


**Prediction of fish weight by type and length**

###### Background: 
In this task I was asked to build a model that would predict in the best way possible the weight of the fish.

The data I used was given to me as part of the course which include the following variables:
  "Species" "Weight" "Length1" "Length2" "Length3" "Height" "Width"

When 'Species' include:
  "Bream" "Roach" "Whitefish" "Parkki" "Perch" "Pike" "Melt"


###### Data analysis process and the selection of the model:

Required Libraries:
library(olsrr)
library(dummies) 
library(MASS)
library(ggplot2)

Presentation of the distribution of fish species-

![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/1.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/2.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/3.jpg)

Primary model after division into dummy variables.
Summary of the first model-

![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/4.jpg)

Species.Pike and Species.Smelt, this indicates that fish from those species have different weights than from other species, given the same
 values of other parameters.
 Note that Whitefish is our baseline hence omittied. Note that if you chose other basis, you could have got other significant Species.
 Length 1 is also significant. Length2 is not for alpha 0.05 but seems to be important since it is for alpha = 0.083.

 R ^ 2: 0.9361. 93% of the variability in Y is explained by X.

multicollinearity analysis-

![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/5.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/6.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/6.5.jpg)


In the first model we can see most tolerance and VIF values indicate multicollinearity.
length1, length2, length3 are extremely correlated. They are also very correlated with Height and Width.
length2 is almost completely explained by the the factor with the largest condition index. Length 1 is also at large explained by it.
width, height are largly explained by the factor with 54.49 condition index. length3 by the factor with 347.65 condition index.
all those indicate multicollinearity.

since length1, length2, length3 are so strongly correlated it is almost a state of complete multicollinearity. We will try to remove 2 of them.

Second model-

![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/7.jpg)

R ^ 2 is 0.9309, almost no change. This is because almost all the information in length2 and length3 is already included in the model by adding length1.

![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/8.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/9.jpg)

Still all the metrics indicate that there is a problem.
 We can see that length1, height and some of the species are still part of an approximate linear combination.
 You should have done another mid step, but we'll remove both Height and Width.

Third model-

![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/10.jpg)

 R ^ 2 still hasn't changed (96.83)
 
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/11.jpg)
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/12.jpg)

looks much better now.
 now, after we've learned some model fit metrics (such as BIC, AIC) we can comapre models acording
 to those metric as well
 try repeat the previous analysis and looking at AIC and R ^ 2-adjusted



error analysis:
histogram of residuals-looks skewed

![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/13.jpg)

QQ Plot- confirms skew

![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/14.jpg)

Standartized residuals vs. prediction-

![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/15.jpg)

Standartized residuals vs. Length1-

![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/16.jpg)

Seems to be a connection between r and y_hat, caused by Length1. Higher values of Length1 have higher residual variance. This looks like heteroscedasticity.

Interactions:
create all interactions (you might have used only part of them) -

len_Bream <- new_fish $ Length1 * new_fish $ Species.Bream

len_Parkki <- new_fish $ Length1 * new_fish $ Species.Parkki

len_Perch <- new_fish $ Length1 * new_fish $ Species.Perch

len_Pike <- new_fish $ Length1 * new_fish $ Species.Pike

len_Roach <- new_fish $ Length1 * new_fish $ Species.Roach

len_Smelt <- new_fish $ Length1 * new_fish $ Species.Smelt


Fourth model-
Including interactions

![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/17.jpg)

re-examine residuals

 Standartized residuals vs. prediction
 
![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/18.jpg)

Standartized residuals vs. Length1

![alt text](https://github.com/chencnaani/Regression-and-Statistical-Models/blob/master/figure-fish/19.jpg)

looks significantly better.





