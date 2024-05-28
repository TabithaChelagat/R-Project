# R-Project(Onging project...)
## Predicting the chances of a customer giving a positive response(Data Exploration, cleaning, formatting and exploration)

Overview 
A superstore is planning for the year-end sale.They want to launch a new offer - gold membership, that gives a 20% discount on all purchases, for only $499 which is $999 on other days.It will be valid only for existing customers and the campaign through phone calls is currently being planned for them. The management feels that the best way to reduce the cost of the campaign is to make a predictive model which will classify customers who might purchase the offer.

##Objectives 
Work will aim to meet the following objectives; 
i. To predict the likelihood of the customers giving a positive response. 
ii. To identify the different factors that affect a customer’s response.

##Questions 
The work will seek to answer the following questions; 
i) What is the likelihood of the customers giving a positive response? 
ii) What are the factors that affect a customer’s response?

##Metrics for Success 
For this work, the success will include coming up with a model that correctly predicts the likelihood of a customer to give a positive response. Success will also be achieved by correctly analyzing and establishing the factors that contribute towards a customer giving a positive response to the Superstore campaign.
We aim to achieve an accuracy level of 90%.

##The Experimental Design 
Below are the steps taken in this analysis 
a. Loading the required libraries 
b. Loading and previewing data 
c. Cleaning the data 
d. Exploratory Data Analysis(EDA) 
e. Creating a model to predict 
d. Drawing conclusions 
e. Giving Recommendations

##Data Relevance and Validation 
The data available is relevant for the intended analysis. It contains information that is significant to predicting the likelihood of a customer giving a positive response. It has data on customers income, education levels, marital status, children in the households, shopping trends, and the responses and complaints.

Here is the content converted into a Markdown table suitable for a GitHub README file:

##Understanding the context The data set we are to work with contains the following columns:

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
```

The dataset has 2240 observations and 22 columns

This dataset can be accessed from this link:Superstore Marketing Campaign

##Reading and Understanding The Dataset
--importing the data

```
store_data = read.csv("superstore_data.csv")

```














