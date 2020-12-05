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

Construction of a primary model after division into dummy variables.
Summary of the first model-

Species.Pike and Species.Smelt, this indicates that fish from those species have different weights than from other species, given the same
 values of other parameters.
 Note that Whitefish is our baseline hence omittied. Note that if you chose other basis, you could have got other significant Species.
 Length 1 is also significant. Length2 is not for alpha 0.05 but seems to be important since it is for alpha = 0.083.

 R ^ 2: 0.9361. 93% of the variability in Y is explained by X.

multicollinearity analysis-
![alt text](https://github.com/chencnaani/Data-Analysis-with-R/blob/master/lab%202/000003.png)


In the first model we can see most tolerance and VIF values ​​indicate multicollinearity.
length1, length2, length3 are extremely correlated. They are also very correlated with Height and Width.
length2 is almost completely explained by the the factor with the largest condition index. Length 1 is also at large explained by it.
width, height are largly explained by the factor with 54.49 condition index. length3 by the factor with 347.65 condition index.
all those indicate multicollinearity.

since length1, length2, length3 are so strongly correlated it is almost a state of complete multicollinearity. We will try to remove 2 of them.

Second model-

R ^ 2 is 0.9309, almost no change. This is because almost all the information in length2 and length3 is already included in the model by adding length1.

Still all the metrics indicate that there is a problem.
 We can see that length1, height and some of the species are still part of an approximate linear combination.
 You should have done another mid step, but we'll remove both Height and Width.

Third model-

 R ^ 2 still hasn't changed (96.83)
looks much better now.
 now, after we've learned some model fit metrics (such as BIC, AIC) we can comapre models acording
 to those metric as well
 try repeat the previous analysis and looking at AIC and R ^ 2-adjusted

![alt text](https://github.com/chencnaani/Data-Analysis-with-R/blob/master/lab%202/000003.png)


error analysis:
histogram of residuals-looks skewed

QQ Plot- confirms skew

Standartized residuals vs. prediction-

Standartized residuals vs. Length1-

Seems to be a connection between r and y_hat, caused by Length1. Higher values ​​of Length1 have higher residual variance. This looks like heteroscedasticity.

![alt text](https://github.com/chencnaani/Data-Analysis-with-R/blob/master/lab%202/1.jpg)

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

re-examine residuals

 Standartized residuals vs. prediction
![alt text](https://github.com/chencnaani/Data-Analysis-with-R/blob/master/lab%202/1.jpg)

Standartized residuals vs. Length1
![alt text](https://github.com/chencnaani/Data-Analysis-with-R/blob/master/lab%202/1.jpg)

looks significantly better.





