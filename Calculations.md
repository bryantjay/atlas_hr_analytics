# Calculations

##### There are six calculations made. The first four of them will also be used as KPI cards.

**Total Employees** is the distinct count of all employees, regardless of whether Attrition has occurred.

    COUNTD([Employee ID])


**Current Employees** is a count of all employees where Attrition is false.

    COUNT(IF [Attrition] = 'No' THEN [Employee ID] ELSE NULL END)

**Past Employees** is a count of all employees where attrition is true.

    COUNT(IF [Attrition] = 'Yes' THEN [Employee ID] ELSE NULL END)

**Attrition Rate** is the ratio of all Past Employees relative to Total Employees.

    [Past Employees] / [Total Employees]

**Employed Status** is effectively a re-labeling of Attrition for one of the dashboard visualizations.

    IF [Attrition] = 'Yes' THEN 'Past'
    ELSEIF [Attrition] = 'No' THEN 'Current'
    ELSE NULL END

Age will be manually binned into **Age Group** for analysis using a custom calculation, so that age outliers under 20 and over 50 are collected into respective tail groups.

    IF [Age] < 20 THEN 'Under 20'
    ELSEIF [Age] < 30 THEN '20-29'
    ELSEIF [Age] < 40 THEN '30-39'
    ELSEIF [Age] < 50 THEN '40-49'
    ELSE 'Over 50' END
