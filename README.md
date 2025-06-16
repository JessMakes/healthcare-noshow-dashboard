## Healthcare No-Show Insights

### Project Overview

This project analyzes a real-world healthcare dataset of over 110,000 patient appointments from Brazil, sourced from Kaggle. The goal was to uncover patterns behind missed appointments (no-shows) and generate actionable strategies to improve patient attendance.

Key variables explored include patient age, gender, chronic medical conditions, and whether an SMS reminder was received. The analysis was conducted using **Excel**, **Power Query**, **Power BI**, and **SQL** for data transformation, visualization, and insight development.

The findings are contextualized with external research showing the significant financial cost of no-shows: approximately **\$150 billion per year in the U.S.** and **millions in annual hospital losses in Australia**.

---

### Key Insights from the Dashboard

* **Ages 41–65 had the highest number of no-shows**
  This middle-aged group accounted for the greatest volume of missed appointments, making them a high-priority segment for intervention.

* **Hypertension patients showed the highest no-show counts among chronic conditions**
  This signals the need for additional engagement efforts with patients managing long-term illnesses.

* **Only about 40% of patients received an SMS reminder**
  Despite limited coverage, SMS reminders proved effective at reducing no-shows.

* **SMS reminders lowered no-show volume by approximately 20%**
  Patients who received reminders were significantly more likely to attend their appointments.

* **Women attended appointments more consistently than men**
  Approximately 66% of attendance was female, suggesting potential to tailor outreach strategies by gender.

---

### Recommendations

* Expand SMS coverage to all patients, as reminders are clearly linked to improved attendance
* Target patients aged 41–65 with additional or repeated reminders
* Implement receptionist follow-ups or calls for patients with chronic conditions, especially hypertension
* Explore gender-based engagement strategies to improve male attendance rates

---

### Data Cleaning and Transformation

The dataset was cleaned and reshaped using **Excel**, **Power Query**, and **SQL** to prepare it for analysis and visualization. Key steps included:

| Task                              | Tool Used   | Columns Affected                   | Description                                                                                       |
| --------------------------------- | ----------- | ---------------------------------- | ------------------------------------------------------------------------------------------------- |
| Label SMS Status                  | Excel       | SMS\_received → SMS\_Status        | Converted binary values: TRUE → "Got SMS", FALSE → "No SMS"                                       |
| Simplify No-show Logic            | Excel       | No-show → Showed\_Up               | Reversed logic: "No" → "Showed Up", "Yes" → "No-Show"                                             |
| Create Age Groups                 | Excel       | Age → Age Band                     | Grouped ages into bands: 0–18, 19–30, 31–45, 46–60, 61+                                           |
| Unpivot Conditions                | Power Query | Diabetes, Hypertension, Alcoholism | Unpivoted into a single Condition column                                                          |
| Add Presence Indicator            | Power Query | Condition → Present                | Created Boolean column indicating if condition is present                                         |
| Filter Relevant Records           | Power Query | Present                            | Kept only Present = TRUE rows for condition-level analysis                                        |
| Relabel Booleans in Attendance    | Power Query | Showed\_Up                         | Replaced TRUE → "Showed Up", FALSE → "No-Show"                                                    |
| Aggregate KPIs & Segment Analysis | SQL         | All Columns                        | Used SQL queries to segment data and summarize metrics by gender, age, conditions, and SMS status |

---

### SQL Queries Used (Aligned to Power BI Dashboard)

Below are the SQL queries that support the key visuals and metrics in the dashboard. These queries reflect logic equivalent to what was applied in Power BI during data exploration and transformation.

#### 1. Total Appointments Scheduled

```sql
SELECT COUNT(*) AS total_appointments
FROM noshow_raw;
```

#### 2. No-Show by Age Band

```sql
SELECT
  CASE
    WHEN Age BETWEEN 0 AND 17 THEN 'Under 18'
    WHEN Age BETWEEN 18 AND 40 THEN '18-40'
    WHEN Age BETWEEN 41 AND 65 THEN '41-65'
    ELSE '66+'
  END AS Age_Band,
  COUNT(*) AS total_appointments,
  SUM(CASE WHEN Showed_up = 'FALSE' THEN 1 ELSE 0 END) AS no_shows
FROM noshow_raw
GROUP BY Age_Band
ORDER BY no_shows DESC;
```

#### 3. Attendance by Chronic Condition

```sql
SELECT 'Hypertension' AS Condition, COUNT(*) AS count
FROM noshow_raw WHERE Hipertension = 'TRUE'
UNION ALL
SELECT 'Diabetes', COUNT(*) FROM noshow_raw WHERE Diabetes = 'TRUE'
UNION ALL
SELECT 'Alcoholism', COUNT(*) FROM noshow_raw WHERE Alcoholism = 'TRUE'
UNION ALL
SELECT 'Handcap', COUNT(*) FROM noshow_raw WHERE Handcap = 'TRUE';
```

#### 4. Total Appointments by SMS Status

```sql
SELECT SMS_received,
       COUNT(*) AS total_appointments
FROM noshow_raw
GROUP BY SMS_received;
```

#### 5. No-Show Count by SMS Status

```sql
SELECT SMS_received,
       SUM(CASE WHEN Showed_up = 'FALSE' THEN 1 ELSE 0 END) AS no_shows
FROM noshow_raw
GROUP BY SMS_received;
```

#### 6. Showed Up Status by Gender

```sql
SELECT Gender,
       COUNT(*) AS total_appointments,
       SUM(CASE WHEN Showed_up = 'TRUE' THEN 1 ELSE 0 END) AS showed_up
FROM noshow_raw
GROUP BY Gender;



### Tools Used

* **Excel**: Data cleaning and column derivation (e.g., SMS labels, age bands)
* **Power Query**: Data reshaping (wide to long format)
* **SQL**: Calculating aggregated metrics, conditional counts, and grouping logic
* **Power BI**: Dashboard visuals and insight development

---

### Dataset Source

**Brazil No-Show Appointments Dataset**
Source: [Kaggle – Joni Arroba](https://www.kaggle.com/datasets/joniarroba/noshowappointments)
Total records: 110,000+ appointments
Usage: Educational and non-commercial purposes only

---

### Financial Impact of Missed Appointments

* **United States**: \~\$150 billion in annual losses; \~\$200 per missed visit
* **Australia**: \$500,000/year loss at St Vincent’s; up to \$3.8 million/month in QLD outpatient clinics
* **Sources**: NSW Government, The Guardian, TransLoc
