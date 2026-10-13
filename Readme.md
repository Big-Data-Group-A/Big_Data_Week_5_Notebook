# Week 5 Lab: Advanced Python + NumPy

**Student ID:** 28816 | **Program:** ISHIMWE Abdul Salam

---

## Overview

This lab explored **list comprehensions, lambda functions, and NumPy** to replace loops with vectorized operations, using 60 days of Kigali weather data (`week5_kigali_weather.csv`).

## Contents


`Week5_YourName.ipynb` 
 `week5_kigali_weather.csv` 
 `README.md` 

## What Was Done

- **Part 1:** Transformed, filtered, and converted temperatures using one-line comprehensions.
- **Part 2:** Used `sorted()` and `max()` with lambda keys to rank scores and find the wettest day.
- **Part 3:** Ran a loop-vs-NumPy speed test and used array methods (`mean`, `max`, `std`, `argmax`) to describe temperatures and find the hottest day.
- **Part 4:** Used boolean masks to count hot/rainy days, total rainfall, and cross-array comparisons.
- **Part 5:** Detected temperature anomalies and compared first 30 vs. last 30 days.
- **Bonus:** Ranked the 5 wettest days.
- **Part 6:** Reflection.

No `for` loops were used in Parts 3–5.

## Key Insight

Rainfall in Kigali was **highly concentrated** — a few heavy-rain days accounted for most of the total. These rainy days were also **cooler** than dry days, consistent with cloud cover and evaporative cooling.

## Reflection (NumPy vs. Python Lists)

In Week 3, averaging a column took ~15 lines of looping and converting. This week, `temps.mean()` did it instantly. NumPy hides the loop, type conversion, and memory management, pushing them into optimized C code. But learning loops first mattered — it taught me what averaging means, how to debug, and when vectorization is safe. Without that foundation, NumPy feels like magic; with it, NumPy feels like power.

