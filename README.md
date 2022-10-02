# DS-Phase-3-Project
The final notebook can be found in the main branch along with the prsentation: 
- Notebook: https://github.com/RaymondLeong94/DS-Phase-3-Project/blob/main/Final%20notebook%20.ipynb 
- Presentation: https://github.com/RaymondLeong94/DS-Phase-3-Project/blob/main/Flatiron%20Phase%203%20Project.pdf

# Introduction
- The purpose of this project was to analyze a dataset of our choice and use different modeling techniques to solve a classification problem. 

- In this case, we are looking at the effectiveness of phone telemarketing campgin and the outcome of a previous one.

- We utilize the Banking Marketing Data Set(s) from a Portuguese banking instition to do so, by looking at their sucess at bank telemarketing on a previous campaign:[Source: [Moro et al., 2014] S. Moro, P. Cortez and P. Rita. A Data-Driven Approach to Predict the Success of Bank Telemarketing. Decision Support Systems, Elsevier, 62:22-31, June 2014]

- I built a final model that justifies that the telemarketing campaign outcomes, and how they can  be improved on. The harmonic mean is 88% but callers only have ~8% succuess rate to sell the product, which means for anomoly detection Decision Trees are fundamentally preferred.

- The dataset consisted of both continuous and categorical values, and that posseses a challenge to determine if a customer will subscribe to a product of the bank( 'y' in the dataset) 


# Dataset description

- The shape of the data frame is 41,188 by 21 columns, there are 41,188 attempts to secure a bank loan in the resulting boolean value of true/valse (needs to be transformed for a decision tree). Business relationships exist because of the customer, thus their demographics matter. 
    
  - Age, job, marital status, education, can be demographical factors of the customer. 
    
  - Default, housing, loan, can be economical factors of the customer. Contact, month, day of week, may indiciate some communication factors. Campaign, p days, previous, poutcome, are factors related to the campaign. 

  - If we cumulate the factors into their respective domains then we can perhaps find some insights.
  
  - Additionally the other factors are explained as follows:

    - We understand that a fiscal year is from the first of Jan to the 31st of December. The following indicators are explained and related to the fiscal year and are external economic factors.

    - Emperical variation rate may be employment rate and is measured every 3 months (quarterly): https://tradingeconomics.com/portugal/employment-rate . 
    
    - Consumer price index is an indicator of showing how a piece of steak costs now and then a few years from now, that index is the rate at which it changes. This is measured every 1 month, according to: https://www.economy.com/portugal/consumer-price-index-cpi. 

    - The consumer confidence index is a survey that measures how 'optimistic or pessimistic they are about finances' https://www.investopedia.com/insights/understanding-consumer-confidence-index/ they are every 1 month. 

    - Euribor is euro interbank offered rate, which is the interest rate at which banks lend each other money, this is every 3 months https://www.global-rates.com/en/interest-rates/euribor/euribor-interest-3-months.aspx.

    - Nr_Employed is the number of employees.

# Purpose
- We are looking at how an previous phone campaign's outcome to a successful contacted customer that bought a 'subscription' from the bank. This helps increase the bank's financial standing by:

- Looking at dominant trends and patterns amongst different demographic, social, political etc domains of a customer prior to calling

- Assessing chances of getting a successful transaction between customers
   
- Using models to help determine if choosing this type of campaigning is worth it. 

![image](https://user-images.githubusercontent.com/98904682/193468522-759633fa-5a19-489a-a790-7aee72dc4fd4.png)
- Highested value count = dominant value in the respective legend 


# Goals
 - using a metric (F1 score) to determine the sucess of the campaign  
- other finding and recommendations that a simple data analysis cannot obtain



# Results
  - Model Timeline: Linear regression. DT with benchmark, DT without benchmark. DT hypertuned. RF. RF hypertuned,
  - Hypertuning with Optuna gives an AUC of .73, which compared to the benchmark variable was .71. Our model outperformed the benchmark model.
  - CF matrix 

![image](https://user-images.githubusercontent.com/98904682/193469247-2432c476-3a78-4b38-8fef-b26fbe455ecd.png)

A CF matrix shows: 
- Expected chance of making a successful phone call 16.14%
- Chance that those calls are lucky 46.76%
- Percentage of failed phone calls 83.85%
- Percentage of sales you would miss by accident 4.44%



## Top features
![image](https://user-images.githubusercontent.com/98904682/193468666-4b6b9c20-3f0e-4a08-ad3f-64ace34bacd8.png)
- The external economic factor is almost twice as influencetial as age. Which is closely followed by the emp var rate than campaign.
- It is clear that this algorithim favors external factors more than other domains 
- The chances of prediciting a 1 overall is 50%, which is a coin flip. But when we look at the macro average we see 71% across both populations (1,0s)

# Conclusion
- Do not launch a phone campaign unless you investigate how certain factors of the economy affect the outcome of the campaign. Adjust the price of your product based on the # of FP and FN 

- If you launch a phone campaign, please address the population you are targeting to increase accuracy potential







