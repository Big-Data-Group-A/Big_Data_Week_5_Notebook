# Big Data Week 5 — Advanced Python + NumPy


This lab focused on analyzing 60 days of Kigali weather data using Python and NumPy. I worked with list comprehensions, lambda functions, NumPy arrays, boolean masking, and anomaly analysis.

The average temperature during the period was 24.00°C, with a maximum of 28.60°C and a minimum of 19.30°C. There were also 18 hot days with temperatures of at least 26°C.

One interesting finding was the difference between the first and second halves of the dataset. The first 30 days had an average temperature of 26.21°C, while the last 30 days averaged 21.78°C. This suggests that Kigali became noticeably cooler during the second half of the period.

The NumPy speed test also showed a significant performance difference. On my computer, the NumPy operation was about 48.7 times faster than the Python loop.

## Reflection

### 1. What did NumPy hide from you?

NumPy hides the loops and calculations behind simple operations such as `mean()`, `max()`, and `min()`. Learning the loop version first helped me understand what was happening step by step before using NumPy to make the calculations simpler and faster.

### 2. What was one insight from the weather analysis?

The main thing I noticed was that the weather became cooler in the second half of the period. The average temperature dropped from 26.21°C in the first 30 days to 21.78°C in the last 30 days.