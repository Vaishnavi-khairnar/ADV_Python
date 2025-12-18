# 5️⃣ reduce() Function

## 2️⃣ Simple Definition
The reduce() function is a special tool that takes a list of items and combines them into a single result by applying a function repeatedly. Think of it like a calculator that keeps using the previous answer for the next calculation - it starts with the first two items, gets a result, then uses that result with the next item, and so on until only one value remains.

## 3️⃣ Why This Topic Exists
Python introduced the reduce() function to help developers combine all items in a list into a single value without writing complex loops with accumulator variables. Before reduce(), programmers had to create accumulator variables, loop through all items, and manually update the accumulator with each item. The reduce() function solves this by providing a clean, functional way to reduce collections to a single value.

## 4️⃣ Real-Life Analogy (MANDATORY)

### The Bakery Dough Mixer Analogy
Imagine you're working in a bakery and need to mix ingredients:

**Traditional Approach (Using Loops):**
- You take a big empty bowl (accumulator variable)
- You add flour and mix (first operation)
- You add sugar and mix again (second operation)
- You add eggs and mix again (third operation)
- You add milk and mix again (fourth operation)
- You have to remember the current mixture state after each addition
- It's easy to lose track or make mistakes

**reduce() Function Approach (Automated Mixer):**
- You put all ingredients in order (the list)
- You set the mixing function (how to combine ingredients)
- The mixer takes first two ingredients, combines them
- Takes that result + next ingredient, combines them
- Continues until only one final mixture remains
- The mixer handles all intermediate steps automatically

**The Benefits:**
- No manual tracking of intermediate states
- Consistent combining process every time
- Much cleaner and less error-prone
- Easy to change the combining method

In Python:
- The "ingredients" are your data items (numbers, strings, objects)
- The "mixing function" is your reduce function
- The "automated mixer" is the reduce() function
- The "final mixture" is the single reduced result

Just like the automated mixer combines all ingredients into one final mixture, reduce() combines all your data items into one final result!

## 5️⃣ Step-by-Step Explanation

### How reduce() Function Works Internally:

- **Accumulator Pattern**: reduce() maintains an accumulator that gets updated with each item
- **Sequential Processing**: Processes items one by one in order
- **Function Application**: Applies the function to accumulator and next item
- **Result Propagation**: Each result becomes the accumulator for the next iteration
- **Final Value**: Returns the final accumulator value after processing all items
- **Import Required**: reduce() is not built-in and must be imported from functools

### Internal Processing:
1. Python receives the reduce() function call with a function and an iterable
2. It takes the first two items and applies the function to get initial result
3. It takes that result and applies the function with the third item
4. This continues until all items are processed
5. The final result is returned

### Performance Benefits:
- More memory efficient than creating intermediate lists
- Cleaner than manual accumulator patterns
- Optimized for reduction operations
- Enables functional programming patterns

## 6️⃣ Basic Syntax Explanation

### reduce() Function Syntax:

```python
# Import required
from functools import reduce

# Basic syntax
reduce(function, iterable, initializer)
```

- `reduce` - Function imported from functools module
- `function` - The function that takes two arguments and returns one result
- `iterable` - The collection of items to reduce
- `initializer` - (Optional) Starting value for the accumulator

### Example 1: Basic reduce() for Summation
```python
from functools import reduce

def add(a, b):
    return a + b

numbers = [1, 2, 3, 4, 5]
result = reduce(add, numbers)

print(result)
```
**Output:**
```
15
```
- `from functools import reduce` - Imports the reduce function
- `def add(a, b):` - Defines a function that adds two numbers
- `reduce(add, numbers)` - Applies add function cumulatively: (((1+2)+3)+4)+5

### Example 2: reduce() with Lambda Function
```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]
result = reduce(lambda x, y: x + y, numbers)

print(result)
```
**Output:**
```
15
```
- `lambda x, y: x + y` - Anonymous function that adds two numbers
- `reduce(lambda x, y: x + y, numbers)` - Same as previous example but with lambda

### Example 3: reduce() with Initializer
```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]
result = reduce(lambda x, y: x + y, numbers, 10)

print(result)
```
**Output:**
```
25
```
- `10` - Initializer value (starting point)
- Process: 10+1=11, 11+2=13, 13+3=16, 16+4=20, 20+5=25

### Example 4: reduce() for Multiplication
```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]
result = reduce(lambda x, y: x * y, numbers)

print(result)
```
**Output:**
```
120
```
- `lambda x, y: x * y` - Multiplies two numbers
- Process: 1×2=2, 2×3=6, 6×4=24, 24×5=120

### Example 5: reduce() with Strings
```python
from functools import reduce

words = ["Hello", " ", "World", "!"]
result = reduce(lambda x, y: x + y, words)

print(result)
```
**Output:**
```
Hello World!
```
- `lambda x, y: x + y` - Concatenates two strings
- Process: "Hello"+" " = "Hello ", "Hello "+"World" = "Hello World", etc.

### Example 6: reduce() for Finding Maximum
```python
from functools import reduce

numbers = [15, 8, 23, 42, 16, 7]
result = reduce(lambda x, y: x if x > y else y, numbers)

print(result)
```
**Output:**
```
42
```
- `lambda x, y: x if x > y else y` - Returns the larger of two numbers
- Keeps the maximum value found so far

## 7️⃣ 10 PRACTICE PROGRAMS (WITH SOLUTION)

### Program 1: Sum of All Numbers
**Question:** Use reduce() to calculate the sum of all numbers in a list.

```python
from functools import reduce

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
total = reduce(lambda x, y: x + y, numbers)
print(total)
```
**Output:**
```
55
```
**Explanation:** The lambda adds numbers cumulatively: (((1+2)+3)+4)+...+10 = 55.

### Program 2: Product of All Numbers
**Question:** Calculate the product of all numbers in a list using reduce().

```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]
product = reduce(lambda x, y: x * y, numbers)
print(product)
```
**Output:**
```
120
```
**Explanation:** The lambda multiplies numbers cumulatively: 1×2×3×4×5 = 120.

### Program 3: Find Maximum Number
**Question:** Find the maximum number in a list using reduce().

```python
from functools import reduce

numbers = [15, 8, 23, 42, 16, 7, 35]
maximum = reduce(lambda x, y: x if x > y else y, numbers)
print(maximum)
```
**Output:**
```
42
```
**Explanation:** The lambda keeps the larger of two numbers at each step, resulting in the maximum.

### Program 4: Find Minimum Number
**Question:** Find the minimum number in a list using reduce().

```python
from functools import reduce

numbers = [15, 8, 23, 42, 16, 7, 35]
minimum = reduce(lambda x, y: x if x < y else y, numbers)
print(minimum)
```
**Output:**
```
7
```
**Explanation:** The lambda keeps the smaller of two numbers at each step, resulting in the minimum.

### Program 5: Concatenate All Strings
**Question:** Join all strings in a list into one string using reduce().

```python
from functools import reduce

words = ["Python", " ", "is", " ", "awesome", "!"]
sentence = reduce(lambda x, y: x + y, words)
print(sentence)
```
**Output:**
```
Python is awesome!
```
**Explanation:** The lambda concatenates strings cumulatively to form the final sentence.

### Program 6: Count Characters in All Strings
**Question:** Count total characters in all strings of a list using reduce().

```python
from functools import reduce

words = ["hello", "world", "python", "programming"]
total_chars = reduce(lambda x, y: x + len(y), words, 0)
print(total_chars)
```
**Output:**
```
28
```
**Explanation:** Starts with 0, adds length of each string: 0+5+5+6+11 = 27.

### Program 7: Check if All Numbers are Even
**Question:** Check if all numbers in a list are even using reduce().

```python
from functools import reduce

numbers = [2, 4, 6, 8, 10]
all_even = reduce(lambda x, y: x and y % 2 == 0, numbers, True)
print(all_even)
```
**Output:**
```
True
```
**Explanation:** Starts with True, ANDs with each number's evenness check.

### Program 8: Create Dictionary from List of Tuples
**Question:** Convert a list of key-value tuples into a dictionary using reduce().

```python
from functools import reduce

pairs = [('a', 1), ('b', 2), ('c', 3), ('d', 4)]
result_dict = reduce(lambda x, y: {**x, y[0]: y[1]}, pairs, {})
print(result_dict)
```
**Output:**
```
{'a': 1, 'b': 2, 'c': 3, 'd': 4}
```
**Explanation:** The lambda merges tuples into a dictionary by unpacking and adding key-value pairs.

### Program 9: Calculate Factorial
**Question:** Calculate factorial of a number using reduce().

```python
from functools import reduce

n = 5
factorial = reduce(lambda x, y: x * y, range(1, n + 1))
print(factorial)
```
**Output:**
```
120
```
**Explanation:** Multiplies all numbers from 1 to n: 1×2×3×4×5 = 120.

### Program 10: Flatten Nested Lists
**Question:** Flatten a list of lists into a single list using reduce().

```python
from functools import reduce

nested_lists = [[1, 2], [3, 4], [5, 6], [7, 8]]
flattened = reduce(lambda x, y: x + y, nested_lists)
print(flattened)
```
**Output:**
```
[1, 2, 3, 4, 5, 6, 7, 8]
```
**Explanation:** The lambda concatenates lists cumulatively to flatten the nested structure.

## 8️⃣ 5 REAL-WORLD PROGRAMS (WITH SOLUTION)

### Program 1: Student Grade Processing
**Problem Statement:** Calculate total scores, averages, and find highest/lowest performing students using reduce().

```python
from functools import reduce

# Student data
students = [
    {'name': 'Alice', 'math': 85, 'science': 92, 'english': 78},
    {'name': 'Bob', 'math': 72, 'science': 68, 'english': 81},
    {'name': 'Charlie', 'math': 91, 'science': 89, 'english': 85},
    {'name': 'Diana', 'math': 65, 'science': 71, 'english': 73},
    {'name': 'Eve', 'math': 88, 'science': 94, 'english': 90}
]

# Calculate total score for each student
def calculate_total(student):
    subjects = ['math', 'science', 'english']
    return reduce(lambda total, subject: total + student[subject], subjects, 0)

# Add total scores to student data
students_with_totals = list(map(lambda s: {**s, 'total': calculate_total(s)}, students))

print("Students with total scores:")
for student in students_with_totals:
    print(f"{student['name']}: Math={student['math']}, Science={student['science']}, "
          f"English={student['english']}, Total={student['total']}")

# Find class total and average
class_total = reduce(lambda total, student: total + student['total'], students_with_totals, 0)
class_average = class_total / len(students_with_totals)

print(f"\nClass total: {class_total}")
print(f"Class average: {class_average:.2f}")

# Find highest and lowest scoring students
highest_scorer = reduce(lambda best, student: 
                       student if student['total'] > best['total'] else best, 
                       students_with_totals)

lowest_scorer = reduce(lambda worst, student: 
                      student if student['total'] < worst['total'] else worst, 
                      students_with_totals)

print(f"\nHighest scorer: {highest_scorer['name']} with {highest_scorer['total']} points")
print(f"Lowest scorer: {lowest_scorer['name']} with {lowest_scorer['total']} points")

# Calculate subject averages
math_total = reduce(lambda total, student: total + student['math'], students, 0)
science_total = reduce(lambda total, student: total + student['science'], students, 0)
english_total = reduce(lambda total, student: total + student['english'], students, 0)

num_students = len(students)
print(f"\nSubject averages:")
print(f"Math: {math_total / num_students:.2f}")
print(f"Science: {science_total / num_students:.2f}")
print(f"English: {english_total / num_students:.2f}")
```
**Logic Explanation:**
- `calculate_total` uses reduce() to sum each student's subject scores
- Class totals calculated by reducing student totals
- Highest/lowest scorers found using reduce() with comparison logic
- Subject averages calculated by reducing subject scores across all students
- Demonstrates how reduce() can aggregate data in multiple ways

### Program 2: Shopping Bill Calculator
**Problem Statement:** Calculate total bills, apply discounts, and find most expensive items using reduce().

```python
from functools import reduce

# Shopping items
items = [
    {'name': 'Shirt', 'price': 30, 'category': 'clothing', 'quantity': 2},
    {'name': 'Jeans', 'price': 50, 'category': 'clothing', 'quantity': 1},
    {'name': 'Book', 'price': 15, 'category': 'education', 'quantity': 3},
    {'name': 'Laptop', 'price': 800, 'category': 'electronics', 'quantity': 1},
    {'name': 'Phone', 'price': 400, 'category': 'electronics', 'quantity': 1}
]

# Calculate total price for each item (price × quantity)
items_with_totals = list(map(lambda item: {**item, 'total_price': item['price'] * item['quantity']}, items))

print("Items with total prices:")
for item in items_with_totals:
    print(f"{item['name']}: ${item['price']} × {item['quantity']} = ${item['total_price']}")

# Calculate subtotal
subtotal = reduce(lambda total, item: total + item['total_price'], items_with_totals, 0)
print(f"\nSubtotal: ${subtotal:.2f}")

# Apply discount based on subtotal
def calculate_discount(subtotal):
    if subtotal > 1000:
        return subtotal * 0.15  # 15% discount
    elif subtotal > 500:
        return subtotal * 0.10  # 10% discount
    else:
        return subtotal * 0.05  # 5% discount

discount_amount = calculate_discount(subtotal)
final_total = subtotal - discount_amount

print(f"Discount: ${discount_amount:.2f}")
print(f"Final total: ${final_total:.2f}")

# Find most expensive item by total price
most_expensive = reduce(lambda expensive, item: 
                       item if item['total_price'] > expensive['total_price'] else expensive, 
                       items_with_totals)

print(f"\nMost expensive item: {most_expensive['name']} (${most_expensive['total_price']:.2f})")

# Calculate totals by category
def categorize_items(acc, item):
    category = item['category']
    if category not in acc:
        acc[category] = {'count': 0, 'total': 0}
    acc[category]['count'] += item['quantity']
    acc[category]['total'] += item['total_price']
    return acc

category_totals = reduce(categorize_items, items_with_totals, {})

print(f"\nCategory breakdown:")
for category, data in category_totals.items():
    print(f"{category}: {data['count']} items, ${data['total']:.2f}")

# Calculate average item price
total_items = reduce(lambda count, item: count + item['quantity'], items, 0)
average_price = subtotal / total_items
print(f"\nAverage price per item: ${average_price:.2f}")
```
**Logic Explanation:**
- Item totals calculated using map() and reduce() for price × quantity
- Subtotal calculated by reducing item totals
- Most expensive item found using reduce() with comparison
- Category breakdown created using reduce() to build a dictionary
- Demonstrates how reduce() can aggregate shopping data in multiple dimensions

### Program 3: Employee Salary Calculator
**Problem Statement:** Calculate payroll totals, bonuses, and department statistics using reduce().

```python
from functools import reduce

# Employee data
employees = [
    {'name': 'Alice', 'salary': 75000, 'department': 'engineering', 'performance': 9.2},
    {'name': 'Bob', 'salary': 45000, 'department': 'sales', 'performance': 8.5},
    {'name': 'Charlie', 'salary': 82000, 'department': 'engineering', 'performance': 7.8},
    {'name': 'Diana', 'salary': 55000, 'department': 'marketing', 'performance': 9.5},
    {'name': 'Eve', 'salary': 68000, 'department': 'sales', 'performance': 8.0},
    {'name': 'Frank', 'salary': 48000, 'department': 'marketing', 'performance': 7.2},
    {'name': 'Grace', 'salary': 92000, 'department': 'engineering', 'performance': 9.8}
]

# Calculate bonuses based on performance
def calculate_bonus(salary, performance):
    if performance >= 9.0:
        return salary * 0.20  # 20% bonus
    elif performance >= 8.0:
        return salary * 0.15  # 15% bonus
    elif performance >= 7.0:
        return salary * 0.10  # 10% bonus
    else:
        return salary * 0.05  # 5% bonus

# Add bonus and total compensation to employee data
employees_with_comp = list(map(lambda emp: {
    **emp, 
    'bonus': calculate_bonus(emp['salary'], emp['performance']),
    'total_comp': emp['salary'] + calculate_bonus(emp['salary'], emp['performance'])
}, employees))

print("Employee compensation:")
for emp in employees_with_comp:
    print(f"{emp['name']}: Salary=${emp['salary']:,}, Bonus=${emp['bonus']:,}, "
          f"Total=${emp['total_comp']:,}")

# Calculate total payroll
total_salaries = reduce(lambda total, emp: total + emp['salary'], employees_with_comp, 0)
total_bonuses = reduce(lambda total, emp: total + emp['bonus'], employees_with_comp, 0)
total_payroll = reduce(lambda total, emp: total + emp['total_comp'], employees_with_comp, 0)

print(f"\nPayroll Summary:")
print(f"Total salaries: ${total_salaries:,}")
print(f"Total bonuses: ${total_bonuses:,}")
print(f"Total payroll: ${total_payroll:,}")

# Find highest and lowest paid employees
highest_paid = reduce(lambda highest, emp: 
                    emp if emp['total_comp'] > highest['total_comp'] else highest, 
                    employees_with_comp)

lowest_paid = reduce(lambda lowest, emp: 
                    emp if emp['total_comp'] < lowest['total_comp'] else lowest, 
                    employees_with_comp)

print(f"\nHighest paid: {highest_paid['name']} (${highest_paid['total_comp']:,})")
print(f"Lowest paid: {lowest_paid['name']} (${lowest_paid['total_comp']:,})")

# Calculate department statistics
def aggregate_department(acc, emp):
    dept = emp['department']
    if dept not in acc:
        acc[dept] = {
            'count': 0, 
            'total_salary': 0, 
            'total_bonus': 0, 
            'avg_performance': 0, 
            'performance_sum': 0
        }
    
    acc[dept]['count'] += 1
    acc[dept]['total_salary'] += emp['salary']
    acc[dept]['total_bonus'] += emp['bonus']
    acc[dept]['performance_sum'] += emp['performance']
    acc[dept]['avg_performance'] = acc[dept]['performance_sum'] / acc[dept]['count']
    
    return acc

department_stats = reduce(aggregate_department, employees_with_comp, {})

print(f"\nDepartment Statistics:")
for dept, stats in department_stats.items():
    print(f"{dept}:")
    print(f"  Employees: {stats['count']}")
    print(f"  Total salary: ${stats['total_salary']:,}")
    print(f"  Total bonus: ${stats['total_bonus']:,}")
    print(f"  Average performance: {stats['avg_performance']:.2f}")

# Calculate average salary and bonus
avg_salary = total_salaries / len(employees_with_comp)
avg_bonus = total_bonuses / len(employees_with_comp)
print(f"\nCompany averages:")
print(f"Average salary: ${avg_salary:,.2f}")
print(f"Average bonus: ${avg_bonus:,.2f}")
```
**Logic Explanation:**
- Employee bonuses calculated based on performance scores
- Total payroll calculated by reducing salary, bonus, and total compensation
- Highest/lowest paid employees found using reduce() with comparison
- Department statistics aggregated using reduce() to build nested dictionary
- Demonstrates how reduce() can handle complex payroll calculations and aggregations

### Program 4: Bank Transaction Processor
**Problem Statement:** Process bank transactions to calculate balances, categorize expenses, and find spending patterns using reduce().

```python
from functools import reduce

# Bank transactions
transactions = [
    {'amount': 1500, 'type': 'deposit', 'description': 'Salary', 'category': 'income'},
    {'amount': 200, 'type': 'withdrawal', 'description': 'Shopping', 'category': 'personal'},
    {'amount': 600, 'type': 'withdrawal', 'description': 'Rent', 'category': 'housing'},
    {'amount': 300, 'type': 'transfer', 'description': 'To friend', 'category': 'personal'},
    {'amount': 50, 'type': 'withdrawal', 'description': 'Coffee', 'category': 'food'},
    {'amount': 1000, 'type': 'deposit', 'description': 'Freelance', 'category': 'income'},
    {'amount': 150, 'type': 'withdrawal', 'description': 'Groceries', 'category': 'food'},
    {'amount': 800, 'type': 'deposit', 'description': 'Investment', 'category': 'income'},
    {'amount': 120, 'type': 'withdrawal', 'description': 'Utilities', 'category': 'housing'},
    {'amount': 2000, 'type': 'deposit', 'description': 'Bonus', 'category': 'income'}
]

# Calculate running balance for each transaction
def calculate_running_balance(transactions):
    return reduce(lambda acc, trans: 
                  acc + [{**trans, 'balance': acc[-1]['balance'] + trans['amount'] if acc else trans['amount']}], 
                  transactions, [])

transactions_with_balance = calculate_running_balance(transactions)

print("Transactions with running balance:")
for trans in transactions_with_balance:
    trans_type = "Credit" if trans['amount'] > 0 else "Debit"
    print(f"{trans['description']}: ${abs(trans['amount']):.2f} {trans_type} -> Balance: ${trans['balance']:.2f}")

# Calculate total income and expenses
total_income = reduce(lambda total, trans: total + trans['amount'] if trans['type'] == 'deposit' else total, transactions, 0)
total_expenses = reduce(lambda total, trans: total + abs(trans['amount']) if trans['type'] != 'deposit' else total, transactions, 0)

print(f"\nTotal income: ${total_income:.2f}")
print(f"Total expenses: ${total_expenses:.2f}")
print(f"Net cash flow: ${total_income - total_expenses:.2f}")

# Find largest transaction
largest_transaction = reduce(lambda largest, trans: 
                            trans if abs(trans['amount']) > abs(largest['amount']) else largest, 
                            transactions)

print(f"\nLargest transaction: {largest_transaction['description']} (${abs(largest_transaction['amount']):.2f})")

# Categorize expenses by category
def categorize_expenses(acc, trans):
    category = trans['category']
    if category not in acc:
        acc[category] = {'count': 0, 'total': 0, 'transactions': []}
    
    acc[category]['count'] += 1
    acc[category]['total'] += abs(trans['amount'])
    acc[category]['transactions'].append(trans)
    return acc

category_breakdown = reduce(categorize_expenses, transactions, {})

print(f"\nExpense breakdown by category:")
for category, data in category_breakdown.items():
    print(f"{category}:")
    print(f"  Count: {data['count']} transactions")
    print(f"  Total: ${data['total']:.2f}")
    print(f"  Average: ${data['total'] / data['count']:.2f}")

# Find average transaction size
total_transactions = len(transactions)
avg_transaction_size = reduce(lambda total, trans: total + abs(trans['amount']), transactions, 0) / total_transactions
print(f"\nAverage transaction size: ${avg_transaction_size:.2f}")

# Calculate savings rate
savings_rate = ((total_income - total_expenses) / total_income) * 100 if total_income > 0 else 0
print(f"Savings rate: {savings_rate:.2f}%")

# Find most frequent transaction category
category_counts = reduce(lambda acc, trans: 
                        {**acc, trans['category']: acc.get(trans['category'], 0) + 1}, 
                        transactions, {})

most_frequent_category = reduce(lambda most, (cat, count): 
                                (cat, count) if count > most[1] else most, 
                                category_counts.items(), ('', 0))

print(f"Most frequent transaction category: {most_frequent_category[0]} ({most_frequent_category[1]} transactions)")
```
**Logic Explanation:**
- Running balance calculated using reduce() to accumulate transaction amounts
- Income and expenses calculated by reducing transactions with type filters
- Category breakdown created using reduce() to build nested dictionary
- Transaction statistics (average, frequency, largest) calculated using reduce()
- Demonstrates how reduce() can handle complex financial calculations and aggregations

### Program 5: Website User Data Processor
**Problem Statement:** Process website user data to calculate engagement metrics, user segments, and activity patterns using reduce().

```python
from functools import reduce

# Website user data
users = [
    {'name': 'Alice', 'last_login': 5, 'posts': 15, 'comments': 25, 'likes': 50, 'subscription': 'premium'},
    {'name': 'Bob', 'last_login': 45, 'posts': 3, 'comments': 8, 'likes': 12, 'subscription': 'basic'},
    {'name': 'Charlie', 'last_login': 15, 'posts': 8, 'comments': 12, 'likes': 30, 'subscription': 'premium'},
    {'name': 'Diana', 'last_login': 60, 'posts': 1, 'comments': 2, 'likes': 5, 'subscription': 'basic'},
    {'name': 'Eve', 'last_login': 3, 'posts': 20, 'comments': 30, 'likes': 80, 'subscription': 'premium'},
    {'name': 'Frank', 'last_login': 25, 'posts': 5, 'comments': 10, 'likes': 18, 'subscription': 'basic'},
    {'name': 'Grace', 'last_login': 8, 'posts': 12, 'comments': 18, 'likes': 45, 'subscription': 'premium'},
    {'name': 'Henry', 'last_login': 90, 'posts': 0, 'comments': 1, 'likes': 2, 'subscription': 'basic'}
]

# Calculate engagement score for each user
def calculate_engagement(user):
    return user['posts'] * 3 + user['comments'] * 2 + user['likes'] * 1

# Add engagement scores to user data
users_with_engagement = list(map(lambda user: {**user, 'engagement_score': calculate_engagement(user)}, users))

print("Users with engagement scores:")
for user in users_with_engagement:
    print(f"{user['name']}: Posts={user['posts']}, Comments={user['comments']}, "
          f"Likes={user['likes']}, Engagement={user['engagement_score']}")

# Calculate total engagement metrics
total_posts = reduce(lambda total, user: total + user['posts'], users_with_engagement, 0)
total_comments = reduce(lambda total, user: total + user['comments'], users_with_engagement, 0)
total_likes = reduce(lambda total, user: total + user['likes'], users_with_engagement, 0)
total_engagement = reduce(lambda total, user: total + user['engagement_score'], users_with_engagement, 0)

print(f"\nTotal platform activity:")
print(f"Posts: {total_posts}")
print(f"Comments: {total_comments}")
print(f"Likes: {total_likes}")
print(f"Total engagement: {total_engagement}")

# Find most engaged user
most_engaged = reduce(lambda most, user: 
                     user if user['engagement_score'] > most['engagement_score'] else most, 
                     users_with_engagement)

print(f"\nMost engaged user: {most_engaged['name']} (Engagement score: {most_engaged['engagement_score']})")

# Find most recently active user
most_recent = reduce(lambda recent, user: 
                    user if user['last_login'] < recent['last_login'] else recent, 
                    users_with_engagement)

print(f"Most recently active: {most_recent['name']} (Last login: {most_recent['last_login']} days ago)")

# Segment users by activity level
def segment_users(acc, user):
    score = user['engagement_score']
    if score > 100:
        segment = 'power'
    elif score > 50:
        segment = 'active'
    elif score > 20:
        segment = 'moderate'
    else:
        segment = 'low'
    
    if segment not in acc:
        acc[segment] = {'count': 0, 'users': []}
    
    acc[segment]['count'] += 1
    acc[segment]['users'].append(user['name'])
    return acc

user_segments = reduce(segment_users, users_with_engagement, {})

print(f"\nUser segments by engagement:")
for segment, data in user_segments.items():
    print(f"{segment.capitalize()} users: {data['count']} ({', '.join(data['users'])})")

# Calculate subscription statistics
def aggregate_subscription(acc, user):
    sub = user['subscription']
    if sub not in acc:
        acc[sub] = {
            'count': 0, 
            'total_engagement': 0, 
            'avg_engagement': 0,
            'total_posts': 0,
            'total_comments': 0,
            'total_likes': 0
        }
    
    acc[sub]['count'] += 1
    acc[sub]['total_engagement'] += user['engagement_score']
    acc[sub]['avg_engagement'] = acc[sub]['total_engagement'] / acc[sub]['count']
    acc[sub]['total_posts'] += user['posts']
    acc[sub]['total_comments'] += user['comments']
    acc[sub]['total_likes'] += user['likes']
    
    return acc

subscription_stats = reduce(aggregate_subscription, users_with_engagement, {})

print(f"\nSubscription statistics:")
for sub_type, stats in subscription_stats.items():
    print(f"{sub_type.capitalize()}:")
    print(f"  Users: {stats['count']}")
    print(f"  Average engagement: {stats['avg_engagement']:.2f}")
    print(f"  Total posts: {stats['total_posts']}")
    print(f"  Total comments: {stats['total_comments']}")
    print(f"  Total likes: {stats['total_likes']}")

# Calculate activity averages
num_users = len(users_with_engagement)
avg_posts = total_posts / num_users
avg_comments = total_comments / num_users
avg_likes = total_likes / num_users
avg_engagement = total_engagement / num_users

print(f"\nPlatform averages:")
print(f"Average posts per user: {avg_posts:.2f}")
print(f"Average comments per user: {avg_comments:.2f}")
print(f"Average likes per user: {avg_likes:.2f}")
print(f"Average engagement per user: {avg_engagement:.2f}")

# Find inactive users (last login > 30 days)
inactive_users = list(filter(lambda user: user['last_login'] > 30, users_with_engagement))
print(f"\nInactive users (last login > 30 days): {len(inactive_users)}")
for user in inactive_users:
    print(f"  {user['name']}: {user['last_login']} days ago")
```
**Logic Explanation:**
- User engagement scores calculated using weighted formula
- Total platform metrics calculated by reducing user activity data
- User segments created using reduce() to build nested dictionary
- Subscription statistics aggregated using reduce() for comprehensive analysis
- Demonstrates how reduce() can handle complex user analytics and segmentation

## 9️⃣ Common Mistakes

### Mistake 1: Forgetting to Import reduce()
**Beginner Mistake:** Trying to use reduce() without importing it from functools.

```python
# WRONG - reduce() not imported
numbers = [1, 2, 3, 4, 5]
result = reduce(lambda x, y: x + y, numbers)  # NameError: name 'reduce' is not defined

# RIGHT - Import reduce() from functools
from functools import reduce
numbers = [1, 2, 3, 4, 5]
result = reduce(lambda x, y: x + y, numbers)  # Works correctly
```

**How to Fix:** Always import reduce() from functools module before using it.

### Mistake 2: Using reduce() with Empty List Without Initializer
**Beginner Mistake:** Calling reduce() on an empty list without providing an initializer.

```python
# WRONG - Empty list without initializer
from functools import reduce
empty_list = []
result = reduce(lambda x, y: x + y, empty_list)  # TypeError: reduce() of empty sequence with no initial value

# RIGHT - Provide initializer for empty lists
from functools import reduce
empty_list = []
result = reduce(lambda x, y: x + y, empty_list, 0)  # Returns 0
```

**How to Fix:** Always provide an initializer when reduce() might receive an empty list.

### Mistake 3: Wrong Function Signature
**Beginner Mistake:** Using a function that doesn't take exactly two arguments.

```python
# WRONG - Function takes one argument
from functools import reduce
numbers = [1, 2, 3, 4, 5]
result = reduce(lambda x: x * 2, numbers)  # TypeError: <lambda>() takes 1 positional argument but 2 were given

# RIGHT - Function takes two arguments
from functools import reduce
numbers = [1, 2, 3, 4, 5]
result = reduce(lambda x, y: x + y, numbers)  # Works correctly
```

**How to Fix:** Ensure the function passed to reduce() takes exactly two arguments.

### Mistake 4: Using reduce() When sum() Would Work Better
**Beginner Mistake:** Using reduce() for simple summation when built-in functions exist.

```python
# WRONG - Using reduce() for simple sum
from functools import reduce
numbers = [1, 2, 3, 4, 5]
total = reduce(lambda x, y: x + y, numbers)  # Unnecessarily complex

# RIGHT - Use built-in sum() for simple cases
numbers = [1, 2, 3, 4, 5]
total = sum(numbers)  # Simpler and more readable
```

**How to Fix:** Use built-in functions like sum(), max(), min() for simple operations; use reduce() for complex custom logic.

### Mistake 5: Not Understanding the Accumulator Pattern
**Beginner Mistake:** Not understanding how the accumulator works in reduce().

```python
# WRONG - Trying to access all items at once
from functools import reduce
numbers = [1, 2, 3, 4, 5]
result = reduce(lambda acc, x: sum(acc) + x, numbers, [])  # Incorrect logic

# RIGHT - Understanding accumulator pattern
from functools import reduce
numbers = [1, 2, 3, 4, 5]
result = reduce(lambda acc, x: acc + x, numbers, 0)  # Correct: 0+1+2+3+4+5 = 15
```

**How to Fix:** Remember that reduce() processes items sequentially, updating the accumulator with each step.

## 🔟 Summary (Revision Notes)

- **reduce() Function** combines all items in an iterable into a single result
- **Import Required**: Must be imported from functools module
- **Syntax**: `reduce(function, iterable, initializer)`
- **Function Signature**: The function must take exactly two arguments (accumulator, current_item)
- **Accumulator Pattern**: Maintains a running result that gets updated with each item
- **Sequential Processing**: Processes items one by one in order
- **Initializer**: Optional starting value for the accumulator (required for empty lists)
- **Common Use Cases**: Summation, multiplication, finding min/max, building dictionaries, flattening lists
- **Performance**: More memory efficient than creating intermediate results
- **Alternatives**: Use built-in functions like sum(), max(), min() for simple cases
- **Best Practices**: Use for complex custom reduction operations; use built-ins for simple cases

---

✅ Topic 5 completed. Ready for Topic 6.