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
1. **Employee Attrition Rate and Workforce Trends:** <br/> To measure the employee attrition rate and analyse overall workforce trends to understand employee turnover patterns.
2. **Department and Job Role Attrition Analysis:** <br/> To identify departments and job roles with higher attrition rates to determine which employee groups are more affected by turnover.
3. **Factors Associated with Employee Attrition:**<br/> To examine the relationships between compensation, job satisfaction, overtime, work experience, years of service and employee attrition.
4. **Interactive HR Dashboard Development:** <br/> To develop an interactive dashboard to visualise employee attrition patterns and key workforce indicators to support data-driven HR decision-making.
5. **Employee Retention Strategy Recommendations:**<br/> To recommend practical strategies to improve employee retention and reduce attrition based on the findings from the workforce analysis and dashboard.

## **Tools to use** ##
HR data set <br/> Power BI - Interactive dashboard and business reporting <br/> Python - Develop and evaluate predictive models

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

After uploading all the dataset, we start with Data Cleansing and Preparation. Out of the dataset used, we can identify that there is 1 discrepancy which was found in Age Group. With this information, we locate the missing data in Age Group and generate a quick statistical summary. The next step is to get the median age and fill in the missing age in the data. 
