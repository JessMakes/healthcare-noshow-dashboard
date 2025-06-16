# Healthcare No-Show Insights 

## Project Overview

This project analyzes a real-world healthcare dataset of over 110,000 patient appointments from Brazil, sourced from Kaggle. The goal was to uncover patterns behind missed appointments (no-shows) and generate actionable strategies to improve patient attendance.

Key variables explored include patient age, gender, chronic medical conditions, and whether an SMS reminder was received. The analysis was conducted using Excel, Power Query, and Power BI for data transformation, visualization, and insight development.

The findings are contextualized with external research showing the significant financial cost of no-shows — approximately $150 billion per year in the U.S. and millions in annual hospital losses in Australia.

---

## Key Insights from the Dashboard

- **Ages 41–65 had the highest number of no-shows**  
  This middle-aged group accounted for the greatest volume of missed appointments, making them a high-priority segment for intervention.

- **Hypertension patients showed the highest no-show counts among chronic conditions**  
  This signals the need for additional engagement efforts with patients managing long-term illnesses.

- **Only about 40% of patients received an SMS reminder**  
  Despite limited coverage, SMS reminders proved effective at reducing no-shows.

- **SMS reminders lowered no-show volume by approximately 20%**  
  Patients who received reminders were significantly more likely to attend their appointments.

- **Women attended appointments more consistently than men**  
  Approximately 66% of attendance was female, suggesting potential to tailor outreach strategies by gender.

---

## Recommendations

- Expand SMS coverage to all patients, as reminders are clearly linked to improved attendance  
- Target patients aged 41–65 with additional or repeated reminders  
- Implement receptionist follow-ups or calls for patients with chronic conditions, especially hypertension  
- Explore gender-based engagement strategies to improve male attendance rates

---

## Data Cleaning and Transformation

The dataset was cleaned and reshaped using Excel and Power Query to prepare it for analysis and visualization. Key steps included:

| Task | Tool Used | Columns Affected | Description |
|------|-----------|------------------|-------------|
| Label SMS Status | Excel | SMS_received → SMS_Status | Converted binary values: TRUE → “Got SMS”, FALSE → “No SMS” |
| Simplify No-show Logic | Excel | No-show → Showed_Up | Reversed logic: "No" → “Showed Up”, "Yes" → “No-Show” |
| Create Age Groups | Excel | Age → Age Band | Grouped ages into bands: 0–18, 19–30, 31–45, 46–60, 61+ |
| Unpivot Conditions | Power Query | Diabetes, Hypertension, Alcoholism | Unpivoted into a single Condition column |
| Add Presence Indicator | Power Query | Condition → Present | Created Boolean column indicating if condition is present |
| Filter Relevant Records | Power Query | Present | Kept only Present = TRUE rows for condition-level analysis |
| Relabel Booleans in Attendance | Power Query | Showed_Up | Replaced TRUE → “Showed Up”, FALSE → “No-Show” |

---

## Tools Used

- **Excel**: Data cleaning and column derivation (e.g., SMS labels, age bands)  
- **Power Query**: Data reshaping (wide to long format)  
- **Power BI**: Dashboard visuals and insight development

---

## Dataset Source

Brazil No-Show Appointments Dataset  
Source: [Kaggle – Joni Arroba](https://www.kaggle.com/datasets/joniarroba/noshowappointments)  
Total records: 110,000+ appointments  
Usage: Educational and non-commercial purposes only

---

## Financial Impact of Missed Appointments

- **United States**: ~$150 billion in annual losses; ~$200 per missed visit  
- **Australia**: $500,000/year loss at St Vincent’s; up to $3.8 million/month in QLD outpatient clinics  
- **Sources**: NSW Government, The Guardian, TransLoc

---

