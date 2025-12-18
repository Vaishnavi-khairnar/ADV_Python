
# Advanced Python Programming

## Course Overview
This course is designed for students who already know Core Python basics.
It focuses on modern Python concepts used in data science, machine learning,
and web development with clear definitions, examples, and real-world use cases.

---

## MODULE 1 — Functional Programming in Python

### 1.1 What is Functional Programming?
Functional Programming is a programming paradigm where computation is done
using functions and immutable data.

Key Features:
- Functions as first-class objects
- Cleaner and shorter code
- Better readability

---

### 1.2 Lambda Functions
A lambda function is a small anonymous function written in a single line.

Syntax:
lambda arguments : expression

Example:
square = lambda x: x * x
print(square(5))

Use Cases:
- Sorting data
- Quick calculations
- Filtering collections

---

### 1.3 map() Function
The map() function applies a function to all items in an iterable.

Example:
numbers = [1, 2, 3, 4]
result = list(map(lambda x: x * 2, numbers))
print(result)

---

### 1.4 filter() Function
The filter() function selects elements based on a condition.

Example:
numbers = [10, 15, 20, 25]
result = list(filter(lambda x: x > 18, numbers))
print(result)

---

### 1.5 reduce() Function
The reduce() function reduces a list to a single value.

Example:
from functools import reduce
numbers = [1, 2, 3, 4]
result = reduce(lambda x, y: x + y, numbers)
print(result)

---

### 1.6 Iterators
Iterators allow traversal of elements one by one.

Example:
nums = iter([1, 2, 3])
print(next(nums))

---

### 1.7 Generators
Generators generate values using the yield keyword.

Example:
def count_up(n):
    for i in range(n):
        yield i

for num in count_up(5):
    print(num)

Advantages:
- Memory efficient
- Faster execution

---

## MODULE 2 — Python for Data Science & Machine Learning

### 2.1 Introduction to Data Science
Data Science involves collecting, cleaning, analyzing,
and visualizing data to extract insights.

---

### 2.2 NumPy
NumPy is used for numerical computing and array operations.

Example:
import numpy as np
arr = np.array([1, 2, 3, 4])
print(arr * 2)

---

### 2.3 Pandas
Pandas is used for data manipulation and analysis.

Example:
import pandas as pd
df = pd.DataFrame({"Name": ["Amit", "Neha"], "Marks": [85, 92]})
print(df)

---

### 2.4 Data Visualization
Data visualization helps understand patterns and trends.

Matplotlib:
Used for basic plotting.

Seaborn:
Used for advanced statistical visualization.

---

### 2.5 Machine Learning with Scikit-Learn
Scikit-Learn is used to build machine learning models.

Example:
from sklearn.linear_model import LinearRegression
model = LinearRegression()

---

## MODULE 3 — Python for Web Development

### 3.1 Introduction to Web Development
Python can be used to build backend systems, APIs, and full-stack applications.

---

### 3.2 Flask Framework
Flask is a lightweight web framework.

Example:
from flask import Flask
app = Flask(__name__)

@app.route("/")
def home():
    return "Hello World"

app.run()

---

### 3.3 Django Framework
Django is a full-featured web framework.

Features:
- Authentication
- Admin panel
- ORM
- Security

---

### 3.4 RESTful APIs
REST APIs allow communication using HTTP methods:
GET, POST, PUT, DELETE

---

### 3.5 Web Scraping
Web scraping extracts data from websites.

Libraries:
- requests
- BeautifulSoup

---

## Course Outcome
After completing this course, students will be able to:
- Write functional Python programs
- Perform data analysis and visualization
- Build machine learning models
- Develop web applications and APIs
