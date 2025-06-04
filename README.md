# PharmNova Inc. Attrition Analysis

## Table of Contents
- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Tools](#tools)
- [Data Preparation](#data-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results and Findings](#results-and-findings)
-  [Recommendations](#recommendations)
-   [Credits](#credits)
-   [References](#references)

### Project Overview
This report analyzes employee attrition patterns using demographic, compensation, and work-related factors. The aim is to identify key trends influencing employee turnover and provide data-backed recommendations to improve retention, ensuring sustained growth and customer loyalty.

![Attrition](https://github.com/user-attachments/assets/a052e43d-1b82-4aef-9365-adfa21fffdc0)

	
### Data Source
[Get data set here](https://selar.co/m/mk-data-consultz1)

### Tools
-  Python: Data Cleaning, Data Analysis
    -   Download Anaconda to access Jupiter Notebook [here](https//microsoft.com)
-  Power BI: Data Visualization
    -   [Download Power BI here](https//microsoft.com)

### Data Preparation
Below are my key steps during data preparation:
-  Loaded data into Jupiter Notebook
   -   ``` data = pd.read_csv ("Attrition Dataset.csv")```
   -    ```data```
-  Cleaned and formatted the data (with python)
    -   replaced values, removed columns, removed duplicates, and changed data type

### Exploratory Data Analysis
This involves examining the data to address the following objectives:
- To quantify and profile attrition across organizational demographics and functions.
- To identify high-risk employee segments contributing to workforce turnover.
- To explore root causes of attrition using satisfaction, education, and tenure metrics. 
- To provide actionable recommendations to improve employee retention and 
organizational stability.

### Data Analysis

Below are some of the Data Analytics Expressions (DAX) featured in the project:
-	Using ```CALCULATE``` function:

  
% Female Attrition = ```VAR Female_Attrition = CALCULATE([Total Attrition],FILTER(Data,Data[Gender]="Female")) VAR Total_Attrition = [Total Attrition]```
```RETURN DIVIDE(Female_Attrition,[Total Attrition],0)```

% High Performance = ```VAR High = CALCULATE([Inactive Employees],FILTER(Data,Data[Performance Status]="High")) VAR Total_Attrition = [Inactive Employees]```
```RETURN DIVIDE(High,Total_Attrition,0)```

% Low Performance = ```VAR Low = CALCULATE([Inactive Employees],FILTER(Data,Data[Performance Status]="Low")) VAR Total_Attrition = [Inactive Employees]```
```RETURN DIVIDE(Low,Total_Attrition,0)```

Active Employees = ```CALCULATE([Total Employees],FILTER(Data,Data[Attrition]="no"))```

Female = ```IF(ISBLANK(CALCULATE([Total Employ-ees],FILTER(Data,Data[Gender]="Female"))),0,CALCULATE([Total Employ-ees],FILTER(Data,Data[Gender]="Female")))```

Recruitment Cost by Department = ```VAR CostPerHire = 5000 ```
```RETURN CALCULATE(COUNT('Data'[emp no]), 'Data'[Attrition] = "Yes") * CostPerHire```



-	Using Aggregates (```SUMX, DIVIDE```)  functions:


% Active = ```DIVIDE([Active Employees],[Total Employees],0)```
  

 Turnover Cost by Role = ```VAR AnnualMultiplier = 1.2```
```RETURN SUMX(FILTER('Data', 'Data'[Attrition] = "Yes"),'Data'[Monthly Income] * 12 * AnnualMultiplier)```
 
%Sales = ```DIVIDE([Sales Department],[Total Attrition])```


%R&D = ```DIVIDE([R&D Department],[Total Attrition])```


%Associates Degree = ```DIVIDE([Associates Degree],[Total Attrition])```



    
### Results and Findings
