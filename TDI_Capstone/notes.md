How does quantitative and qualitative analysis actually work?

What's their scope?

What tools separate or bring them together?





Are findings different from insights?



4 major types of analysis

1\. Descriptive

2\. Diagnostic

3\. Prescriptive

4\. Predictive



What is exploratory data analysis?

EDA is an analysis method involving looking for patterns and relationships in the data. It usually leads to hypothesis to guide further analysis.

But what's the scope of this term?



Say I have a problem to solve, how do I go about getting data to use to solve that problem? Do I begin to look at a specific aspect or category or generally available data?

Is there a difference between data and dataset?







Phase 1: Data Cleaning



Phase 2: Understanding the Dataset



Phase 3: Univariate Analysis



Phase 4: Churn Analysis



Phase 5: Bivariate Analysis



Phase 6: Correlation \& Drivers



Phase 7: Prediction



Build a simple churn prediction model.



Typical process:



Train/Test Split

↓

Encode Categorical Variables

↓

Train Model

↓

Evaluate Accuracy

↓

Confusion Matrix

↓

Feature Importance



Phase 8: Business Recommendations





Project Structure:

TDI\_Capstone

│

├── Dataset

├── notebooks

│   ├── cleaning.ipynb

│   └── exploratory.ipynb

│

├── Project\_Brief.pdf

└── notes.txt



\--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------



Your organization depends on the insights you uncover to make data-driven decisions, innovate, and maintain a competitive edge.



During analysis, we'll usually define the problem, define our objectives from the problem, coin questions that guide analysis aimed at solving the problem.



Project Title: Bank Customer Churn



Details: Data contains account information for 10,000 customers at a European bank, including details on their credit score, balance, products, and whether they have churned.



Problem: An European bank has noticed an increase in churning among customers across different regions. The bank would like to gain an insight or overview of what is happening, including information on how to predict and prevent future churning to avoid losing profitable customers and future revenue.



Objective: Prepare and analyze the data to get an idea of what's going on in the bank, what's causing churning, patterns across demographics and region, and also how to prevent future churning.



Guided Questions:



1\. What is the current churn situation in the bank? Who is leaving and why?



2\. What attributes are more common among churners than non-churners?



3\. How does churn vary across customer segments and regions?



4\. Can churn be predicted to avoid future occurrences and maintain a competitive edge?



Others:

Are customers really churning or is it random?

Which factors have the strongest influence on customer churn?

Who is leaving?

Why are they leaving?





\--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Data Understanding and cleaning



A distribution shows:



Where values concentrate

Spread

Skewness

Outliers





CustomerId	str

Surname		str

CreditScore	int

Geography	str

Gender		str

Age		int

Tenure		int

Balance		float

NumOfProducts	int

HasCrCard	Boolean/int

IsActiveMember	Boolean/int

EstimatedSalary	float

Exited		Boolean/int





##### **Cleaning**

1. There was no null or missing row in the dataset
2. The customerid dtype was changed from int to str
3. From the summary statistics with measures such as min and max, it's known that there are no invalid values.
4. There were no inconsistencies, weird values as well as whitespaces in the category columns.
5. There were no invalid values, like wrong negatives in the numerical columns.

##### 

##### **Feature Engineering**



**Age Bracket: 18-30, 31-45, 46-60, 61-100**

**CreditScore Tier: 300-379, 580-669, 670-739, 740-799, 800-850**

**BalanceSegment: bins=\[-1, 0, 50000, 150000, 300000], labels=\['Zero', 'Low', 'Medium', 'High']**

**SalaryGroup: q=4, labels=\['Low', 'Medium-Low', 'Medium-High', 'High'**







##### **UNIVARIATE ANALYSIS**



1. The credit score distribution is approximately bell-shaped, with most customers concentrated between 600 and 700 and centered around 650.(but it tails to the left more because of some outliers)
2. A larger population of customers are from France with a proportion of 50.14% of the total customer number, while Germany and Spain both accommodate 25.09% and 24.77% of customer base respectively.
3. Male customers are more concentrated than female customers by a difference of 9.14%.
4. The age distribution is rightly skewed, with concentration focused between age 30 and 40 and centered around 37. The right tail skew shows there are ages well above this central tendency (37) since 75% of customers are 44 years old or less.(A higher number of customers are young or young adults).
5. Most customers own 1 or 2 products with relatively few customers owning 3 or 4 products. At least 75% of customers own 2 or fewer products.
6. Customer tenure is fairly evenly distributed between 1 and 9 years, while relatively fewer customers have tenure of 0 or 10 years.(This indicates a large number of customers are not new in the company).
7. The distribution of the data shows at least 25% of the customers have a balance of 0 (which might be a signal). The distribution is a zero-inflated normal distribution.
8. The Estimated Salary appear to be relatively evenly distributed across the range of 11.58 to 199992.48 with no single value overwhelmingly dominating the others.(The company has a fair mix of low class and high class customers).
9. The ratio of active members to inactive members is close with active members edging by 3.02%. Churn seems highly significant with a churn rate of 20.37%, meaning about 1 in every 5 customers has left.
10. A high number of customers have credit cards.





##### **BIVARIATE ANALYSIS**

1. Even though a higher number of the entire customer base are from France(more than half), it experiences the lowest churn recording. Germany, however, that has the second lowest population leads in churn with a rate of 32.44% followed by Spain.
2. The data shows that females churn the most overall, edging with a difference of 8.61%. Each region also shows that a higher number of customers that left are females.
3. It is revealed that Older Adults churn the most overall (51.12%) followed by Seniors. Further Investigation showed that this pattern of Older Adults and Seniors leaving is consistent across each region and gender with females leading across all age brackets.
4. Bivariate analysis shows that customer credit score and tenure have no meaningful impact on loyalty, with churn remaining flat at roughly 20% regardless of credit trustworthiness and how long a customer has been with the bank.



Further Recommendation: Investigate other variables that drive churn regardless of a customer's tenure or credit tier.

5\. 100% of customers with 4 products and 82.71% of those with 3 products have left the company, signaling high operational and financial risk.

6\. Even though the percentages are close, customers with no credit cards are said to have churned than others.

7\. Inactive customers record a higher churn rate than active customers (26.85% to 14.27%)

8\. Active customers with credit card are more loyal.

9\. Churn is concentrated among customers with low balance with a surprising observation where churn rate is lowest among customers with zero balance. Low balance is a higher predictor of churn than zero balance.

10\. Salary Group clusters around the baseline, 20% providing no meaningful insight.



Note: Even though France experienced the lowest churn recording, it gaps Spain in churn among Older Adults(5.13%).



Major Concerning Variables: Age, Gender, Geography, **Number of Products, Balance, Active**, Credit Card





##### **MULTIVARIATE ANALYSIS**



1. Even though Older Adults seem to be a high risk segment, having a churn rate of over 51%. The real driver seems to be the number of products the customers have with the company because those with two products maintained a significantly low churn rate across all segment. Even Older Adults that recorded the highest churn rate recorded a significant reduction in rate of churn when they had two products.



For thought: Is it difficult for them to handle the products or they have bad experiences? They should have had more ties to the bank.



2\.  Further analysis further reveals that the number of products is a major predictor of churn. Cross tabulating Geography and NumOfProducts showed that across all regions, churn was high corresponding to customers having 1, 3 or 4 products while significantly lower when they had two products. The same can be said concerning genders.



3\. Germany is seen to lose high profile customers with no customer having zero balance and the churn rate for those with low balance is 0%. Therefore, the concentration is concentrated around those with medium and high balance



4\. Active status of customers is furthered confirmed to predict churn with previous analyses already establishing that inactive customers record a higher churn rate than active customers. It is shown that even customers with low balance(high churn status) churned less significantly when they are active. This is also backed up across categories, like age group, geography, gender.



5\. Further analysis reveal that female customers with low balance are less loyal than others. Similar thing can be said across the age brackets, where older adults and others who have low balance are less loyal to the business.





###### **Note: Across all my analysis, FOUR variables stand out as the major predictor or associator of churn: Number of Products, Active Status, Customer Balance, Credit Card. These variables directly affect churn across geography, gender, age groups.**

###### 

###### **Concerning Credit Card, my hypothesis is if they are more active, then they should have credit card. It doesn't seem so, but let's see if I can use a statistical method to prove that.**

###### 

###### **However, there is something weird about Credit Cards, Older Adults and Seniors churned less when they have Credit Card but Adults and Young Adults churned less with Credit Card.**





##### **Final Stage:**



Validate hypothesis for active and credit card

Check correlation using scatter plot for the key variables mentioned

Use linear regression to predict churn, if possible





Frame the insights found better and make recommendations





##### **Next Step:**

Refine testing\_prediction: Dive into the machine learning notebook to execute some code optimizations (like class balancing or threshold tuning) to try and boost that recall score.





Python Boilerplate

bank-customer-churn-analysis/

├── data/

│   ├── bank\_churn\_data\_raw.csv

│   └── bank\_churn\_data\_cleaned.csv

├── notebooks/

│   ├── 01\_data\_cleaning.ipynb

│   ├── 02\_exploratory\_demographics.ipynb

│   ├── 03\_exploratory\_financials.ipynb

│   └── 04\_hypothesis\_testing\_prediction.ipynb

├── reports/

│   ├── customer\_demographic\_exploratory.png

│   ├── financial\_account\_footprint.png

│   └── customer\_churn\_dashboard.png

├── .gitignore

├── README.md

└── requirements.txt





\# 🏦 End-to-End Bank Customer Attrition Analysis \& Predictive Modeling



!\[Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat\&logo=python\&logoColor=white)

!\[Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=flat\&logo=pandas)

!\[Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine%20Learning-F7931E?style=flat\&logo=scikit-learn)

!\[Status](https://img.shields.io/badge/Project-Completed-brightgreen)



\## 📌 Executive Summary

Customer attrition poses a significant financial threat to retail banking operations. Acquiring a new customer costs up to 5x more than retaining an existing one. This project provides an end-to-end data analytics and predictive solution that identifies core drivers of customer churn across 10,000 retail bank accounts and deploys a machine learning pipeline to flag high-risk customers prior to account closure.



\---



\## 🎯 Key Business Questions \& Findings

1\. \*\*Which demographic segments are leaking capital?\*\*

&#x20;  \* \*\*German branch accounts\*\* exhibit a \*\*32.44% churn rate\*\*—double the attrition rates of France (16.15%) and Spain (16.67%).

&#x20;  \* \*\*Older Adults (Ages 45–60)\*\* account for the highest demographic vulnerability with a \*\*51.12% exit rate\*\*.

2\. \*\*What product and channel behaviors correlate with account closures?\*\*

&#x20;  \* Multi-product bundling reveals extreme friction: customers holding \*\*3 or 4 products\*\* face a \*\*82.71% to 100% churn rate\*\*.

&#x20;  \* Platform engagement acts as a massive retention anchor—inactive members exit at nearly double the rate of active members (\*\*26.85% vs. 14.27%\*\*).



\---



\## 🔬 Statistical Hypothesis Testing (Chi-Square)



To rigorously validate whether observed behavioral patterns were statistically significant drivers or merely random background noise, Chi-Square Tests of Independence ($\\alpha = 0.05$) were conducted:



| Behavioral Variable | Hypothesis Test | $p$-value | Decision | Business Takeaway |

| :--- | :--- | :--- | :--- | :--- |

| \*\*IsActiveMember\*\* | $H\_0$: Active status is independent of Churn | \*\*`0.000000`\*\* | \*\*Reject $H\_0$\*\* | Highly significant driver; digital portal engagement directly anchors customer retention. |

| \*\*HasCrCard\*\* | $H\_0$: Credit Card ownership is independent of Churn | \*\*`0.492372`\*\* | \*\*Fail to Reject $H\_0$\*\* | No statistical relationship; issuing credit cards does not alter retention probability. |



\---



\## 📈 Executive Dashboards



\### 1. Financial Account Footprint \& Operational Risk

!\[Financial Account Footprint](./reports/financial\_account\_footprint.png)



\### 2. Executive Customer Churn Overview

!\[Customer Churn Dashboard](./reports/customer\_churn\_dashboard.png)



\---



\## 🤖 Predictive Machine Learning Model



A \*\*Random Forest Classifier\*\* was trained on an 80/20 train-test split (max depth constrained to prevent overfitting) to evaluate churn probability:



\* \*\*Overall Model Accuracy:\*\* `86.05%`

\* \*\*Precision (Class 1 - Churn):\*\* `78%`

\* \*\*Recall (Class 1 - Churn):\*\* `40%`



\### Strategic Model Trade-off:

The model prioritizes \*\*High Precision (78%)\*\* over Recall (40%). This ensures that automated alerts generated for account managers are highly trustworthy, eliminating false alarms and avoiding unnecessary retention discounts on low-risk accounts.



\---



\## 💡 Strategic Recommendations for Bank Leadership

1\. \*\*Targeted Digital Re-engagement:\*\* Implement automated automated push notifications and email workflows for inactive account holders after 30 days of portal inactivity.

2\. \*\*Product Bundle Restructuring:\*\* Conduct an operational review of customer accounts holding 3+ products to resolve fee structures or product complexity causing churn.

3\. \*\*Regional Taskforce (Germany):\*\* Launch a targeted audit on customer service and competitive pricing in the German branch network to mitigate regional leakage.



\---



\## 🛠️ Tech Stack \& Dependencies

\* \*\*Data Manipulation:\*\* `pandas`, `numpy`

\* \*\*Visualization:\*\* `matplotlib`, `seaborn`

\* \*\*Statistical Inference:\*\* `scipy.stats`

\* \*\*Machine Learning:\*\* `scikit-learn`



\---



\## 🚀 How to Run This Project Locally



1\. \*\*Clone the repository:\*\*

&#x20;  ```bash

&#x20;  git clone \[https://github.com/your-username/bank-customer-churn-analysis.git](https://github.com/your-username/bank-customer-churn-analysis.git)

&#x20;  cd bank-customer-churn-analysis

&#x20;  ```



2\. \*\*Create and activate a virtual environment (optional but recommended):\*\*

&#x20;  ```bash

&#x20;  python -m venv venv

&#x20;  source venv/bin/activate  # On Windows: venv\\Scripts\\activate

&#x20;  ```



3\. \*\*Install dependencies:\*\*

&#x20;  ```bash

&#x20;  pip install -r requirements.txt

&#x20;  ```



4\. \*\*Launch Jupyter Notebooks:\*\*

&#x20;  ```bash

&#x20;  jupyter notebook notebooks/

&#x20;  ```
































STEPS TO TAKE




Step 2: Create a .gitignore File

A .gitignore file tells Git which files or folders NOT to upload to GitHub (such as temporary cache files, virtual environments, or massive raw datasets).



In VS Code, click the New File icon in the Explorer panel.



Name the file exactly: .gitignore (note the dot at the beginning).



Paste the following contents inside:



Plaintext

\# Python temporary files

\_\_pycache\_\_/

\*.py\[cod]



\# Jupyter Notebook checkpoints

.ipynb\_checkpoints/



\# Virtual environments

venv/

env/

.venv/



\# OS hidden files

.DS\_Store

Thumbs.db

Step 3: Create a requirements.txt File

This file allows anyone downloading your repository to install all your project libraries in one go.



Create a new file named requirements.txt.



List the libraries used in your analysis:



Plaintext

numpy

pandas

matplotlib

seaborn

scikit-learn

scipy

Step 4: Create and Draft Your README.md

Now, let's build the core documentation file.



Create a new file named README.md.



Open the file in VS Code.



Open the Side-by-Side Preview:



Press Ctrl + K, then press V (on Mac: Cmd + K, then V).



This opens a live visual panel on the right so you can see your headings, tables, and images update in real time as you write!



Paste the boilerplate code provided in our previous discussion into README.md.



Important Note on Image Paths:

In your README.md, make sure your image paths point relative to your reports/ folder:



Markdown

!\[Financial Footprint](./reports/financial\_account\_footprint.png)

Step 5: Initialize Git in VS Code

Now we turn your project folder into a Git-tracked workspace.



Open the integrated terminal in VS Code by pressing Ctrl + \~ (backtick) or clicking Terminal > New Terminal from the top menu.



Run this command to initialize Git:



Bash

git init

Set your main branch name to main:



Bash

git branch -M main

Step 6: Create the Repository on GitHub

Open your web browser and go to GitHub.com.



Click the + icon in the top-right corner and select New repository.



Fill in the details:



Repository name: bank-customer-churn-analysis



Description: End-to-End Retail Bank Churn Analytics and Predictive Modeling



Public / Private: Select Public (so employers/recruiters can see it).



Initialize repository options: Leave "Add a README file", "Add .gitignore", and "Choose a license" UNCHECKED (because we already created them locally in VS Code).



Click Create repository.



Step 7: Connect Local VS Code to GitHub and Push

After creating the repository, GitHub will show a page with quick setup commands. Copy and run the commands under "…or push an existing repository from the command line" inside your VS Code terminal:



Stage all your files:



Bash

git add .

Commit (save) your files with a message:



Bash

git commit -m "Initial commit: complete project files and documentation"

Link your local project to GitHub: (replace YOUR-USERNAME with your actual GitHub username)



Bash

git remote add origin https://github.com/YOUR-USERNAME/bank-customer-churn-analysis.git

Push your files live to GitHub:



Bash

git push -u origin main

(Note: If Git asks you to log in or authenticate, follow the browser popup prompt to sign in with your GitHub account).



Step 8: Verify Your Live Portfolio

Refresh your repository page on GitHub.com.



You will see your files (data, notebooks, reports, README.md) neatly organized.



Scroll down below the file listing—GitHub automatically renders your README.md file into a polished, professional webpage complete with your formatting, tables, and high-definition charts!






A NICE IDEA: Make this a project others can follow and use to practice building. Make it open source, advertise it, create content for it, reach people to push it out


whats the '' for in `0.000000`? For the dashboard, there are three





























