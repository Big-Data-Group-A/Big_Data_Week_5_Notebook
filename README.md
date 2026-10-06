# Week 5 Lab — Advanced Python + NumPy

**Course:** Introduction to Big Data Analytics  
**Institution:** AUCA (African University College of Kigali)  
**Instructor:** Prince Ishimwe  
**Student:** MANZI Fred — ID: 26634  
**Branch:** `week5_MANZI_Fred_26634`

---

## About This Notebook

This is my Week 5 lab submission. The topic is **Advanced Python + NumPy** — writing less code that runs faster.

The notebook covers:
- **Part 1** — List comprehensions (transform, filter, type conversion)
- **Part 2** — Lambda functions with `sorted` and `max`
- **Part 3** — NumPy arrays, speed test, temperature statistics
- **Part 4** — Boolean masking (hot days, rain report, cross-array analysis)
- **Part 5** — Anomaly detection and seasonal trend
- **Bonus** — Top 5 wettest days using `zip` + `sorted` + `lambda`
- **Part 6** — Reflection

---

## Dataset

`week5_kigali_weather.csv` — 60 days of Kigali weather data (September–October 2026)

| Column | Description |
|---|---|
| `day` | Day number (1–60) |
| `date` | Date (YYYY-MM-DD) |
| `temp_c` | Temperature in Celsius |
| `rainfall_mm` | Rainfall in millimeters |
| `humidity_pct` | Humidity percentage |

---

## Key Findings

- The **hottest day** was **2026-09-17** at **28.6°C**
- There were **20 hot days** (≥ 26°C), all in September
- Total rainfall over 60 days: **314.6 mm** across **20 rainy days**
- Kigali got **significantly cooler** in October — September averaged **26.21°C** vs October at **21.78°C** (a drop of ~4.4°C)
- The **5 wettest days** were all in September

---

## Files

| File | Description |
|---|---|
| `Week5_Fredm.ipynb` | Main lab notebook with all exercises |
| `week5_kigali_weather.csv` | Dataset used in the notebook |
| `README.md` | This file |
