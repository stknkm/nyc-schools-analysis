# 📊 SAT Data Cleaning & Database Population

## 📌 Overview
This section describes the cleaning of SAT score data and loading into a PostgreSQL database.  

## 🛠 Cleaning Steps
- Standardized column names (lowercase, underscores, no special characters)  
- Dropped unnecessary columns (`internal_school_id`, `contact_extension`)  
- Converted numeric strings into proper numbers (`errors="coerce"`)  
- Ensured SAT scores are within valid range (200–800)  
- Added `sat_total_avg_score` column  

## 🗄 SQL Schema
```sql
CREATE TABLE serhii_sotnichenko_sat_scores (
    dbn TEXT PRIMARY KEY,
    school_name TEXT,
    num_of_sat_test_takers INT,
    sat_critical_reading_avg_score FLOAT,
    sat_math_avg_score FLOAT,
    sat_writing_avg_score FLOAT,
    sat_total_avg_score FLOAT,
    pct_students_tested FLOAT,
    academic_tier_rating INT
);
