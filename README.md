# Employee Attrition Dashboard (Power BI)

This project looks into whether employee attrition at a company is a broad problem or something concentrated in specific groups, since the answer changes what a company should actually do about it. It uses the IBM HR Analytics dataset of 1,470 employees, and the analysis was built in Power BI.

The reason the question matters is that a company treating attrition as a general problem will respond very differently to one that knows exactly where it is concentrated. This project follows the evidence to find out which one is actually true here.

An interactive Power BI file is included in this repo, along with screenshots of the main dashboard pages below.

## Executive Summary

- **Attrition rate: 16%** (237 of 1,470 employees)
- **Retention rate: 84%**
- **231 employees currently match the highest risk profile** (0 to 5 years tenure, working overtime)
- **Estimated cost of attrition: 1.70M**, based on an average replacement cost of 1.5 times monthly income per departure. This is an estimate, not a figure pulled directly from company data, and the multiplier can be adjusted depending on how conservative a company wants to be
- **Sales Representative is the single highest risk role**, at 40% attrition against the 16% company average
- **Overtime is the strongest factor found**, tripling attrition rate across almost every group tested

## Key Findings

**Attrition is concentrated, not spread evenly across the company.**
Looking at department alone, Sales sits at 21%, HR at 19%, and R&D at 14%. That already points to Sales as the area of concern, but department is a broad grouping. Breaking it down by job role tells a sharper story: Sales Representative on its own sits at 40%, nearly double what the department figure suggested. The department number was hiding how bad it actually was for this one role.

**Overtime is the strongest driver of attrition in this dataset.**
Company wide, employees working overtime have a 31% attrition rate, compared to 10% for those who do not, roughly three times higher. Within Sales Representatives specifically, the gap is even sharper: 66.7% for those working overtime against 28.8% for those who are not.

**New employees working overtime are the highest risk group in the company.**
Employees with 5 years or less at the company who are also working overtime show a 43% attrition rate, the highest figure found across the whole analysis. Right now, 231 current employees fall into exactly this profile. That is not a historical number, it is a live headcount of people currently sitting in the riskiest segment identified.

**Job satisfaction matters, but overtime overrides it.**
Attrition drops from 23% at the lowest satisfaction level down to 11% at the highest, which follows the pattern you would expect. But once overtime is factored in, even the most satisfied employees working overtime show a 21% attrition rate, higher than dissatisfied employees who are not working overtime (18%). Overtime turns out to be the stronger factor by a clear margin.

**A real pay gap exists between employees who left and those who stayed, even within the same role.**
Company wide, employees who left earned about 30% less on average than those who stayed. That gap could partly be explained by junior roles simply paying less and turning over more for unrelated reasons, so this was checked again using only Sales Representatives, where everyone holds the same job title. The gap was still there, just smaller, at 15.5%, which suggests pay itself is a real factor, not just a byproduct of job level.

## Recommendations

- **Review staffing and overtime distribution within the Sales Representative role first.** This single role accounts for the highest attrition in the company, and overtime is the strongest factor tied to it.
- **Focus retention efforts on the first 5 years of employment, specifically where overtime is involved.** This is the highest risk window identified, and 231 current employees fall directly into this group today.
- **Investigate compensation for Sales Representatives specifically**, since a real pay gap exists even when comparing people doing the exact same job.
- **Treat satisfaction as a secondary indicator, not the primary lever.** It correlates with attrition, but overtime has a stronger and more consistent effect across every group tested.

## What This Cannot Tell You

This dataset is a single snapshot with no date fields, so it cannot show whether attrition is rising or falling over time, only how things look right now.

The relationships found here are correlations, not proven causes. Overtime, satisfaction, and pay are all linked to attrition, but this data cannot fully separate which factor is the root cause versus a symptom of another. For example, it is possible that employees already planning to leave avoid overtime, rather than overtime pushing them to leave.

Some groups in the data were too small to draw conclusions from reliably, such as employees with more than 15 years at the company (in some cases fewer than 10 people), and were left out of the findings for that reason.

The cost of attrition figure is an estimate based on a standard replacement cost multiplier (1.5 times monthly income), not an actual company reported cost.

## Dashboard Pages

1. **Executive Overview** – core business metrics (attrition rate, retention rate, high risk headcount, estimated cost of attrition), plus department and job role breakdown

   ![Executive Overview](images/01_executive_overview.png.png)

2. **Risk Drivers** – overtime, satisfaction, and how they combine with tenure

   ![Risk Drivers](images/02_risk_drivers.png.png)

3. **Compensation** – the pay gap, company wide and within one role

   ![Compensation](images/03_compensation.png)

4. **Sales Rep Spotlight** – a focused look at the highest risk role

   ![Sales Rep Spotlight](images/04_sales_rep_spotlight.png)

Earlier working pages, where each hypothesis was tested individually before being pulled together, are kept in the file but hidden, in case anyone wants to see the process behind the final pages.

## Tools Used

Power BI Desktop, using Power Query for data preparation and DAX for the measures (CALCULATE, DIVIDE, AVERAGE).

## Files in This Repo

- `IBM_HR_Analytics.pbix` – the Power BI file
- `Employee_Attrition_Report.docx` – a written version of this same analysis
- `images/` – screenshots of the four main dashboard pages
