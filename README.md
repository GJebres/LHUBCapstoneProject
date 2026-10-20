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

## **Exploratory Data Analysis** ##
After uploading all the dataset, we start with Data Cleansing and Preparation. Out of the dataset used, we can identify that there is 1 discrepancy which was found in Age Group. With this information, we locate the missing data in Age Group and generate a quick statistical summary. The next step is to get the median age and fill in the missing age in the data. 

## **Attrition Analysis** ##
The analysis starts with the Employee Attrition analysis (RO1) to know the numbers of employees who left and those who stayed. The result shows that the number(percentage) of staff who stayed is 1233(83.88%) and those who left is 237 (16.12%)

The next step is to address the attrition based on the department, job role, age group and overtime status to determine which employee groups are more affected by the turnover.

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/b56537bf-b0cd-4a62-9c52-1abd09d5ae66" /> <br/>
| Department | Attrition Rate (%) |
| :--- | :--- |
| Human Resources | 19.05 |
| Research & Development | 13.84 |
| Sales | 20.63 |

<img width="628" height="470" alt="image" src="https://github.com/user-attachments/assets/b93d1357-dd26-4f70-96fd-f3d42438c615" /> <br/>
| Job Role | Attrition Rate (%) |
| :--- | :---: |
| Sales Representative | 39.76 |
| Laboratory Technician | 23.94 |
| Human Resources | 23.08 |
| Sales Executive | 17.48 |
| Research Scientist | 16.10 |
| Manufacturing Director | 6.90 |
| Healthcare Representative | 6.87 |
| Manager | 4.90 |
| Research Director | 2.50 |

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/41e66119-7092-4683-8973-2820786a3af5" /> <br/>
| Age Group | Attrition Rate (%) |
| :--- | :---: |
| Under 26 | 35.77 |
| 26-35 | 19.24 |
| 36-45 | 9.13 |
| 46-55 | 11.50 |
| 56 and above | 17.02 |

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/dcf0fe92-d28c-491b-b89b-f7d10c0e310b" /> <br/>
| Overtime | Attrition Rate (%) |
| :--- | :---: |
| No | 10.44 |
| Yes | 30.53 |

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/236369bb-9626-4f60-984a-fd496780d6ba" /> <br/>
| Attrition | Average Monthly Income |
| :--- | :---: |
| No | 6832.74 |
| Yes | 4787.09 |

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/28987680-05a6-4ee6-9278-6ea510df0e8b" /> <br/>
| Attrition  Job Satisfaction | No | Yes | Attrition Rate (%)|
| :--- | :--- | :--- | :--- |
| 1 | 223 | 66 | 22.84 |
| 2 | 234 | 46 | 16.43 |
| 3 | 369 | 73 | 16.52 |
| 4 | 407 | 52 | 11.33 |

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/440fc4da-8db4-4a3d-b1bd-cefcef5b8800" /> <br/>
| Attrition Work Life balance | No | Yes | 
| :--- | :--- | :--- | 
| 1 | 68.75 | 31.25 |
| 2 | 83.14 | 16.86 |
| 3 | 85.78 | 14.22 |
| 4 | 82.35 | 17.65 |

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/1a78f59b-81d9-4b3d-9976-2168524b7b9c" /> <br/>
|  | Attrition Rate (%) |
| :--- | :---: |
| No | 11.86 |
| Yes | 8.24 |

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/f82059b6-ddb8-4d82-9d9d-9c5860bf622a" /> <br/>
|  | Attrition Rate (%) |
| :--- | :---: |
| No | 7.37 |
| Yes | 5.13 |


