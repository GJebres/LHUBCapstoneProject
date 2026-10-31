**Prepared by R Hadi**

<p align="center">
<img width="300" height="300" alt="squarlogo" src="https://github.com/user-attachments/assets/c19be037-2e06-4055-a40e-cfa9c41ec5bc" />
<p/>
  
# **Employee Attrition Analysis and Retention Improvement - IBM HR Analytics**

In today's fast-paced world, businesses and organizations face the challenge of extracting meaningful insights from the overwhelming amount of data at their disposal. Traditional methods often fall short, necessitating a more sophisticated and efficient solution.

## **Project Overview** ##
Employee turnover can increase hiring and training costs, reduce productivity and create extra work for remaining employees. However, HR managers may not know which factors are linked to employees leaving or which groups of employees are more likely to leave the company.

## **Problem Statement** ##
How can a company identify the key factors linked to employee turnover and use predictive analysis to identify employees who may be more likely to leave, so that it can reduce staff turnover, lower costs, increase productivity and support better workforce planning?

## **Research Objectives** ##
1. **Employee Attrition Rate and Workforce Analysis:** <br/> To measure the overall employee attrition rate and compare employees who leave with those who remain in the organisation.
2. **Department and Job Role Attrition Analysis:** <br/> To identify departments and job roles with higher employee attrition rates and examine differences in turnover across employee groups.
3. **Compensation and Employee Attrition Analysis:**<br/> To analyse the relationship between employee salary, compensation and attrition to understand how compensation levels are associated with employee turnover.
4. **Employee Satisfaction and Work Environment Analysis:** <br/> To examine the relationships between job satisfaction, work environment, work-life balance and employee attrition.
5. **Overtime, Work Experience and Tenure Analysis:**<br/> To investigate the relationships between overtime, work experience, years of service and employee attrition to identify workforce patterns associated with employee turnover.

## **Tools to use** ##
HR data set <br/> Power BI - Interactive dashboard and business reporting <br/> Python - Develop and evaluate predictive models

## **Part 1. Descriptive Analyis** ##
## **Dataset Overview** ##
For this project, there are 5 datasets (Compensation, Employees, Employment Status, Experience and Performance) to use for this analysis.

### Compensation
Dataset 1: Compensation.csv  
**Shape:** (1470, 7)

| EmployeeNumber | DailyRate | HourlyRate | MonthlyIncome | MonthlyRate | PercentSalaryHike | StockOptionLevel |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 0 | 1102 | 94 | 5993 | 19479 | 11 | 0 |
| 1 | 279 | 61 | 5130 | 24907 | 23 | 1 |
| 2 | 1373 | 92 | 2090 | 2396 | 15 | 0 |

### Employees
Dataset 2: Employees.csv  
**Shape:** (1470, 14)

| EmployeeNumber | Age | Gender | MaritalStatus | Education | EducationField | Department | JobRole | JobLevel | BusinessTravel | DistanceFromHome | EmployeeCount | Over18 | StandardHours |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 0 | 41.0 | Female | Single | 2 | Life Sciences | Sales | Sales Executive | 2 | Travel_Rarely | 1 | 1 | Y | 80 |
| 1 | 49.0 | Male | Married | 1 | Life Sciences | Research & Development | Research Scientist | 2 | Travel_Frequently | 8 | 1 | Y | 80 |
| 2 | 37.0 | Male | Single | 2 | Other | Research & Development | Laboratory Technician | 1 | Travel_Rarely | 2 | 1 | Y | 80 |

### Employment Status
Dataset 3: EmploymentStatus.csv  
**Shape:** (1470, 3)

| EmployeeNumber | Attrition | OverTime |
| :--- | :--- | :--- |
| 0 | Yes | Yes |
| 1 | No | No |
| 2 | Yes | Yes |

### Experience
Dataset 4: Experience.csv  
**Shape:** (1470, 8)

| EmployeeNumber | NumCompaniesWorked | TotalWorkingYears | TrainingTimesLastYear | YearsAtCompany | YearsInCurrentRole | YearsSinceLastPromotion | YearsWithCurrManager |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 0 | 8 | 8 | 0 | 6 | 4 | 0 | 5 |
| 1 | 2 | 1 | 10 | 3 | 10 | 7 | 1 | 7 |
| 2 | 4 | 6 | 7 | 3 | 0 | 0 | 0 | 0 |

### Performance
Dataset 5: Performance.csv  
**Shape:** (1470, 7)

| EmployeeNumber | PerformanceRating | EnvironmentSatisfaction | JobInvolvement | JobSatisfaction | RelationshipSatisfaction | WorkLifeBalance |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 0 | 3 | 2 | 3 | 4 | 1 | 1 |
| 1 | 2 | 4 | 3 | 2 | 2 | 4 | 3 |
| 2 | 4 | 3 | 4 | 2 | 3 | 2 | 3 |

## **Exploratory Data Analysis** ##
After uploading all five datasets, we begin by cleaning and preparing the data for analysis. During the initial review, we identify missing values in the Age Group column. We locate the missing data, review the statistical summary and calculate the median age to fill in the missing values. This helps ensure that the data is complete and ready for analysis.

Next, we analyse employee attrition by comparing employees who left the company with those who stayed. We also examine attrition by department, job role, age group and overtime status to identify patterns among different employee groups.

Finally, we combine all five datasets to examine the factors associated with employee attrition. These include compensation, job satisfaction, overtime, work experience and years of service. The findings help us better understand employee attrition patterns and identify areas where the company may improve employee retention.

- Total data: 1470 records, 35 columns.  
- All data types are in order and there are no nulls.

| EmployeeNumber | Age | Gender | MaritalStatus | Education | EducationField | Department | JobRole | JobLevel | BusinessTravel | ... | YearsAtCompany | YearsInCurrentRole | YearsSinceLastPromotion | YearsWithCurrManager | PerformanceRating | EnvironmentSatisfaction | JobInvolvement | JobSatisfaction | RelationshipSatisfaction | WorkLifeBalance |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **0** \| 1 | 41.0 | Female | Single | 2 | Life Sciences | Sales | Sales Executive | 2 | Travel_Rarely | ... | 6 | 4 | 0 | 5 | 3 | 2 | 3 | 4 | 1 | 1 |
| **1** \| 2 | 49.0 | Male | Married | 1 | Life Sciences | Research & Development | Research Scientist | 2 | Travel_Frequently | ... | 10 | 7 | 1 | 7 | 4 | 3 | 2 | 2 | 4 | 3 |
| **2** \| 4 | 37.0 | Male | Single | 2 | Other | Research & Development | Laboratory Technician | 1 | Travel_Rarely | ... | 0 | 0 | 0 | 0 | 3 | 4 | 2 | 3 | 2 | 3 |
| **3** \| 5 | 33.0 | Female | Married | 4 | Life Sciences | Research & Development | Research Scientist | 1 | Travel_Frequently | ... | 8 | 7 | 3 | 0 | 3 | 4 | 3 | 3 | 3 | 3 |
| **4** \| 7 | 27.0 | Male | Married | 1 | Medical | Research & Development | Laboratory Technician | 1 | Travel_Rarely | ... | 2 | 2 | 2 | 2 | 3 | 1 | 3 | 2 | 4 | 3 |

*5 rows × 35 columns*

## **Attrition Analysis** ##
The analysis starts with the Employee Attrition analysis (RO1) to know the numbers of employees who left and those who stayed. The result shows that the number(percentage) of staff who stayed is 1233(83.88%) and those who left is 237 (16.12%)

| Attrition |	Employee | Count | Percentage (%) |
| :--- | :--- | :--- | :--- |
| 0 |	No |	1233	| 83.88 |
| 1	| Yes | 237 |	16.12 |

The next step is to address the attrition based on the department, job role (RO2).

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/b56537bf-b0cd-4a62-9c52-1abd09d5ae66" /> <br/>
| Department | No | Yes |Attrition Rate (%) |
| :--- | :--- | :--- | :--- |
| Human Resources | 51 | 12 | 19.05 |
| Research & Development | 828 | 133 | 13.84 |
| Sales | 354 | 92 | 20.63 |

<img width="628" height="470" alt="image" src="https://github.com/user-attachments/assets/b93d1357-dd26-4f70-96fd-f3d42438c615" /> <br/>
| Attrition | No | Yes | Attrition Rate (%) |
| :--- | :--- | :--- | :--- |
| Job Role |   |  |  |                                             
| Sales Representative | 50 | 33 | 39.76 |
| Laboratory Technician | 197 | 62 | 23.94 |
| Human Resources | 40 | 12 | 23.08 |
| Sales Executive | 269 | 57 | 17.48 |
| Research Scientist | 245 | 47 | 16.10 |
| Manufacturing Director | 135 | 10 | 6.90 |
| Healthcare Representative | 122 | 9 | 6.87 |
| Manager | 97 | 5 | 4.90 |
| Research Director | 78 | 2 | 2.50 |

To find out the compensation and employee attrition (RO3), we look into Monthly Income, Percentage of Salary Increase, Stock Option Level and categorise Income Band. 
**Compare compensation by attrition status**
| Attrition | Monthly Income | Percent Salary Hike |	Stock Option Level |
| :--- | :--- | :--- | :--- |
| No |	6832.74 |	15.23 |	0.85 |
| Yes |	4787.09 |	15.10 |	0.53 |

**Group employees into monthly income bands**
| Attrition	| No	| Yes	| Attrition Rate (%) |
| :--- | :--- | :--- | :--- |
| Income Band |  |  |  |			
| Below 3,000	| 71.39	| 28.61	| 28.61 |
| 3,000–4,999 | 85.88 |	14.12 |	14.12 |
| 5,000–7,999 |	90.00 |	10.00 |	10.00 |
| 8,000 and above	| 89.50 |	10.50 |	10.50 |

For Employee Satisfaction and Work Environment analysis (RO4), we look at attrition rates due to Job Satisfaction, Environment and Work-Life balance.

<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/6eb7f8d5-3887-4fad-ba1a-851758db1484" />

| Attrition	| No	| Yes	| Attrition Rate (%) |
| :--- | :--- | :--- | :--- |
| 1	| 223	| 66	| 22.84 |
| 2	| 234	| 46	| 16.43 |
| 3	| 369	| 73	| 16.52 |
| 4	| 407	| 52	| 11.33 |

<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/c7d8a10c-08da-46df-aaa7-6f74454f8326" />

| Attrition	| No	| Yes |
| :--- | :--- | :--- |
| 1	| 74.65	| 25.35 |
| 2	| 85.02	| 14.98 |
| 3	| 86.31	| 13.69 |
| 4	| 86.55	| 13.45 |

<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/6bd5c956-8892-49cf-bc7c-456478a5d301" />

| Attrition	| No	| Yes |
| :--- | :--- | :--- |
| 1	| 68.75	| 31.25 |
| 2	| 83.14	| 16.86 |
| 3	| 85.78	| 14.22 |
| 4	| 82.35 |	17.65 |

And finally to address Overtime, Work Experience and Tenure Analysis (RO5), we look at the number of employees who left and stayed, and calculate the attrition rate for each group. Then we proceed with work experience and length of service in the company

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/0bb3c009-54d9-4077-82db-4021a748c6db" />

| Attrition	| No	| Yes	| Attrition Rate (%) |
| :--- | :--- | :--- | :--- |
| Overtime |  |  |  |
| No	| 944	| 110	| 10.44 |
| Yes	| 289	| 127	| 30.53 |

**Average Work Experience and Tenure by Attrition**

| Attrition | Total Working Years | Years At Company	| Years In Current Role |	Years Since Last Promotion |
| :--- | :--- | :--- | :--- | :--- |
| No	| 11.86	| 7.37	| 4.48 | 2.23 |
| Yes	| 8.24 | 5.13	| 2.90	| 1.95 |

<img width="1446" height="710" alt="image" src="https://github.com/user-attachments/assets/3754be21-5091-49be-aabe-94e8939e3742" />

**Summary of the findings**

| Analysis	| Result	| Key findings |
| :--- | :--- | :--- |
| Overall Employee Attrition (RO1)	| 1,470 employees analysed; 237 left (16.12%) and 1,233 stayed (83.88%). | Most employees stayed with the company, but approximately 1 in 6 employees left. The overall attrition rate provides a baseline for evaluating differences across employee groups. |
| Attrition by Department (RO2)	| Sales: 20.63% <br/> Human Resources: 19.05% <br/> Research & Development: 13.84%.	| Sales had the highest department-level attrition rate, followed by Human Resources. Research & Development had the lowest rate among the three departments.|
| Attrition by Job Role	(RO2) | Sales Representatives: 39.76% <br/> Laboratory Technicians: 23.94% <br/> Human Resources: 23.08% <br/> Research Directors: 2.50%.	| Sales Representatives had the highest attrition rate among the selected job roles, suggesting that their workload, incentives, management support and career progression warrant further investigation. |
| Attrition by Compensation	(RO3) | Employees earning below 3,000 had a 28.61% attrition rate, compared with 10.00% for those earning 5,000–7,999 and 10.50% for those earning 8,000 or more.	| Employees in the lowest income band had substantially higher attrition. HR could investigate salary competitiveness, benefits and pay progression. |
| Job Satisfaction	(RO4) | Attrition was 22.84% for satisfaction level 1 and 11.33% for level 4.	| Employees with the lowest job satisfaction had a higher attrition rate than those with the highest satisfaction. |
| Environment Satisfaction (RO4) | Attrition was 25.35% for satisfaction level 1 and 13.45% for level 4.	| Lower environment satisfaction was associated with higher attrition, highlighting the importance of examining employees' workplace experiences. |
| Work-Life Balance	(RO4)| Employees with work-life balance level 1 had a 31.25% attrition rate, compared with 14.22% for level 4 | Employees reporting the lowest work-life balance had a substantially higher attrition rate, making this an important area for further investigation. |
| Overtime (RO5) | Employees working overtime had a 30.53% attrition rate, compared with 10.44% among employees who did not work overtime. | The overtime group had approximately 2.92 times the attrition rate of the non-overtime group. HR should investigate workload, staffing and overtime patterns.|
| Work Experience (RO5) |Employees who stayed had an average of 11.86 total working years, compared with 8.24 years for employees who left. Attrition was 28.80% for employees with 0–5 years of experience and 7.73% for those with over 20 years. | Employees who left generally had less overall work experience. Attrition rates were higher among less-experienced employees.|
| Years of Service (RO5) | Employees with 0–2 years of service had a 29.82% attrition rate, compared with 8.13% for those with over 10 years of service. | Employees with shorter company tenure had higher attrition. Onboarding, mentoring and early-career support may warrant further investigation.|

## **Part 2. Predictive Analyis** ##

Having completed Descriptive analysis earlier, we are now using Predictive analysis to estimate which staff is more likely to leave. The data used in Descriptive analysis will be the base of the information. Predictive analysis will use the historical pattern to build a model that estimates which employees who are more likely to stay or to leave the company.

The preparation included:

•	Selecting relevant employee attributes.  
•	Separating the target variable, Attrition, from the predictor variables.  
•	Preparing numeric and categorical features.  
•	Encoding categorical data where required.  
•	Splitting the data into training and testing sets.  
•	Training models using the training data and evaluating them on unseen test data.  

The cleaned matrix was reduced to 33 columns during preparation. The data preparation is needed to provide a consistent set of inputs to learn from. By separating training and testing data, it provides a way to assess how well the models perform on records they were not trained on.

<img width="296" height="254" alt="image" src="https://github.com/user-attachments/assets/f062a32e-063f-432e-a89b-37aaaa81a0bd" />

## **Training and Testing Models** ##
• Logistic Regression  
• Random Forest

| Model | Accuracy (%) | Precision (%) | Recall (%) | F1-score (%) | ROC-AUC (%) |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 75.17 | 34.88 | 63.83 | 45.11 | 80.24 |
| Random Forest | 84.69 | 66.67 | 8.51 | 15.09 | 79.18 |

<img width="1190" height="590" alt="image" src="https://github.com/user-attachments/assets/9d4a0de9-b9b7-448a-ad7a-f9917e434bb7" />

| Evaluation Matrics | Score |
|---|---:|
| Accuracy (%): | Random Forest (84.69%) |
| Precision (%): | Random Forest (66.67%) |
| Recall (%): | Logistic Regression (63.83%) |
| F1-score (%): | Logistic Regression (45.11%) |
| ROC-AUC (%): | Logistic Regression (80.24%) |

<img width="1163" height="495" alt="image" src="https://github.com/user-attachments/assets/9cd35727-3813-432b-af1a-de323203e756" />

The confusion matrix provides a more detailed view of the model's mistake. 
In Logistic Regression, 30 employees are identified out of 47 and missed 17
In Random Forest, 20 employees are identified out of 47 and missed 27.

<img width="989" height="690" alt="image" src="https://github.com/user-attachments/assets/e8c66975-6225-4db2-bd3c-e675093b7ac0" />

Random Forest provides a feature-important ranking. These variables represent relative contributions within the model and not the percentage of attrition caused by each sector. It helps HR who may wish to investigate such as compensation, experience and tenure.

## **Power BI** ##
The test predictions were then exported to Power BI Desktop. It contains 294 test records.

The Predictive Analysis focuses on the following  
• Actual vs Predicted Attrition  
• Predicted Employee Attrition Risk Distribution  
• Top 5 Predictive Features - Random Forest  

<img width="1443" height="804" alt="image" src="https://github.com/user-attachments/assets/bbaeb5be-9876-459d-bd01-190beaf06fa6" />

## **Observation** ##

**Model Comparison Table**

| Model | Threshold | Accuracy (%) | Precision (%) | Recall (%) | F1-score (%) | ROC-AUC (%) |
|---|---:|---:|---:|---:|---:| ---:|
| Logistic Regression | 0.50 | 75.17 | 34.88 | 63.83 | 45.11 | 0.80 |
| Random Forest | 0.30 | 84.01 | 50.00 | 42.55 | 45.98 | 0.79 |

**Actual vs Predicted Attrition Chart** - The chart shows the actual attrition outcomes in the test dataset with the model's predictions and provides an initial visual assessment of prediction patterns.

**Predicted Employee Attrition Risk Distribution** - The chart shows how the employees in the test dataset are distributed across the project's three predicted risk bands.

| Risk Group | Employee | Percentage |
| :-- | :-- | :-- |
| Low Risk | 116 | 39.46% |
| Medium Risk | 92 | 31.29% |
| High Risk | 86 | 29.25 % |
| Total | 294 | 100% |

**Top 5 Predictive Features - Random Forest** - The scores show relative measures produced by Random Forest model. They show the probabilities that an employee will leave or percentages of employees affected. 

## **HR - Recommendation** ##

| **Recommendation** | **Supporting Finding** | **Suggested HR Action** |
|---|---|---|
| **1. Review High-Attrition Job Roles** | Sales Representatives had an attrition rate of 39.76%. | Review sales targets, workload, incentives, management support and career progression. |
| **2. Review Compensation and Benefits** | Employees earning below 3,000 had an attrition rate of 28.61%. | Compare compensation and benefits with job responsibilities, internal salary ranges and market benchmarks. |
| **3. Improve Employee Engagement** | Employees with the lowest job involvement rating had an attrition rate of 33.73%. | Conduct employee surveys, regular manager check-ins and career development discussions. |
| **4. Manage Overtime and Workload** | Employees working overtime had an attrition rate of 30.53%. | Monitor overtime frequency, workload distribution and staffing levels, and assess whether additional support is needed. |
| **5. Strengthen Support for New Employees** | Employees with 0–2 years of service had an attrition rate of 29.82%. | Improve onboarding, mentoring, early performance feedback and career planning. |

## **Conclusion** ##
This project analysed 1,470 employee records from the IBM HR Analytics dataset to understand why employees leave the company. The analysis found higher attrition rates among Sales Representatives, lower-income employees, employees with poor work-life balance, those working overtime, and employees with fewer years of service. Two predictive models, Logistic Regression and Random Forest, were used to estimate employee attrition, with different strengths in identifying employees who might leave and making correct predictions. The results were presented through Power BI dashboards, together with recommendations to improve compensation, manage workloads, increase employee engagement and provide better support for new employees. Overall, this project shows how data analysis and visualisation can help HR make better decisions and plan ways to retain employees. Further testing is needed before using the predictions in actual HR decisions.



