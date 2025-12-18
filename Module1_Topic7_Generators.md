# 7️⃣ Generators

## 2️⃣ Simple Definition
Generators are special functions that produce a sequence of values over time instead of all at once. Think of them like a vending machine - you press the button and get one item, then press again for the next item, without the machine needing to stock all items at the beginning.

## 3️⃣ Why This Topic Exists
Python introduced generators to help developers work with large or infinite sequences without using too much memory. Before generators, programmers had to create entire lists in memory even when they only needed to process items one at a time. Generators solve this by producing values on-demand, making it possible to work with huge datasets or even infinite sequences efficiently.

## 4️⃣ Real-Life Analogy (MANDATORY)

### The Bakery Fresh Bread Production Analogy
Imagine you're running a bakery:

**Traditional Approach (Making All Bread at Once):**
- You bake all day's bread in the morning (500 loaves)
- You need huge ovens and storage space
- If you only sell 100 loaves, 400 go stale
- You waste ingredients and energy on unsold bread
- Your bakery can only handle limited daily production

**Generator Approach (Baking Fresh Bread on Demand):**
- You bake one loaf at a time as customers order
- You only need one small oven
- Every customer gets fresh bread
- No waste from unsold bread
- Your bakery can handle unlimited daily demand

**The Benefits:**
- No storage problems from overproduction
- Fresh product for every customer
- Efficient use of resources
- Can handle any amount of demand

In Python:
- The "bread orders" are your data requests
- The "fresh baking" is generator producing values
- The "one loaf at a time" is yield statement
- The "customer gets fresh bread" is on-demand value generation

Just like baking fresh bread on demand saves resources and provides fresh product, generators save memory and provide values as needed!

## 5️⃣ Step-by-Step Explanation

### How Generators Work Internally:

- **Function Suspension**: Generators can pause execution and resume later
- **Yield Statement**: `yield` returns a value and pauses the function
- **State Preservation**: Generator remembers its state between calls
- **Lazy Evaluation**: Values are produced only when requested
- **Memory Efficiency**: Only one value exists in memory at a time
- **Iterator Protocol**: Generators automatically implement iterator protocol

### Internal Processing:
1. Python calls the generator function to create a generator object
2. The generator function runs until it encounters `yield`
3. The yielded value is returned to the caller
4. Function state is saved (local variables, execution position)
5. When called again, function resumes from where it left off
6. This continues until function completes or raises StopIteration

### Performance Benefits:
- Constant memory usage regardless of sequence size
- Faster startup time (no need to process entire sequence)
- Can represent infinite sequences
- More efficient than building large lists

## 6️⃣ Basic Syntax Explanation

### Generator Function Syntax:

```python
def generator_function():
    yield value1
    yield value2
    # ... more yields
```

### Example 1: Basic Generator Function
```python
def simple_generator():
    yield 1
    yield 2
    yield 3

# Create generator object
gen = simple_generator()

# Get values one by one
print(next(gen))  # 1
print(next(gen))  # 2
print(next(gen))  # 3
# print(next(gen))  # Would raise StopIteration
```
- `def simple_generator():` - Defines a generator function
- `yield 1` - Returns 1 and pauses execution
- `gen = simple_generator()` - Creates generator object (doesn't run function yet)
- `next(gen)` - Resumes function until next yield

### Example 2: Generator with Loop
```python
def count_up_to(n):
    for i in range(1, n + 1):
        yield i

# Use generator
counter = count_up_to(5)
for num in counter:
    print(num)
```
**Output:**
```
1
2
3
4
5
```
- `for i in range(1, n + 1):` - Loop that generates numbers
- `yield i` - Returns each number and pauses
- `for num in counter:` - Automatically handles generator protocol

### Example 3: Generator Expression
```python
# Generator expression (like list comprehension but with parentheses)
squares = (x * x for x in range(1, 6))

# Use generator expression
for square in squares:
    print(square)
```
**Output:**
```
1
4
9
16
25
```
- `(x * x for x in range(1, 6))` - Generator expression syntax
- Similar to list comprehension but uses parentheses
- Produces squares one by one, not all at once

### Example 4: Generator with State
```python
def fibonacci():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

# Get first 10 Fibonacci numbers
fib_gen = fibonacci()
for _ in range(10):
    print(next(fib_gen))
```
**Output:**
```
0
1
1
2
3
5
8
13
21
34
```
- `a, b = 0, 1` - Initialize Fibonacci sequence
- `yield a` - Returns current number and pauses
- `a, b = b, a + b` - Update sequence for next iteration
- Generator can produce infinite sequence

### Example 5: Generator from Large Dataset
```python
def process_large_file(filename):
    with open(filename, 'r') as file:
        for line in file:
            # Process line and yield result
            processed_line = line.strip().upper()
            yield processed_line

# Use generator for memory-efficient file processing
file_processor = process_large_file('large_file.txt')
for line in file_processor:
    print(line)
    # Only one line in memory at a time
```
- `with open(filename, 'r') as file:` - Opens file safely
- `for line in file:` - Reads file line by line (memory efficient)
- `yield processed_line` - Returns processed line without storing all lines
- Generator processes huge files without loading everything into memory

## 7️⃣ 10 PRACTICE PROGRAMS (WITH SOLUTION)

### Program 1: Simple Number Generator
**Question:** Create a generator that yields numbers from 1 to 5.

```python
def numbers_generator():
    for num in range(1, 6):
        yield num

# Use the generator
for number in numbers_generator():
    print(number)
```
**Output:**
```
1
2
3
4
5
```
**Explanation:** The generator yields numbers 1 through 5 one at a time.

### Program 2: Even Numbers Generator
**Question:** Create a generator that yields only even numbers up to 10.

```python
def even_numbers():
    for num in range(2, 11, 2):
        yield num

# Use the generator
for even in even_numbers():
    print(even)
```
**Output:**
```
2
4
6
8
10
```
**Explanation:** The generator uses range with step 2 to yield even numbers.

### Program 3: Squares Generator
**Question:** Create a generator that yields squares of numbers from 1 to 5.

```python
def squares_generator():
    for num in range(1, 6):
        yield num * num

# Use the generator
for square in squares_generator():
    print(square)
```
**Output:**
```
1
4
9
16
25
```
**Explanation:** The generator calculates and yields square of each number.

### Program 4: String Character Generator
**Question:** Create a generator that yields characters of a string one by one.

```python
def string_generator(text):
    for char in text:
        yield char

# Use the generator
word = "Hello"
for character in string_generator(word):
    print(character)
```
**Output:**
```
H
e
l
l
o
```
**Explanation:** The generator iterates through string and yields each character.

### Program 5: Generator Expression for Squares
**Question:** Use generator expression to create squares of numbers 1-5.

```python
squares = (x * x for x in range(1, 6))

# Use the generator expression
for square in squares:
    print(square)
```
**Output:**
```
1
4
9
16
25
```
**Explanation:** Generator expression creates squares without storing all in memory.

### Program 6: Fibonacci Generator
**Question:** Create a generator that yields first 10 Fibonacci numbers.

```python
def fibonacci_generator(count):
    a, b = 0, 1
    for _ in range(count):
        yield a
        a, b = b, a + b

# Use the generator
for fib in fibonacci_generator(10):
    print(fib)
```
**Output:**
```
0
1
1
2
3
5
8
13
21
34
55
```
**Explanation:** The generator yields Fibonacci sequence using the classic algorithm.

### Program 7: Prime Numbers Generator
**Question:** Create a generator that yields prime numbers up to 20.

```python
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True

def primes_generator(limit):
    for num in range(2, limit + 1):
        if is_prime(num):
            yield num

# Use the generator
for prime in primes_generator(20):
    print(prime)
```
**Output:**
```
2
3
5
7
11
13
17
19
```
**Explanation:** The generator checks each number for primality and yields only primes.

### Program 8: Generator with Condition
**Question:** Create a generator that yields numbers from 1-10 that are divisible by 3.

```python
def divisible_by_three():
    for num in range(1, 11):
        if num % 3 == 0:
            yield num

# Use the generator
for num in divisible_by_three():
    print(num)
```
**Output:**
```
3
6
9
```
**Explanation:** The generator yields only numbers that satisfy the divisibility condition.

### Program 9: Generator for Powers of 2
**Question:** Create a generator that yields powers of 2 up to 2^8.

```python
def powers_of_two():
    power = 1
    for _ in range(9):  # 2^0 to 2^8
        yield power
        power *= 2

# Use the generator
for power in powers_of_two():
    print(power)
```
**Output:**
```
1
2
4
8
16
32
64
128
256
```
**Explanation:** The generator doubles the value each time to create powers of 2.

### Program 10: Generator with Multiple Yields
**Question:** Create a generator that yields multiple values per iteration.

```python
def multi_yield_generator():
    for i in range(3):
        yield i
        yield i * 10
        yield i * 100

# Use the generator
for value in multi_yield_generator():
    print(value)
```
**Output:**
```
0
0
0
1
10
100
2
20
200
```
**Explanation:** Each loop iteration yields three different values based on the same number.

## 8️⃣ 5 REAL-WORLD PROGRAMS (WITH SOLUTION)

### Program 1: Student Grade Processing
**Problem Statement:** Process student grades using generators to calculate statistics without loading all data at once.

```python
# Student grades generator
def student_grades_generator():
    students = [
        {'name': 'Alice', 'math': 85, 'science': 92, 'english': 78},
        {'name': 'Bob', 'math': 72, 'science': 68, 'english': 81},
        {'name': 'Charlie', 'math': 91, 'science': 89, 'english': 85},
        {'name': 'Diana', 'math': 65, 'science': 71, 'english': 73},
        {'name': 'Eve', 'math': 88, 'science': 94, 'english': 90}
    ]
    
    for student in students:
        # Calculate total score
        total = student['math'] + student['science'] + student['english']
        
        # Add total to student data
        student_with_total = {**student, 'total': total}
        
        yield student_with_total

# Process students one by one
student_totals = []
subject_totals = {'math': 0, 'science': 0, 'english': 0}

print("Processing students:")
for student in student_grades_generator():
    student_totals.append(student['total'])
    subject_totals['math'] += student['math']
    subject_totals['science'] += student['science']
    subject_totals['english'] += student['english']
    
    print(f"{student['name']}: Math={student['math']}, Science={student['science']}, "
          f"English={student['english']}, Total={student['total']}")

# Calculate statistics
total_students = len(student_totals)
class_total = sum(student_totals)
class_average = class_total / total_students

print(f"\nClass Statistics:")
print(f"Total students: {total_students}")
print(f"Class total: {class_total}")
print(f"Class average: {class_average:.2f}")

print(f"\nSubject Totals:")
for subject, total in subject_totals.items():
    average = total / total_students
    print(f"{subject}: {total} (Average: {average:.2f})")

# Find highest and lowest scoring students
highest_total = max(student_totals)
lowest_total = min(student_totals)

print(f"\nScore Analysis:")
print(f"Highest total: {highest_total}")
print(f"Lowest total: {lowest_total}")
```
**Logic Explanation:**
- Generator yields student data one at a time with calculated totals
- Statistics calculated during iteration without storing all student data
- Memory efficient processing of student information
- Demonstrates how generators can handle educational data processing

### Program 2: Shopping Bill Calculator
**Problem Statement:** Process shopping items using generators to calculate bills and categorize expenses.

```python
# Shopping items generator
def shopping_items_generator():
    items = [
        {'name': 'Shirt', 'price': 30, 'category': 'clothing', 'quantity': 2},
        {'name': 'Jeans', 'price': 50, 'category': 'clothing', 'quantity': 1},
        {'name': 'Book', 'price': 15, 'category': 'education', 'quantity': 3},
        {'name': 'Laptop', 'price': 800, 'category': 'electronics', 'quantity': 1},
        {'name': 'Phone', 'price': 400, 'category': 'electronics', 'quantity': 1},
        {'name': 'Shoes', 'price': 80, 'category': 'clothing', 'quantity': 1}
    ]
    
    for item in items:
        # Calculate item total
        item_total = item['price'] * item['quantity']
        
        # Add total to item data
        item_with_total = {**item, 'total': item_total}
        
        yield item_with_total

# Process items one by one
category_totals = {}
grand_total = 0

print("Processing shopping items:")
for item in shopping_items_generator():
    category = item['category']
    
    # Update category totals
    if category not in category_totals:
        category_totals[category] = 0
    category_totals[category] += item['total']
    
    # Update grand total
    grand_total += item['total']
    
    print(f"{item['name']}: ${item['price']} × {item['quantity']} = ${item['total']} ({category})")

# Calculate discounts based on category totals
def calculate_discount(category_total):
    if category_total > 500:
        return category_total * 0.15  # 15% discount
    elif category_total > 100:
        return category_total * 0.10  # 10% discount
    else:
        return category_total * 0.05  # 5% discount

print(f"\nCategory Breakdown:")
for category, total in category_totals.items():
    discount = calculate_discount(total)
    final_total = total - discount
    print(f"{category}: ${total:.2f} - Discount: ${discount:.2f} = ${final_total:.2f}")

# Calculate final bill
total_discount = sum(calculate_discount(total) for total in category_totals.values())
final_bill = grand_total - total_discount

print(f"\nBill Summary:")
print(f"Grand total: ${grand_total:.2f}")
print(f"Total discount: ${total_discount:.2f}")
print(f"Final bill: ${final_bill:.2f}")

# Find most expensive category
most_expensive_category = max(category_totals, key=category_totals.get)
print(f"\nMost expensive category: {most_expensive_category} (${category_totals[most_expensive_category]:.2f})")
```
**Logic Explanation:**
- Generator yields shopping items one at a time with calculated totals
- Category totals and grand total calculated during iteration
- Discounts applied based on category spending
- Memory efficient processing of shopping cart data

### Program 3: Employee Salary Calculator
**Problem Statement:** Process employee data using generators to calculate payroll and department statistics.

```python
# Employee data generator
def employees_generator():
    employees = [
        {'name': 'Alice', 'salary': 75000, 'department': 'engineering', 'performance': 9.2},
        {'name': 'Bob', 'salary': 45000, 'department': 'sales', 'performance': 8.5},
        {'name': 'Charlie', 'salary': 82000, 'department': 'engineering', 'performance': 7.8},
        {'name': 'Diana', 'salary': 55000, 'department': 'marketing', 'performance': 9.5},
        {'name': 'Eve', 'salary': 68000, 'department': 'sales', 'performance': 8.0},
        {'name': 'Frank', 'salary': 48000, 'department': 'marketing', 'performance': 7.2},
        {'name': 'Grace', 'salary': 92000, 'department': 'engineering', 'performance': 9.8}
    ]
    
    for emp in employees:
        # Calculate bonus based on performance
        if emp['performance'] >= 9.0:
            bonus = emp['salary'] * 0.20  # 20% bonus
        elif emp['performance'] >= 8.0:
            bonus = emp['salary'] * 0.15  # 15% bonus
        elif emp['performance'] >= 7.0:
            bonus = emp['salary'] * 0.10  # 10% bonus
        else:
            bonus = emp['salary'] * 0.05  # 5% bonus
        
        # Calculate total compensation
        total_comp = emp['salary'] + bonus
        
        # Add compensation data to employee
        emp_with_comp = {**emp, 'bonus': bonus, 'total_comp': total_comp}
        
        yield emp_with_comp

# Process employees one by one
department_stats = {}
total_payroll = 0
employee_count = 0

print("Processing employees:")
for emp in employees_generator():
    dept = emp['department']
    
    # Update department statistics
    if dept not in department_stats:
        department_stats[dept] = {
            'count': 0,
            'total_salary': 0,
            'total_bonus': 0,
            'total_comp': 0,
            'performance_sum': 0
        }
    
    department_stats[dept]['count'] += 1
    department_stats[dept]['total_salary'] += emp['salary']
    department_stats[dept]['total_bonus'] += emp['bonus']
    department_stats[dept]['total_comp'] += emp['total_comp']
    department_stats[dept]['performance_sum'] += emp['performance']
    
    # Update totals
    total_payroll += emp['total_comp']
    employee_count += 1
    
    print(f"{emp['name']}: Salary=${emp['salary']:,}, Bonus=${emp['bonus']:,}, "
          f"Total=${emp['total_comp']:,} ({dept})")

# Calculate department averages
for dept, stats in department_stats.items():
    stats['avg_salary'] = stats['total_salary'] / stats['count']
    stats['avg_bonus'] = stats['total_bonus'] / stats['count']
    stats['avg_comp'] = stats['total_comp'] / stats['count']
    stats['avg_performance'] = stats['performance_sum'] / stats['count']

print(f"\nDepartment Statistics:")
for dept, stats in department_stats.items():
    print(f"\n{dept.capitalize()}:")
    print(f"  Employees: {stats['count']}")
    print(f"  Average Salary: ${stats['avg_salary']:,.2f}")
    print(f"  Average Bonus: ${stats['avg_bonus']:,.2f}")
    print(f"  Average Total Compensation: ${stats['avg_comp']:,.2f}")
    print(f"  Average Performance: {stats['avg_performance']:.2f}")

print(f"\nPayroll Summary:")
print(f"Total employees: {employee_count}")
print(f"Total payroll: ${total_payroll:,}")
print(f"Average compensation: ${total_payroll / employee_count:,.2f}")
```
**Logic Explanation:**
- Generator yields employee data one at a time with calculated compensation
- Department statistics built incrementally during iteration
- Payroll totals calculated without storing all employee data
- Memory efficient processing of HR data

### Program 4: Bank Transaction Processor
**Problem Statement:** Process bank transactions using generators to track balances and categorize expenses.

```python
# Bank transactions generator
def transactions_generator():
    transactions = [
        {'date': '2023-12-01', 'amount': 1500, 'type': 'deposit', 'description': 'Salary'},
        {'date': '2023-12-03', 'amount': -200, 'type': 'withdrawal', 'description': 'Shopping'},
        {'date': '2023-12-05', 'amount': -600, 'type': 'withdrawal', 'description': 'Rent'},
        {'date': '2023-12-07', 'amount': -300, 'type': 'transfer', 'description': 'To friend'},
        {'date': '2023-12-08', 'amount': -50, 'type': 'withdrawal', 'description': 'Coffee'},
        {'date': '2023-12-10', 'amount': 1000, 'type': 'deposit', 'description': 'Freelance'},
        {'date': '2023-12-12', 'amount': -150, 'type': 'withdrawal', 'description': 'Groceries'},
        {'date': '2023-12-15', 'amount': 800, 'type': 'deposit', 'description': 'Investment'},
        {'date': '2023-12-16', 'amount': -120, 'type': 'withdrawal', 'description': 'Utilities'},
        {'date': '2023-12-20', 'amount': 2000, 'type': 'deposit', 'description': 'Bonus'}
    ]
    
    running_balance = 0
    
    for trans in transactions:
        # Update running balance
        running_balance += trans['amount']
        
        # Add balance to transaction
        trans_with_balance = {**trans, 'balance': running_balance}
        
        yield trans_with_balance

# Process transactions one by one
category_expenses = {}
total_income = 0
total_expenses = 0

print("Processing transactions:")
for trans in transactions_generator():
    # Categorize expenses
    if trans['amount'] < 0:  # It's an expense
        category = trans['description'].split()[0]  # Use first word as category
        if category not in category_expenses:
            category_expenses[category] = 0
        category_expenses[category] += abs(trans['amount'])
        total_expenses += abs(trans['amount'])
    else:
        total_income += trans['amount']
    
    trans_type = "Credit" if trans['amount'] > 0 else "Debit"
    print(f"{trans['date']}: {trans['description']} - ${abs(trans['amount']):.2f} {trans_type} -> Balance: ${trans['balance']:.2f}")

# Calculate financial summary
net_cash_flow = total_income - total_expenses

print(f"\nFinancial Summary:")
print(f"Total Income: ${total_income:.2f}")
print(f"Total Expenses: ${total_expenses:.2f}")
print(f"Net Cash Flow: ${net_cash_flow:.2f}")

# Analyze expense categories
print(f"\nExpense Categories:")
for category, amount in category_expenses.items():
    percentage = (amount / total_expenses) * 100
    print(f"{category}: ${amount:.2f} ({percentage:.1f}%)")

# Find largest transaction
largest_deposit = 0
largest_withdrawal = 0

# Reset generator to find largest transactions
for trans in transactions_generator():
    if trans['amount'] > 0 and trans['amount'] > largest_deposit:
        largest_deposit = trans['amount']
    elif trans['amount'] < 0 and abs(trans['amount']) > largest_withdrawal:
        largest_withdrawal = abs(trans['amount'])

print(f"\nTransaction Analysis:")
print(f"Largest deposit: ${largest_deposit:.2f}")
print(f"Largest withdrawal: ${largest_withdrawal:.2f}")
```
**Logic Explanation:**
- Generator yields transactions one at a time with running balance
- Category expenses and financial summary calculated during iteration
- Memory efficient processing of financial data
- Demonstrates how generators can handle transaction processing

### Program 5: Website User Data Processor
**Problem Statement:** Process website user data using generators to analyze engagement and user segments.

```python
# Website user data generator
def users_generator():
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
    
    for user in users:
        # Calculate engagement score
        engagement_score = user['posts'] * 3 + user['comments'] * 2 + user['likes'] * 1
        
        # Add engagement score to user data
        user_with_engagement = {**user, 'engagement_score': engagement_score}
        
        yield user_with_engagement

# Process users one by one
user_segments = {'active': [], 'moderate': [], 'inactive': []}
subscription_stats = {'premium': 0, 'basic': 0}
total_metrics = {'posts': 0, 'comments': 0, 'likes': 0, 'engagement': 0}
user_count = 0

print("Processing users:")
for user in users_generator():
    # Segment users by activity
    if user['last_login'] < 15:
        user_segments['active'].append(user['name'])
    elif user['last_login'] < 45:
        user_segments['moderate'].append(user['name'])
    else:
        user_segments['inactive'].append(user['name'])
    
    # Update subscription statistics
    subscription_stats[user['subscription']] += 1
    
    # Update total metrics
    total_metrics['posts'] += user['posts']
    total_metrics['comments'] += user['comments']
    total_metrics['likes'] += user['likes']
    total_metrics['engagement'] += user['engagement_score']
    user_count += 1
    
    print(f"{user['name']}: Posts={user['posts']}, Comments={user['comments']}, "
          f"Likes={user['likes']}, Engagement={user['engagement_score']} ({user['subscription']})")

# Calculate platform statistics
avg_posts = total_metrics['posts'] / user_count
avg_comments = total_metrics['comments'] / user_count
avg_likes = total_metrics['likes'] / user_count
avg_engagement = total_metrics['engagement'] / user_count

print(f"\nPlatform Statistics:")
print(f"Total users: {user_count}")
print(f"Total posts: {total_metrics['posts']}")
print(f"Total comments: {total_metrics['comments']}")
print(f"Total likes: {total_metrics['likes']}")
print(f"Average posts per user: {avg_posts:.2f}")
print(f"Average comments per user: {avg_comments:.2f}")
print(f"Average likes per user: {avg_likes:.2f}")
print(f"Average engagement per user: {avg_engagement:.2f}")

# User segment analysis
print(f"\nUser Segments:")
for segment, user_list in user_segments.items():
    percentage = (len(user_list) / user_count) * 100
    print(f"{segment.capitalize()}: {len(user_list)} users ({percentage:.1f}%)")
    if user_list:
        print(f"  Users: {', '.join(user_list)}")

# Subscription analysis
print(f"\nSubscription Analysis:")
for sub_type, count in subscription_stats.items():
    percentage = (count / user_count) * 100
    print(f"{sub_type.capitalize()}: {count} users ({percentage:.1f}%)")

# Find most and least engaged users
# Reset generator to find engagement extremes
highest_engagement = 0
lowest_engagement = float('inf')
most_engaged_user = ""
least_engaged_user = ""

for user in users_generator():
    if user['engagement_score'] > highest_engagement:
        highest_engagement = user['engagement_score']
        most_engaged_user = user['name']
    
    if user['engagement_score'] < lowest_engagement:
        lowest_engagement = user['engagement_score']
        least_engaged_user = user['name']

print(f"\nEngagement Analysis:")
print(f"Most engaged: {most_engaged_user} (Score: {highest_engagement})")
print(f"Least engaged: {least_engaged_user} (Score: {lowest_engagement})")
```
**Logic Explanation:**
- Generator yields user data one at a time with calculated engagement scores
- User segments and platform statistics built incrementally
- Multiple passes through generator for different analyses
- Memory efficient processing of user analytics data

## 9️⃣ Common Mistakes

### Mistake 1: Confusing Generators with Regular Functions
**Beginner Mistake:** Expecting generators to return lists instead of generator objects.

```python
# WRONG - Expecting list from generator
def my_generator():
    yield 1
    yield 2
    yield 3

result = my_generator()
print(result)  # Prints generator object, not [1, 2, 3]

# RIGHT - Convert to list or iterate
def my_generator():
    yield 1
    yield 2
    yield 3

result = list(my_generator())  # Convert to list
print(result)  # [1, 2, 3]

# OR iterate directly
for value in my_generator():
    print(value)
```

**How to Fix:** Remember that generator functions return generator objects, not lists. Use `list()` or iterate.

### Mistake 2: Using return Instead of yield
**Beginner Mistake:** Using `return` instead of `yield` in generator functions.

```python
# WRONG - Using return instead of yield
def bad_generator():
    for i in range(5):
        return i  # Returns on first iteration

# RIGHT - Using yield
def good_generator():
    for i in range(5):
        yield i  # Yields each value
```

**How to Fix:** Use `yield` to return values from generators, not `return`.

### Mistake 3: Trying to Reuse Exhausted Generator
**Beginner Mistake:** Trying to use a generator after it's been exhausted.

```python
# WRONG - Reusing exhausted generator
def number_generator():
    for i in range(3):
        yield i

gen = number_generator()
print(list(gen))  # [0, 1, 2]
print(list(gen))  # [] - generator is exhausted

# RIGHT - Create new generator for each use
def number_generator():
    for i in range(3):
        yield i

print(list(number_generator()))  # [0, 1, 2]
print(list(number_generator()))  # [0, 1, 2] - fresh generator
```

**How to Fix:** Create a new generator each time you need to iterate through the sequence.

### Mistake 4: Confusing Generator Expressions with List Comprehensions
**Beginner Mistake:** Using wrong syntax for generator expressions.

```python
# WRONG - Using brackets instead of parentheses
gen_expression = [x * x for x in range(5)]  # This is list comprehension

# RIGHT - Using parentheses for generator expression
gen_expression = (x * x for x in range(5))  # This is generator expression
```

**How to Fix:** Use parentheses `()` for generator expressions, brackets `[]` for list comprehensions.

### Mistake 5: Modifying Generator State Incorrectly
**Beginner Mistake:** Trying to modify generator state from outside the function.

```python
# WRONG - Trying to modify generator state
def counter_generator():
    count = 0
    while count < 5:
        yield count
        count += 1

gen = counter_generator()
gen.count = 10  # This doesn't work!

# RIGHT - Let generator manage its own state
def counter_generator():
    count = 0
    while count < 5:
        yield count
        count += 1

gen = counter_generator()
for num in gen:
    print(num)  # 0, 1, 2, 3, 4
```

**How to Fix:** Let generators manage their own state internally; don't try to modify from outside.

## 🔟 Summary (Revision Notes)

- **Generators** are special functions that produce values on-demand using `yield`
- **Memory Efficient**: Only one value exists in memory at a time
- **Lazy Evaluation**: Values are generated only when requested
- **State Preservation**: Generators remember their state between calls
- **Yield Statement**: `yield` returns a value and pauses execution
- **Generator Functions**: Defined like regular functions but use `yield`
- **Generator Expressions**: Similar to list comprehensions but use parentheses
- **Iterator Protocol**: Generators automatically implement iterator protocol
- **Infinite Sequences**: Can represent infinite sequences without memory issues
- **Common Use Cases**: Processing large files, streaming data, memory-efficient processing
- **Benefits**: Constant memory usage, faster startup, can handle infinite sequences

---

✅ Topic 7 completed. Module 1 complete!