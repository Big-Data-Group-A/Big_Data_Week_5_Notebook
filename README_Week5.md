# Week 5 Lab: Python Lists, Sorting & NumPy (Kigali Weather)

**Course:** Introduction to Big Data Analytics, AUCA
**Student:** Ishimwe Muhire Johnson (20252SEN147)
**Notebook:** `week5_ISHIMWE_MUHIRE_JOHNSON_20252SEN147.ipynb`

This lab starts with plain Python (lists, sorting) and then moves to **NumPy**, which makes the same work shorter and much faster. In the second half, NumPy analyses 60 days of Kigali weather (September and October 2026).

---

## Files

| File | What it is |
|---|---|
| `week5_ISHIMWE_MUHIRE_JOHNSON_20252SEN147.ipynb` | The notebook with all code, answers and reflections |
| `week5_kigali_weather.xlsx` | Original weather data (Excel), needed to run the notebook |
| `week5_kigali_weather.csv` | Created automatically by the notebook from the Excel file |
| `README_Week5.md` | This file |

---

## The weather data

60 days of Kigali weather. After the first column, which holds an ID, the columns are:

| Column | Meaning |
|---|---|
| `date` | Day of the observation (`YYYY-MM-DD`) |
| temperature | Daily temperature in °C |
| rain | Rainfall in mm (0 means a dry day) |
| humidity | Humidity in % |

**Date gotcha:** Excel stores dates as numbers. The notebook converts them back into real dates (`unit="D", origin="1899-12-30"`) before saving the CSV.

---

## How to run

1. Put the notebook and `week5_kigali_weather.xlsx` in the same folder.
2. Install the libraries if needed:
   ```
   pip install numpy pandas openpyxl
   ```
3. Open the notebook in Jupyter and choose **Kernel → Restart & Run All**.

The cell that reads the Excel file must run before the cells that read the CSV, so run the notebook from top to bottom.

---

## What the notebook does

| Part | Topic | What you practise |
|---|---|---|
| 1 | List comprehensions | Convert °C to °F, filter hot and cool days, turn text into numbers and average them |
| 2 | Sorting with `lambda` | Top 3 students with `sorted(...)`, wettest day with `max(..., key=...)` |
| 3 | NumPy arrays | Speed test, mean/max/min/std, loading the CSV by hand, `argmax` for the hottest day |
| 4 | Boolean masks | Count hot days, rainy days, combine conditions with `&` |
| 5 | Anomalies and trends | Days far from the mean, first 30 days vs last 30 days |
| Bonus | Top 5 wettest days | `sorted` + `zip` |
| Reflections | Short written answers | What NumPy hides, and one insight about Kigali |

---

## Results

| Exercise | Result |
|---|---|
| 1.1 Temperatures in °F | 75.92, 78.62, 83.48, 66.74, 78.8, 71.78 |
| 1.2 Hot days (26 °C or more) | 28.6, 26.0 |
| 1.2 Cool days, rounded (below 24 °C) | 19, 22 |
| 1.3 Average of the raw text values | 24.55 |
| 2.1 Top 3 students | Samuel 92, Diane 91, Aline 85 |
| 2.2 Wettest day in the rain log | Day 14, 26.2 mm |
| 3.1 Speed test (1,000,000 numbers) | Python 0.089 s vs NumPy 0.020 s, about 4x faster |
| 3.3 Hottest day | 2026-09-17, 28.6 °C |
| 4.1 Hot days | 18 days, average 27.11 °C |
| 4.2 Rain | 16 rainy days, 331.20 mm total, heaviest day 26.2 mm |
| 4.3 Temperature on rainy vs dry days | 24.14 °C vs 23.95 °C |
| 4.3 Hot and rainy days | 5 |
| 4.3 Days with humidity 70 or more | 16 |
| 5.1 Anomalies | 9 days more than 3 °C above the mean, 8 days more than 3 °C below |
| 5.2 Trend | First 30 days 26.21 °C, last 30 days 21.78 °C, difference -4.43 °C |

**Bonus, top 5 wettest days:** 2026-09-07 (26.2 mm), 2026-09-14 (25.1), 2026-09-21 (24.0), 2026-09-05 (22.9), 2026-09-28 (22.9).

**Main finding:** Kigali got cooler, about 4.4 °C lower in the last 30 days than in the first 30.

---

## Key ideas, in plain words

| Idea | Meaning | Example from the notebook |
|---|---|---|
| **List comprehension** | A short way to build a new list from an old one | `[round(t*9/5+32, 2) for t in temps_c]` |
| **`lambda`** | A tiny one-line function, often used for sorting | `key=lambda s: s[1]` sorts by the second item |
| **NumPy array** | A fast list of numbers that supports maths on the whole list at once | `arr * 2` |
| **Boolean mask** | A True/False array used to pick values | `temps[temps >= 26]` |
| **`argmax`** | The position of the biggest value | `np.argmax(temps)` finds the hottest day |
| **Anomaly** | How far a value is from the average | `temps - temps.mean()` |

---

## Things to check before submitting

I read through the notebook and found a few points worth fixing.

1. **The average in Part 3 prints the wrong number.** The code `f"Average :{temps_c.mean():.0f}.00°C"` prints `24.00°C`, but the real mean of those six temperatures is **24.38**. The `.00` was typed by hand after rounding to a whole number. Use `{temps_c.mean():.2f}` instead and it will print `24.38°C`.
2. **The reflection mentions things the code never calculated.** It says temperature and humidity moved in opposite directions and that rain was always 15 to 26 mm. Neither was measured in the notebook. Either add a short check (for example `np.corrcoef(temps, hum)` and `rain[rain > 0].min()`) or reword those sentences so they only claim what you measured.
3. **Run Restart & Run All once more** before submitting, so every cell shows fresh outputs in order.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| `FileNotFoundError: week5_kigali_weather.xlsx` | Put the Excel file in the same folder as the notebook |
| `ImportError: openpyxl` | Run `pip install openpyxl` |
| `ValueError: could not convert string to float` | The CSV has a different column order; check the column positions in the cell that builds `rows` |
| Dates look like `46327` | Run the cell that converts Excel dates first |
| Speed test shows different times | Normal; timing changes with your computer, but NumPy should still be much faster |

---

