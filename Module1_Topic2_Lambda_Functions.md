# 2️⃣ Lambda Functions

## 2️⃣ Simple Definition
Lambda functions are small, anonymous functions that you can write in just one line of code. Think of them as shortcuts for creating simple functions without giving them a name. They're like sticky notes - you write a quick reminder, use it once, and then throw it away.

## 3️⃣ Why This Topic Exists
Python introduced lambda functions to help developers write shorter, cleaner code when they need simple functions for a short time. Before lambda functions, programmers had to define full functions with `def` even for very simple operations like adding two numbers or checking if a value is positive. Lambda functions solve this by letting you create quick functions right where you need them, making code more readable and concise.

## 4️⃣ Real-Life Analogy (MANDATORY)

### The Disposable Calculator Analogy
Imagine you need to do a quick calculation:

**Regular Function (Like a Scientific Calculator):**
- You buy a scientific calculator (define a function)
- You give it a name and store it in your drawer
- You can use it many times
- It takes up space and requires maintenance

**Lambda Function (Like a Disposable Calculator):**
- You grab a scrap paper and write a simple formula
- You use it immediately for your calculation
- You throw it away when done
- No storage needed, no maintenance required

**When to Use Which:**
- Use the scientific calculator for complex, repeated calculations
- Use the disposable paper for quick, one-time calculations

In Python:
- Use `def` for complex functions you'll use multiple times
- Use `lambda` for simple functions you need just once

Just like you wouldn't buy a new calculator for every simple addition, you don't need a full function definition for every simple operation in your code!

## 5️⃣ Step-by-Step Explanation

### How Lambda Functions Work Internally:

- **Anonymous Nature**: Lambda functions don't have names - they're created and used immediately
- **Single Expression**: They can only contain one expression, not multiple statements
- **Automatic Return**: The result of the expression is automatically returned (no `return` keyword needed)
- **Memory Efficiency**: They're more memory-efficient than regular functions for simple operations
- **Creation Speed**: Python creates lambda functions faster than regular functions
- **Syntax Simplicity**: The syntax is `lambda arguments: expression` - much shorter than `def`

### Internal Processing:
1. Python sees the `lambda` keyword
2. It creates a function object in memory
3. It stores the expression logic without naming the function
4. The function can be used immediately or assigned to a variable
5. After use, it can be garbage collected like any other object

## 6️⃣ Basic Syntax Explanation

### Lambda Function Syntax:

```python
# Basic lambda syntax
lambda arguments: expression
```

- `lambda` - Keyword that tells Python we're creating an anonymous function
- `arguments` - Input values the function accepts (like function parameters)
- `:` - Separates arguments from the expression
- `expression` - The calculation or operation to perform (automatically returned)

### Example 1: Simple Lambda
```python
# Regular function
def add_five(x):
    return x + 5

# Equivalent lambda function
add_five_lambda = lambda x: x + 5

print(add_five_lambda(10))  # Output: 15
```
- `lambda x:` - Takes one argument named `x`
- `x + 5` - The expression that adds 5 to x
- The result is automatically returned

### Example 2: Multiple Arguments
```python
# Regular function
def multiply(a, b):
    return a * b

# Equivalent lambda function
multiply_lambda = lambda a, b: a * b

print(multiply_lambda(4, 5))  # Output: 20
```
- `lambda a, b:` - Takes two arguments `a` and `b`
- `a * b` - Multiplies the two arguments
- No `return` keyword needed

### Example 3: Lambda with No Arguments
```python
# Regular function
def get_pi():
    return 3.14159

# Equivalent lambda function
pi_lambda = lambda: 3.14159

print(pi_lambda())  # Output: 3.14159
```
- `lambda:` - No arguments needed
- `3.14159` - Returns the constant value
- Still need parentheses when calling

### Example 4: Conditional Expression in Lambda
```python
# Regular function
def absolute_value(x):
    if x >= 0:
        return x
    else:
        return -x

# Equivalent lambda function
abs_lambda = lambda x: x if x >= 0 else -x

print(abs_lambda(-5))   # Output: 5
print(abs_lambda(10))   # Output: 10
```
- `lambda x:` - Takes one argument
- `x if x >= 0 else -x` - Ternary conditional expression
- Returns x if positive, otherwise returns -x

## 7️⃣ 10 PRACTICE PROGRAMS (WITH SOLUTION)

### Program 1: Basic Lambda Addition
**Question:** Create a lambda function that adds two numbers.

```python
add = lambda x, y: x + y
result = add(5, 3)
print(result)
```
**Output:**
```
8
```
**Explanation:** The lambda takes two arguments and returns their sum.

### Program 2: Lambda for Squaring
**Question:** Create a lambda function that squares a number.

```python
square = lambda x: x * x
print(square(4))
print(square(7))
```
**Output:**
```
16
49
```
**Explanation:** The lambda multiplies the input by itself to square it.

### Program 3: Lambda for Even/Odd Check
**Question:** Create a lambda function that returns "Even" for even numbers and "Odd" for odd numbers.

```python
even_odd = lambda x: "Even" if x % 2 == 0 else "Odd"
print(even_odd(10))
print(even_odd(7))
```
**Output:**
```
Even
Odd
```
**Explanation:** Uses modulo operator to check divisibility by 2 and returns appropriate string.

### Program 4: Lambda for String Operations
**Question:** Create a lambda function that converts a string to uppercase and adds exclamation mark.

```python
excited = lambda s: s.upper() + "!"
print(excited("hello"))
print(excited("python"))
```
**Output:**
```
HELLO!
PYTHON!
```
**Explanation:** The lambda converts string to uppercase and concatenates exclamation mark.

### Program 5: Lambda for List Length Check
**Question:** Create a lambda function that returns "Long" if list has more than 5 items, otherwise "Short".

```python
list_size = lambda lst: "Long" if len(lst) > 5 else "Short"
print(list_size([1, 2, 3, 4, 5, 6, 7]))
print(list_size([1, 2, 3]))
```
**Output:**
```
Long
Short
```
**Explanation:** Uses len() function to check list size and returns appropriate label.

### Program 6: Lambda for Temperature Conversion
**Question:** Create a lambda function that converts Celsius to Fahrenheit.

```python
c_to_f = lambda c: (c * 9/5) + 32
print(c_to_f(0))
print(c_to_f(100))
print(c_to_f(25))
```
**Output:**
```
32.0
212.0
77.0
```
**Explanation:** Applies the formula F = (C × 9/5) + 32 to convert temperature.

### Program 7: Lambda for Discount Calculation
**Question:** Create a lambda function that calculates price after applying a discount percentage.

```python
apply_discount = lambda price, discount: price * (1 - discount/100)
print(apply_discount(100, 10))  # 10% discount
print(apply_discount(50, 25))   # 25% discount
```
**Output:**
```
90.0
37.5
```
**Explanation:** Calculates discounted price by multiplying by (1 - discount/100).

### Program 8: Lambda for Age Classification
**Question:** Create a lambda function that classifies age as "Child", "Adult", or "Senior".

```python
age_group = lambda age: "Child" if age < 18 else "Adult" if age < 65 else "Senior"
print(age_group(12))
print(age_group(25))
print(age_group(70))
```
**Output:**
```
Child
Adult
Senior
```
**Explanation:** Uses nested ternary operators to classify age into three groups.

### Program 9: Lambda for String Reversal
**Question:** Create a lambda function that reverses a string.

```python
reverse_string = lambda s: s[::-1]
print(reverse_string("hello"))
print(reverse_string("python"))
```
**Output:**
```
olleh
nohtyp
```
**Explanation:** Uses string slicing with step -1 to reverse the string.

### Program 10: Lambda for Grade Calculation
**Question:** Create a lambda function that converts numeric score to letter grade.

```python
grade = lambda score: "A" if score >= 90 else "B" if score >= 80 else "C" if score >= 70 else "D" if score >= 60 else "F"
print(grade(95))
print(grade(85))
print(grade(75))
print(grade(55))
```
**Output:**
```
A
B
C
F
```
**Explanation:** Uses multiple ternary conditions to assign letter grades based on score ranges.

## 8️⃣ 5 REAL-WORLD PROGRAMS (WITH SOLUTION)

### Program 1: Student Grade Processing
**Problem Statement:** Process a list of student scores and apply different grading curves using lambda functions.

```python
# Student scores
student_scores = [85, 92, 78, 65, 88, 73, 95, 81]

# Different grading curves using lambda
standard_curve = lambda score: min(100, score + 5)
generous_curve = lambda score: min(100, score + 10)
strict_curve = lambda score: max(0, score - 3)

# Apply curves to all scores
standard_grades = list(map(standard_curve, student_scores))
generous_grades = list(map(generous_curve, student_scores))
strict_grades = list(map(strict_curve, student_scores))

print("Original scores:", student_scores)
print("Standard curve:", standard_grades)
print("Generous curve:", generous_grades)
print("Strict curve:", strict_grades)
```
**Logic Explanation:**
- `standard_curve` adds 5 points to each score (capped at 100)
- `generous_curve` adds 10 points to each score (capped at 100)
- `strict_curve` subtracts 3 points from each score (minimum 0)
- `map()` function applies each lambda to all scores in the list
- Demonstrates how lambda functions enable flexible data transformation

### Program 2: Shopping Bill Calculator
**Problem Statement:** Calculate total bills for different customer types using lambda functions for discounts.

```python
# Shopping items
items = [
    {'name': 'Shirt', 'price': 30},
    {'name': 'Jeans', 'price': 50},
    {'name': 'Shoes', 'price': 40},
    {'name': 'Hat', 'price': 15}
]

# Calculate subtotal
subtotal = sum(item['price'] for item in items)

# Different discount calculations using lambda
regular_discount = lambda total: total * 0.95  # 5% discount
member_discount = lambda total: total * 0.85  # 15% discount
vip_discount = lambda total: max(0, total - 20)  # $20 flat discount

# Apply different discounts
regular_total = regular_discount(subtotal)
member_total = member_discount(subtotal)
vip_total = vip_discount(subtotal)

print(f"Subtotal: ${subtotal:.2f}")
print(f"Regular customer: ${regular_total:.2f}")
print(f"Member customer: ${member_total:.2f}")
print(f"VIP customer: ${vip_total:.2f}")
```
**Logic Explanation:**
- `regular_discount` applies 5% discount (multiply by 0.95)
- `member_discount` applies 15% discount (multiply by 0.85)
- `vip_discount` applies $20 flat discount with minimum of $0
- Lambda functions make discount logic concise and easy to modify
- Shows how lambda functions simplify business rule implementation

### Program 3: Employee Salary Calculator
**Problem Statement:** Calculate net salaries for employees with different bonus and tax structures using lambda functions.

```python
# Employee data
employees = [
    {'name': 'Alice', 'base_salary': 5000, 'performance': 'excellent'},
    {'name': 'Bob', 'base_salary': 4000, 'performance': 'good'},
    {'name': 'Charlie', 'base_salary': 6000, 'performance': 'average'},
    {'name': 'Diana', 'base_salary': 3500, 'performance': 'excellent'}
]

# Bonus calculations using lambda
bonus_calculator = lambda base, perf: (
    base * 0.2 if perf == 'excellent' else
    base * 0.1 if perf == 'good' else
    base * 0.05
)

# Tax calculations using lambda
tax_calculator = lambda gross: (
    gross * 0.7 if gross > 6000 else
    gross * 0.8 if gross > 4000 else
    gross * 0.85
)

# Calculate salaries for each employee
for emp in employees:
    bonus = bonus_calculator(emp['base_salary'], emp['performance'])
    gross_salary = emp['base_salary'] + bonus
    net_salary = tax_calculator(gross_salary)
    
    print(f"{emp['name']}: Base=${emp['base_salary']}, Bonus=${bonus:.2f}, Net=${net_salary:.2f}")
```
**Logic Explanation:**
- `bonus_calculator` uses nested ternary operators to calculate bonus based on performance
- `tax_calculator` applies different tax rates based on gross salary ranges
- Lambda functions encapsulate complex business rules in single lines
- Demonstrates how lambda functions can handle conditional logic efficiently

### Program 4: Bank Transaction Processor
**Problem Statement:** Categorize and process bank transactions using lambda functions for validation and categorization.

```python
# Bank transactions
transactions = [
    {'amount': 1500, 'type': 'deposit', 'description': 'Salary'},
    {'amount': 200, 'type': 'withdrawal', 'description': 'Shopping'},
    {'amount': 600, 'type': 'withdrawal', 'description': 'Rent'},
    {'amount': 300, 'type': 'transfer', 'description': 'To friend'},
    {'amount': 50, 'type': 'withdrawal', 'description': 'Coffee'}
]

# Validation function using lambda
is_valid_transaction = lambda t: t['amount'] > 0 and t['type'] in ['deposit', 'withdrawal', 'transfer']

# Categorization function using lambda
categorize_transaction = lambda t: (
    'income' if t['type'] == 'deposit' and t['amount'] > 1000 else
    'small_income' if t['type'] == 'deposit' else
    'major_expense' if t['type'] == 'withdrawal' and t['amount'] > 500 else
    'regular_expense' if t['type'] == 'withdrawal' else
    'transfer'
)

# Process transactions
valid_transactions = list(filter(is_valid_transaction, transactions))
categorized_transactions = [
    {**t, 'category': categorize_transaction(t)} for t in valid_transactions
]

print("Valid and categorized transactions:")
for t in categorized_transactions:
    print(f"${t['amount']} {t['type']} ({t['description']}) -> {t['category']}")
```
**Logic Explanation:**
- `is_valid_transaction` validates transactions using logical conditions
- `categorize_transaction` assigns categories based on amount and type
- `filter()` uses lambda to keep only valid transactions
- Dictionary comprehension adds category to each transaction
- Shows how lambda functions work well with functional programming tools

### Program 5: Website User Data Processor
**Problem Statement:** Process website user data to identify active and engaged users using lambda functions.

```python
# Website user data
users = [
    {'name': 'Alice', 'last_login': 5, 'posts': 15, 'comments': 25, 'subscription': 'premium'},
    {'name': 'Bob', 'last_login': 45, 'posts': 3, 'comments': 8, 'subscription': 'basic'},
    {'name': 'Charlie', 'last_login': 15, 'posts': 8, 'comments': 12, 'subscription': 'premium'},
    {'name': 'Diana', 'last_login': 60, 'posts': 1, 'comments': 2, 'subscription': 'basic'},
    {'name': 'Eve', 'last_login': 3, 'posts': 20, 'comments': 30, 'subscription': 'premium'}
]

# Activity calculation using lambda
calculate_activity_score = lambda posts, comments: posts + (comments * 2)

# Engagement level using lambda
engagement_level = lambda score: 'high' if score > 50 else 'medium' if score > 20 else 'low'

# User filtering using lambda
is_active_user = lambda user: user['last_login'] < 30
is_premium_user = lambda user: user['subscription'] == 'premium'

# Process users
active_users = list(filter(is_active_user, users))
premium_users = list(filter(is_premium_user, users))

# Add calculated fields to users
processed_users = [
    {
        **user,
        'activity_score': calculate_activity_score(user['posts'], user['comments']),
        'engagement': engagement_level(calculate_activity_score(user['posts'], user['comments']))
    }
    for user in users
]

print("All users with activity scores:")
for user in processed_users:
    print(f"{user['name']}: Score={user['activity_score']}, Engagement={user['engagement']}")

print(f"\nActive users: {len(active_users)}")
print(f"Premium users: {len(premium_users)}")
```
**Logic Explanation:**
- `calculate_activity_score` weights comments more than posts (2x)
- `engagement_level` categorizes users based on activity score
- `is_active_user` and `is_premium_user` filter users based on criteria
- Dictionary comprehension adds calculated fields to each user
- Demonstrates how lambda functions enable complex data processing pipelines

## 9️⃣ Common Mistakes

### Mistake 1: Using Statements Instead of Expressions
**Beginner Mistake:** Trying to use multiple statements or assignments in lambda functions.

```python
# WRONG - Lambda can't contain statements
wrong_lambda = lambda x: y = x + 5; return y

# RIGHT - Lambda must be a single expression
right_lambda = lambda x: x + 5
```

**How to Fix:** Remember that lambda functions can only contain expressions, not statements. Use regular functions for complex logic.

### Mistake 2: Forgetting to Assign Lambda to Variable
**Beginner Mistake:** Creating a lambda but not storing or using it immediately.

```python
# WRONG - Lambda is created but lost
lambda x: x * 2  # This lambda is immediately garbage collected

# RIGHT - Assign to variable or use immediately
double = lambda x: x * 2
print(double(5))

# OR use immediately
print((lambda x: x * 2)(5))
```

**How to Fix:** Either assign the lambda to a variable or use it immediately after creation.

### Mistake 3: Overcomplicating Lambda Functions
**Beginner Mistake:** Making lambda functions too complex and hard to read.

```python
# WRONG - Too complex for a lambda
complex_lambda = lambda x: x * 2 if x > 10 else x * 3 if x > 5 else x * 4

# RIGHT - Use regular function for complex logic
def complex_function(x):
    if x > 10:
        return x * 2
    elif x > 5:
        return x * 3
    else:
        return x * 4
```

**How to Fix:** Use regular functions for complex logic. Keep lambdas simple and readable.

### Mistake 4: Using Lambda When Regular Function is Better
**Beginner Mistake:** Using lambda functions when a regular function would be more appropriate.

```python
# WRONG - Lambda assigned to a variable for repeated use
add = lambda x, y: x + y  # Better as a regular function

# RIGHT - Use regular function for named, reusable functions
def add(x, y):
    return x + y

# RIGHT - Use lambda for one-time operations
result = list(map(lambda x: x + 1, numbers))
```

**How to Fix:** Use regular functions for named, reusable code. Use lambdas for simple, one-time operations.

### Mistake 5: Not Understanding Lambda Scope
**Beginner Mistake:** Misunderstanding how lambda functions capture variables from their environment.

```python
# WRONG - Common pitfall with loops
functions = []
for i in range(5):
    functions.append(lambda x: x + i)  # All lambdas capture the same i (which becomes 4)

# RIGHT - Capture current value with default argument
functions = []
for i in range(5):
    functions.append(lambda x, i=i: x + i)  # Each lambda gets its own i
```

**How to Fix:** Be careful with variable capture in closures. Use default arguments to capture current values.

## 🔟 Summary (Revision Notes)

- **Lambda Functions** are small, anonymous functions written in a single line
- **Syntax**: `lambda arguments: expression`
- **Anonymous**: No function name, created and used immediately
- **Single Expression**: Can only contain one expression, not multiple statements
- **Automatic Return**: The expression result is automatically returned
- **Multiple Arguments**: Can accept multiple arguments separated by commas
- **Conditional Expressions**: Can use ternary operators for conditional logic
- **Common Use Cases**: Short functions for map(), filter(), sorted(), etc.
- **Memory Efficient**: More efficient than regular functions for simple operations
- **Readability**: Keep lambdas simple - use regular functions for complex logic
- **Best Practices**: Use for simple, one-time operations; use regular functions for complex logic

---

✅ Topic 2 completed. Ready for Topic 3.