# 4️⃣ filter() Function

## 2️⃣ Simple Definition
The filter() function is a built-in Python tool that selects only the items from a list (or any iterable) that meet a specific condition. Think of it like a sieve - you pour in a mixture of items, and only the ones that fit through the holes (meet the condition) come out the other side.

## 3️⃣ Why This Topic Exists
Python introduced the filter() function to help developers easily extract items that meet certain criteria without writing complex loops with if statements. Before filter(), programmers had to create empty lists, loop through all items, check each item with an if statement, and manually append matching items to the new list. The filter() function solves this by providing a clean, efficient way to select items based on conditions.

## 4️⃣ Real-Life Analogy (MANDATORY)

### The Airport Security Check Analogy
Imagine you're going through airport security:

**Traditional Approach (Using Loops):**
- You stand in a long line with all passengers
- Security officer checks each passenger one by one
- If passenger has valid documents → let them through
- If passenger has invalid documents → send them to secondary check
- Officer has to manually remember who passed and who failed
- It's time-consuming and error-prone

**filter() Function Approach (Automated Security Gate):**
- All passengers walk through an automated security gate
- The gate automatically scans each passenger
- Only passengers with valid documents pass through
- Invalid documents are automatically rejected
- The gate handles all screening automatically

**The Benefits:**
- No manual checking for each passenger
- Consistent criteria applied to everyone
- Much faster and more efficient
- Easy to change the security criteria

In Python:
- The "passengers" are your data items (numbers, strings, objects)
- The "security criteria" is your condition function
- The "automated gate" is the filter() function
- The "passengers who pass" are the filtered results

Just like the security gate automatically filters passengers, filter() automatically filters your data based on your conditions!

## 5️⃣ Step-by-Step Explanation

### How filter() Function Works Internally:

- **Condition Testing**: filter() applies a function that returns True or False to each item
- **Iterator Creation**: It creates an iterator that yields only items that return True
- **Lazy Evaluation**: Results are generated only when needed, not all at once
- **Boolean Filtering**: Only items that evaluate to True are included in results
- **Order Preservation**: The result maintains the original order of matching items
- **Memory Efficiency**: Doesn't create the entire result list in memory at once

### Internal Processing:
1. Python receives the filter() function call with a condition function and an iterable
2. It creates an iterator object that will test each item
3. For each request, it applies the condition function to the next item
4. If the condition returns True, it yields the item; if False, it skips it
5. When converted to list, all matching items are collected at once

### Performance Benefits:
- Faster than manual loops for simple filtering
- More memory efficient for large datasets
- Cleaner, more readable code
- Optimized C implementation in Python

## 6️⃣ Basic Syntax Explanation

### filter() Function Syntax:

```python
# Basic syntax
filter(function, iterable)
```

- `filter` - Built-in function name
- `function` - The function that returns True or False for each item
- `iterable` - The collection of items to filter (list, tuple, etc.)

### Example 1: Basic filter() with Regular Function
```python
def is_even(x):
    return x % 2 == 0

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
result = filter(is_even, numbers)
result_list = list(result)

print(result_list)
```
**Output:**
```
[2, 4, 6, 8, 10]
```
- `def is_even(x):` - Defines a function that returns True if number is even
- `filter(is_even, numbers)` - Applies is_even function to each number
- `list(result)` - Converts the filter object to a list

### Example 2: filter() with Lambda Function
```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
result = list(filter(lambda x: x > 5, numbers))

print(result)
```
**Output:**
```
[6, 7, 8, 9, 10]
```
- `lambda x: x > 5` - Anonymous function that returns True if number is greater than 5
- `filter(lambda x: x > 5, numbers)` - Filters numbers greater than 5
- `list(...)` - Converts the filter object to a list immediately

### Example 3: filter() with Strings
```python
words = ["apple", "banana", "cherry", "date", "elderberry", "fig"]
result = list(filter(lambda word: len(word) > 5, words))

print(result)
```
**Output:**
```
['banana', 'cherry', 'elderberry']
```
- `lambda word: len(word) > 5` - Returns True if word length is greater than 5
- `filter(lambda word: len(word) > 5, words)` - Filters words longer than 5 characters
- Only words with more than 5 characters are included

### Example 4: filter() with None (Truthiness)
```python
mixed_list = [0, 1, "", "hello", [], [1, 2], {}, {"a": 1}, None, True, False]
result = list(filter(None, mixed_list))

print(result)
```
**Output:**
```
[1, 'hello', [1, 2], {'a': 1}, True]
```
- `filter(None, mixed_list)` - Uses None to filter out "falsy" values
- Truthy values (non-zero, non-empty, True) are kept
- Falsy values (0, empty string, empty list, None, False) are removed

### Example 5: filter() with Complex Objects
```python
people = [
    {'name': 'Alice', 'age': 25, 'city': 'New York'},
    {'name': 'Bob', 'age': 17, 'city': 'Chicago'},
    {'name': 'Charlie', 'age': 30, 'city': 'New York'},
    {'name': 'Diana', 'age': 16, 'city': 'Boston'}
]

# Filter adults (age >= 18)
adults = list(filter(lambda person: person['age'] >= 18, people))

# Filter people from New York
ny_residents = list(filter(lambda person: person['city'] == 'New York', people))

print("Adults:", adults)
print("New York residents:", ny_residents)
```
**Output:**
```
Adults: [{'name': 'Alice', 'age': 25, 'city': 'New York'}, {'name': 'Charlie', 'age': 30, 'city': 'New York'}]
New York residents: [{'name': 'Alice', 'age': 25, 'city': 'New York'}, {'name': 'Charlie', 'age': 30, 'city': 'New York'}]
```
- `lambda person: person['age'] >= 18` - Returns True if person is 18 or older
- `lambda person: person['city'] == 'New York'` - Returns True if person lives in New York
- filter() works with complex objects and dictionaries

## 7️⃣ 10 PRACTICE PROGRAMS (WITH SOLUTION)

### Program 1: Filter Even Numbers
**Question:** Use filter() to get only even numbers from a list.

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)
```
**Output:**
```
[2, 4, 6, 8, 10, 12, 14]
```
**Explanation:** The lambda function returns True for even numbers (divisible by 2), so filter() keeps only those.

### Program 2: Filter Positive Numbers
**Question:** Filter out negative numbers and zero, keeping only positive numbers.

```python
numbers = [-5, -3, -1, 0, 1, 3, 5, 7, 9]
positive_numbers = list(filter(lambda x: x > 0, numbers))
print(positive_numbers)
```
**Output:**
```
[1, 3, 5, 7, 9]
```
**Explanation:** The lambda returns True only for numbers greater than 0, filtering out negatives and zero.

### Program 3: Filter Long Words
**Question:** Get only words that have more than 4 characters.

```python
words = ["cat", "dog", "elephant", "fox", "giraffe", "hen", "iguana"]
long_words = list(filter(lambda word: len(word) > 4, words))
print(long_words)
```
**Output:**
```
['elephant', 'giraffe', 'iguana']
```
**Explanation:** The lambda checks word length and returns True only for words longer than 4 characters.

### Program 4: Filter Palindromes
**Question:** Filter to get only palindrome words (read the same forwards and backwards).

```python
words = ["level", "hello", "radar", "world", "madam", "python", "civic"]
palindromes = list(filter(lambda word: word == word[::-1], words))
print(palindromes)
```
**Output:**
```
['level', 'radar', 'madam', 'civic']
```
**Explanation:** The lambda compares each word with its reverse, returning True only for palindromes.

### Program 5: Filter Prime Numbers
**Question:** Filter to get only prime numbers from a list.

```python
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
prime_numbers = list(filter(is_prime, numbers))
print(prime_numbers)
```
**Output:**
```
[2, 3, 5, 7, 11, 13]
```
**Explanation:** The is_prime function checks if a number is prime, and filter() keeps only the prime numbers.

### Program 6: Filter Students by Grade
**Question:** Filter students who scored above 80.

```python
students = [
    {'name': 'Alice', 'score': 85},
    {'name': 'Bob', 'score': 72},
    {'name': 'Charlie', 'score': 91},
    {'name': 'Diana', 'score': 78},
    {'name': 'Eve', 'score': 88}
]

high_scorers = list(filter(lambda student: student['score'] > 80, students))
print(high_scorers)
```
**Output:**
```
[{'name': 'Alice', 'score': 85}, {'name': 'Charlie', 'score': 91}, {'name': 'Eve', 'score': 88}]
```
**Explanation:** The lambda checks the 'score' field and returns True only for scores above 80.

### Program 7: Filter Strings Starting with Vowel
**Question:** Get only words that start with a vowel.

```python
words = ["apple", "banana", "orange", "grape", "elephant", "kiwi", "umbrella"]
vowel_words = list(filter(lambda word: word[0].lower() in 'aeiou', words))
print(vowel_words)
```
**Output:**
```
['apple', 'orange', 'elephant', 'umbrella']
```
**Explanation:** The lambda checks if the first character (lowercased) is in the vowel string.

### Program 8: Filter Perfect Squares
**Question:** Filter to get only perfect square numbers.

```python
import math

def is_perfect_square(n):
    if n < 0:
        return False
    root = int(math.sqrt(n))
    return root * root == n

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 16, 20, 25, 30]
perfect_squares = list(filter(is_perfect_square, numbers))
print(perfect_squares)
```
**Output:**
```
[1, 4, 9, 16, 25]
```
**Explanation:** The function checks if the square root of the number is an integer, indicating a perfect square.

### Program 9: Filter Employees by Department
**Question:** Filter employees who work in the 'engineering' department.

```python
employees = [
    {'name': 'Alice', 'department': 'engineering'},
    {'name': 'Bob', 'department': 'sales'},
    {'name': 'Charlie', 'department': 'engineering'},
    {'name': 'Diana', 'department': 'marketing'},
    {'name': 'Eve', 'department': 'engineering'}
]

engineers = list(filter(lambda emp: emp['department'] == 'engineering', employees))
print(engineers)
```
**Output:**
```
[{'name': 'Alice', 'department': 'engineering'}, {'name': 'Charlie', 'department': 'engineering'}, {'name': 'Eve', 'department': 'engineering'}]
```
**Explanation:** The lambda checks the 'department' field and returns True only for 'engineering'.

### Program 10: Filter Numbers in Range
**Question:** Get only numbers between 20 and 50 (inclusive).

```python
numbers = [10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60]
in_range = list(filter(lambda x: 20 <= x <= 50, numbers))
print(in_range)
```
**Output:**
```
[20, 25, 30, 35, 40, 45, 50]
```
**Explanation:** The lambda uses compound condition to check if number is between 20 and 50 inclusive.

## 8️⃣ 5 REAL-WORLD PROGRAMS (WITH SOLUTION)

### Program 1: Student Grade Processing
**Problem Statement:** Filter students based on different performance criteria using filter() function.

```python
# Student data
students = [
    {'name': 'Alice', 'math': 85, 'science': 92, 'english': 78, 'attendance': 95},
    {'name': 'Bob', 'math': 72, 'science': 68, 'english': 81, 'attendance': 88},
    {'name': 'Charlie', 'math': 91, 'science': 89, 'english': 85, 'attendance': 92},
    {'name': 'Diana', 'math': 65, 'science': 71, 'english': 73, 'attendance': 85},
    {'name': 'Eve', 'math': 88, 'science': 94, 'english': 90, 'attendance': 98},
    {'name': 'Frank', 'math': 79, 'science': 82, 'english': 77, 'attendance': 75}
]

# Different filtering criteria
high_math_scorers = list(filter(lambda s: s['math'] >= 85, students))
high_science_scorers = list(filter(lambda s: s['science'] >= 90, students))
good_attendance = list(filter(lambda s: s['attendance'] >= 90, students))
overall_performers = list(filter(lambda s: s['math'] + s['science'] + s['english'] >= 250, students))

print("High math scorers (>=85):")
for student in high_math_scorers:
    print(f"  {student['name']}: {student['math']}")

print("\nHigh science scorers (>=90):")
for student in high_science_scorers:
    print(f"  {student['name']}: {student['science']}")

print("\nGood attendance (>=90%):")
for student in good_attendance:
    print(f"  {student['name']}: {student['attendance']}%")

print("\nOverall performers (total >=250):")
for student in overall_performers:
    total = student['math'] + student['science'] + student['english']
    print(f"  {student['name']}: {total}")

# Multiple criteria filtering
excellent_students = list(filter(
    lambda s: s['math'] >= 80 and s['science'] >= 80 and s['english'] >= 80 and s['attendance'] >= 90,
    students
))

print("\nExcellent students (all subjects >=80 AND attendance >=90%):")
for student in excellent_students:
    print(f"  {student['name']}: Math={student['math']}, Science={student['science']}, "
          f"English={student['english']}, Attendance={student['attendance']}%")
```
**Logic Explanation:**
- Multiple filter() operations apply different criteria to select students
- Lambda functions check individual subject scores and attendance
- Final filter() combines multiple conditions using logical operators
- Demonstrates how filter() can segment data based on various performance metrics

### Program 2: Shopping Bill Calculator
**Problem Statement:** Filter shopping items based on different criteria using filter() function.

```python
# Shopping items with categories and prices
items = [
    {'name': 'Shirt', 'price': 30, 'category': 'clothing', 'brand': 'Nike'},
    {'name': 'Jeans', 'price': 50, 'category': 'clothing', 'brand': 'Levi\'s'},
    {'name': 'Book', 'price': 15, 'category': 'education', 'brand': 'Penguin'},
    {'name': 'Laptop', 'price': 800, 'category': 'electronics', 'brand': 'Dell'},
    {'name': 'Phone', 'price': 400, 'category': 'electronics', 'brand': 'Apple'},
    {'name': 'Shoes', 'price': 80, 'category': 'clothing', 'brand': 'Adidas'},
    {'name': 'Pen', 'price': 2, 'category': 'education', 'brand': 'Bic'},
    {'name': 'Tablet', 'price': 300, 'category': 'electronics', 'brand': 'Samsung'}
]

# Filter by different criteria
expensive_items = list(filter(lambda item: item['price'] > 100, items))
clothing_items = list(filter(lambda item: item['category'] == 'clothing', items))
electronics_items = list(filter(lambda item: item['category'] == 'electronics', items))
affordable_items = list(filter(lambda item: item['price'] < 50, items))

print("Expensive items (> $100):")
for item in expensive_items:
    print(f"  {item['name']}: ${item['price']} ({item['category']})")

print("\nClothing items:")
for item in clothing_items:
    print(f"  {item['name']}: ${item['price']} ({item['brand']})")

print("\nElectronics items:")
for item in electronics_items:
    print(f"  {item['name']}: ${item['price']} ({item['brand']})")

print("\nAffordable items (< $50):")
for item in affordable_items:
    print(f"  {item['name']}: ${item['price']}")

# Complex filtering - affordable electronics
affordable_electronics = list(filter(
    lambda item: item['category'] == 'electronics' and item['price'] < 500,
    items
))

print("\nAffordable electronics (< $500):")
for item in affordable_electronics:
    print(f"  {item['name']}: ${item['price']} ({item['brand']})")

# Filter by brand
apple_products = list(filter(lambda item: item['brand'] == 'Apple', items))
print("\nApple products:")
for item in apple_products:
    print(f"  {item['name']}: ${item['price']}")
```
**Logic Explanation:**
- Multiple filter() operations segment items by price, category, and brand
- Lambda functions check individual properties of each item
- Complex filtering combines multiple conditions with logical operators
- Demonstrates how filter() can help customers find products based on specific criteria

### Program 3: Employee Salary Calculator
**Problem Statement:** Filter employees based on salary, department, and performance criteria.

```python
# Employee data
employees = [
    {'name': 'Alice', 'salary': 75000, 'department': 'engineering', 'performance': 9.2, 'years_experience': 5},
    {'name': 'Bob', 'salary': 45000, 'department': 'sales', 'performance': 8.5, 'years_experience': 3},
    {'name': 'Charlie', 'salary': 82000, 'department': 'engineering', 'performance': 7.8, 'years_experience': 8},
    {'name': 'Diana', 'salary': 55000, 'department': 'marketing', 'performance': 9.5, 'years_experience': 4},
    {'name': 'Eve', 'salary': 68000, 'department': 'sales', 'performance': 8.0, 'years_experience': 6},
    {'name': 'Frank', 'salary': 48000, 'department': 'marketing', 'performance': 7.2, 'years_experience': 2},
    {'name': 'Grace', 'salary': 92000, 'department': 'engineering', 'performance': 9.8, 'years_experience': 10},
    {'name': 'Henry', 'salary': 52000, 'department': 'sales', 'performance': 8.8, 'years_experience': 5}
]

# Filter by different criteria
high_earners = list(filter(lambda emp: emp['salary'] >= 70000, employees))
engineers = list(filter(lambda emp: emp['department'] == 'engineering', employees))
high_performers = list(filter(lambda emp: emp['performance'] >= 9.0, employees))
experienced_employees = list(filter(lambda emp: emp['years_experience'] >= 5, employees))

print("High earners (>= $70,000):")
for emp in high_earners:
    print(f"  {emp['name']}: ${emp['salary']:,}")

print("\nEngineers:")
for emp in engineers:
    print(f"  {emp['name']}: ${emp['salary']:,} (Performance: {emp['performance']})")

print("\nHigh performers (>= 9.0):")
for emp in high_performers:
    print(f"  {emp['name']}: {emp['performance']} ({emp['department']})")

print("\nExperienced employees (>= 5 years):")
for emp in experienced_employees:
    print(f"  {emp['name']}: {emp['years_experience']} years")

# Complex filtering - high-performing, experienced engineers
top_engineers = list(filter(
    lambda emp: emp['department'] == 'engineering' and emp['performance'] >= 8.0 and emp['years_experience'] >= 5,
    employees
))

print("\nTop engineers (engineering AND performance >= 8.0 AND experience >= 5 years):")
for emp in top_engineers:
    print(f"  {emp['name']}: ${emp['salary']:,}, Performance: {emp['performance']}, "
          f"Experience: {emp['years_experience']} years")

# Filter underpaid high performers
underpaid_high_performers = list(filter(
    lambda emp: emp['performance'] >= 9.0 and emp['salary'] < 60000,
    employees
))

print("\nUnderpaid high performers (performance >= 9.0 AND salary < $60,000):")
for emp in underpaid_high_performers:
    print(f"  {emp['name']}: ${emp['salary']:,}, Performance: {emp['performance']}")
```
**Logic Explanation:**
- Multiple filter() operations segment employees by salary, department, performance, and experience
- Lambda functions check individual and combined criteria
- Complex filtering identifies specific employee groups for targeted HR actions
- Demonstrates how filter() can support workforce analysis and decision-making

### Program 4: Bank Transaction Processor
**Problem Statement:** Filter bank transactions based on amount, type, and time criteria.

```python
# Bank transactions with dates
transactions = [
    {'amount': 1500, 'type': 'deposit', 'description': 'Salary', 'date': '2023-12-01', 'category': 'income'},
    {'amount': 200, 'type': 'withdrawal', 'description': 'Shopping', 'date': '2023-12-03', 'category': 'personal'},
    {'amount': 600, 'type': 'withdrawal', 'description': 'Rent', 'date': '2023-12-05', 'category': 'housing'},
    {'amount': 300, 'type': 'transfer', 'description': 'To friend', 'date': '2023-12-07', 'category': 'personal'},
    {'amount': 50, 'type': 'withdrawal', 'description': 'Coffee', 'date': '2023-12-08', 'category': 'personal'},
    {'amount': 1000, 'type': 'deposit', 'description': 'Freelance', 'date': '2023-12-10', 'category': 'income'},
    {'amount': 150, 'type': 'withdrawal', 'description': 'Groceries', 'date': '2023-12-12', 'category': 'food'},
    {'amount': 800, 'type': 'deposit', 'description': 'Investment return', 'date': '2023-12-15', 'category': 'investment'},
    {'amount': 120, 'type': 'withdrawal', 'description': 'Utilities', 'date': '2023-12-16', 'category': 'housing'},
    {'amount': 2000, 'type': 'deposit', 'description': 'Bonus', 'date': '2023-12-20', 'category': 'income'}
]

# Filter by different criteria
large_transactions = list(filter(lambda t: abs(t['amount']) > 500, transactions))
deposits = list(filter(lambda t: t['type'] == 'deposit', transactions))
withdrawals = list(filter(lambda t: t['type'] == 'withdrawal', transactions))
personal_expenses = list(filter(lambda t: t['category'] == 'personal', transactions))

print("Large transactions (> $500):")
for trans in large_transactions:
    print(f"  {trans['date']}: ${trans['amount']} {trans['type']} ({trans['description']})")

print("\nDeposits:")
for trans in deposits:
    print(f"  {trans['date']}: ${trans['amount']} ({trans['description']})")

print("\nWithdrawals:")
for trans in withdrawals:
    print(f"  {trans['date']}: ${trans['amount']} ({trans['description']})")

print("\nPersonal expenses:")
for trans in personal_expenses:
    print(f"  {trans['date']}: ${trans['amount']} ({trans['description']})")

# Complex filtering - large personal expenses
large_personal_expenses = list(filter(
    lambda t: t['category'] == 'personal' and t['type'] == 'withdrawal' and t['amount'] > 100,
    transactions
))

print("\nLarge personal expenses (> $100):")
for trans in large_personal_expenses:
    print(f"  {trans['date']}: ${trans['amount']} ({trans['description']})")

# Filter by date range (transactions in first half of December)
early_december = list(filter(
    lambda t: t['date'] >= '2023-12-01' and t['date'] <= '2023-12-15',
    transactions
))

print("\nEarly December transactions (Dec 1-15):")
for trans in early_december:
    print(f"  {trans['date']}: ${trans['amount']} {trans['type']} ({trans['description']})")

# Filter income sources
income_sources = list(filter(lambda t: t['category'] == 'income', transactions))
total_income = sum(t['amount'] for t in income_sources)
print(f"\nTotal income: ${total_income:,}")

# Filter housing expenses
housing_expenses = list(filter(lambda t: t['category'] == 'housing', transactions))
total_housing = sum(t['amount'] for t in housing_expenses)
print(f"Total housing expenses: ${total_housing:,}")
```
**Logic Explanation:**
- Multiple filter() operations segment transactions by amount, type, category, and date
- Lambda functions check individual and combined criteria
- Complex filtering identifies specific transaction patterns for financial analysis
- Demonstrates how filter() can support budget tracking and financial decision-making

### Program 5: Website User Data Processor
**Problem Statement:** Filter website users based on activity, engagement, and subscription criteria.

```python
# Website user data
users = [
    {'name': 'Alice', 'last_login': 5, 'posts': 15, 'comments': 25, 'likes': 50, 
     'subscription': 'premium', 'join_date': '2023-01-15', 'email_verified': True},
    {'name': 'Bob', 'last_login': 45, 'posts': 3, 'comments': 8, 'likes': 12, 
     'subscription': 'basic', 'join_date': '2023-03-20', 'email_verified': True},
    {'name': 'Charlie', 'last_login': 15, 'posts': 8, 'comments': 12, 'likes': 30, 
     'subscription': 'premium', 'join_date': '2023-02-10', 'email_verified': False},
    {'name': 'Diana', 'last_login': 60, 'posts': 1, 'comments': 2, 'likes': 5, 
     'subscription': 'basic', 'join_date': '2023-04-05', 'email_verified': True},
    {'name': 'Eve', 'last_login': 3, 'posts': 20, 'comments': 30, 'likes': 80, 
     'subscription': 'premium', 'join_date': '2023-01-01', 'email_verified': True},
    {'name': 'Frank', 'last_login': 25, 'posts': 5, 'comments': 10, 'likes': 18, 
     'subscription': 'basic', 'join_date': '2023-05-12', 'email_verified': False},
    {'name': 'Grace', 'last_login': 8, 'posts': 12, 'comments': 18, 'likes': 45, 
     'subscription': 'premium', 'join_date': '2023-02-28', 'email_verified': True},
    {'name': 'Henry', 'last_login': 90, 'posts': 0, 'comments': 1, 'likes': 2, 
     'subscription': 'basic', 'join_date': '2023-06-01', 'email_verified': False}
]

# Filter by different criteria
active_users = list(filter(lambda u: u['last_login'] < 30, users))
premium_users = list(filter(lambda u: u['subscription'] == 'premium', users))
verified_users = list(filter(lambda u: u['email_verified'], users))
posters = list(filter(lambda u: u['posts'] > 5, users))

print("Active users (last login < 30 days):")
for user in active_users:
    print(f"  {user['name']}: {user['last_login']} days ago")

print("\nPremium users:")
for user in premium_users:
    print(f"  {user['name']}: {user['subscription']}")

print("\nEmail verified users:")
for user in verified_users:
    print(f"  {user['name']}: {'Verified' if user['email_verified'] else 'Not verified'}")

print("\nActive posters (> 5 posts):")
for user in posters:
    print(f"  {user['name']}: {user['posts']} posts")

# Complex filtering - highly engaged premium users
highly_engaged_premium = list(filter(
    lambda u: u['subscription'] == 'premium' and 
              u['posts'] + u['comments'] + u['likes'] > 50 and
              u['last_login'] < 15,
    users
))

print("\nHighly engaged premium users (premium AND activity > 50 AND last login < 15 days):")
for user in highly_engaged_premium:
    activity = user['posts'] + user['comments'] + user['likes']
    print(f"  {user['name']}: Activity score {activity}, Last login {user['last_login']} days ago")

# Filter inactive unverified users (target for re-engagement)
inactive_unverified = list(filter(
    lambda u: u['last_login'] > 30 and not u['email_verified'],
    users
))

print("\nInactive unverified users (last login > 30 days AND email not verified):")
for user in inactive_unverified:
    print(f"  {user['name']}: {user['last_login']} days ago, Email: {'Verified' if user['email_verified'] else 'Not verified'}")

# Filter power users (high activity across all metrics)
power_users = list(filter(
    lambda u: u['posts'] > 10 and u['comments'] > 15 and u['likes'] > 25,
    users
))

print("\nPower users (posts > 10 AND comments > 15 AND likes > 25):")
for user in power_users:
    print(f"  {user['name']}: Posts: {user['posts']}, Comments: {user['comments']}, Likes: {user['likes']}")

# Filter long-term users (joined before March 2023)
long_term_users = list(filter(
    lambda u: u['join_date'] < '2023-03-01',
    users
))

print("\nLong-term users (joined before March 2023):")
for user in long_term_users:
    print(f"  {user['name']}: Joined {user['join_date']}")
```
**Logic Explanation:**
- Multiple filter() operations segment users by activity, subscription, verification, and engagement
- Lambda functions check individual and combined criteria
- Complex filtering identifies specific user groups for targeted marketing and engagement strategies
- Demonstrates how filter() can support user segmentation and behavioral analysis

## 9️⃣ Common Mistakes

### Mistake 1: Forgetting to Convert filter() to List
**Beginner Mistake:** Trying to print filter() object directly or use it like a list.

```python
# WRONG - Printing filter object directly
numbers = [1, 2, 3, 4, 5, 6]
result = filter(lambda x: x % 2 == 0, numbers)
print(result)  # Prints <filter object at 0x...>

# RIGHT - Convert to list or iterate
numbers = [1, 2, 3, 4, 5, 6]
result = list(filter(lambda x: x % 2 == 0, numbers))
print(result)  # Prints [2, 4, 6]
```

**How to Fix:** Always convert filter() to list using `list()` or iterate through it directly.

### Mistake 2: Using Function That Doesn't Return Boolean
**Beginner Mistake:** Using a function that doesn't return True or False in filter().

```python
# WRONG - Function doesn't return boolean
def double(x):
    return x * 2

numbers = [1, 2, 3, 4, 5]
result = list(filter(double, numbers))  # Unexpected behavior

# RIGHT - Function must return True or False
def is_even(x):
    return x % 2 == 0

numbers = [1, 2, 3, 4, 5]
result = list(filter(is_even, numbers))  # Works correctly
```

**How to Fix:** Ensure the function passed to filter() returns a boolean value (True or False).

### Mistake 3: Using Assignment in Lambda Function
**Beginner Mistake:** Trying to use assignment statements in lambda functions.

```python
# WRONG - Assignment not allowed in lambda
numbers = [1, 2, 3, 4, 5]
result = list(filter(lambda x: y = x * 2; y > 5, numbers))

# RIGHT - Use expression directly
numbers = [1, 2, 3, 4, 5]
result = list(filter(lambda x: x * 2 > 5, numbers))

# OR use regular function
def check_condition(x):
    y = x * 2
    return y > 5

result = list(filter(check_condition, numbers))
```

**How to Fix:** Lambda functions can only contain expressions, not statements. Use regular functions for complex logic.

### Mistake 4: Using filter() When List Comprehension is Better
**Beginner Mistake:** Using filter() for simple conditions where list comprehension is more readable.

```python
# WRONG - filter() for simple condition
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))

# RIGHT - List comprehension is more readable here
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = [x for x in numbers if x % 2 == 0]
```

**How to Fix:** Use list comprehensions for simple filtering; use filter() for existing functions or complex conditions.

### Mistake 5: Not Understanding Lazy Evaluation
**Beginner Mistake:** Assuming filter() processes all items immediately.

```python
# WRONG - Assuming immediate processing
def slow_check(x):
    print(f"Checking {x}")
    return x > 5

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
result = filter(slow_check, numbers)  # Nothing printed yet
print("Filter created")
print(list(result))  # Checking happens here

# RIGHT - Understanding lazy evaluation
def slow_check(x):
    print(f"Checking {x}")
    return x > 5

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
result = filter(slow_check, numbers)
# Only when we iterate or convert to list does the checking happen
```

**How to Fix:** Remember that filter() creates an iterator that processes items only when needed.

## 🔟 Summary (Revision Notes)

- **filter() Function** selects items from an iterable based on a condition function
- **Syntax**: `filter(function, iterable)`
- **Returns Iterator**: filter() returns a filter object (iterator), not a list
- **Boolean Function**: The function must return True or False for each item
- **Lazy Evaluation**: Processes items only when needed (memory efficient)
- **Order Preservation**: Maintains the original order of matching items
- **Conversion**: Use `list(filter(...))` to get a list of results
- **None as Function**: `filter(None, iterable)` removes falsy values
- **Performance**: Faster than manual loops for simple filtering
- **Common Use Cases**: Data selection, validation, removing unwanted items
- **Alternative**: List comprehensions can be more readable for simple conditions
- **Best Practices**: Use for existing functions, complex conditions, or when working with large datasets

---

✅ Topic 4 completed. Ready for Topic 5.