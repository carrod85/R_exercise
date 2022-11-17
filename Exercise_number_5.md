# Exercise number 5


> In the file TempEst.txt are average temperatures of every months in mea-
sured from 1866 to 2018 in Tartu (Estonia). Note that decimal places
separator is here comma. Please analyse this data in the following ways:
1) Compare average temperature and median temperature of every months.
Round these temperatures to 1 decimal place;
2) Compare distributions of monthly average with normal distribution. For
which month is normal distribution bets suited. For which months is normal
distribution farthest from reality. Apply for example Kolmogorov-Smirnov
or Shapiro-Wilk test. But all other goodness-of-fit tests are also acceptable;
3) Which conclusions would you draw from results of points 1) and 2).

We have to find out if the distribution follows a normal distribution or not. 

**H0= Normally distributed**
**H1!= Not normal**

How to find out that the distribution of temperatures follow normal distribution? There is no way to have a total certainty that it will follow that, however we can be sure when it isn't normal.
To help us accept or reject the null hypothesis H0 we can apply one of the several tests available for this. One can be Chi-squared test but also the Shapiro test suggested on the instructions of the task.
We will go to try the Shapiro Test and we will use the p-value indicator to accept or reject our hypothesis. On top of that we will calculate skeweness and kurtosis of our data to have more certainty of that (specially when our p-value is far from 1 (ideal)).
Shapiro test can be used for a sample size up to 2000 records

We first read the data and obtain from data median, mean and round the values
---
**loading file and obtaining basic parameters**
TempEst=read.table('./TempEst.txt',header=TRUE,sep="\t", dec=",")
attach(TempEst)
median=apply(TempEst, 2, median, na.rm=TRUE)
mean = colMeans(TempEst, na.rm=TRUE)

> round(median, digits= 1)
J    F  Mar  Apr  May  Jun  Jul  Aug Sept  Oct  Nov  Dec 
-5.6 -6.3 -2.4  4.0 10.9 14.9 17.1 15.6 10.8  5.5  0.3 -3.8




**Saving colnames in variable**
> namesOfColumns=colnames(TempEst, do.NULL = TRUE, prefix = "col")



**Printing them out THE SHAPIRO TEST RESULTS for Normality for every month.**
> for (val in namesOfColumns){print(shapiro.test(TempEst[[val]]))}

Results of Hypothesis Test
--------------------------

Alternative Hypothesis:          

Test Name:                       Shapiro-Wilk normality test

Data:                            TempEst[[val]]

Test Statistic:                  W = 0.9691068

P-value:                         0.00155946


Results of Hypothesis Test
--------------------------

Alternative Hypothesis:          

Test Name:                       Shapiro-Wilk normality test

Data:                            TempEst[[val]]

Test Statistic:                  W = 0.9916614

P-value:                         0.5069143


Results of Hypothesis Test
--------------------------

Alternative Hypothesis:          

Test Name:                       Shapiro-Wilk normality test

Data:                            TempEst[[val]]

Test Statistic:                  W = 0.9868421

P-value:                         0.1543043


Results of Hypothesis Test
--------------------------

Alternative Hypothesis:          

Test Name:                       Shapiro-Wilk normality test

Data:                            TempEst[[val]]

Test Statistic:                  W = 0.9903166

P-value:                         0.3736958


Results of Hypothesis Test
--------------------------

Alternative Hypothesis:          

Test Name:                       Shapiro-Wilk normality test

Data:                            TempEst[[val]]

Test Statistic:                  W = 0.8319313

P-value:                         5.19215e-12


Results of Hypothesis Test
--------------------------

Alternative Hypothesis:          

Test Name:                       Shapiro-Wilk normality test

Data:                            TempEst[[val]]

Test Statistic:                  W = 0.992624

P-value:                         0.6163172


Results of Hypothesis Test
--------------------------

Alternative Hypothesis:          

Test Name:                       Shapiro-Wilk normality test

Data:                            TempEst[[val]]

Test Statistic:                  W = 0.9764995

P-value:                         0.00977573


Results of Hypothesis Test
--------------------------

Alternative Hypothesis:          

Test Name:                       Shapiro-Wilk normality test

Data:                            TempEst[[val]]

Test Statistic:                  W = 0.9876659

P-value:                         0.1989633


Results of Hypothesis Test
--------------------------

Alternative Hypothesis:          

Test Name:                       Shapiro-Wilk normality test

Data:                            TempEst[[val]]

Test Statistic:                  W = 0.99459

P-value:                         0.8471508


Results of Hypothesis Test
--------------------------

Alternative Hypothesis:          

Test Name:                       Shapiro-Wilk normality test

Data:                            TempEst[[val]]

Test Statistic:                  W = 0.9842891

P-value:                         0.07963203


Results of Hypothesis Test
--------------------------

Alternative Hypothesis:          

Test Name:                       Shapiro-Wilk normality test

Data:                            TempEst[[val]]

Test Statistic:                  W = 0.9773938

P-value:                         0.01276409


Results of Hypothesis Test
--------------------------

Alternative Hypothesis:          

Test Name:                       Shapiro-Wilk normality test

Data:                            TempEst[[val]]

Test Statistic:                  W = 0.9799923

P-value:                         0.02444436

 


## KURTOSIS

> for (val in namesOfColumns){print(paste(val,kurtosis(TempEst[[val]], na.rm=TRUE)))}
[1] "J -0.345573555627177"
[1] "F -0.185510803056404"
[1] "Mar -0.179220048218813"
[1] "Apr -0.314910469515675"
[1] "May 19.5405616813947"
[1] "Jun -0.18344009444504"
[1] "Jul -0.0682939860289829"
[1] "Aug 0.0883120715299135"
[1] "Sept -0.254813056031095"
[1] "Oct -0.262823751009824"
[1] "Nov 0.0407711164537929"
[1] "Dec 0.602459203870844"



## SKEWNESS


> for (val in namesOfColumns){print(paste(val,skewness(TempEst[[val]], na.rm=TRUE)))}
[1] "J -0.503605398008498"
[1] "F -0.281133820643302"
[1] "Mar -0.347980229548974"
[1] "Apr -0.0894054288893054"
[1] "May 2.54271104993422"
[1] "Jun 0.113126040161845"
[1] "Jul 0.505348370504123"
[1] "Aug 0.369426398969964"
[1] "Sept -0.0657630925448627"
[1] "Oct -0.347926284878006"
[1] "Nov -0.504130929257893"
[1] "Dec -0.526562012858827"


The skewness will inform us about the skewnees of the normal distribution. It is accepted a deviation when the value of skewness is less than -2 and 2. This is intrensically related to the difference between median and mean. When these values are the same or close there is no skewness.
The kurtosis is  a measure of the "tailedness" and it is accepted also for values between -2 and 2. 

# Having perfomed all these tests we can come to the conclusion that January (P-value: 0.00155946) , May (P-value:   5.19215e-12, skewness: 2.54271104993422, kurtosis: 19.5405616813947), July (P-value:  0.00977573), November (P-value:  0.01276409) and December (P-value:  0.02444436)  don’t have normal distribution.
