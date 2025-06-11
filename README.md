Healthcare-noshow Insights 


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


# Reducing Missed Appointments: Who Misses, Why, and How to Improve

## Project Overview

This project analyzes a real-world healthcare dataset of over 110,000 patient appointments from Brazil, sourced from Kaggle. The goal was to uncover patterns behind missed appointments (no-shows) and generate actionable strategies to improve patient attendance.

Key variables explored include patient age, gender, chronic medical conditions, and whether an SMS reminder was received. The analysis was conducted using Excel, Power Query, and Power BI for data transformation, visualization, and insight development.

The findings are contextualized with external research showing the significant financial cost of no-shows — approximately $150 billion per year in the U.S. and millions in annual hospital losses in Australia.

---

## Key Insights from the Dashboard

- Ages 41–65 had the highest number of no-shows  
  This middle-aged group accounted for the greatest volume of missed appointments, making them a high-priority segment for intervention.

- Hypertension patients showed the highest no-show counts among chronic conditions  
  This signals the need for additional engagement efforts with patients managing long-term illnesses.

- Only about 40% of patients received an SMS reminder  
  Despite limited coverage, SMS reminders proved effective at reducing no-shows.

- SMS reminders lowered no-show volume by approximately 20%  
  Patients who received reminders were significantly more likely to attend their appointments.

- Women attended appointments more consistently than men  
  Approximately 66% of attendance was female, suggesting potential to tailor outreach strategies by gender.

---

## Recommendations

- Expand SMS coverage to all patients, as reminders are clearly linked to improved attendance  
- Target patients aged 41–65 with additional or repeated reminders, given their high no-show volume  
- Implement receptionist follow-ups or calls for patients with chronic conditions, especially hypertension  
- Explore gender-based engagement strategies — such as message timing or format — to improve male attendance rates

---

## Tools Used

- Excel: Data cleaning and derived columns (e.g., age bands, SMS labels)  
- Power Query: Wide-to-long format reshaping for chronic condition analysis  
- Power BI: Visualizations, insight extraction, and executive summary design

---

## Dataset Source

Brazil No-Show Appointments Dataset  
Source: [Kaggle - Joni Arroba](https://www.kaggle.com/datasets/joniarroba/noshowappointments)  
Contains over 110,000 appointment records  
Used for educational, non-commercial purposes

---

## Financial Impact of Missed Appointments

- United States: Approximately $150 billion in annual losses; $200 per missed visit  
- Australia: $500,000 annual loss at St Vincent’s Hospital; up to $3.8 million per month in QLD specialist clinics  
- Sources: NSW Government, The Guardian, TransLoc




