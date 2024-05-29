**R-Project(Ongoing project...)**
**Predicting the chances of a customer giving a positive response(Data Exploration, cleaning, formatting and analysis)**

***Overview***
A superstore is planning for the year-end sale.They want to launch a new offer - gold membership, that gives a 20% discount on all purchases, for only $499 which is $999 on other days.It will be valid only for existing customers and the campaign through phone calls is currently being planned for them. The management feels that the best way to reduce the cost of the campaign is to make a predictive model which will classify customers who might purchase the offer.

***Objectives***
Work will aim to meet the following objectives; 
i. To predict the likelihood of the customers giving a positive response. 
ii. To identify the different factors that affect a customer’s response.

***Questions***
The work will seek to answer the following questions; 
i) What is the likelihood of the customers giving a positive response? 
ii) What are the factors that affect a customer’s response?

***Metrics for Success***
For this work, the success will include coming up with a model that correctly predicts the likelihood of a customer to give a positive response. Success will also be achieved by correctly analyzing and establishing the factors that contribute towards a customer giving a positive response to the Superstore campaign.
We aim to achieve an accuracy level of 90%.

***The Experimental Design***
Below are the steps taken in this analysis 
a. Loading the required libraries 
b. Loading and previewing data 
c. Cleaning the data 
d. Exploratory Data Analysis(EDA) 
e. Creating a model to predict 
d. Drawing conclusions 
e. Giving Recommendations

**Data Relevance and Validation**
The data available is relevant for the intended analysis. It contains information that is significant to predicting the likelihood of a customer giving a positive response. It has data on customers income, education levels, marital status, children in the households, shopping trends, and the responses and complaints.

***Understanding the context The data set we are to work with contains the following columns:***

| **ID** | **Attribute** | **Description** |
|--------|---------------|-----------------|
| a.     | ID            | Unique ID of each customer |
| b.     | Year_Birth    | Age of the customer |
| c.     | Complain      | 1 if the customer complained in the last 2 years |
| d.     | Dt_Customer   | Date of customer’s enrollment with the company |
| e.     | Education     | Customer’s level of education |
| f.     | Marital       | Customer’s marital status |
| g.     | Kidhome       | Number of small children in customer’s household |
| h.     | Teenhome      | Number of teenagers in customer’s household |
| i.     | Income        | Customer’s yearly household income |
| j.     | MntFishProducts | The amount spent on fish products in the last 2 years |
| k.     | MntMeatProducts | The amount spent on meat products in the last 2 years |
| l.     | MntFruits     | The amount spent on fruits products in the last 2 years |
| m.     | MntSweetProducts | Amount spent on sweet products in the last 2 years |
| n.     | MntWines      | The amount spent on wine products in the last 2 years |
| o.     | MntGoldProds  | The amount spent on gold products in the last 2 years |
| p.     | NumDealsPurchases | Number of purchases made with discount |
| q.     | NumCatalogPurchases | Number of purchases made using catalog (buying goods to be shipped through the mail) |
| r.     | NumStorePurchases | Number of purchases made directly in stores |
| s.     | NumWebPurchases | Number of purchases made through the company’s website |
| t.     | NumWebVisitsMonth | Number of visits to company’s website in the last month |
| u.     | Response (target) | 1 if customer accepted the offer in the last campaign, 0 otherwise |
| v.     | Recency       | Number of days since the last purchase |


The dataset has 2240 observations and 22 columns

This dataset can be accessed from this link:Superstore Marketing Campaign

**Reading and Understanding The Dataset**
***importing the data***

```
store_data = read.csv("superstore_data.csv")

```
* Reading the first five rows of the data set
```
head(superstore_data,5)

```
```
##      Id Year_Birth  Education Marital_Status Income Kidhome Teenhome
## 1  1826       1970 Graduation       Divorced  84835       0        0
## 2     1       1961 Graduation         Single  57091       0        0
## 3 10476       1958 Graduation        Married  67267       0        1
## 4  1386       1967 Graduation       Together  32474       1        1
## 5  5371       1989 Graduation         Single  21474       1        0
##   Dt_Customer Recency MntWines MntFruits MntMeatProducts MntFishProducts
## 1   6/16/2014       0      189       104             379             111
## 2   6/15/2014       0      464         5              64               7
## 3   5/13/2014       0      134        11              59              15
## 4   11/5/2014       0       10         0               1               0
## 5    8/4/2014       0        6        16              24              11
##   MntSweetProducts MntGoldProds NumDealsPurchases NumWebPurchases
## 1              189          218                 1               4
## 2                0           37                 1               7
## 3                2           30                 1               3
## 4                0            0                 1               1
## 5                0           34                 2               3
##   NumCatalogPurchases NumStorePurchases NumWebVisitsMonth Response Complain
## 1                   4                 6                 1        1        0
## 2                   3                 7                 5        1        0
## 3                   2                 5                 2        0        0
## 4                   0                 2                 7        0        0
## 5                   1                 2                 7        1        0
```

* Reading the last 5 rows of the data set
```
tail(superstore_data,5)
```
```
##         Id Year_Birth  Education Marital_Status Income Kidhome Teenhome
## 2236 10142       1976        PhD       Divorced  66476       0        1
## 2237  5263       1977   2n Cycle        Married  31056       1        0
## 2238    22       1976 Graduation       Divorced  46310       1        0
## 2239   528       1978 Graduation        Married  65819       0        0
## 2240  4070       1969        PhD        Married  94871       0        2
##      Dt_Customer Recency MntWines MntFruits MntMeatProducts MntFishProducts
## 2236    7/3/2013      99      372        18             126              47
## 2237   1/22/2013      99        5        10              13               3
## 2238   3/12/2012      99      185         2              88              15
## 2239  11/29/2012      99      267        38             701             149
## 2240    1/9/2012      99      169        24             553             188
##      MntSweetProducts MntGoldProds NumDealsPurchases NumWebPurchases
## 2236               48           78                 2               5
## 2237                8           16                 1               1
## 2238                5           14                 2               6
## 2239              165           63                 1               5
## 2240                0          144                 1               8
##      NumCatalogPurchases NumStorePurchases NumWebVisitsMonth Response Complain
## 2236                   2                11                 4        0        0
## 2237                   0                 3                 8        0        0
## 2238                   1                 5                 8        0        0
## 2239                   4                10                 3        0        0
## 2240                   5                 4                 7        1        0
```

* Checking for the data types of the variables
```
str(superstore_data)
```
```
## 'data.frame':    2240 obs. of  22 variables:
##  $ Id                 : int  1826 1 10476 1386 5371 7348 4073 1991 4047 9477 ...
##  $ Year_Birth         : int  1970 1961 1958 1967 1989 1958 1954 1967 1954 1954 ...
##  $ Education          : chr  "Graduation" "Graduation" "Graduation" "Graduation" ...
##  $ Marital_Status     : chr  "Divorced" "Single" "Married" "Together" ...
##  $ Income             : int  84835 57091 67267 32474 21474 71691 63564 44931 65324 65324 ...
##  $ Kidhome            : int  0 0 0 1 1 0 0 0 0 0 ...
##  $ Teenhome           : int  0 0 1 1 0 0 0 1 1 1 ...
##  $ Dt_Customer        : chr  "6/16/2014" "6/15/2014" "5/13/2014" "11/5/2014" ...
##  $ Recency            : int  0 0 0 0 0 0 0 0 0 0 ...
##  $ MntWines           : int  189 464 134 10 6 336 769 78 384 384 ...
##  $ MntFruits          : int  104 5 11 0 16 130 80 0 0 0 ...
##  $ MntMeatProducts    : int  379 64 59 1 24 411 252 11 102 102 ...
##  $ MntFishProducts    : int  111 7 15 0 11 240 15 0 21 21 ...
##  $ MntSweetProducts   : int  189 0 2 0 0 32 34 0 32 32 ...
##  $ MntGoldProds       : int  218 37 30 0 34 43 65 7 5 5 ...
##  $ NumDealsPurchases  : int  1 1 1 1 2 1 1 1 3 3 ...
##  $ NumWebPurchases    : int  4 7 3 1 3 4 10 2 6 6 ...
##  $ NumCatalogPurchases: int  4 3 2 0 1 7 10 1 2 2 ...
##  $ NumStorePurchases  : int  6 7 5 2 2 5 7 3 9 9 ...
##  $ NumWebVisitsMonth  : int  1 5 2 7 7 2 6 5 4 4 ...
##  $ Response           : int  1 1 0 0 1 1 1 0 0 0 ...
##  $ Complain           : int  0 0 0 0 0 0 0 0 0 0 ...
```
The output shows that the dataset has 22 columns and 2240 rows.With 3 characters and the rest as integers.

* Checking the dimension of the data
```
dim(superstore_data)
```
```
## [1] 2240   22
```
This dataset has 2240 rows and 22 columns

**Cleaning the Dataset**
***Checking for missing variables***
```
colSums(is.na(superstore_data))
```
```
##                  Id          Year_Birth           Education      Marital_Status 
##                   0                   0                   0                   0 
##              Income             Kidhome            Teenhome         Dt_Customer 
##                  24                   0                   0                   0 
##             Recency            MntWines           MntFruits     MntMeatProducts 
##                   0                   0                   0                   0 
##     MntFishProducts    MntSweetProducts        MntGoldProds   NumDealsPurchases 
##                   0                   0                   0                   0 
##     NumWebPurchases NumCatalogPurchases   NumStorePurchases   NumWebVisitsMonth 
##                   0                   0                   0                   0 
##            Response            Complain 
##                   0                   0
```
This shows that the Income column is the only one with missing values.

* Replacing the missing values with the mean of the column
```
superstore_data = store_data %>%
  mutate(Income = if_else(is.na(Income), mean(Income, na.rm = TRUE), Income))
```
* Checking to confirm the missing variables have been filled
```
colSums(is.na(superstore_data))
```
```
##                  Id          Year_Birth           Education      Marital_Status 
##                   0                   0                   0                   0 
##              Income             Kidhome            Teenhome         Dt_Customer 
##                   0                   0                   0                   0 
##             Recency            MntWines           MntFruits     MntMeatProducts 
##                   0                   0                   0                   0 
##     MntFishProducts    MntSweetProducts        MntGoldProds   NumDealsPurchases 
##                   0                   0                   0                   0 
##     NumWebPurchases NumCatalogPurchases   NumStorePurchases   NumWebVisitsMonth 
##                   0                   0                   0                   0 
##            Response            Complain 
##                   0                   0
```
Observation: This shows that all missing values have been replaced with the mean,hence no missing values.

* Checking for the unique values in the Marital Status column
```
library(dplyr)
```
```
unique_values<-unique(superstore_data$Marital_Status)

```
```
unique_values
## [1] "Divorced" "Single"   "Married"  "Together" "Widow"    "YOLO"     "Alone"   
## [8] "Absurd"
```
* Changing the variables in the Marital status column that are not in line
```
superstore_data = superstore_data %>% 
  mutate(Marital_Status = case_when(
    Marital_Status == "YOLO" ~ "Single",
    Marital_Status == "Alone" ~ "Single",
    Marital_Status == "Absurd" ~ "Single",
    TRUE ~ Marital_Status
  ))

```

* Checking to see whether the variables in the Marital Status column have been changed
```
unique_marital<-unique(superstore_data$Marital_Status)
unique_marital
```
```
* Checking to see whether the variables in the Marital Status column have been changed
unique_marital<-unique(superstore_data$Marital_Status)
unique_marital
## [1] "Divorced" "Single"   "Married"  "Together" "Widow"
```

**Performing Exploratory Data Analysis**

* A pie chart of the educational level of the customers
```
Education <-table(superstore_data$Education)
Education
```
```
## 
##   2n Cycle      Basic Graduation     Master        PhD 
##        203         54       1127        370        486
```
```
pie(Education, col=hcl.colors(5))
```
![download](https://github.com/TabithaChelagat/R-Project/assets/112205355/4bc9ea2d-b3eb-4e2f-9f1d-ea08a123dfbe)

Observation: 
Most of the customers are in the graduation sub-category, this is followed by those who hold PHDs and Masters. The least are those with basic education.

* Ggplot comparing Income vs Education
```
library("ggplot2") #Library that supports plotting
ggplot(data=superstore_data)+
  geom_bar(mapping = aes(x = Education, y = Income, fill = Education, color = "purple"), stat = "identity")+
  labs(title = "Income Vs Education", x = "Education", y = "Income")
```
![download](https://github.com/TabithaChelagat/R-Project/assets/112205355/bc31c8cb-9b1d-4baa-a6d5-a06cde7fac65)

Observation: 
The ggplot shows that those who have graduated have the highest income with those with basic education have the least income.

* A scatter plot of year of birth vs sweet products
```
ggplot(data=superstore_data)+
  geom_point(mapping = aes(x = Year_Birth, y = MntSweetProducts, color = "navy"))+
  labs(title = "Year of birth vs sweet products", x = "Year of Birth", y = "Sweet Products")
```
![download](https://github.com/TabithaChelagat/R-Project/assets/112205355/8f5317e7-2efb-4a5e-8cc0-fb1bfa5ad417)

Observation: 
The scatter shows that majority of the people born between 1950 and 1980 are the most purchases of sweet products.

* A table of complains
```
complains<-table(superstore_data$Complain)
complains
```
```
## 
##    0    1 
## 2219   21
```
* Barplot of complains
```
barplot(complains)
```
![download](https://github.com/TabithaChelagat/R-Project/assets/112205355/95b7e423-93c6-44da-90f8-8f3f67ab0830)

Observation: 
The barplot for complains showing that the data is imbalanced

* Comparing the Year of birth against Complain
```
ggplot(data=superstore_data)+
  geom_bar(mapping = aes(y=Complain, x=Year_Birth, fill="purple"), stat ="identity")+
  labs(title="Complains is relation to year of birth", y="Complain", x="Year of Birth")
```
![download](https://github.com/TabithaChelagat/R-Project/assets/112205355/7d47a848-f483-4880-bd9b-b93d0db484ab)

Observation: Most complaints were recorded from customers born between 1950 and 1980.

* Barplot for response
```
responses<-table(superstore_data$Response)
barplot(responses)
```
![download](https://github.com/TabithaChelagat/R-Project/assets/112205355/62c5cede-8e95-4a48-9fd7-e7e711758767)

Observation: 
This barplot shows the variance of Responses which shows imbalanced data.

* Comparing the Year of birth against Response
```
ggplot(data=superstore_data)+
  geom_bar(mapping = aes(x=Year_Birth, y=Response, fill="purple"), stat ="identity")+
  labs(title="Response is relation to year of birth", x="Year of Birth", y="Response")
```

![download](https://github.com/TabithaChelagat/R-Project/assets/112205355/74b1f1ef-0ca4-49d6-b356-be0cb4491d5b)

Observation: 
Most responses were recorded from customers born from 1940. the highest number came from customers born around 1970.

* Scatter plot between Year of birth and Fish products
```
ggplot(data=superstore_data)+
  geom_point(mapping = aes(x=Year_Birth, y=MntFishProducts, color="navy"), stat ="identity")+
  labs(title="MntFishProducts is relation to year of birth", x="Year of Birth", y="MntFishProducts")
```
![download](https://github.com/TabithaChelagat/R-Project/assets/112205355/21279256-34d5-481c-83b2-4a4e01a0ac18)

* Scatter plot showing year of birth versus amount of wine purchased 
```
ggplot(data=superstore_data)+
  geom_point(mapping = aes(x=Year_Birth, y=MntWines, color="navy"), stat ="identity")+
  labs(title="MntWines is relation to year of birth", x="Year of Birth", y="MntWines")
```

![download](https://github.com/TabithaChelagat/R-Project/assets/112205355/9601ccdf-93b0-4a57-827b-893cc5658f1b)

* Boxplot between Income and  Marital Status

```
ggplot(data=superstore_data)+
  geom_line(mapping = aes(y=Income, x=Marital_Status, color="navy"), stat ="identity")+
  labs(title="Income Vs Marital Status", y="Income", x="Marital Status")
```
![download](https://github.com/TabithaChelagat/R-Project/assets/112205355/26145e6a-a63a-4df0-a0cb-cd79fd69c03a)

Observation: 
Almost all categories have similar incomes, the widowed have a higher average income while those who are together have some extremely high cases of income levels.









