# Women-on-Credit-Card-Overdues
Background

The historical context paints a vivid picture: before the advent of the Equal Credit Opportunity Act in 1974, women were systematically marginalized in the financial sphere. Their access to credit cards was restricted, often requiring male cosigners or facing outright denial based on gender. This discrimination not only perpetuated gendered financial dependencies but also might have instilled misconceptions regarding women's creditworthiness. Fast forward to today, it becomes paramount to understand whether these outdated notions have any empirical grounding or if they are remnants of a prejudiced past. As a leading commercial bank, our goal is twofold:
Equity & Fairness: By examining the actual credit behavior of female clients, we can ensure our policies are rooted in fairness and devoid of gender biases, aligning with both ethical standards and legal requirements.
Optimized Financial Strategy: A clear understanding of payment behaviors across genders can inform our credit policies, risk assessment protocols, and customer outreach strategies, leading to a more robust and optimized financial approach.
In light of evolving societal norms and regulations, and with a historical backdrop of gendered discrimination in financial access, our study aims to undertake a rigorous, data-driven investigation into the credit behavior of female clients. 





Data Understanding & Content 

In order to understand female client's credit behavior, we collect raw data from our comprehensive credit card dataset. The dataset consists of application_record table and credit_record table, which contains clients personal information and credit card payment information, respectively. 
We propose to deploy a logistic regression model. This model is tailored to understand the influence of gender on credit card overdues while controlling for significant socio-economic variables. We choose log odds of Status(Credit Card Overdues) as the dependent variable in the model. Status is a binary variable, which captures whether a credit card overdues. This study also includes one explanatory variable, Gender, and 6 control variables, including number of children, annual income, education level, marital status, employment duration, and family size.







Key Variables

Dependent Variables

STATUS: It is a categorical variable, and it captures whether the client is overdue or pay off credit card payment.(

0: 1-29 days past due 

1: 30-59 days past due 

2: 60-89 days overdue 

3: 90-119 days overdue 

4: 120-149 days overdue 

5: Overdue or bad debts, write-offs for more than 150 days C: paid off that month X: No loan for the month). 

We decided to convert 0,1,2,3,4,5 as 1 and convert C and X as 0










Independent Variables

Gender(CODE_GENDER) is a categorical variable and it captures whether the client is female or male. We decided to convert Female as 1 and Male as 0.

Whether Own Car(FLAG_OWN_CAR) is a categorical variable and it captures whether the client own a car. We decided to convert Yes as 1 and No as 0.

Whether Own property(FLAG_OWN_REALTY) is a categorical variable and it captures whether the client own a property. We decided to convert Yes as 1 and No as 0.

Annual Income(AMT_INCOME_TOTAL) is a continuous variable and it captures the annual income of client. 

Marital status(NAME_FAMILY_STATUS) is a categorical variable and it captures whether the client Married', 'Single / not married', 'Separated', 'Civil marriage',or  'Widow'. We decided to convert Marriage as 1 and unMarriage as 0.

Marital Status(NAME_FAMILY_STATUS) is a categorical variable that indicates whether the client is single or married. 

Employment duration(DAYS_EMPLOYED) is a continuous variable and it captures the total number of days of employment or unemployment. 

Record month(MONTHS_BALANCE) is a continuous variable and it captures the month of the extracted data is the starting point, backwards, 0 is the current month, -1 is the previous month, and so on.

Family Size(CNT_FAM_MEMBERS) is a continuous variable and it captures the number of family members for each client. Control variables will provide nuanced insights, ensuring that the results are well-adjusted and not driven by confounding factors.

Birthday(DAYS_BIRTH) is a continuous variable and it captures the age of clients; Count backwards from current day (0), -1 means yesterday. We decided to convert to the age of clients.

Education Level(NAME_EDUCATION_TYPE) is a categorical variable and it captures the highest level of education for each customer. 






Research Question:
Whether female customers of credit cards are more likely to have overdue or bad debts.






Gender and Credit Card 

Hypothesis: Women credit card holders are more likely to have overdue or bad debts.

Hypothesis: Women credit card holders are less likely to have overdue or bad debts.
