# Week 5 Assignment – Advanced Python + NumPy

A Python notebook that uses advanced Python techniques and NumPy to analyze 60 days of Kigali weather data. Built as a Week 5 assignment for AUCA Introduction to Big Data Analytics coursework.

## What It Does

- **List comprehensions**: Converts temperatures, filters hot and cool temperatures, and converts string values into floats.
- **Lambda functions**: Ranks student results and identifies the wettest day from a rainfall log.
- **NumPy arrays**: Loads the Kigali weather dataset into NumPy arrays and performs numerical calculations efficiently.
- **Statistics**: Calculates the mean, maximum, minimum, and standard deviation of temperatures.
- **Boolean masking**: Identifies hot days, rainy days, high-humidity days, and days that are both hot and rainy.
- **Weather analysis**: Compares average temperatures between rainy and dry days.
- **Anomaly detection**: Identifies unusually hot and unusually cool days based on the average temperature.
- **Trend analysis**: Compares the first 30 days with the last 30 days to determine the temperature trend.
- **Bonus analysis**: Finds the top 5 wettest days in the dataset.
- **Reflection**: Summarizes what was learned about NumPy, Boolean masking, and weather trends.

## Files

- `Week5_NwoguJennifer.ipynb` — completed Jupyter Notebook containing all Week 5 exercises
- `week5_kigali_weather.csv` — input dataset containing 60 days of Kigali weather data
- `Week5_NwoguJennifer_Report.docx` — ½–1 page report summarizing the analysis and main weather insight
- `1-1.png` through `5-2.png` — screenshots of the Week 5 exercises
- `bonus.png` — screenshot of the Bonus exercise
- `README.md` — description of the Week 5 assignment and its contents

## How to Run

Open `Week5_NwoguJennifer.ipynb` using Jupyter Notebook or JupyterLab.

Make sure `week5_kigali_weather.csv` is in the same folder as the notebook before running the cells.

## Requirements

- Python 3.x
- Jupyter Notebook or JupyterLab
- NumPy
- `week5_kigali_weather.csv`

## Notes

- The weather dataset contains 60 days of Kigali weather observations.
- The analysis uses NumPy vectorized operations instead of `for` loops in Parts 3–5, as required by the assignment.
- Boolean masking is used to filter weather data based on conditions such as temperature, rainfall, and humidity.
- The first 30 days had an average temperature of **26.21°C**, while the last 30 days had an average of **21.78°C**.
- The overall analysis shows that **Kigali became cooler during the second half of the dataset**.

## Author

**Nwogu Jennifer**  
**AUCA**  
**Week 5 – Advanced Python + NumPy**
