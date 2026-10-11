# Week 5 — Advanced Python + NumPy Lab

**Student:** Irembere Olivier 28392

**Course:** Intro to Big Data Analytics

**Group:** A

**Lab:** Week 5 — Advanced Python + NumPy

**Notebook:** `week5_IREMBERE_OLIVIER.ipynb`

**Dataset:** `week5_kigali_weather.csv`

**Instructor:** Prince Ishimwe

---

## Overview

This lab focused on advanced Python programming and numerical data analysis using NumPy.

The dataset contains **60 daily weather records from Kigali, Rwanda**, covering September and October 2026.

The main topics covered were:

- List comprehensions
- Lambda functions
- Sorting and ranking
- NumPy arrays
- Vectorized operations
- Performance comparison between Python loops and NumPy
- Array statistics
- Boolean masking
- Cross-array analysis
- Anomaly detection
- Temperature trend analysis
- Data interpretation and reflection

The main objective was to perform data analysis using fewer lines of code while making calculations more efficient with NumPy.

---

## Part 1 — List Comprehensions

### Exercise 1.1 — Transform

A list comprehension was used to convert temperatures from Celsius to Fahrenheit.

The conversion formula was:

```python
F = (C * 9/5) + 32
```

The operation converted every temperature in the original list into Fahrenheit without using a traditional `for` loop block.

### Exercise 1.2 — Filter

List comprehensions were used to filter temperatures based on specific conditions.

- `hot` contains temperatures greater than or equal to 26 °C.
- `cool_rounded` contains temperatures below 24 °C, rounded to the nearest integer.

![Part 1.1 Screenshot](Screenshots/part1apng)

### Exercise 1.3 — Convert Types

The `raw` list contained numeric values stored as strings.

A list comprehension converted the strings into floating-point numbers, and the average was calculated from the resulting list.

```python
raw = ["24.4", "25.9", "28.6", "19.3"]
```
![Part 1.3Screenshot](screenshots/part1b.png)


## Part 2 — Lambda Functions

### Exercise 2.1 — Rank with `sorted()`

The student results were sorted from the highest score to the lowest using `sorted()` with a lambda function as the sorting key.

The top three students were then printed.

**Results:**

```text
Diane: 91
Samuel: 92
```

**Note:** The correct descending order begins with Samuel (92), followed by Diane (91), then Aline (85).

### Exercise 2.2 — Find the Wettest Day

The `max()` function was used with a lambda function to identify the day with the highest rainfall from `rain_log`.

Each record contains a day number and its rainfall in millimeters.

**Result:**

```text
Wettest day: Day 14
Rainfall: 26.2 mm
```

This exercise demonstrated how lambda functions can select records based on a particular value without writing a separate function.

---
![Part 2Screenshot](screenshots/part2.png)

## Part 3 — NumPy Arrays

### Exercise 3.1 — The Speed Test

A performance test compared a traditional Python loop with a NumPy operation using one million numbers.

The NumPy operation multiplied the entire array by two using vectorized computation.

![Part 3.1 Screenshot](screenshots/part3a.png)

The results demonstrated how NumPy can perform numerical operations efficiently without explicitly iterating through every element in Python.

### Exercise 3.2 — Describe the Temperatures

NumPy array methods were used to calculate descriptive statistics for the temperature dataset.

The following values were calculated:

- Mean temperature
- Maximum temperature
- Minimum temperature
- Standard deviation

### Exercise 3.3 — The Hottest Day

`np.argmax()` was used to identify the position of the highest temperature in the NumPy array.

That position was then used to retrieve the corresponding date and temperature.

![Part 3.2&3 Screenshot](screenshots/part3b.png)

This exercise demonstrated how the same array position can be used to associate a temperature with its corresponding date.

---

## Part 4 — Boolean Masking

### Exercise 4.1 — Hot Days

A Boolean mask was created to identify temperatures greater than or equal to 26 °C.

The mask was used to count hot days and calculate their average temperature.

![Part 4.1 Screenshot](screenshots/part4a.png)

### Exercise 4.2 — Rain Report

Boolean masking was used to identify rainy days, defined as days with rainfall greater than zero.

The analysis calculated:

- Number of rainy days
- Total rainfall across all 60 days
- Heaviest single-day rainfall

![Part 4.2 Screenshot](screenshots/part4b.png)

### Exercise 4.3 — Cross-Array Analysis

Masks created from the rainfall array were applied to the temperature array to compare temperatures on rainy and dry days.

The analysis also counted days that were both hot and rainy and days with humidity greater than or equal to 70%.

![Part 4.3 Screenshot](screenshots/part4c.png)

This exercise demonstrated how Boolean masks can connect information across multiple arrays when the arrays represent the same observations in the same order.

---

## Part 5 — Anomalies and Trends

### Exercise 5.1 — Anomaly Detection

Temperature anomalies were calculated by subtracting the mean temperature from every temperature value.

```python
anomaly = temps - temps.mean()
```

A positive anomaly indicates a temperature above the mean, while a negative anomaly indicates a temperature below the mean.

The analysis identified:

- Dates with temperatures more than 3 °C above the mean.
- The number of days with temperatures more than 3 °C below the mean.

![Part 5.1 Screenshot](screenshots/part5a.png)

### Exercise 5.2 — Is the Season Changing?

The first 30 days were compared with the last 30 days using NumPy array slicing.

```python
temps[:30]
temps[30:]
```

The average temperature for each period was calculated and compared to determine whether the second half of the dataset was warmer or cooler.

![Part 5.2 Screenshot](screenshots/part5b.png)

This comparison provides a simple way to investigate temperature changes over the observed period. It does not, by itself, establish a long-term seasonal or climate trend.

---

## Bonus — Top 5 Wettest Days (+3 Marks)

The `zip()` function was used to pair dates with rainfall values. The resulting records were sorted in descending order by rainfall using `sorted()` and a lambda function.

The five wettest days were then printed.

![Part bonus ](screenshots/part-bonus.png)
This exercise combined array data with Python's built-in sorting tools to rank weather events.

---

## Part 6 — Reflection

### 1. What Did NumPy Hide, and Why Learn Loops First?

NumPy hides much of the repetitive work required to process individual values in an array. Instead of writing a loop to calculate an average, for example, I can use `temps.mean()`. NumPy handles the calculation internally and also provides methods for other operations, such as finding the maximum, minimum, and standard deviation.

Learning loops first is still important because they help me understand how data is processed step by step. They also help me understand accumulators, conditions, and the logic behind calculations. With that foundation, I can better understand what NumPy is doing and when vectorized operations are more appropriate.

### 2. One Insight About Kigali's Weather

For example, I can compare the average temperature on rainy days with the average temperature on dry days to investigate whether the observed rainy days were generally cooler or warmer. I can also compare the first and last 30 days to see how the average temperature changed during the period.

## Conclusion

This lab provided practical experience with advanced Python features and NumPy-based data analysis.

The exercises demonstrated how list comprehensions simplify data transformations, lambda functions support sorting and ranking, and NumPy arrays enable efficient numerical calculations. Boolean masking made it possible to filter weather records and compare different conditions, while anomaly detection and time-period comparisons helped investigate patterns in Kigali's weather data.

Overall, the lab strengthened my understanding of vectorized computation and how Python can be used to analyze real-world datasets.

---

**Institution:** Adventist University of Central Africa (AUCA)  
**Course:** Introduction to Big Data Analytics  
**Lab:** Week 5 — Advanced Python + NumPy  
**Instructor:** Prince Ishimwe
