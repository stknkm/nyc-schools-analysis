# 📊 SAT Data Cleaning & Database Population

## 📌 Overview
This section describes the cleaning of SAT score data and loading into a PostgreSQL database.  

## Cleaning Logic
- Standardized column names (lowercase, underscores, removed special characters).
- Dropped unnecessary columns (`sat_critical_readng_avg_score`, `internal_school_id`, `contact_extension`).
- Converted numeric columns:
  - `num_of_sat_test_takers` → Int64
  - SAT score columns → Float
- Set invalid SAT scores (<200 or >800) to NaN.
- Converted `pct_students_tested` from strings with "%" to float, handling "N/A" as NaN.
- Converted `academic_tier_rating` to Int64.
- Added `sat_total_avg_score` as the sum of individual SAT score columns.

## Challenges
- Some columns contained non-numeric values like `"s"` or `"N/A"`.
- Handling duplicates and typos in column names.
- Ensuring correct data types for PostgreSQL integration.

## SQL Schema / Integration Notes
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
