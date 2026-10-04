# AUCA · Introduction to Big Data Analytics
## Week 5 Lab Report: Advanced Python + NumPy
**Student Name:** Kwizera Pacifique  
**Student ID:** 28064  
**Course:** Introduction to Big Data Analytics  
**Instructor:** Prince Ishimwe (Prince.ishimwe@auca.ac.rw)  
**Dataset:** `week5_kigali_weather.csv` / `.xlsx` (60 daily records, September–October 2026)

---

## 1. Executive Summary

This lab focuses on advancing beyond standard iterative Python loops by leveraging **list comprehensions**, **lambda expressions**, and **vectorized NumPy operations**. Using Kigali's 60-day weather record (September 1, 2026 – October 30, 2026), we analyzed temperature, precipitation, and humidity trends, identifying anomalies, weather correlations, and a significant seasonal cooling trend.

---

## 2. Methodology & Code Implementations

### Part 1 · List Comprehensions (6 marks)
- **Exercise 1.1 — Transform (Fahrenheit Conversion):**
  Converts each Celsius temperature using the formula $F = C \times \frac{9}{5} + 32$ in a single line:
  ```python
  fahrenheit = [t * 9/5 + 32 for t in temps_list]
  # Result: [75.92, 78.62, 83.48, 66.74, 78.8, 71.78]
  ```
- **Exercise 1.2 — Filter (Thresholds & Rounding):**
  Filters days $\ge 26^\circ\text{C}$ and temperatures $< 24^\circ\text{C}$ rounded:
  ```python
  hot = [t for t in temps_list if t >= 26]
  cool_rounded = [round(t) for t in temps_list if t < 24]
  # Hot: [28.6, 26.0] | Cool Rounded: [19, 22]
  ```
- **Exercise 1.3 — Type Conversion & Average:**
  Parses string records into floating-point numbers and calculates the mean:
  ```python
  raw_floats = [float(x) for x in raw]
  avg_temp = sum(raw_floats) / len(raw_floats)
  # Result: 24.55 °C
  ```

---

### Part 2 · Lambda Functions (4 marks)
- **Exercise 2.1 — Sorting with Custom Key:**
  Ranks student records descending by score:
  ```python
  results = [("Aline", 85), ("Eric", 78), ("Diane", 91), ("Samuel", 92), ("Grace", 76)]
  ranked = sorted(results, key=lambda r: r[1], reverse=True)
  # Top 3: [('Samuel', 92), ('Diane', 91), ('Aline', 85)]
  ```
- **Exercise 2.2 — Finding Maximum with Key:**
  Identifies the day with the highest recorded rainfall in a single statement:
  ```python
  rain_log = [(3, 0.0), (7, 12.5), (11, 3.2), (14, 26.2), (18, 8.9)]
  wettest_day = max(rain_log, key=lambda p: p[1])
  # Result: (14, 26.2) -> Day 14 with 26.2 mm
  ```

---

### Part 3 · NumPy Arrays & Vectorization (8 marks)
- **Exercise 3.1 — Performance Benchmark:**
  A performance test comparing a pure Python list comprehension against a NumPy array multiplication (`1,000,000` elements):
  - **Python List Loop:** `~0.0798s`
  - **NumPy Vectorized:** `~0.0024s`
  - **Speedup:** NumPy was **~33x faster** on the local execution machine.
- **Exercise 3.2 — Temperature Descriptive Statistics:**
  Computed via array methods:
  - **Mean:** `24.00 °C` (matches lab checkpoint)
  - **Max:** `28.6 °C`
  - **Min:** `19.3 °C`
  - **Standard Deviation:** `2.61 °C`
- **Exercise 3.3 — Peak Temperature Date:**
  ```python
  pos = np.argmax(temps)
  # Result: 2026-09-17 at 28.6 °C
  ```

---

### Part 4 · Boolean Masking (10 marks)
Vectorized conditional indexing was employed across the 60 days without using any procedural `for` loops:
- **Exercise 4.1 — Hot Days ($\ge 26^\circ\text{C}$):**
  - Count: **18 days**
  - Average Temperature: **27.11 °C**
- **Exercise 4.2 — Rain Report:**
  - Rainy Days (`rain > 0`): **16 days**
  - Total Rainfall: **331.20 mm**
  - Heaviest Rainfall: **26.2 mm**
- **Exercise 4.3 — Cross-Array Masking:**
  - Average Temperature on Rainy Days: **24.14 °C**
  - Average Temperature on Dry Days: **23.95 °C**
  - Hot AND Rainy Days: **5 days**
  - Days with Humidity $\ge 70\%$: **16 days**

---

### Part 5 · Anomalies, Trends & Bonus (10 marks)
- **Exercise 5.1 — Vectorized Anomaly Detection:**
  Anomaly is defined as deviation from mean: `anomaly = temps - temps.mean()`.
  - **Extreme Warm Days ($> +3^\circ\text{C}$ above mean):**
    `['2026-09-07', '2026-09-09', '2026-09-11', '2026-09-12', '2026-09-14', '2026-09-16', '2026-09-17', '2026-09-19', '2026-09-22']` (9 days)
  - **Extreme Cool Days ($< -3^\circ\text{C}$ below mean):**
    **8 days**
- **Exercise 5.2 — Seasonal Shift Comparison:**
  - First 30 Days Mean (September): **26.21 °C**
  - Last 30 Days Mean (October): **21.78 °C**
  - **Finding:** Kigali got substantially **cooler**, dropping by **~4.43 °C** between early September and late October.
- **Bonus (+3) — Top 5 Wettest Days:**
  ```python
  wettest = sorted(zip(dates, rain), key=lambda pair: pair[1], reverse=True)[:5]
  ```
  1. `2026-09-07`: **26.2 mm**
  2. `2026-09-14`: **25.1 mm**
  3. `2026-09-21`: **24.0 mm**
  4. `2026-09-05`: **22.9 mm**
  5. `2026-09-28`: **22.9 mm**

---

## 3. Reflection Responses (Part 6)

### Question 1: What did NumPy hide from you, and why was it still important to learn the loop version first?
> **Answer:**  
> NumPy abstracted away the procedural mechanics of iteration: initializing an accumulator, memory reallocation, index boundary management, step-by-step arithmetic addition, and dividing by count. Underneath, NumPy replaced Python's dynamic type checking and interpreted bytecode with precompiled, contiguous C-level SIMD operations.  
> Learning the manual loop first in Week 3 was essential because it builds algorithmic understanding of computational complexity and internal data flow. When datasets present missing values (`NaN`), nested record structures, or custom business logic that cannot be expressed purely through built-in primitives, having a solid grasp of explicit iteration enables developers to diagnose errors and reason through algorithmic trade-offs instead of treating libraries as opaque black boxes.

### Question 2: One insight about Kigali's weather that your analysis revealed.
> **Answer:**  
> The analysis revealed that Kigali experienced a pronounced seasonal temperature drop between September and October 2026, falling from **26.21 °C** down to **21.78 °C** (a drop of 4.43 °C). Furthermore, rain occurred throughout both halves (16 rainy days delivering 331.2 mm), and rainy days were virtually the same temperature as dry days (**24.14 °C** vs. **23.95 °C**). This proves that the autumn cooling trend in Kigali was driven by broader macro-climatic changes rather than localized cooling from rainfall events.

---

## 4. Final Submission Checklist

- [x] **All exercises implemented and tested without errors**
- [x] **No `for` loops used in Parts 3 through 5 (strictly vectorized NumPy operations and boolean masks)**
- [x] **Part 6 Reflection questions thoroughly answered**
- [x] **Bonus problem completed (+3 marks)**
- [x] **Notebook saved locally as `Week5_KwizeraPacifique.ipynb`**
- [x] **Colab Action:** Rename Colab notebook title from `Untitled4.ipynb` to `Week5_KwizeraPacifique` before submission.
