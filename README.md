# Week 5 Lab: Advanced Python + NumPy

**Student:** Hirwa Ngenzi Honore
**Student ID:** 29111
**Course:** Introduction to Big Data Analytics, AUCA
**Instructor:** Prince Ishimwe
**Lab:** Week 5, "Write Less, Compute Faster" (35 marks + 3 bonus)

## About this lab

This lab covers list comprehensions, `lambda`, NumPy arrays, boolean masking,
and simple anomaly and trend detection. The data is 60 days of Kigali weather
(1 September to 30 October 2026): temperature, rainfall and humidity.

Rule of the lab: no `for` loops in Parts 3 to 5 (only the Bonus printing).

## Repository contents

| File / folder | Description |
|---|---|
| `Lab_3.pdf` | Lab instructions (Week 5) |
| `Week5_HirwaNgenzi.ipynb` | Completed lab notebook |
| `week5_kigali_weather.xlsx` | Kigali weather dataset (60 rows, original Excel file) |
| `screenshots/` | Screenshots of the output of each part |
| `README.md` | This file |

> File names above should match what is actually in the repository. Edit this
> table if a name is different.

## Dataset

Columns: `day`, `date`, `temp_c`, `rainfall_mm`, `humidity_pct`.

Note: in the Excel file the dates are stored as numbers (for example `46282`).
The notebook converts them to real dates (`2026-09-17`) when loading:

```python
df["date"] = pd.to_datetime(df["date"], unit="D", origin="1899-12-30").dt.strftime("%Y-%m-%d")
```

## How to run

1. Install the libraries: `pip install numpy pandas openpyxl`
2. Put the dataset file in the same folder as the notebook.
3. Open `Week5_HirwaNgenzi.ipynb` and choose Restart and Run All.

Run the loading cell first. Part 1 uses a small list called `temps_list` so it
does not overwrite the `temps` array used in Parts 3 to 5.

## Key results

| Question | Result |
|---|---|
| Mean temperature (checkpoint) | 24.00 °C |
| Max / Min / Std | 28.6 °C / 19.3 °C / 2.61 °C |
| Hottest day | 2026-09-17 (28.6 °C) |
| Hot days (26 °C or more) | 18, average 27.11 °C |
| Rainy days / total rain / heaviest day | 16 / 331.2 mm / 26.2 mm |
| Average temperature, rainy vs dry days | 24.14 °C vs 23.95 °C |
| Hot and rainy days | 5 |
| Days with humidity 70% or more | 16 |
| Days more than 3 °C above / below the mean | 9 / 8 |
| First 30 days vs last 30 days | 26.21 °C vs 21.78 °C (cooler) |

**Insight:** Kigali cooled by about 4.4 °C from September to October, while
humidity rose. Rainy days were not noticeably cooler than dry days, so the
cooling follows the season rather than individual rain events.

## Screenshots

Screenshots of each part's output are in the `screenshots/` folder.

| Part | File |
|---|---|
| Part 1: List comprehensions | `screenshots/part1_comprehensions.png` |
| Part 2: lambda | `screenshots/part2_lambda.png` |
| Part 3: NumPy arrays | `screenshots/part3_numpy.png` |
| Part 4: Boolean masking | `screenshots/part4_masking.png` |
| Part 5: Anomalies and trends | `screenshots/part5_anomalies.png` |
| Bonus: Top 5 wettest days | `screenshots/bonus_wettest.png` |
