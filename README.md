# Employee Attrition Dashboard (Power BI)

This project looks into whether employee attrition at a company is a broad problem or something concentrated in specific groups, since the answer changes what a company should actually do about it. The dataset has 1,470 employees from the IBM HR Analytics dataset, and the analysis was built in Power BI.

The reason the question matters is that a company responding to a general attrition problem will do very different things compared to one that knows the issue sits in one role, or one type of working condition. The goal here was to find out which one it actually is, and follow the evidence from there.

## What I was trying to answer

Before opening Power BI, I wrote down one main question I wanted the whole project to answer:

> What are the key drivers of employee attrition at this company, and which employee groups are at the highest risk of leaving?

And the idea I wanted to test:

> Attrition is not random. It is concentrated in certain groups, like people who work overtime, are paid less, are not satisfied, or are new to the company. If that is true, the company can focus on those groups instead of trying generic things for everyone.

## About the data

The dataset has one row per employee, with things like age, department, job role, overtime, income, satisfaction scores, and whether they left the company or not.

A few notes on how I cleaned it:
- I checked for duplicate employee numbers. There were none.
- I checked every column for blank values and typos. The data was clean.
- I removed three columns that had the same value for every single row (EmployeeCount, Over18, StandardHours). They had no use for analysis.
- There is no date column anywhere in this dataset. That means I could not look at attrition over time. Everything here is a snapshot, so all my comparisons are between groups, not trends over time. I want to be upfront about that since it is a real limit of this dataset.
- I kept everything in one flat table instead of building a more complex model with several tables. I thought about splitting it up, but there was no second dataset to connect it to, so doing that would have just added complexity without adding any real value.

## What I found

**Overall attrition rate: 16%** (237 out of 1,470 employees left)

### Sales Representatives are the highest risk role
Looking at department alone, Sales had the highest attrition (21%). But when I went one level deeper into job role, Sales Representative on its own showed a 40% attrition rate, way higher than the department number suggested. The department figure was hiding how bad it was for this one role specifically.

### Overtime is the biggest factor I found
This showed up again and again, no matter which group I looked at.

- Company wide: people working overtime had a 31% attrition rate, compared to 10% for those who do not.
- Sales Representatives only: 66.7% attrition for those working overtime, compared to 28.8% for those who do not.

### Job satisfaction matters, but less than overtime
Attrition drops as satisfaction goes up (23% at the lowest satisfaction level down to 11% at the highest). But when I checked overtime and satisfaction together, overtime won out. Even employees with the highest satisfaction score who worked overtime still had a 21% attrition rate, higher than unhappy employees who did not work overtime (18%). So satisfaction is not the main thing driving people to leave. Overtime is.

### New employees working overtime are the riskiest group I found
Employees with less than 5 years at the company who also work overtime have a 43% attrition rate. This was the highest number I found across the whole project. I did not trust the data for people with more than 15 years at the company, since there were very few people in those groups (sometimes under 10 people), so I left those out of my conclusions.

### Pay matters too, even within the same job
People who left earned about 30% less on average than people who stayed, company wide. I wanted to check if this was just because lower paid jobs naturally have more turnover, so I checked it again using only Sales Representatives, same job, different pay. The gap was still there, just smaller, about 15.5%. That tells me pay itself is a real factor, not just a side effect of which job someone has.

## What I would tell the company, based on this

- Overtime is the strongest single thing linked to people leaving. I would look at this first.
- Sales Representatives need attention specifically, not just the Sales department as a whole.
- New employees who are also working overtime are the group most likely to leave. This combination is worth addressing early, maybe in the first year.
- Pay plays a real role too, even comparing people in the exact same job.

## What this project cannot tell you

- This is one snapshot in time, so I cannot say if attrition is going up or down, only how it looks right now.
- I found things that are linked together (like overtime and leaving), but that does not prove one causes the other. For example, maybe unhappy people avoid overtime instead of overtime making people unhappy. I cannot tell which way it goes from this data alone.
- A few groups in the data were too small to trust (like employees with 30+ years at the company), so I left those out rather than making claims I could not back up.

## Dashboard pages

The Power BI file has four main pages:

1. **Executive Overview** – the main KPIs, the biggest finding, and a quick look at department and job role

   ![Executive Overview](images/01_executive_overview.png.png)

2. **Risk Drivers** – overtime, satisfaction, and how they combine with tenure

   ![Risk Drivers](images/02_risk_drivers.png.png)

3. **Compensation** – the pay gap, company wide and within one role

   ![Compensation](images/03_compensation.png)

4. **Sales Rep Spotlight** – a closer look at the highest risk role

   ![Sales Rep Spotlight](images/04_sales_rep_spotlight.png)

Screenshots of all four pages are in the `images` folder. I also kept my early working pages inside the file (hidden, not deleted) in case anyone wants to see how I tested each idea step by step.

## Tools used

Power BI Desktop, using Power Query for cleaning the data and DAX for the measures (mainly CALCULATE, DIVIDE, and AVERAGE).

## Files in this repo

- `IBM_HR_Analytics.pbix` – the Power BI file
- `Employee_Attrition_Report.docx` – a written version of this same analysis
- `images/` – screenshots of the four main dashboard pages
