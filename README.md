# Student Attendance Analytics with Pandas

A pandas project that cleans, explores and analyses a class attendance sheet (CSE-A, Data Science & GenAI, 3rd year) to find students at risk of falling below the 75% attendance requirement.

## Files

| File | Description |
|------|-------------|
| `Project_Student_Attendance_Analytics_with_Pandas.ipynb` | Notebook with all 20 solved questions and their outputs |
| `attendance.xlsx` | Input data (65 students, 12 columns). Originally `csea_attendance.xlsx` |
| `critical_students.csv` | Output of Q20(a): all students with Status "Critical" |
| `summary_by_status.csv` | Output of Q20(b): summary statistics grouped by Status |
| `top10_risk_score.csv` | Output of Q20(c): top 10 students by Risk Score |

## Dataset

Columns: Roll No, Student Name, Subject, Total Classes, Present, Absent, Excused, Attendance %, Status, Classes Needed (75%), Last Present Date, Consecutive Absences.

Status breakdown: 19 Critical, 26 Warning, 20 Safe.

## What the notebook covers

1. **Data Inspection (Q1-Q4):** head, shape, dtypes, missing values, snake_case column names, converting `Attendance %` to float and `Last Present Date` to datetime ("Never" becomes NaT).
2. **Filtering & Selection (Q5-Q8):** Critical students, fully absent students, `.loc` / `.iloc`, long absence streaks.
3. **Grouping & Aggregation (Q9-Q12):** `groupby` and `.agg()` by Status, attendance categories, overall totals.
4. **Feature Engineering (Q13-Q16):** Risk Score, numeric Classes Needed, `apply()` with lambda, `pd.cut` bins.
5. **Advanced Analysis (Q17-Q20):** pivot table, duplicate base names, merge with a Student_Details table, CSV export.

## Setup and usage

```bash
pip install pandas numpy openpyxl jupyter
jupyter notebook Project_Student_Attendance_Analytics_with_Pandas.ipynb
```

Keep `attendance.xlsx` in the same folder as the notebook, then run all cells. The three CSV files are written to that folder.

## Notes and assumptions

- **Missing values:** there are no true nulls. "Never" appears as text in 3 rows of `Last Present Date`.
- **Attendance categories:** Q10 (Excellent / Good / Average / Poor) and Q16 (Critical / Warning / Good / Excellent via `pd.cut`) use different bands, as the questions specify.
- **Risk Score:** `Absent * 0.4 + Consecutive Absences * 0.6`.
- **Duplicate names (Q18):** the base name is the first word of the name with bracketed text removed, so "ANANYA B" and "ANANYA NAYAK (UMESH NAYAK)" both count as ANANYA.
- **Student_Details (Q19):** this table is hypothetical, built from the roll numbers (branch CSE, semester 5) plus two non-matching roll numbers to show the inner join dropping them.

## Tech

Python 3, pandas, NumPy, openpyxl, Jupyter.
