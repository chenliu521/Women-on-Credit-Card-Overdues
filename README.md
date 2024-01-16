# Women-on-Credit-Card-Overdues
## Background

The historical context paints a vivid picture: before the advent of the Equal Credit Opportunity Act in 1974, women were systematically marginalized in the financial sphere. Their access to credit cards was restricted, often requiring male cosigners or facing outright denial based on gender. This discrimination not only perpetuated gendered financial dependencies but also might have instilled misconceptions regarding women's creditworthiness. Fast forward to today, it becomes paramount to understand whether these outdated notions have any empirical grounding or if they are remnants of a prejudiced past. As a leading commercial bank, our goal is twofold:

* Equity & Fairness: By examining the actual credit behavior of female clients, we can ensure our policies are rooted in fairness and devoid of gender biases, aligning with both ethical standards and legal requirements.
  
* Optimized Financial Strategy: A clear understanding of payment behaviors across genders can inform our credit policies, risk assessment protocols, and customer outreach strategies, leading to a more robust and optimized financial approach.
In light of evolving societal norms and regulations, and with a historical backdrop of gendered discrimination in financial access, our study aims to undertake a rigorous, data-driven investigation into the credit behavior of female clients. 

## Data Understanding & Content 

In order to understand female client's credit behavior, we collect raw data from our comprehensive credit card dataset. The dataset consists of application_record table and credit_record table, which contains clients personal information and credit card payment information, respectively. 
We propose to deploy a logistic regression model. This model is tailored to understand the influence of gender on credit card overdues while controlling for significant socio-economic variables. We choose log odds of Status(Credit Card Overdues) as the dependent variable in the model. Status is a binary variable, which captures whether a credit card overdues. This study also includes one explanatory variable, Gender, and 6 control variables, including number of children, annual income, education level, marital status, employment duration, and family size.

## Key Variables

* Dependent Variables

STATUS:
It is a categorical variable, and it captures whether the client is overdue or pay off credit card payment.(

0: 1-29 days past due 

1: 30-59 days past due 

2: 60-89 days overdue 

3: 90-119 days overdue 

4: 120-149 days overdue 

5: Overdue or bad debts, write-offs for more than 150 days C: paid off that month X: No loan for the month). 

We decided to convert 0,1,2,3,4,5 as 1 and convert C and X as 0




* Independent Variables

** Gender(CODE_GENDER) is a categorical variable and it captures whether the client is female or male. We decided to convert Female as 1 and Male as 0.

** Whether Own Car(FLAG_OWN_CAR) is a categorical variable and it captures whether the client own a car. We decided to convert Yes as 1 and No as 0.

** Whether Own property(FLAG_OWN_REALTY) is a categorical variable and it captures whether the client own a property. We decided to convert Yes as 1 and No as 0.

** Annual Income(AMT_INCOME_TOTAL) is a continuous variable and it captures the annual income of client. 

** Marital status(NAME_FAMILY_STATUS) is a categorical variable and it captures whether the client Married', 'Single / not married', 'Separated', 'Civil marriage',or  'Widow'. We decided to convert Marriage as 1 and unMarriage as 0.

** Marital Status(NAME_FAMILY_STATUS) is a categorical variable that indicates whether the client is single or married. 

** Employment duration(DAYS_EMPLOYED) is a continuous variable and it captures the total number of days of employment or unemployment. 

** Record month(MONTHS_BALANCE) is a continuous variable and it captures the month of the extracted data is the starting point, backwards, 0 is the current month, -1 is the previous month, and so on.

** Family Size(CNT_FAM_MEMBERS) is a continuous variable and it captures the number of family members for each client. Control variables will provide nuanced insights, ensuring that the results are well-adjusted and not driven by confounding factors.

** Birthday(DAYS_BIRTH) is a continuous variable and it captures the age of clients; Count backwards from current day (0), -1 means yesterday. We decided to convert to the age of clients.

Education Level(NAME_EDUCATION_TYPE) is a categorical variable and it captures the highest level of education for each customer. 

## Research Question:
Whether female customers of credit cards are more likely to have overdue or bad debts.






Gender and Credit Card 

Hypothesis: Women credit card holders are more likely to have overdue or bad debts.

Hypothesis: Women credit card holders are less likely to have overdue or bad debts.


## Summary Statistics and Data Visualization

* Gender VS Overdue
<img width="468" alt="image" src="https://github.com/chenliu521/Women-on-Credit-Card-Overdues/assets/71107771/d377c501-4dde-4f4c-b031-2e8662b78ce1">

The bar chart indicates that males have a slightly higher overdue rate than females—1.7% compared to 1.4%. This suggests that in the dataset, males are marginally more likely to have overdue payments.

* Income VS Gender VS Overdue
  
<img width="468" alt="image" src="https://github.com/chenliu521/Women-on-Credit-Card-Overdues/assets/71107771/b48f7428-9e32-468f-9dac-bc381c849bfc">

Income Bin: 27,000 to 177,000 - In this range, females consistently show a higher ratio of overdue payments compared to males. This could indicate that within the lower to upper-middle-income categories, females may be more likely to experience financial stress or have higher credit utilization that leads to overdue payments. The reasons behind this could be multifaceted, including potential income disparities, different spending habits, or societal factors that influence financial obligations.
/
Income Bin: 177,000 to 360,000 - As we move into the higher income brackets, the trend reverses, with males exhibiting a higher ratio of overdue payments than females. This shift could suggest that among the higher-income earners, males might be engaging in riskier financial behaviors or could be shouldering larger financial burdens that result in higher rates of overdue payments.

* EDUCATION_LEVEL VS Gender VS Overdue
<img width="468" alt="image" src="https://github.com/chenliu521/Women-on-Credit-Card-Overdues/assets/71107771/5237ee1d-e4ee-4215-a149-9002a196488d">

'Higher education' level: female exhibit a higher overdue rate compared to male. This suggests that despite higher educational attainment, females that lead to a greater incidence of overdue payments in this subgroup.
/
Conversely, at the 'Lower secondary' education level: males exhibit a higher overdue rate than females, with males at 68.82% compared to females at 64.05%. This suggests that among those with the least amount of formal education, men are more likely to have overdue payments.

* Marriage VS Gender VS Overdue
<img width="506" alt="image" src="https://github.com/chenliu521/Women-on-Credit-Card-Overdues/assets/71107771/fef56b56-802d-49bf-b4c1-61403d3e2899">

Unmarried Individuals(0): The overdue ratio is relatively lower for both genders, with females at 22.43% and males at 15.97%. This could imply that unmarried individuals have fewer financial responsibilities or are more cautious with their credit obligations. The higher ratio for unmarried females compared to males might suggest lower credit management for women who are single.
/
Married Individuals(1): A substantial rise in the overdue ratio is observed upon marriage, escalating to 77.57% for females and an even higher 84.02% for males. This dramatic increase for married males, which surpasses that of females, may reflect additional financial burdens commonly assumed post-marriage for family-related expenses.

## Modeling 
* Logistic Regression
  
<img width="468" alt="image" src="https://github.com/chenliu521/Women-on-Credit-Card-Overdues/assets/71107771/1d8ff1fc-4869-4e10-a9d1-628ff90e1812">
<img width="376" alt="image" src="https://github.com/chenliu521/Women-on-Credit-Card-Overdues/assets/71107771/03ddbc0b-97e7-4f0f-aef0-9246b41253fc">

The coefficient for gender (female) is negative across the different late payment categories, with a p-value of 0.000, which is highly significant. 
This negative coefficient suggests that, all else being constant, being female is associated with a decrease in the log odds of having overdue or bad debts compared to being male.
Given the significant negative coefficient for gender, it would suggest that female customers are less likely to have overdue or bad debts than male customers.
We are also 95% confident that OWN_REALTY, total income, EDUCATION_LEVEL, CNT_FAM_MEMBERS, Employment years and Age are significant with varying degrees of influence on the probability of late payment.
/

Logistic Model Prediction and Evaluation: 
Training-Test Split: Our dataset was divided using a 70:30 split to ensure a balanced approach to training and evaluation. 

<img width="409" alt="image" src="https://github.com/chenliu521/Women-on-Credit-Card-Overdues/assets/71107771/c923b4ef-75d2-4fb6-81c8-5411fd64268b">

Hyperparameter Tuning: employed `GridSearchCV` to find the optimal hyperparameters. The search concluded with the following best parameters, yielding the highest cross-validation score:
•	‘C’: 0.0001, ‘penalty’: 11, ‘solver’: liblinear
•	Classification score: 98.46%

<img width="254" alt="image" src="https://github.com/chenliu521/Women-on-Credit-Card-Overdues/assets/71107771/3ea2c3ee-bc48-49bc-931f-cb862c8564e4">

* Linear Regression
<img width="468" alt="image" src="https://github.com/chenliu521/Women-on-Credit-Card-Overdues/assets/71107771/8434be97-acd9-42b9-902b-b569ef3871b9">

The coefficient for gender (female) is negative across the different late payment categories, with a p-value of 0.000, which is highly significant, indicating that all else being constant, being female is associated with one unit of decrease in the having overdue or bad debts compared to being male.


Interaction effects where gender combined with education, marriage, and income are significant. They have p-value is 0.000.

In the interaction term, the coefficient of the interaction term between female and education level is -0.0011 with a significant p-value. This implies that, holding all other variables constant, the effect of gender (female) on overdue decreases by 0.0011 when the level of education is increased by one level.

In the interaction term, the coefficient of the interaction term between female and Marriage is 0.0042 with a significant p-value. This implies that, holding all other variables constant, the effect of gender (female) on overdue increases by 0.0042, when the customer is Marriage.

In the interaction term, the coefficient of the interaction term between female and Income is 4.781e-08, with a significant p-value. This implies that, holding all other variables constant, the effect of gender (female) on overdue decreases by 4.781e-08, when the customer income increase by 1.

## Limitation
Although this analysis is comprehensive in its approach to analyzing the impact of gender on credit card delinquency, it encounters several limitations. First, there is no perfect accuracy and completeness in a data set. The historical background of credit data may affect data bias, and the data set mainly reflects a subset of commercial bank customers and may not represent the majority of the population.

Our model still has Omitted Variables bias; Economic Recession is the determinate of Credit Card Overdue or bad debts (Bad Economic Recession can increase the customer have overdue or bad debt in Credit card payment) Economic Recession is correlated with Female(Bad Economic Recession can allow Female customers lose their job)

Our Model doesn’t have any reverse causality.

## Conclusion
Our finding directly challenges the historical discrimination against women regarding creditworthiness. It indicates that the old prejudices are not empirically grounded, as the data shows that female clients demonstrate better or at least equal credit behavior compared to male clients.

This analysis aligns with the bank's objectives of ensuring equity and fairness and can inform optimized financial strategies that do not perpetuate outdated gender biases. It suggests that female clients should not be viewed through the lens of historical prejudices but rather evaluated based on actual data, which shows them as creditworthy as their male counterparts, if not more so. The bank can use these insights to further refine their credit policies and risk assessment protocols to be more inclusive and fair, while also possibly considering female clients as a lower credit risk segment.

We used logistic regression and linear regression models to analyze the credit behavior of female customers and gained important insights, particularly the impact of education on credit card delinquency.

Delving deeper,  we realized that education level may be an important factor for gender and thus determining the likelihood of being overdue. In the linear regression model, the coefficient of female is -0.0132 and the coefficient of the interaction term between female and education level is -0.0011 with a significant p-value. This implies that, holding all other variables constant, the effect of gender (female) on delinquency decreases by 0.0011 when the level of education is increased by one level. We can develop a strategy for banks to limit the credit card limit for credit card holders with low educational levels so that they use less money when they spend.

