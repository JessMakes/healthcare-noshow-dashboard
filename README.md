Healthcare-noshow Insights Dashboard


This project is based on the public "No-Show Appointments" dataset originally published on Kaggle. 
It contains 110K+ medical appointments from Brazil, including patient demographics, chronic conditions, and SMS reminders.
Data was used for non-commercial, educational purposes only.

I cleaned and transformed the dataset using Excel and Power Query in Power BI to support the dashboard visuals and insight generation.


## Data Cleaning & Transformation Summary

| Task Description                     | Tool Used    | Column(s) Affected                    | Steps Involved                                                                 |
|-------------------------------------|--------------|----------------------------------------|--------------------------------------------------------------------------------|
| **Label SMS Status**                | Excel        | `SMS_received` → `SMS_Status`         | Converted binary values: `TRUE` → “Got SMS”, `FALSE` → “No SMS”               |
| **Simplify No-show Logic**          | Excel        | `No-show` → `Showed_Up`               | Reversed logic: `"No"` → “Showed Up”, `"Yes"` → “No-Show”                     |
| **Create Age Groups**               | Excel        | `Age` → `Age Band`                    | Grouped ages into bands: 0–18, 19–30, 31–45, 46–60, 61+                        |
| **Unpivot Conditions**              | Power Query  | `Diabetes`, `Hypertension`, `Alcoholism` | Unpivoted into a single `Condition` column                                     |
| **Add Presence Indicator**          | Power Query  | `Condition` → `Present`               | Created Boolean column indicating if condition is present                      |
| **Filter Relevant Records**         | Power Query  | `Present`                             | Kept only `Present = TRUE` rows for condition-level analysis                  |
| **Relabel Booleans in Attendance**  | Power Query  | `Showed_Up`                           | Replaced `TRUE` → “Showed Up”, `FALSE` → “No-Show”                             |



A Power Bi Project analyzing no-show rates across demographic and SMS remindedrs
Reducing Missed Appointments: Who Misses, Why, and How to Improve

Project Summary:
This project analyzes 428,000 patient appointments from a real-world healthcare dataset to uncover patterns behind missed appointments (no-shows). 
The interactive Power BI dashboard explores trends across age, gender, medical conditions, and the effectiveness of SMS reminders. 
The goal is to support data-driven decisions that improve patient attendance, optimize scheduling, and enhance operational efficiency.

Dashboard Highlights

1. Total Appointments Scheduled

Total Volume: 427,950 appointments.
Even small improvements in show-up rate can lead to large operational gains.

2. No-Show Rate by Age Band
Highest no-shows: 41–65 and 18–40 age groups.

Recommendation: Prioritize reminders and flexible scheduling for working-age adults.

3. Attendance by Chronic Condition
Higher attendance: Hypertension, diabetes.
Lower attendance: Alcoholism, handicap.

Recommendation: Provide additional support or follow-up for vulnerable groups.

4. Gender-Based Attendance
Insight: Women showed up more often than men.

Recommendation: Explore possible barriers men face and adjust outreach strategies.

5. SMS Reminder Effectiveness
No-shows with SMS: 38,272
No-shows without SMS: 48,448

Recommendation: SMS reminders help but aren’t a silver bullet. Combine with personalized follow-up.

6. SMS Distribution by Age Group
Most SMS sent: 41–65 and 18–40
Insight: Despite high SMS volume, no-show rates remain high for these groups.

Recommendation: Experiment with SMS tone, timing, and frequency.

7. No-Show Flag Summary
Overall no-shows: 86,720 (~20%)
Opportunity: Reducing no-shows by even 5% can free up over 21,000 appointments/year.

Business Impact

Reducing no-shows improves:
Patient access to care
Clinic efficiency
Staff resource planning
Revenue recovery

This dashboard enables targeted interventions for high-risk groups and channels (e.g. SMS).

Tools Used

Power BI: Dashboard creation and interactive analysis
Excel: Data wrangling and no-show flag logic

Next Steps

Segment analysis by clinic location or time of day
Share filtered dashboards with care teams for local actions


Prepared by Jessica | Healthcare Analytics Portfolio
Note: To view and interact with the dashboard file (.pbix), you'll need to have Microsoft Power BI Desktop installed on your computer.

