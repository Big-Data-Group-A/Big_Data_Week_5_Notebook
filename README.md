
# Week 5 Lab — Advanced Python + NumPy
### Kigali Weather Analysis (60 days, Sept–Oct 2026)

**Student:** Maurice BYIRINGIRO
**Student ID:** 28216
**Course:** Introduction to Big Data
**Week:** 5
**Date:** October 2026

---

## 📌 Project Overview

This lab explores NumPy's vectorized computation by analyzing 60 days of Kigali
weather data (September–October 2026). The goal was to replace traditional Python
`for` loops with NumPy array operations and boolean masking — writing less code
that runs dramatically faster.

**Key columns in the dataset:**
| Column | Description |
|--------|-------------|
| `day` | Day number (1–60) |
| `date` | Calendar date (2026-09-01 → 2026-10-30) |
| `temp_c` | Daily temperature in °C |
| `rainfall_mm` | Daily rainfall in millimeters |
| `humidity_pct` | Relative humidity (%) |

---

## 🎯 Learning Objectives

- Use **list comprehensions** to transform, filter, and convert data
- Use **lambda functions** with `sorted()` and `max()` for custom ranking
- Apply **NumPy array methods** (`.mean()`, `.std()`, `.argmax()`) instead of loops
- Master **boolean masking** for conditional filtering across arrays
- Detect **anomalies** using vectorized arithmetic (`temps - temps.mean()`)
- Measure the **speed advantage** of vectorized vs. looped computation

---

## 📂 Repository Structure

.
├── Week5_BYIRINGIRO_Maurice_28216.ipynb # Main notebook
├── week5_kigali_weather.csv # Dataset
├── README.md # This file
└── screenshots/ # Output captures
text


---

## 🛠️ How to Run

**Prerequisites:** Python 3.9+, NumPy, pandas, Jupyter

```bash
# Clone
git clone https://github.com/<your-username>/week5-kigali-weather.git
cd week5-kigali-weather

# Install dependencies
pip install numpy pandas jupyter

# Launch
jupyter notebook Week5_BYIRINGIRO_Maurice_28216.ipynb

The CSV must sit next to the notebook — the loading cell reads it by filename.
📊 Key Results
Part 3 — Descriptive Statistics (NumPy)
Metric	Value
Mean temperature	24.00 °C
Max temperature	28.60 °C
Min temperature	19.30 °C
Std deviation	2.54 °C
Hottest day	2026-09-12
Part 4 — Boolean Masking
Question	Answer
Hot days (≥26 °C)	21 days
Rainy days (>0 mm)	14 days
Total rainfall	~285 mm
Heaviest day	26.2 mm
Hot and rainy days	5 days
Humid days (≥70 %)	22 days
Part 5 — Anomalies & Trends
Question	Answer
Days >3 °C above mean	9 days
Days >3 °C below mean	8 days
First 30 days avg	~25.80 °C
Last 30 days avg	~22.20 °C
Trend	Kigali cooled by ~3.6 °C across the 60-day window
Bonus — Top 5 Wettest Days

See screenshots/09_bonus_top5_wettest.png
⚡ The NumPy Speed Advantage

A side-by-side benchmark of doubling 1,000,000 numbers:
Method	Time	Relative
Python loop / list comprehension	~0.5 s	1×
NumPy vectorized arr * 2	~0.005 s	~100× faster

https://screenshots/04_part3_numpy_speed.png

Why? NumPy stores numbers in a contiguous memory block and runs compiled C
loops underneath. Python loops carry per-item overhead (type lookups, object
creation). For data of any real size, vectorization wins by orders of magnitude.
🔍 Insight — Kigali's Weather Over 60 Days

    Kigali cooled by roughly 3.6 °C across the 60-day window and rain was highly
    concentrated. The first 30 days averaged ~25.8 °C with several dry, hot spells;
    the last 30 averaged ~22.2 °C. Rainfall was "bursty" — most days were completely
    dry (only 14 of 60 days had any rain), but a handful of days carried 15–26 mm.
    This pattern is consistent with the onset of Kigali's long rainy season (Sept–Nov),
    which brings cooler air and concentrated downpours rather than evenly-spread rain.

This insight emerged directly from vectorized analysis: temps[:30].mean() vs
temps[30:].mean() and rain[rain > 0].mean() reveal the pattern in one line each.
🧠 Reflection

1. What NumPy hid from me — and why loops mattered first

NumPy hid the iteration machinery: the loop, the accumulator variable, the memory
management, the type handling. temps.mean() replaced ~15 lines of Week 3 code.
But learning the loop version first built the mental model — I now know what
mean() actually computes (sum ÷ count), which means I can debug it when the
number looks wrong, and I know loops are the right tool when a problem can't be
vectorized cleanly.

2. What the analysis revealed

See the Insight section above — Kigali shows a clear cooling trend with bursty
rainfall across this window, matching its seasonal pattern.
