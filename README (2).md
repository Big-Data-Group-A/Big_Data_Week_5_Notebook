# Week 5 Lab — Advanced Python + NumPy

**Name:** Sultan Ray
**Student ID:** 28214
**Course:** Introduction to Big Data Analytics, AUCA
**Instructor:** Prince Ishimwe

## Overview
This is my Week 5 lab. I analysed 60 days of Kigali weather (September to October 2026) using list comprehensions, lambdas, NumPy arrays, and boolean masks.

## Files
- `Week5_Sultan_Ray_28214.ipynb`: the notebook with all exercises, comments, the Part 6 reflection, and the short report.
- `week5_kigali_weather.xlsx`: the dataset (60 daily records: day, date, temp_c, rainfall_mm, humidity_pct).

## How to run (Google Colab)
1. Open the notebook in Colab (File > Upload notebook).
2. Upload `week5_kigali_weather.xlsx` using the folder icon on the left.
3. Click Runtime > Run all.

## Notes
- My data file was Excel, and the dates were saved as numbers, so the loading cell converts them to real dates.
- No for loops are used in Parts 3 to 5. The only loop is for printing in the Bonus, which the lab allows.

## Key results
| Item | Result |
|---|---|
| Mean temperature | 24.00 °C |
| Hot days (>= 26 °C) | 18 (average 27.11 °C) |
| Rainy days / total rainfall | 16 days / 331.2 mm |
| Rainy vs dry avg temp | 24.14 °C vs 23.95 °C |
| First 30 vs last 30 days | 26.21 °C vs 21.78 °C (cooler) |
| Temperature-rain correlation | about 0.09 |

## Insight
I expected rain to make days cooler, but it didn't. The bigger change was the season: the last 30 days averaged about 4.4 °C cooler than the first 30. This is only 60 days, so it doesn't say much about Kigali's long-term climate.
