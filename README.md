# Analysis of Otago Prime Grocery Store

*Tools: Looker Studio, Python, SQLite*

## Introduction
I worked on this project as part of the semifinals for Logika UI 2022, a national-scale statistics competition held by Universitas Indonesia.
![otago-1](https://github.com/katlynkenisha/Otago/assets/109913754/69c0bf4c-75c3-4d94-ba54-b03547ec8ef2)

In this case, Otago Prime is a local grocery store-chain. The objective of the research was to perform data cleaning activities, conduct an exploratory analysis to discover insights, as well as create recommendations for membership tiers based on customer spending habits.

## Methodology
### 1. Data Collection
The dataset consists of 4 primary files:
- 3 **transaction** files detailing customer transactions from 2018-2020.
- **Customer** file containing the existing customer database.
- **Product** file outlining the product specifics such as brand and price.
- **Trial** file containing a list of customers alongside their respective membership tiers based on a trial done.

### 2. Data Cleaning
The data cleaning process was done using SQLite due to each file being connected to one another. The SQL codes used can be found inside the ‘code’ folder. The steps taken include:
- Transforming transaction dates to represent only the year due to incomplete dates for 2018 and 2019.
- Combining all the transactions into a single table.
- Reformatting purchase details in the transaction table by introducing separate columns for items purchased and quantity of items -purchased.
- Extracting product category and brand details into the transaction table.
- Calculating total spent by customers based on item’s price and quantity purchased.
- Creating a new table to analyze transactions based on each customer.
- Creating a new feature to calculate the average amount of money spent by customers on each transaction and the average number of transactions done in a year.

### 3. Data Visualization
The data visualization process was done using Looker Studio. The dashboard produced can be found inside the ‘dashboard’ folder. Some of the key findings from the data visualization process include:

![otago-2](https://github.com/katlynkenisha/Otago/assets/109913754/b284c796-ef74-457d-a3a5-e0534ea83430)
- Otago Prime’s best-selling products are eggs while its best-selling brand is Auckland’s best.

![otago-3](https://github.com/katlynkenisha/Otago/assets/109913754/6f27cd0e-d90a-4fee-b894-5d8af2aa881c)
- Otago Prime’s branch in Auckland has the greatest contribution towards its gross revenue.

![otago-4](https://github.com/katlynkenisha/Otago/assets/109913754/502271ec-f70a-4e49-b7df-07e4652f08cd)
- Although the number of transactions kept on increasing, the gross revenue experienced a decrease in 2020.

### 4. Modeling
To categorize membership tiers, the features used include:
- All-time transaction count
- Average spent per transaction
- Average transactions in a year

Classification was done by testing all supervised learning algorithms on the trial dataset. Results show that KNN, Decision Tree, and Naive Bayes model resulted in the highest accuracies. Next, these models were used to predict the membership tiers for each customer. The requirement for each membership tier found were as follows:
| Variable | Bronze | Silver | Gold |
| :--- | :---: | :---: | :---: |
| All-time transaction count | 19-20 | 28 | 144 |
| Average spent per transaction | 39-40 | 65-67 | 213 |
| Average transactions in a year | 6 | 9 | 48 |

## Conclusion
The defined criteria offer distinct thresholds to help classify customers into specific membership tiers based on their transaction history and spending behavior. This categorization allows for the implementation of personalized marketing strategies that can be applied to increase customer loyalty and further increase Otago Prime’s revenue in the future.
