# Week 5 Lab: Advanced Python + NumPy

\---

## 1\. Overview

This lab was about writing **less code that runs faster**. I used three tools:

1. **List comprehensions** to build and filter lists in one line.
2. **`lambda` functions** to sort and compare records by a chosen field.
3. **NumPy** to do maths on whole columns at once (vectorization) and to filter data with **boolean masks**, with no `for` loops.

I used all of it on 60 days of real Kigali weather (September to October 2026).

This README replaces my screenshots. For every exercise it gives the task, my approach, the real output from my notebook, and what I learned.

\---

## 2\. How to run my notebook

1. Put `week5\_kigali\_weather.csv` in the same folder as `Week5\_YourName.ipynb`.
2. Open the notebook in Jupyter or Google Colab.
3. Run the cells **from top to bottom**, starting with the setup cell in Section 0.


> \*\*Lesson I learned the hard way:\*\* I got `NameError: name 'temps' is not defined` in Exercise 3.2. The cause was that the setup cell had not run, so Python had never created `temps`. A notebook only knows what has been run, in the order it was run. When something breaks, I restart the kernel and run everything top to bottom.


\---

## 3\. The dataset

|Column|Meaning|Type after loading|
|-|-|-|
|`day`|Day number (1 to 60)|not used|
|`date`|Calendar date|text array `dates`|
|`temp\_c`|Temperature in °C|float array `temps`|
|`rainfall\_mm`|Rainfall in millimetres|float array `rain`|
|`humidity\_pct`|Humidity in %|float array `hum`|



**Loading steps (Section 0):**

```python
with open("week5\_kigali\_weather.csv") as f:
    lines = f.readlines()\[1:]                         # skip the header row
rows  = \[ln.strip().split(",") for ln in lines]       # split each line into 5 pieces
temps = np.array(\[float(r\[2]) for r in rows])         # text -> float -> NumPy array
```

**Output:** `Days loaded: 60`


**What I learned:**

* My Week 3 skills (file reading, `.strip()`, `.split()`) and my Week 5 skills (comprehensions, `np.array`) work together.
* Everything in a CSV is **text**. I have to convert it with `float()` before doing maths, otherwise `"24.4" + "25.9"` just glues the text together.
* All four arrays have 60 items in the same order, so position `i` in every array is the **same day**. Later I use a mask from one array to pick data from another.


\---


## 4\. Part 1: 



1.1:
 
---

```python
temps\_f = \[t \* 9/5 + 32 for t in temps\_list]
```

**Output:** `\[75.92, 78.62, 83.48, 66.74000000000001, 78.8, 71.78]`


**What I learned:**


* This one line replaces the 4-line Week 3 loop (`new list`, `for`, `append`).
* `66.74000000000001` is not a bug. Computers store decimals in binary, so tiny rounding errors appear. I can use `round()` to tidy it.
* I named the list `temps\_list` so I would not overwrite the NumPy array `temps`. Reusing a variable name silently replaces the old value, which is a classic bug.


### 1.2:



```python
hot          = \[t for t in temps\_list if t >= 26]
cool\_rounded = \[round(t) for t in temps\_list if t < 24]
```

**Output:** `hot: \[28.6, 26.0]` and `cool\_rounded: \[19, 22]`


**What I learned:**


* Adding `if` at the end filters, and it does the same job as loop + `if` + `append` from Week 3.
* A comprehension can transform and filter at once. In (b) I filter with `t < 24` and round each value that passes.
* Comprehensions suit **simple** transforms. If the logic gets complicated, a normal loop is clearer.


1.3

---

```python
raw\_floats = \[float(x) for x in raw]
print(sum(raw\_floats) / len(raw\_floats))
```

**Output:** `\[24.4, 25.9, 28.6, 19.3]` and `Average: 24.55`


**What I learned:**

* This is exactly what happens when I read a CSV: values arrive as strings and must be converted before averaging.
* The average is just `sum / count`. This is the accumulator idea from Week 3 in two built-in functions.
* Half of data cleaning is fixing types.


\---

## 5\. Part 2: 

2.1: 

---

```python
ranked = sorted(results, key=lambda s: s\[1], reverse=True)
print(ranked\[:3])
```

**Output:** `Top 3: \[('Samuel', 92), ('Diane', 91), ('Aline', 85)]`


**What I learned:**


* `key=` tells `sorted()` **what to sort by**. Without it, Python would sort alphabetically by name.
* `reverse=True` puts the highest score first.
* `ranked\[:3]` is slicing from Week 1 (start included, end excluded).


2.2:

---

```python
wettest = max(rain\_log, key=lambda r: r\[1])
```

**Output:** `Wettest day: (14, 26.2)`


**What I learned:**


* `max()` with a `key` returns the **whole record** (day and rain), not just the biggest number.
* It does in one line what needed a loop with a "best so far" variable in Week 3.
* This same idea returns later as `df.apply(lambda ...)` in Pandas.


\---

## 6\. Part 3:

&#x20;3.1:

---

I doubled one million numbers two ways: a Python loop (comprehension) and NumPy (`arr \* 2`).


**My result:** NumPy was roughly  **times faster** on my machine.

**What I learned:**


* **Vectorization** means I describe *what* to compute (`arr \* 2`) and NumPy does the looping in fast compiled C.
* Speed depends on the machine, and the gap grows as the data grows. That matters for Big Data with millions of rows.
* A NumPy array holds **one data type** (all `float64`). That restriction is part of why it is fast.


3.2:

---

```python
print(f"Mean: {temps.mean():.2f} °C")
print(f"Max:  {temps.max():.1f} °C")
print(f"Min:  {temps.min():.1f} °C")
print(f"Std:  {temps.std():.2f} °C")
```

**Output:**

```
Mean: 24.00 °C      (matches the lab checkpoint)
Max:  28.6 °C
Min:  19.3 °C
Std:  2.61 °C
```


**What I learned:**


* Each method replaces a Week 3 accumulator loop.
* **Standard deviation** measures spread, meaning how far values typically sit from the mean. A std of 2.61 means a typical day is about 2.6 °C away from 24.00 °C.
* `:.2f` in an f-string formats a number to 2 decimal places.


3.3: 

---

```python
pos = np.argmax(temps)
print(f"Hottest day: {dates\[pos]} at {temps\[pos]} °C")
```

**Output:** `Hottest day: 2026-09-17 at 28.6 °C`


**What I learned:**


* `np.argmax` returns the **position** of the maximum, not the maximum itself.
* Because the arrays line up by position, the same `pos` finds the date in `dates` and the value in `temps`.


\---

7\. Part 4:

---

A **mask** is a True/False array, for example `temps >= 26`.

* `temps\[mask]` keeps only the `True` positions (**select**).
* `mask.sum()` counts the `True` values, because True = 1 and False = 0 (**count**).


4.1:

---

```python
hot\_mask = temps >= 26
hot\_mask.sum()                 # (a)
temps\[hot\_mask].mean()         # (b)
```

**Output:** (a) **18** hot days, (b) average **27.11 °C**


4.2:

---

```python
(rain > 0).sum()       # (a)
rain.sum()             # (b)
rain.max()             # (c)
```

**Output:** (a) **16** rainy days, (b) **331.2 mm** total, (c) heaviest day **26.2 mm** on 2026-09-07


4.3:

---

```python
temps\[rain > 0].mean()                  # (a) rainy days
temps\[rain == 0].mean()                 # (a) dry days
((temps >= 26) \& (rain > 0)).sum()      # (b) hot AND rainy
(hum >= 70).sum()                       # (c) humid days
```

**Output:**

|Question|Answer|
|-|-|
|(a) Average temperature on rainy days|**24.14 °C**|
|(a) Average temperature on dry days|**23.95 °C**|
|(b) Hot **and** rainy days|**5**|
|(c) Days with humidity of at least 70|**16**|




**What I learned in Part 4:**


* Masking is filtering without loops. Pandas filtering in Week 7 and SQL `WHERE` use the same idea.
* A mask built from one array (`rain > 0`) can select data from another (`temps\[...]`), because both are in the same day order.
* To combine conditions on arrays I must use **`\&`** (and) and **`|`** (or), not the words `and` / `or`. Each condition needs its own **parentheses**: `(temps >= 26) \& (rain > 0)`.
* Use `==` to compare and `=` to assign. `rain == 0` finds the dry days.
* **Insight:** rainy days (24.14 °C) and dry days (23.95 °C) have almost the same average temperature. Rain on a given day does not explain how hot it was.


\---

## 8\. Part 5:

5.1:

---

```python
anomaly = temps - temps.mean()      # every day minus the average, in one step
dates\[anomaly > 3]                  # (a) unusually hot days
(anomaly < -3).sum()                # (b) unusually cold days
```

**Output:**

* (a) Days more than 3 °C above the mean (9 days): `2026-09-07, 09-09, 09-11, 09-12, 09-14, 09-16, 09-17, 09-19, 09-22`
* (b) Days more than 3 °C below the mean: **8**


**What I learned:**


* An **anomaly** is how far a value is from normal. Positive means hotter than average, negative means cooler.
* `temps - temps.mean()` subtracts a single number from all 60 values at once. This is vectorized maths.
* A mask applied to `dates` returns the **dates** instead of the temperatures. A mask can select from any array of the same length.


5.2:

---

```python
temps\[:30].mean()      # first 30 days
temps\[30:].mean()      # last 30 days
```

**Output:** first 30 days **26.21 °C**, last 30 days **21.78 °C**


**Conclusion:** Kigali got **cooler**. The second half of the period was about **4.4 °C lower** than the first half.



**What I learned:**

* Slicing works the same as in lists: `\[:30]` is days 1 to 30 and `\[30:]` is days 31 to 60.
* Comparing two halves is a simple way to spot a trend. A single overall average (24.00) would have hidden the change.

Bonus:

---

```python
pairs = list(zip(dates, rain))
top5  = sorted(pairs, key=lambda p: p\[1], reverse=True)\[:5]
```

**Output:**

```
2026-09-07: 26.2 mm
2026-09-14: 25.1 mm
2026-09-21: 24.0 mm
2026-09-05: 22.9 mm
2026-09-28: 22.9 mm
```


**What I learned:**


* `zip(dates, rain)` pairs the two arrays into `(date, rainfall)` tuples, and then `sorted` and `lambda` from Part 2 rank them.
* This brings together comprehensions, `lambda`, and arrays in one task.
* The wettest days fall in September, which fits the cooling and humidity trend. The loop at the end is only used to **print**, which the lab allows.

\---

9\. Part 6: Reflection

---

**1. What did NumPy hide from me, and why learn the loop version first?**

`temps.mean()` hides a whole accumulator loop. It starts a total at zero, adds every value, counts the items, and divides. In Week 3 I wrote that loop by hand, so now I understand what `.mean()` really does. That matters because real data is messy (like the `"N/A"` scores in Week 3), and I can only debug or trust a shortcut if I know the process underneath it.


**2. One insight about Kigali's weather.**

Over these 60 days, Kigali cooled from about 26.2 °C in the first 30 days to 21.8 °C in the last 30. Rainy and dry days had almost the same average temperature (24.14 vs 23.95 °C). So the cooling comes from the **time of the season**, not from whether it rained on a particular day.

\---


## 10\. Summary of what I learned

|Skill|Big idea|Where I used it|
|-|-|-|
|List comprehension|Build or filter a list in one line|Ex 1.1 to 1.3, data loading|
|`lambda` + `key=`|Tell `sorted` / `max` what to compare by|Ex 2.1, 2.2, Bonus|
|NumPy arrays|One data type, fast maths, built-in statistics|Ex 3.2, 3.3|
|Vectorization|Do maths on a whole column at once|Ex 3.1, 5.1|
|Boolean masks|Filter and count without loops|Ex 4.1 to 4.3, 5.1|
|Slicing|Compare parts of an array|Ex 5.2|

## 

## 11\. Mistakes I made or watched out for

* Running a cell before the setup cell, which causes `NameError`.
* Overwriting `temps` (the array) with `temps` (the list). I fixed this by naming the list `temps\_list`.
* Using `and` / `or` instead of `\&` / `|` on arrays.
* Forgetting parentheses around each condition in a combined mask.
* Confusing `=` (assign) with `==` (compare).
* Forgetting that `argmax` gives a **position**, not a value.


12. How this connects to Big Data
---

* **Vectorization** is the same mindset as Pandas (Week 7) and PySpark (Week 12): describe what to compute and let the engine decide how.
* **Masks** are the same idea as SQL `WHERE` and Pandas filtering.
* **NumPy** is the engine underneath Pandas and Scikit-learn, so I will use it all semester.

