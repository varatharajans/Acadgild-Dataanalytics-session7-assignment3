# Acadgild-Dataanalytics-session7-assignment3
DATA ANALYTICS WITH R, EXCEL AND TABLEAU SESSION 7ASSIGNMENT 3
 & next
(Box plot & Whiskers) as separate markdown 
 
varatharajan
June 14, 2018

1. Create a box and whisker plot by class using mtcars dataset.

summary(cars)
boxplot(mtcars$mpg)
boxplot(mtcars$mpg, horizontal = TRUE)
boxplot(mtcars$mpg, col = 'blue')
boxplot(mtcars$mpg, border = 'red')
boxplot(mtcars$mpg, range = 0)
boxplot(mtcars$mpg, range = 1)
boxplot(mtcars$mpg, range = 1, outline = FALSE)
boxplot(mtcars$mpg ~ mtcars$cyl)
mpg_split <- split(mtcars$mpg, mtcars$cyl)
mpg_split
mpg_4 <- mpg_split$`4`
mpg_6 <- mpg_split$`6`
mpg_8 <- mpg_split$`8`
boxplot(mpg_4, mpg_6, mpg_8)
boxplot(mtcars$mpg ~ mtcars$cyl, col = 'blue')
boxplot(mtcars$mpg ~ mtcars$cyl,col = c('red', 'blue', 'yellow'))
boxplot(mtcars$mpg ~ mtcars$cyl, range = 1, outline = TRUE,horizontal = TRUE, col = c('red', 'blue', 'yellow'), main = 'Miles Per Gallon by Cylinders',ylab = 'Number of Cylinders', xlab = 'Miles Per Gallon',names = c('Four', 'Six', 'Eight'))



{r setup, include=FALSE} knitr::opts_chunk$set(echo = TRUE)

            

session7 assignment3
(Box plot & Whiskers)
varatharajan
June 14, 2018

library(ggplot2)
library(xtable)
head(mtcars)
mtcars$cyl <- factor(mtcars$cyl)
mtcars$labels <- row.names(mtcars)
summary(mtcars)
library(gridExtra)
library(ggplot2)
library(ggthemes)
library(tufte)
p <- ggplot(data = mtcars, aes(x = cyl, y = mpg, fill = cyl))

p <- p + geom_boxplot() +ggtitle("Car Milage Data") +labs(x = "Number of Cylinders", y = "Miles Per Gallon") +scale_fill_discrete(name = "Cylinders")

p

p <- ggplot(mtcars, aes(x = wt, y = mpg)) +geom_point() +ggtitle("Cars")
p2 <- ggplot(mtcars, aes(x = wt, y = mpg, colour = factor(gear))) +geom_point() +ggtitle("Cars")

p3 <- p2 + facet_wrap(~ am)p + geom_rangeframe() +theme_tufte() + scale_x_continuous(breaks = extended_range_breaks()(mtcars$wt)) +scale_y_continuous(breaks = extended_range_breaks()(mtcars$mpg))

p4 <- ggplot(mtcars, aes(factor(cyl), mpg))p4 + theme_tufte(ticks=FALSE) + geom_tufteboxplot()p4 + theme_tufte(ticks=FALSE) +geom_tufteboxplot(median.type = "line")p4 + theme_tufte(ticks=FALSE) +geom_tufteboxplot(median.type = "line", whisker.type = 'point', hoffset = 0)p4 + theme_tufte(ticks=FALSE) +geom_tufteboxplot(median.type = "line", whisker.type = 'line', hoffset = 0, width = 3)

{r setup, include=FALSE} knitr::opts_chunk$set(echo = TRUE)


mpg
<dbl>	cyl
<fctr>	disp
<dbl>	hp
<dbl>	drat
<dbl>	wt
<dbl>	qsec
<dbl>	vs
<dbl>	am
<fctr>	
Mazda RX4	21.0	6cyl	160	110	3.90	2.620	16.46	0	Manual	
Mazda RX4 Wag	21.0	6cyl	160	110	3.90	2.875	17.02	0	Manual	
Datsun 710	22.8	4cyl	108	93	3.85	2.320	18.61	1	Manual	
Hornet 4 Drive	21.4	6cyl	258	110	3.08	3.215	19.44	1	Automatic	
Hornet Sportabout	18.7	8cyl	360	175	3.15	3.440	17.02	0	Automatic	
Valiant	18.1	6cyl	225	105	2.76	3.460	20.22	1	Automatic	
6 rows | 1-10 of 12 columns
 

 
 	mpg
<dbl>	cyl
<fctr>	disp
<dbl>	hp
<dbl>	drat
<dbl>	wt
<dbl>	
Mazda RX4	21.0	6cyl	160	110	3.90	2.620	
Mazda RX4 Wag	21.0	6cyl	160	110	3.90	2.875	
Datsun 710	22.8	4cyl	108	93	3.85	2.320	
Hornet 4 Drive	21.4	6cyl	258	110	3.08	3.215	
Hornet Sportabout	18.7	8cyl	360	175	3.15	3.440	
Valiant	18.1	6cyl	225	105	2.76	3.460	
							
6 rows | 1-7 of 12 columns
data.frame
6 x 12
      mpg          cyl          disp             hp             drat      
 Min.   :10.40   4cyl:11   Min.   : 71.1   Min.   : 52.0   Min.   :2.760  
 1st Qu.:15.43   6cyl: 7   1st Qu.:120.8   1st Qu.: 96.5   1st Qu.:3.080  
 Median :19.20   8cyl:14   Median :196.3   Median :123.0   Median :3.695  
 Mean   :20.09             Mean   :230.7   Mean   :146.7   Mean   :3.597  
 3rd Qu.:22.80             3rd Qu.:326.0   3rd Qu.:180.0   3rd Qu.:3.920  
 Max.   :33.90             Max.   :472.0   Max.   :335.0   Max.   :4.930  
       wt             qsec             vs                 am         gear   
 Min.   :1.513   Min.   :14.50   Min.   :0.0000   Automatic:19   3gears:15  
 1st Qu.:2.581   1st Qu.:16.89   1st Qu.:0.0000   Manual   :13   4gears:12  
 Median :3.325   Median :17.71   Median :0.0000                  5gears: 5  
 Mean   :3.217   Mean   :17.85   Mean   :0.4375                             
 3rd Qu.:3.610   3rd Qu.:18.90   3rd Qu.:1.0000                             
 Max.   :5.424   Max.   :22.90   Max.   :1.0000                             
      carb          labels         
 Min.   :1.000   Length:32         
 1st Qu.:2.000   Class :character  
 Median :2.000   Mode  :character  
 Mean   :2.812                     
 3rd Qu.:4.000                     
 Max.   :8.000                     
R Console
 
 

  


p3 <- p2 + facet_wrap(~ am)p + geom_rangeframe() +theme_tufte() + 
scale_x_continuous(breaks = extended_range_breaks()(mtcars$wt)) +
scale_y_continuous(breaks = extended_range_breaks()(mtcars$mpg))
 


Whisker type box plot


p4 <- ggplot(mtcars, aes(factor(cyl), mpg))p4 + theme_tufte(ticks=FALSE) + geom_tufteboxplot()p4 + theme_tufte(ticks=FALSE) +geom_tufteboxplot(median.type = "line")p4 + theme_tufte(ticks=FALSE) +geom_tufteboxplot(median.type = "line", whisker.type = 'point', hoffset = 0)p4 + theme_tufte(ticks=FALSE) +geom_tufteboxplot(median.type = "line", whisker.type = 'line', hoffset = 0, width = 3)


 

R Markdown
This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see http://rmarkdown.rstudio.com.
When you click the Knit button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:
{r cars} summary(cars)
Including Plots
You can also embed plots, for example:
{r pressure, echo=FALSE} plot(pressure)
Note that the echo = FALSE parameter was added to the code chunk to prevent printing of the R code that generated the plot.

R Markdown
This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see http://rmarkdown.rstudio.com.
When you click the Knit button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:
{r cars} summary(cars)
Including Plots
You can also embed plots, for example:
{r pressure, echo=FALSE} plot(pressure)
Note that the echo = FALSE parameter was added to the code chunk to prevent printing of the R code that generated the plot.
 
     speed           dist       
 Min.   : 4.0   Min.   :  2.00  
 1st Qu.:12.0   1st Qu.: 26.00  
 Median :15.0   Median : 36.00  
 Mean   :15.4   Mean   : 42.98  
 3rd Qu.:19.0   3rd Qu.: 56.00  
 Max.   :25.0   Max.   :120.00  
$`4cyl`
 [1] 22.8 24.4 22.8 32.4 30.4 33.9 21.5 27.3 26.0 30.4 21.4

$`6cyl`
[1] 21.0 21.0 21.4 18.1 19.2 17.8 19.7

$`8cyl`
 [1] 18.7 14.3 16.4 17.3 15.2 10.4 10.4 14.7 15.5 15.2 13.3 19.2 15.8 15.0

R Console


