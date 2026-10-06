# Week 5 Lab (Lab 3) — Advanced Python + NumPy

**Course:** Introduction to Big Data Analytics, AUCA  
**Instructor:** Prince Ishimwe  
**Name:** MUCYO GAD  
**Student ID:** 28339  
**Program:** IT/Software  

## Overview

This lab practises list comprehensions, `lambda`, NumPy arrays, boolean masking and anomaly/trend analysis. The data is 60 days of Kigali weather (1 September – 30 October 2026) with temperature, rainfall and humidity.

## Files in this submission

| File | Description |
|---|---|
| `Week5_YourName.ipynb` | Completed notebook with all exercises run (Parts 1–5, Bonus, Part 6) |
| `week5_kigali_weather.csv` | Dataset: `day, date, temp_c, rainfall_mm, humidity_pct` |
| `Week5_YourName_Screenshots.pdf` | Screenshots of each exercise's code and output |
| `Week5_Report_YourName.docx` | Short report (one insight about Kigali's weather) |
| `README.md` | This file |

## How to run

1. Open `Week5_YourName.ipynb` in Google Colab (or Jupyter / VS Code).
2. Upload `week5_kigali_weather.csv` to the same place as the notebook. In Colab, run the upload cell and choose the file.
3. Run all cells from top to bottom (**Runtime → Run all**).

**Requirements:** Python 3, `numpy`, `pandas`.

## What each part covers

| Part | Topic | Marks |
|---|---|---|
| 1 | List comprehensions (transform, filter, convert types) | 6 |
| 2 | `lambda` with `sorted` and `max` | 4 |
| 3 | NumPy arrays (speed test, statistics, hottest day) | 8 |
| 4 | Boolean masking (hot days, rain report, cross-array analysis) | 10 |
| 5 | Anomalies and trends | 7 |
| Bonus | Top 5 wettest days with `zip` and `sorted` | +3 |
| 6 | Reflection (required) | — |

**Rule followed:** no `for` loops in Parts 3–5. The only loop is for printing the Bonus, as the lab allows.

## Key results

- Mean temperature: **24.00 °C** (min 19.3, max 28.6, std 2.61)
- Hottest day: **2026-09-17** at 28.6 °C
- Hot days (≥ 26 °C): **18**, average 27.11 °C
- Rainy days: **16**, total rainfall **331.2 mm**, heaviest day 26.2 mm
- Rainy vs dry day temperature: 24.14 °C vs 23.95 °C; hot and rainy days: 5
- Days with humidity ≥ 70: 16
- Days more than 3 °C above the mean: 9; more than 3 °C below: 8
- First 30 days average 26.21 °C, last 30 days 21.78 °C, so Kigali got about **4.4 °C cooler**

## Main insight

Kigali became cooler and more humid over the 60 days. All 18 hot days fell in the first half, while average humidity rose from about 58% to 66%. With only 60 days of data, a longer record would be needed to confirm a lasting trend.

## Notes

- The speed-test result in Exercise 3.1 depends on the machine, so it will differ between runs.
- Files uploaded to Colab are deleted when the session ends, so upload the CSV again each time.
