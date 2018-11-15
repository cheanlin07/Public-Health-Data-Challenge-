# Public-Health-Data-Challenge-Drug & Alcohol Addiction
A data visualization project that analyzes the age groups affected by drug &amp; alcohol overdoses in the top five states with their death rates.

The project was an entry to participate in the annual public health data challenge created by the American Statistical Association. 

Team Name: Regeanomics

Team Members: Che-An Lin, Jenna Monchamp, Zach Schwartz, Lordia Larbi-Asare

Team Sponsor: Nicholas Reich

Course Name: PUBLTH460 Telling Stories with Data - class is taught by Nicholas Reich

Data analysis and visualization were created using R. 

Powerpoint was created using Google Slide.

Dataset is provided from Centers for Disease Control and Prevention: https://wonder.cdc.gov/mcd.html

The complete output of the code is published in Rpubs: http://rpubs.com/andy890928/asachallenge460

The goal of this project is to analyze the age groups affected by drugs &amp; alcohol overdoses in the top 5 states with their death rates, and determine the relationship between the death rate and causes of death.

We used bar charts to show the death rates and causes of death in the top five states

![alt text](https://i.imgur.com/XSPtJWQ.jpg)
![alt text](https://i.imgur.com/diObLCu.jpg)

We used linear regression to determine the relationship between the death rate and causes of death

```{r}
library(ggplot2)
#Import the dataset to RStudio
Data <- read.delim("MCDthisOne.txt", header = T)

Data_Drug <- Data[Data$MCD...Drug.Alcohol.Induced.Code == "D",]
Data_Alcohol <- Data[Data$MCD...Drug.Alcohol.Induced.Code == "A",]
Data_Other <- Data[Data$MCD...Drug.Alcohol.Induced.Code == "O",]

#Determine the R-squared value for regression analysis
m1 <- lm(Deaths ~ (MCD...Drug.Alcohol.Induced.Code == "A") + Ten.Year.Age.Groups, data = Data_Alcohol)
summary(m1)

m2 <- lm(Deaths~(MCD...Drug.Alcohol.Induced.Code == "D") + Ten.Year.Age.Groups, data = Data_Drug)
summary(m2)

#Determine the correlation value for regression analysis
cor(as.numeric(Data_Alcohol$Ten.Year.Age.Groups), Data_Alcohol$Deaths)
cor(as.numeric(Data_Drug$Ten.Year.Age.Groups), Data_Drug$Deaths)
```
