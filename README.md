# Week 5 Lab: Advanced Python and NumPy

**Student:** NZIZA Ben\
**Student ID:** 26142\
**Topic:** Introduction to Big Data Analytics\
**Project:** Week 5 -- Advanced Python and NumPy

## 1. Project Overview

This project practices using Python and NumPy to work with data. The lab
starts with normal Python lists and loops, then uses NumPy to perform
calculations on a larger dataset.

The weather dataset contains **60 days of Kigali weather information**,
including temperature, rainfall, and humidity. The notebook uses this
data to calculate statistics and look for patterns in the weather.

## 2. Files in This Project

Make sure these files are kept together in your project folder:

-   `Week5_26142_Nziza_Ben.ipynb` --- the Jupyter notebook
    containing the code, outputs, and reflection answers. Your
    downloaded notebook may have a slightly different filename.
-   `week5_kigali_weather.csv` --- the weather dataset used by the
    notebook.
-   `README.md` --- this file, which explains the project.

If your instructor also requires screenshots and a short report, include
those as separate files when submitting.

## 3. Tools and Libraries

-   **Python** --- used to write and run the code.
-   **NumPy** --- used to calculate statistics and filter weather data
    efficiently.
-   **Jupyter Notebook / Google Colab** --- used to run the notebook.
-   **CSV file** --- stores the weather observations in rows and
    columns.

## 4. What the Notebook Covers

The notebook contains exercises on:

1.  Converting temperatures from Celsius to Fahrenheit.
2.  Filtering temperature values and rounding selected values.
3.  Converting text values to numbers and calculating an average.
4.  Sorting records with a `lambda` function and finding the wettest
    record in a sample.
5.  Comparing the execution time of a Python list-based calculation and
    a NumPy calculation.
6.  Loading the Kigali weather CSV into NumPy arrays.
7.  Calculating the mean, maximum, minimum, and standard deviation of
    temperatures.
8.  Finding the hottest day.
9.  Counting hot days and calculating average temperature on those days.
10. Counting rainy days, calculating total rainfall, and finding the
    heaviest rainfall.
11. Comparing temperatures on rainy and dry days.
12. Identifying unusually hot and cool days.
13. Comparing average temperatures in the first 30 days and the last 30
    days.
14. Finding the five wettest days.
15. Answering reflection questions about NumPy and the weather data.

The main analysis uses NumPy arrays and vectorized operations instead of
writing explicit `for` loops for each calculation.

## 5. How to Run the Notebook

### Option A: Google Colab

1.  Open [Google Colab](https://colab.research.google.com/).
2.  Upload the completed `.ipynb` notebook.
3.  Upload `week5_kigali_weather.csv` to the Colab session, or place it
    in the same working location as the notebook.
4.  If the notebook reads the CSV using a relative filename, make sure
    the file is named exactly `week5_kigali_weather.csv`.
5.  Select **Runtime → Run all**.
6.  Check that each cell runs without errors and displays its expected
    output.

### Option B: Jupyter Notebook

1.  Install Python and Jupyter Notebook, if they are not already
    installed.
2.  Put the notebook and CSV file in the same folder.
3.  Open Jupyter Notebook and open the `.ipynb` file.
4.  Run the cells from top to bottom.

NumPy is required. If it is missing in your Python environment, install
it with:

``` bash
pip install numpy
```

## 6. Main Findings from the Weather Data

The notebook's analysis produced these results for the supplied 60-day
dataset:

-   **Average temperature:** 24.00°C
-   **Highest temperature:** 28.60°C, recorded on 17 September 2026
-   **Lowest temperature:** 19.30°C
-   **Hot days:** 18 days, using the notebook's threshold of 26°C or
    above
-   **Rainy days:** 16 days, using the notebook's rainfall condition
-   **Total rainfall:** 331.20 mm
-   **Heaviest daily rainfall:** 26.20 mm
-   **Average temperature in the first 30 days:** 26.21°C
-   **Average temperature in the last 30 days:** 21.78°C

### Weather insight

The average temperature was 26.21°C in the first half of the dataset and
21.78°C in the second half. This means that the second half of the
recorded period was cooler on average. This finding describes the
supplied 60-day dataset; it should not be treated as a conclusion about
Kigali's weather in general.

## 7. What I Learned

This lab helped me practise using Python lists, functions, lambda
expressions, and NumPy arrays. I learned that NumPy can perform
calculations on many values at once, which can make large numerical
calculations faster than handling each value individually in a Python
loop. I also learned how to use data filtering and summary statistics to
find patterns in a weather dataset.

## 8. Before Submitting

-   [ ] The notebook and CSV file are included.
-   [ ] The CSV filename matches the filename used in the code.
-   [ ] All notebook cells have been run from top to bottom.
-   [ ] There are no unexpected errors.
-   [ ] The reflection questions are answered.
-   [ ] Required screenshots and the short report are included, if
    requested by the instructor.
-   [ ] The README file is included.

------------------------------------------------------------------------

**Note:** The findings above come from the weather dataset used in this
lab. If the CSV data or notebook calculations change, run the notebook
again and update the results in this README.
