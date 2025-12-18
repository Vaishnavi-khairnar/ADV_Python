# 6️⃣ Iterators

## 2️⃣ Simple Definition
Iterators are objects that let you go through a collection of items one by one, without loading everything into memory at once. Think of them like a TV remote control - you can only change to the next channel, you can't go back, and you don't need to know all channels in advance to use it.

## 3️⃣ Why This Topic Exists
Python introduced iterators to help developers work with large datasets or infinite sequences without running out of memory. Before iterators, programmers had to load entire collections into memory even when they only needed to process items one at a time. Iterators solve this by providing a memory-efficient way to access items sequentially, making it possible to work with huge datasets or even infinite sequences.

## 4️⃣ Real-Life Analogy (MANDATORY)

### The Book Reading Analogy
Imagine you're reading a very long book:

**Traditional Approach (Loading Everything at Once):**
- You try to memorize the entire book before reading
- You need perfect memory to remember every page
- If the book is too long, your brain gets overwhelmed
- You can only read books that fit in your memory capacity

**Iterator Approach (Reading Page by Page):**
- You read one page at a time
- You only need to remember the current page
- You can read books of any length, even infinitely long ones
- You move forward one page at a time without going back

**The Benefits:**
- No memory overload from trying to remember everything
- Can handle books of any size
- Focus only on current content
- Efficient use of mental resources

In Python:
- The "book" is your collection (list, file, database, etc.)
- The "page by page reading" is the iterator
- The "current page" is the current item
- The "turning to next page" is the next() operation

Just like reading page by page lets you handle books of any size, iterators let you handle data of any size!

## 5️⃣ Step-by-Step Explanation

### How Iterators Work Internally:

- **Iterator Protocol**: Objects that implement `__iter__()` and `__next__()` methods
- **State Management**: Iterators keep track of their current position
- **Lazy Evaluation**: Items are generated only when requested, not in advance
- **Memory Efficiency**: Only one item exists in memory at a time
- **Single Direction**: Can only move forward, not backward
- **Exhaustion**: Once all items are consumed, iterator raises StopIteration

### Internal Processing:
1. Python calls `iter()` on an iterable to get an iterator
2. The `__iter__()` method returns an iterator object
3. Python calls `next()` on the iterator to get the first item
4. The `__next__()` method returns the current item and advances position
5. This continues until `__next__()` raises StopIteration
6. The for loop automatically handles this exception to end iteration

### Performance Benefits:
- Constant memory usage regardless of collection size
- Can work with infinite sequences
- Faster startup time (no need to process entire collection)
- Enables processing of datasets larger than available memory

## 6️⃣ Basic Syntax Explanation

### Iterator Creation and Usage:

```python
# Create iterator from iterable
my_iterator = iter(iterable)

# Get next item
next_item = next(my_iterator)

# Manual iteration
try:
    while True:
        item = next(my_iterator)
        # Process item
except StopIteration:
    # Iterator is exhausted
```

### Example 1: Basic Iterator from List
```python
numbers = [1, 2, 3, 4, 5]
number_iterator = iter(numbers)

print(next(number_iterator))  # 1
print(next(number_iterator))  # 2
print(next(number_iterator))  # 3
print(next(number_iterator))  # 4
print(next(number_iterator))  # 5
# print(next(number_iterator))  # Would raise StopIteration
```
- `iter(numbers)` - Creates an iterator from the list
- `next(number_iterator)` - Gets the next item from iterator
- After 5 calls, iterator is exhausted and raises StopIteration

### Example 2: Using Iterator in for Loop
```python
numbers = [1, 2, 3, 4, 5]
number_iterator = iter(numbers)

for num in number_iterator:
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
- `for` loop automatically handles the iterator protocol
- Calls `next()` internally until StopIteration is raised
- No need to manually handle StopIteration exception

### Example 3: Iterator from String
```python
text = "Hello"
text_iterator = iter(text)

for char in text_iterator:
    print(char)
```
**Output:**
```
H
e
l
l
o
```
- Strings are iterable and can be converted to iterators
- Each iteration yields one character

### Example 4: Iterator from File
```python
# Create a sample file
with open('sample.txt', 'w') as f:
    f.write('Line 1\nLine 2\nLine 3')

# Read file using iterator
with open('sample.txt', 'r') as f:
    file_iterator = iter(f)
    print(next(file_iterator).strip())  # Line 1
    print(next(file_iterator).strip())  # Line 2
```
- File objects are iterators that yield lines one by one
- Memory efficient for reading large files

### Example 5: Custom Iterator Class
```python
class Countdown:
    def __init__(self, start):
        self.current = start
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.current <= 0:
            raise StopIteration
        self.current -= 1
        return self.current + 1

# Use custom iterator
countdown = Countdown(3)
for num in countdown:
    print(num)
```
**Output:**
```
3
2
1
```
- `__iter__()` returns the iterator object itself
- `__next__()` returns current value and decrements counter
- Raises StopIteration when countdown reaches zero

## 7️⃣ 10 PRACTICE PROGRAMS (WITH SOLUTION)

### Program 1: Basic Iterator Usage
**Question:** Create an iterator from a list and manually iterate through it.

```python
fruits = ['apple', 'banana', 'cherry', 'date']
fruit_iterator = iter(fruits)

print(next(fruit_iterator))
print(next(fruit_iterator))
print(next(fruit_iterator))
print(next(fruit_iterator))
```
**Output:**
```
apple
banana
cherry
date
```
**Explanation:** The iterator yields each fruit one by one when next() is called.

### Program 2: Iterator with Exception Handling
**Question:** Use iterator with proper exception handling for exhaustion.

```python
numbers = [10, 20, 30]
number_iterator = iter(numbers)

try:
    while True:
        print(next(number_iterator))
except StopIteration:
    print("Iterator exhausted!")
```
**Output:**
```
10
20
30
Iterator exhausted!
```
**Explanation:** The try-except block catches StopIteration when iterator is exhausted.

### Program 3: String Iterator
**Question:** Create an iterator from a string and count characters.

```python
word = "python"
char_iterator = iter(word)
char_count = 0

try:
    while True:
        char = next(char_iterator)
        print(f"Character {char_count + 1}: {char}")
        char_count += 1
except StopIteration:
    print(f"Total characters: {char_count}")
```
**Output:**
```
Character 1: p
Character 2: y
Character 3: t
Character 4: h
Character 5: o
Character 6: n
Total characters: 6
```
**Explanation:** Iterator yields each character, allowing us to count them.

### Program 4: Iterator from Range
**Question:** Create an iterator from range and process numbers.

```python
numbers = range(1, 6)
number_iterator = iter(numbers)

squares = []
for num in number_iterator:
    squares.append(num * num)

print(squares)
```
**Output:**
```
[1, 4, 9, 16, 25]
```
**Explanation:** Iterator from range yields numbers 1-5, which are then squared.

### Program 5: Multiple Iterators from Same List
**Question:** Create multiple independent iterators from the same list.

```python
colors = ['red', 'green', 'blue']
iterator1 = iter(colors)
iterator2 = iter(colors)

print("Iterator 1:", next(iterator1))
print("Iterator 1:", next(iterator1))
print("Iterator 2:", next(iterator2))
print("Iterator 1:", next(iterator1))
print("Iterator 2:", next(iterator2))
```
**Output:**
```
Iterator 1: red
Iterator 1: green
Iterator 2: red
Iterator 1: blue
Iterator 2: green
```
**Explanation:** Multiple iterators are independent and maintain separate positions.

### Program 6: Iterator with List Comprehension
**Question:** Use iterator in list comprehension to create new list.

```python
numbers = [1, 2, 3, 4, 5]
number_iterator = iter(numbers)

doubled = [num * 2 for num in number_iterator]
print(doubled)
```
**Output:**
```
[2, 4, 6, 8, 10]
```
**Explanation:** List comprehension consumes the iterator and creates new list.

### Program 7: Iterator Exhaustion Check
**Question:** Check if iterator is exhausted without using exception.

```python
numbers = [1, 2, 3]
number_iterator = iter(numbers)

# Get all items
items = list(number_iterator)
print("Items:", items)

# Try to get more (should be empty)
more_items = list(number_iterator)
print("More items:", more_items)
```
**Output:**
```
Items: [1, 2, 3]
More items: []
```
**Explanation:** Once iterator is exhausted, it yields no more items.

### Program 8: Iterator with Conditional Processing
**Question:** Process only even numbers from an iterator.

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
number_iterator = iter(numbers)

even_numbers = []
for num in number_iterator:
    if num % 2 == 0:
        even_numbers.append(num)

print(even_numbers)
```
**Output:**
```
[2, 4, 6, 8, 10]
```
**Explanation:** Iterator yields all numbers, but we only keep even ones.

### Program 9: Iterator with enumerate()
**Question:** Use enumerate() with iterator to get index and value.

```python
fruits = ['apple', 'banana', 'cherry']
fruit_iterator = iter(fruits)

for index, fruit in enumerate(fruit_iterator):
    print(f"Index {index}: {fruit}")
```
**Output:**
```
Index 0: apple
Index 1: banana
Index 2: cherry
```
**Explanation:** enumerate() adds index tracking to iterator iteration.

### Program 10: Iterator with zip()
**Question:** Combine two iterators using zip().

```python
names = ['Alice', 'Bob', 'Charlie']
scores = [85, 92, 78]

name_iterator = iter(names)
score_iterator = iter(scores)

for name, score in zip(name_iterator, score_iterator):
    print(f"{name}: {score}")
```
**Output:**
```
Alice: 85
Bob: 92
Charlie: 78
```
**Explanation:** zip() combines two iterators, yielding pairs of corresponding items.

## 8️⃣ 5 REAL-WORLD PROGRAMS (WITH SOLUTION)

### Program 1: Student Grade Processing
**Problem Statement:** Process student grades using iterators to calculate statistics without loading all data at once.

```python
# Student grades from different subjects
student_grades = [
    {'name': 'Alice', 'math': 85, 'science': 92, 'english': 78},
    {'name': 'Bob', 'math': 72, 'science': 68, 'english': 81},
    {'name': 'Charlie', 'math': 91, 'science': 89, 'english': 85},
    {'name': 'Diana', 'math': 65, 'science': 71, 'english': 73},
    {'name': 'Eve', 'math': 88, 'science': 94, 'english': 90}
]

# Create iterator for student grades
grade_iterator = iter(student_grades)

# Process students one by one
student_totals = []
subject_totals = {'math': 0, 'science': 0, 'english': 0}

try:
    while True:
        student = next(grade_iterator)
        
        # Calculate student total
        total = student['math'] + student['science'] + student['english']
        student_totals.append({'name': student['name'], 'total': total})
        
        # Update subject totals
        subject_totals['math'] += student['math']
        subject_totals['science'] += student['science']
        subject_totals['english'] += student['english']
        
        print(f"Processed: {student['name']} - Total: {total}")
        
except StopIteration:
    print("\nAll students processed!")

# Calculate final statistics
total_students = len(student_totals)
class_total = sum(student['total'] for student in student_totals)
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
highest_student = max(student_totals, key=lambda x: x['total'])
lowest_student = min(student_totals, key=lambda x: x['total'])

print(f"\nHighest scorer: {highest_student['name']} ({highest_student['total']})")
print(f"Lowest scorer: {lowest_student['name']} ({lowest_student['total']})")
```
**Logic Explanation:**
- Iterator processes students one at a time without loading all into memory
- Student totals and subject totals calculated during iteration
- Statistics computed after processing all students
- Demonstrates memory-efficient processing of student data

### Program 2: Shopping Bill Calculator
**Problem Statement:** Process shopping items using iterators to calculate bills and categorize expenses.

```python
# Shopping items with categories
shopping_items = [
    {'name': 'Shirt', 'price': 30, 'category': 'clothing', 'quantity': 2},
    {'name': 'Jeans', 'price': 50, 'category': 'clothing', 'quantity': 1},
    {'name': 'Book', 'price': 15, 'category': 'education', 'quantity': 3},
    {'name': 'Laptop', 'price': 800, 'category': 'electronics', 'quantity': 1},
    {'name': 'Phone', 'price': 400, 'category': 'electronics', 'quantity': 1},
    {'name': 'Shoes', 'price': 80, 'category': 'clothing', 'quantity': 1},
    {'name': 'Pen', 'price': 2, 'category': 'education', 'quantity': 5}
]

# Create iterator for shopping items
item_iterator = iter(shopping_items)

# Process items one by one
processed_items = []
category_totals = {}
grand_total = 0

try:
    while True:
        item = next(item_iterator)
        
        # Calculate item total
        item_total = item['price'] * item['quantity']
        
        # Add to processed items
        processed_item = {**item, 'total': item_total}
        processed_items.append(processed_item)
        
        # Update category totals
        category = item['category']
        if category not in category_totals:
            category_totals[category] = 0
        category_totals[category] += item_total
        
        # Update grand total
        grand_total += item_total
        
        print(f"Processed: {item['name']} - {item['quantity']} × ${item['price']} = ${item_total}")
        
except StopIteration:
    print("\nAll items processed!")

# Calculate discounts based on category totals
def calculate_discount(category_total):
    if category_total > 500:
        return category_total * 0.15  # 15% discount
    elif category_total > 100:
        return category_total * 0.10  # 10% discount
    else:
        return category_total * 0.05  # 5% discount

# Apply discounts to each category
category_discounts = {}
for category, total in category_totals.items():
    discount = calculate_discount(total)
    category_discounts[category] = discount

print(f"\nCategory Breakdown:")
for category, total in category_totals.items():
    discount = category_discounts[category]
    final_total = total - discount
    print(f"{category}: ${total:.2f} - Discount: ${discount:.2f} = ${final_total:.2f}")

# Calculate final bill
total_discount = sum(category_discounts.values())
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
- Iterator processes shopping items one at a time
- Category totals and grand total calculated during iteration
- Discounts applied based on category spending
- Demonstrates memory-efficient shopping cart processing

### Program 3: Employee Salary Calculator
**Problem Statement:** Process employee data using iterators to calculate payroll and department statistics.

```python
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

# Create iterator for employees
employee_iterator = iter(employees)

# Process employees one by one
processed_employees = []
department_stats = {}
total_payroll = 0

try:
    while True:
        emp = next(employee_iterator)
        
        # Calculate bonus based on performance
        if emp['performance'] >= 9.0:
            bonus = emp['salary'] * 0.20
        elif emp['performance'] >= 8.0:
            bonus = emp['salary'] * 0.15
        elif emp['performance'] >= 7.0:
            bonus = emp['salary'] * 0.10
        else:
            bonus = emp['salary'] * 0.05
        
        # Calculate total compensation
        total_comp = emp['salary'] + bonus
        
        # Add to processed employees
        processed_emp = {**emp, 'bonus': bonus, 'total_comp': total_comp}
        processed_employees.append(processed_emp)
        
        # Update department statistics
        dept = emp['department']
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
        department_stats[dept]['total_bonus'] += bonus
        department_stats[dept]['total_comp'] += total_comp
        department_stats[dept]['performance_sum'] += emp['performance']
        
        # Update total payroll
        total_payroll += total_comp
        
        print(f"Processed: {emp['name']} - Salary: ${emp['salary']:,}, Bonus: ${bonus:,}, Total: ${total_comp:,}")
        
except StopIteration:
    print("\nAll employees processed!")

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

# Find highest and lowest compensated employees
highest_comp = max(processed_employees, key=lambda x: x['total_comp'])
lowest_comp = min(processed_employees, key=lambda x: x['total_comp'])

print(f"\nCompensation Analysis:")
print(f"Highest compensated: {highest_comp['name']} (${highest_comp['total_comp']:,})")
print(f"Lowest compensated: {lowest_comp['name']} (${lowest_comp['total_comp']:,})")

print(f"\nPayroll Summary:")
print(f"Total payroll: ${total_payroll:,}")
print(f"Average compensation: ${total_payroll / len(processed_employees):,.2f}")
```
**Logic Explanation:**
- Iterator processes employees one at a time
- Bonuses calculated based on performance scores
- Department statistics built incrementally during iteration
- Demonstrates memory-efficient payroll processing

### Program 4: Bank Transaction Processor
**Problem Statement:** Process bank transactions using iterators to track balances and categorize expenses.

```python
# Bank transactions
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

# Create iterator for transactions
transaction_iterator = iter(transactions)

# Process transactions one by one
processed_transactions = []
category_expenses = {}
running_balance = 0

try:
    while True:
        trans = next(transaction_iterator)
        
        # Update running balance
        running_balance += trans['amount']
        
        # Add balance to transaction
        processed_trans = {**trans, 'balance': running_balance}
        processed_transactions.append(processed_trans)
        
        # Categorize expenses
        if trans['amount'] < 0:  # It's an expense
            category = trans['description'].split()[0]  # Use first word as category
            if category not in category_expenses:
                category_expenses[category] = 0
            category_expenses[category] += abs(trans['amount'])
        
        trans_type = "Credit" if trans['amount'] > 0 else "Debit"
        print(f"{trans['date']}: {trans['description']} - ${abs(trans['amount']):.2f} {trans_type} -> Balance: ${running_balance:.2f}")
        
except StopIteration:
    print("\nAll transactions processed!")

# Calculate financial summary
total_income = sum(t['amount'] for t in processed_transactions if t['amount'] > 0)
total_expenses = sum(abs(t['amount']) for t in processed_transactions if t['amount'] < 0)
net_cash_flow = total_income + total_expenses  # total_expenses is negative

print(f"\nFinancial Summary:")
print(f"Total Income: ${total_income:.2f}")
print(f"Total Expenses: ${abs(total_expenses):.2f}")
print(f"Net Cash Flow: ${net_cash_flow:.2f}")
print(f"Final Balance: ${running_balance:.2f}")

# Analyze expense categories
print(f"\nExpense Categories:")
for category, amount in category_expenses.items():
    percentage = (amount / abs(total_expenses)) * 100
    print(f"{category}: ${amount:.2f} ({percentage:.1f}%)")

# Find largest transaction
largest_transaction = max(processed_transactions, key=lambda x: abs(x['amount']))
smallest_transaction = min(processed_transactions, key=lambda x: abs(x['amount']))

print(f"\nTransaction Analysis:")
print(f"Largest: {largest_transaction['description']} (${abs(largest_transaction['amount']):.2f})")
print(f"Smallest: {smallest_transaction['description']} (${abs(smallest_transaction['amount']):.2f})")

# Calculate average transaction size
avg_transaction = sum(abs(t['amount']) for t in processed_transactions) / len(processed_transactions)
print(f"Average transaction size: ${avg_transaction:.2f}")
```
**Logic Explanation:**
- Iterator processes transactions one at a time
- Running balance updated during iteration
- Expense categories built incrementally
- Financial summary calculated after processing all transactions
- Demonstrates memory-efficient transaction processing

### Program 5: Website User Data Processor
**Problem Statement:** Process website user data using iterators to analyze engagement and user segments.

```python
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

# Create iterator for users
user_iterator = iter(users)

# Process users one by one
processed_users = []
user_segments = {'active': [], 'moderate': [], 'inactive': []}
subscription_stats = {'premium': 0, 'basic': 0}
total_metrics = {'posts': 0, 'comments': 0, 'likes': 0}

try:
    while True:
        user = next(user_iterator)
        
        # Calculate engagement score
        engagement_score = user['posts'] * 3 + user['comments'] * 2 + user['likes'] * 1
        
        # Add engagement score to user data
        processed_user = {**user, 'engagement_score': engagement_score}
        processed_users.append(processed_user)
        
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
        
        print(f"Processed: {user['name']} - Engagement: {engagement_score}, Last login: {user['last_login']} days ago")
        
except StopIteration:
    print("\nAll users processed!")

# Calculate platform statistics
total_users = len(processed_users)
avg_posts = total_metrics['posts'] / total_users
avg_comments = total_metrics['comments'] / total_users
avg_likes = total_metrics['likes'] / total_users

print(f"\nPlatform Statistics:")
print(f"Total users: {total_users}")
print(f"Total posts: {total_metrics['posts']}")
print(f"Total comments: {total_metrics['comments']}")
print(f"Total likes: {total_metrics['likes']}")
print(f"Average posts per user: {avg_posts:.2f}")
print(f"Average comments per user: {avg_comments:.2f}")
print(f"Average likes per user: {avg_likes:.2f}")

# User segment analysis
print(f"\nUser Segments:")
for segment, user_list in user_segments.items():
    percentage = (len(user_list) / total_users) * 100
    print(f"{segment.capitalize()}: {len(user_list)} users ({percentage:.1f}%)")
    if user_list:
        print(f"  Users: {', '.join(user_list)}")

# Subscription analysis
print(f"\nSubscription Analysis:")
for sub_type, count in subscription_stats.items():
    percentage = (count / total_users) * 100
    print(f"{sub_type.capitalize()}: {count} users ({percentage:.1f}%)")

# Find most and least engaged users
most_engaged = max(processed_users, key=lambda x: x['engagement_score'])
least_engaged = min(processed_users, key=lambda x: x['engagement_score'])

print(f"\nEngagement Analysis:")
print(f"Most engaged: {most_engaged['name']} (Score: {most_engaged['engagement_score']})")
print(f"Least engaged: {least_engaged['name']} (Score: {least_engaged['engagement_score']})")

# Calculate engagement levels
engagement_levels = {'high': 0, 'medium': 0, 'low': 0}
for user in processed_users:
    if user['engagement_score'] > 100:
        engagement_levels['high'] += 1
    elif user['engagement_score'] > 50:
        engagement_levels['medium'] += 1
    else:
        engagement_levels['low'] += 1

print(f"\nEngagement Levels:")
for level, count in engagement_levels.items():
    percentage = (count / total_users) * 100
    print(f"{level.capitalize()}: {count} users ({percentage:.1f}%)")
```
**Logic Explanation:**
- Iterator processes users one at a time
- Engagement scores calculated during iteration
- User segments and statistics built incrementally
- Platform analysis performed after processing all users
- Demonstrates memory-efficient user data processing

## 9️⃣ Common Mistakes

### Mistake 1: Trying to Reuse Exhausted Iterator
**Beginner Mistake:** Trying to use an iterator after it's been exhausted.

```python
# WRONG - Reusing exhausted iterator
numbers = [1, 2, 3]
number_iterator = iter(numbers)
print(list(number_iterator))  # [1, 2, 3]
print(list(number_iterator))  # [] - iterator is exhausted

# RIGHT - Create new iterator for each use
numbers = [1, 2, 3]
print(list(iter(numbers)))  # [1, 2, 3]
print(list(iter(numbers)))  # [1, 2, 3] - fresh iterator
```

**How to Fix:** Create a new iterator each time you need to iterate through the collection.

### Mistake 2: Not Handling StopIteration Exception
**Beginner Mistake:** Calling next() without handling the StopIteration exception.

```python
# WRONG - No exception handling
numbers = [1, 2, 3]
number_iterator = iter(numbers)
print(next(number_iterator))  # 1
print(next(number_iterator))  # 2
print(next(number_iterator))  # 3
print(next(number_iterator))  # Raises StopIteration and crashes

# RIGHT - Handle the exception
numbers = [1, 2, 3]
number_iterator = iter(numbers)
try:
    while True:
        print(next(number_iterator))
except StopIteration:
    print("Iterator exhausted!")
```

**How to Fix:** Always handle StopIteration exception when manually using next().

### Mistake 3: Modifying Collection While Iterating
**Beginner Mistake:** Changing the collection while iterating over it.

```python
# WRONG - Modifying during iteration
numbers = [1, 2, 3, 4, 5]
number_iterator = iter(numbers)
for num in number_iterator:
    if num == 3:
        numbers.remove(num)  # This causes problems!

# RIGHT - Create new collection or use comprehension
numbers = [1, 2, 3, 4, 5]
filtered_numbers = [num for num in numbers if num != 3]
```

**How to Fix:** Don't modify the collection while iterating. Create a new collection instead.

### Mistake 4: Assuming Iterator Order
**Beginner Mistake:** Assuming iterators always maintain order or can be reset.

```python
# WRONG - Assuming order and reset capability
my_set = {3, 1, 4, 2}
set_iterator = iter(my_set)
print(next(set_iterator))  # Order is not guaranteed
# Can't reset iterator to beginning

# RIGHT - Use ordered collections when order matters
my_list = [3, 1, 4, 2]
list_iterator = iter(my_list)
print(next(list_iterator))  # Order is preserved
```

**How to Fix:** Use lists or tuples when order matters; remember iterators can't be reset.

### Mistake 5: Confusing Iterables and Iterators
**Beginner Mistake:** Not understanding the difference between iterables and iterators.

```python
# WRONG - Treating all iterables like iterators
numbers = [1, 2, 3]
print(next(numbers))  # Error: list is not an iterator

# RIGHT - Convert iterable to iterator first
numbers = [1, 2, 3]
number_iterator = iter(numbers)
print(next(number_iterator))  # Works correctly
```

**How to Fix:** Remember that lists, strings, etc. are iterables but not iterators. Use iter() to get an iterator.

## 🔟 Summary (Revision Notes)

- **Iterators** are objects that provide sequential access to collection items
- **Iterator Protocol**: Objects with `__iter__()` and `__next__()` methods
- **Memory Efficient**: Only one item exists in memory at a time
- **Lazy Evaluation**: Items are generated only when requested
- **Single Direction**: Can only move forward, not backward
- **Exhaustion**: Once all items are consumed, iterator raises StopIteration
- **Creation**: Use `iter(iterable)` to create an iterator from an iterable
- **Usage**: Use `next(iterator)` to get the next item
- **for Loop**: Automatically handles iterator protocol and StopIteration
- **Common Use Cases**: Processing large files, streaming data, memory-efficient processing
- **Benefits**: Constant memory usage, can handle infinite sequences, faster startup

---

✅ Topic 6 completed. Ready for Topic 7.