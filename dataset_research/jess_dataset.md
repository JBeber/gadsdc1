#Infert Dataset Research 

This dataset is about the Infertility after Spontaneous and Induced Abortion.

## How I Lodaed the Data Set In 
Infert is a data set that comes pre-loaded into R. 

To load the infert data set into R. I used the following: 

data(infert)

##Structure of the Dataset 

The str fuction displays the structure of an object and tells me how many variables, objects of a data frame and displays the first few rows. 

By running  str(infert) 


I get this result: 
```
'data.frame':	248 obs. of  8 variables:
 $ education     : Factor w/ 3 levels "0-5yrs","6-11yrs",..: 1 1 1 1 2 2 2 2 2 2 ...
 $ age           : num  26 42 39 34 35 36 23 32 21 28 ...
 $ parity        : num  6 1 6 4 3 4 1 2 1 2 ...
 $ induced       : num  1 1 2 2 1 2 0 0 0 0 ...
 $ case          : num  1 1 1 1 1 1 1 1 1 1 ...
 $ spontaneous   : num  2 0 0 0 1 1 0 0 1 0 ...
 $ stratum       : int  1 2 3 4 5 6 7 8 9 10 ...
 $ pooled.stratum: num  3 1 4 2 32 36 6 22 5 19 ..
 ```

This tells me there are 248 objects loaded in my dataframe. The 8 columns of data for this dataset are  education, age, parity, induced, case, spontaneous, stratum, and pooled.stratum. 

To find missing values in each column, I used the sapply function. There were no missing values in any column: 

```
sapply(infert, function(x) sum(is.na(x)))
```

```
     education            age         parity        induced           case 
             0              0              0              0              0 
   spontaneous        stratum pooled.stratum 
             0              0              0 
```

## About the Dataset 

The help claims for R explains this dataset as a "This is a matched case-control study dating from before the availability of conditional logistic regression."

The dataset was from a 1976 schoolerly article called Induced abortion and secondary infertility by the following authors: Trichopoulos D, Handanos N, Danezis J, Kalandidi A, Kalapothaki V.

My dataset appears to have been written about often especally in writings that teach R since this is one of pre-loaded in datasets. Here is an example: [An Introduction to R](http://www.math.vu.nl/sto/onderwijs/statlearn/R-Binder.pdf)

##Simple Statistics for the Dataset

By running summary(infert) I was able to get simple statistics for each column

```
  education        age            parity         induced            case       
 0-5yrs : 12   Min.   :21.00   Min.   :1.000   Min.   :0.0000   Min.   :0.0000  
 6-11yrs:120   1st Qu.:28.00   1st Qu.:1.000   1st Qu.:0.0000   1st Qu.:0.0000  
 12+ yrs:116   Median :31.00   Median :2.000   Median :0.0000   Median :0.0000  
               Mean   :31.50   Mean   :2.093   Mean   :0.5726   Mean   :0.3347  
               3rd Qu.:35.25   3rd Qu.:3.000   3rd Qu.:1.0000   3rd Qu.:1.0000  
               Max.   :44.00   Max.   :6.000   Max.   :2.0000   Max.   :1.0000  
  spontaneous        stratum      pooled.stratum 
 Min.   :0.0000   Min.   : 1.00   Min.   : 1.00  
 1st Qu.:0.0000   1st Qu.:21.00   1st Qu.:19.00  
 Median :0.0000   Median :42.00   Median :36.00  
 Mean   :0.5766   Mean   :41.87   Mean   :33.58  
 3rd Qu.:1.0000   3rd Qu.:62.25   3rd Qu.:48.25  
 Max.   :2.0000   Max.   :83.00   Max.   :63.00 
 ```
Using the Hmisc package I was able to get some more indepth statistics for the datast. To run this package I used the following 

```
install.packages("Hmisc")
library(Hmisc)
describe(infert) 
```
The output using this package was a bit more discriptive. It included the following breakdown for each column n, nmiss, unique, mean, 5,10,25,50,75,90,95th percentiles and the 5 lowest and 5 highest scores. 
```
infert 

 8  Variables      248  Observations
-------------------------------------------------------------------------------------
education 
      n missing  unique 
    248       0       3 

0-5yrs (12, 5%), 6-11yrs (120, 48%), 12+ yrs (116, 47%) 
-------------------------------------------------------------------------------------
age 
      n missing  unique    Mean     .05     .10     .25     .50     .75     .90 
    248       0      21    31.5   24.00   25.00   28.00   31.00   35.25   39.00 
    .95 
  40.00 

lowest : 21 23 24 25 26, highest: 39 40 41 42 44 
-------------------------------------------------------------------------------------
parity 
      n missing  unique    Mean 
    248       0       6   2.093 

           1  2  3  4 5 6
Frequency 99 81 36 18 6 8
%         40 33 15  7 2 3
-------------------------------------------------------------------------------------
induced 
      n missing  unique    Mean 
    248       0       3  0.5726 

0 (143, 58%), 1 (68, 27%), 2 (37, 15%) 
-------------------------------------------------------------------------------------
case 
      n missing  unique     Sum    Mean 
    248       0       2      83  0.3347 
-------------------------------------------------------------------------------------
spontaneous 
      n missing  unique    Mean 
    248       0       3  0.5766 

0 (141, 57%), 1 (71, 29%), 2 (36, 15%) 
-------------------------------------------------------------------------------------
stratum 
      n missing  unique    Mean     .05     .10     .25     .50     .75     .90 
    248       0      83   41.87    5.00    9.00   21.00   42.00   62.25   75.00 
    .95 
  79.00 

lowest :  1  2  3  4  5, highest: 79 80 81 82 83 
-------------------------------------------------------------------------------------
pooled.stratum 
      n missing  unique    Mean     .05     .10     .25     .50     .75     .90 
    248       0      63   33.58    5.00    9.00   19.00   36.00   48.25   55.00 
    .95 
  59.00 

lowest :  1  2  3  4  5, highest: 59 60 61 62 63 
-------------------------------------------------------------------------------------
```
