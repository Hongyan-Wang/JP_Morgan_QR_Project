# JP_Morgan_Project
## Task 1 - Investigate and analyze price data



* AIM: pricing the natural gas storage contract
* OBJ1: extrapolate external data to increase granularity (Data preparation)
* OBJ2: analyse seasonality & annual trends 
* OBJ3: price the contract using historical data to make future gas price prediction


**Background info:**
Commodity storage contract: an agreement (between warehouse owners and participants in the supply chain) to store an agreed quality of any physical commodity in a warehouse for specified amount of time.

**Key terms of such contracts:** 
*  periodic storage fees, withdraws/injections limits.
*  Injection date: is the time when the commodity is purchased and stored
*  Withdraw date: the commodity is withdrawn from the storage.

**Data source:** monthly snapshot of prices which represents the market price of natural gas delivered at the end of each calendar month.
Data available for next 18mo + historical

**Task:** EDA historical data and an extrapolation for an extra year.
Estimate purchase price at any date in the past and extrapolate for one year into the future.


## Task 2 - Create a prototype pricing model


They believe the winter will be colder than expected, so they want to buy gas now to store and sell in winter in order to take advantage of the resulting increase in gas prices.
The concept is simple: any trade agreement is as valuable as the price you can sell minus the price at which you are able to buy.


**Aim:** Write a function that is able to use the data you created previously to price the contract.

Write a function that takes these inputs and gives back the value of the contract. You can assume there is no transport delay and that interest rates are zero. Market holidays, weekends, and bank holidays need not be accounted for. Test your code by selecting a few sample inputs.

**Model input:**
>  1.   Injection dates.
>  2.   Withdrawal dates.
>  3.   The prices at which the commodity can be purchased/sold on those dates.
>  4.   The rate at which the gas can be injected/withdrawn.
>  5.   The maximum volume that can be stored.
>  6.   Storage costs.

**Model output:** estimated price model

- Price_sell/ _buy = Price * Volume
- Price_contract = Price_sell - Price_buy - cost
- cost = Gas_Inj_Withdraw + Storage + Transport
- Transport = Transport_per_time *2
- Storage = Storage_rate * Storage_time
- Storage_time = Withdraw_date - In_date

  

## Task 3 - Predict the PD (Probability of default) for a borrower

**Aim**
Use the provided data to train a function that will estimate the probability of default for a borrower.

**Objectives**
1. Produce a function that can take in the properties of a loan and output the  expected loss.
2. Explore some technique including
> * Simple regression: -- Accuracy of the Logistic Regression model is:  0.99; Accuracy of Logisitic Regression model after replace variable is: 0.9979 
> * XGBoost: -- Accuracy of the XGBoost is 0.9998
> * Random forest: -- Accuracy of the Random Forest model is 0.9997


3. Use multiple methods and provide a comparative analysis.

**Raw data info:**
- borrower
- income
- total loans outstanding
- Previsouly defaulted on a loan
- Assuming a recovery rate of 10%, this can be used to give the expected loss on a loan.

## Task 4: Bucket FICO scores

Charlie wants to build a **machine learning model** that will predict the probability of default, but while you are discussing the methodology, she mentions that the architecture she is using requires `*categorical data*`. As FICO ratings can take integer values in a large range, they will need to be mapped into `*buckets*`.

**Defination**

> FICO (Fair Isaac Corportation)

> Founders: Bill Fair/ Earl Isaac

A FICO score is a standardized credit score created by the Fair Isaac Corporation (FICO) that quantifies the creditworthiness of a borrower to a value between 300 to 850, based on various factors.

FICO scores are used in 90% of mortgage application decisions in the United States.

**Task**

The risk manager provides you with FICO scores for the borrowers in the bank’s portfolio and wants you to **construct a technique for predicting the PD (probability of default)** for the borrowers using these scores.

- **Aim**
> - Create a rating map that maps the FICO score of the borrowers to a rating where a lower rating signifies a better credit score.
> - You could consider many ways of solving the problem by optimizing different properties of the resulting buckets, such as the mean squared error or log-likelihood

* The process of doing this is known as quantization.
