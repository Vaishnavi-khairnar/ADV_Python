# 1️⃣ What is Functional Programming?

## 2️⃣ Simple Definition
Functional Programming is a way of writing code where we use functions as the main building blocks. In this style, we treat functions like special tools that take input and give output without changing anything else. Think of it like using a calculator - you put in numbers, press buttons, and get results without the calculator remembering what you did before.

## 3️⃣ Why This Topic Exists
Python introduced functional programming to help developers write cleaner, shorter, and more readable code. Before functional programming, programmers had to write many lines of code with loops and temporary variables to do simple operations. Functional programming solves this by providing built-in tools that handle common patterns automatically, reducing the chance of errors and making code easier to understand.

## 4️⃣ Real-Life Analogy (MANDATORY)

### The Restaurant Kitchen Analogy
Imagine you're working in a restaurant kitchen:

**Traditional Programming (Imperative Style):**
- You take ingredients from the fridge
- You chop vegetables step by step
- You add them to a pan one by one
- You stir and check temperature constantly
- You remember everything you did in your head

**Functional Programming Style:**
- You have special stations (functions) that do one job perfectly
- You send ingredients to the "chopping station" - it gives back chopped vegetables
- You send those to the "cooking station" - it gives back cooked food
- Each station doesn't remember previous orders - it just does its job
- You can combine stations in different ways without changing them

Just like the kitchen stations, functional programming gives us special tools (functions) that:
- Take input (ingredients)
- Process it (chop, cook, mix)
- Give output (prepared food)
- Don't remember what happened before

This makes cooking (programming) faster, cleaner, and less prone to mistakes!

## 5️⃣ Step-by-Step Explanation

### How Functional Programming Works Internally:

- **Functions are First-Class Citizens**: In Python, functions can be treated like variables - you can pass them as arguments, return them from other functions, and store them in data structures

- **Immutable Data**: Instead of changing existing data, functional programming creates new data. Think of it like making a photocopy instead of writing on the original document

- **Pure Functions**: These are functions that always give the same output for the same input, without side effects (like changing global variables or printing to the screen)

- **Higher-Order Functions**: These are functions that can take other functions as arguments or return functions as results

- **Function Composition**: You can combine small functions to create more complex operations, like connecting building blocks

- **Declarative Style**: Instead of telling Python "how" to do something step-by-step, you just say "what" you want to achieve

## 6️⃣ Basic Syntax Explanation

### Key Concepts in Functional Programming:

```python
# 1. Functions as variables
def greet(name):
    return f"Hello, {name}!"

# Store function in a variable
my_function = greet
result = my_function("Alice")  # Output: "Hello, Alice!"
```
- `def greet(name):` - Defines a function named 'greet' that takes one parameter
- `my_function = greet` - Assigns the function to a variable (no parentheses)
- `my_function("Alice")` - Calls the function through the variable

```python
# 2. Functions as arguments
def apply_operation(func, value):
    return func(value)

def square(x):
    return x * x

result = apply_operation(square, 5)  # Output: 25
```
- `apply_operation(func, value)` - Takes a function and a value as parameters
- `func(value)` - Calls the function that was passed as an argument
- `apply_operation(square, 5)` - Passes the square function as an argument

```python
# 3. Functions returning functions
def get_multiplier(factor):
    def multiply(x):
        return x * factor
    return multiply

double = get_multiplier(2)
result = double(10)  # Output: 20
```
- `get_multiplier(factor)` - Returns a new function based on the factor
- `def multiply(x):` - Inner function that uses the outer function's parameter
- `double = get_multiplier(2)` - Creates a specialized function

## 7️⃣ 10 PRACTICE PROGRAMS (WITH SOLUTION)

### Program 1: Basic Function Assignment
**Question:** Create a function that adds two numbers, assign it to a variable, and call it through the variable.

```python
def add_numbers(a, b):
    return a + b

# Assign function to variable
sum_function = add_numbers

# Call through variable
result = sum_function(5, 3)
print(result)
```
**Output:**
```
8
```
**Explanation:** We assigned the `add_numbers` function to `sum_function` variable and called it through that variable.

### Program 2: Function as Argument
**Question:** Create a function that takes another function and a value, applies the function twice to the value.

```python
def apply_twice(func, value):
    return func(func(value))

def add_five(x):
    return x + 5

result = apply_twice(add_five, 10)
print(result)
```
**Output:**
```
20
```
**Explanation:** `apply_twice` first applies `add_five` to 10 (getting 15), then applies it again to 15 (getting 20).

### Program 3: Function Returning Function
**Question:** Create a function that returns a function that adds a specific number.

```python
def create_adder(n):
    def adder(x):
        return x + n
    return adder

add_ten = create_adder(10)
result = add_ten(5)
print(result)
```
**Output:**
```
15
```
**Explanation:** `create_adder(10)` returns a function that adds 10 to any number, which we store in `add_ten`.

### Program 4: Function List
**Question:** Store multiple functions in a list and call them sequentially.

```python
def greet_hello(name):
    return f"Hello, {name}!"

def greet_hi(name):
    return f"Hi, {name}!"

def greet_hey(name):
    return f"Hey, {name}!"

greetings = [greet_hello, greet_hi, greet_hey]

for greet_func in greetings:
    print(greet_func("Alice"))
```
**Output:**
```
Hello, Alice!
Hi, Alice!
Hey, Alice!
```
**Explanation:** We stored three different greeting functions in a list and called each one in a loop.

### Program 5: Function Dictionary
**Question:** Use functions as values in a dictionary to perform different operations.

```python
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

operations = {
    'add': add,
    'subtract': subtract,
    'multiply': multiply
}

result1 = operations['add'](5, 3)
result2 = operations['multiply'](4, 6)
print(result1, result2)
```
**Output:**
```
8 24
```
**Explanation:** We used operation names as keys to access different functions from the dictionary.

### Program 6: Higher-Order Function with Multiple Functions
**Question:** Create a function that applies multiple functions to a value and returns all results.

```python
def apply_all_functions(funcs, value):
    results = []
    for func in funcs:
        results.append(func(value))
    return results

def square(x):
    return x * x

def cube(x):
    return x * x * x

def double(x):
    return x * 2

functions = [square, cube, double]
results = apply_all_functions(functions, 3)
print(results)
```
**Output:**
```
[9, 27, 6]
```
**Explanation:** We applied three different functions to the value 3 and collected all results in a list.

### Program 7: Function Composition
**Question:** Create a function that composes two functions (applies one after the other).

```python
def compose(f, g):
    return lambda x: f(g(x))

def add_one(x):
    return x + 1

def double(x):
    return x * 2

add_then_double = compose(double, add_one)
double_then_add = compose(add_one, double)

result1 = add_then_double(5)  # (5 + 1) * 2 = 12
result2 = double_then_add(5)  # (5 * 2) + 1 = 11
print(result1, result2)
```
**Output:**
```
12 11
```
**Explanation:** `compose` creates a new function that applies `g` first, then `f`. The order matters!

### Program 8: Conditional Function Selection
**Question:** Create a function that returns different functions based on a condition.

```python
def get_operation(operation_type):
    if operation_type == 'square':
        return lambda x: x * x
    elif operation_type == 'cube':
        return lambda x: x * x * x
    else:
        return lambda x: x

square_func = get_operation('square')
cube_func = get_operation('cube')
identity_func = get_operation('other')

print(square_func(4))
print(cube_func(3))
print(identity_func(10))
```
**Output:**
```
16
27
10
```
**Explanation:** `get_operation` returns different lambda functions based on the input parameter.

### Program 9: Function with State (Closure)
**Question:** Create a function that remembers a value between calls (closure).

```python
def make_counter():
    count = 0
    
    def increment():
        nonlocal count
        count += 1
        return count
    
    return increment

counter1 = make_counter()
counter2 = make_counter()

print(counter1())  # 1
print(counter1())  # 2
print(counter2())  # 1 (separate counter)
print(counter1())  # 3
```
**Output:**
```
1
2
1
3
```
**Explanation:** Each counter function remembers its own `count` value between calls (closure).

### Program 10: Functional Pipeline
**Question:** Create a pipeline of functions that process data step by step.

```python
def pipeline(data, functions):
    result = data
    for func in functions:
        result = func(result)
    return result

def clean_text(text):
    return text.strip().lower()

def remove_spaces(text):
    return text.replace(' ', '')

def add_prefix(text):
    return 'processed_' + text

processing_functions = [clean_text, remove_spaces, add_prefix]
original_text = "  Hello World  "
processed = pipeline(original_text, processing_functions)
print(processed)
```
**Output:**
```
processed_helloworld
```
**Explanation:** The data flows through each function in the pipeline, with each function transforming the result of the previous one.

## 8️⃣ 5 REAL-WORLD PROGRAMS (WITH SOLUTION)

### Program 1: Student Grade Processing
**Problem Statement:** Given a list of student scores, apply different grading functions to calculate final grades.

```python
def apply_grading_curve(scores, curve_function):
    return [curve_function(score) for score in scores]

def standard_curve(score):
    return min(100, score + 5)

def generous_curve(score):
    return min(100, score + 10)

def strict_curve(score):
    return max(0, score - 3)

# Student scores
student_scores = [85, 92, 78, 65, 88, 73]

# Apply different curves
standard_grades = apply_grading_curve(student_scores, standard_curve)
generous_grades = apply_grading_curve(student_scores, generous_curve)
strict_grades = apply_grading_curve(student_scores, strict_curve)

print("Original:", student_scores)
print("Standard:", standard_grades)
print("Generous:", generous_grades)
print("Strict:", strict_grades)
```
**Logic Explanation:** 
- `apply_grading_curve` takes a list of scores and a curve function
- It applies the curve function to each score using a list comprehension
- Different curve functions implement different grading policies
- This demonstrates how functional programming allows flexible data processing

### Program 2: Shopping Bill Calculator
**Problem Statement:** Calculate the total bill for shopping items with different discount functions.

```python
def calculate_total(items, price_func, discount_func):
    subtotal = sum(price_func(item) for item in items)
    final_total = discount_func(subtotal)
    return final_total

def regular_price(item):
    return item['price']

def member_price(item):
    return item['price'] * 0.9  # 10% member discount

def no_discount(total):
    return total

def seasonal_discount(total):
    if total > 100:
        return total * 0.85  # 15% discount for orders over $100
    return total

def loyalty_discount(total):
    return max(0, total - 20)  # $20 flat discount

# Shopping items
cart_items = [
    {'name': 'Shirt', 'price': 30},
    {'name': 'Jeans', 'price': 50},
    {'name': 'Shoes', 'price': 40}
]

# Calculate different totals
regular_total = calculate_total(cart_items, regular_price, no_discount)
member_total = calculate_total(cart_items, member_price, seasonal_discount)
loyalty_total = calculate_total(cart_items, regular_price, loyalty_discount)

print(f"Regular total: ${regular_total:.2f}")
print(f"Member with seasonal discount: ${member_total:.2f}")
print(f"Regular with loyalty discount: ${loyalty_total:.2f}")
```
**Logic Explanation:**
- `calculate_total` takes items, a pricing function, and a discount function
- Pricing functions determine how to calculate item prices (regular vs. member)
- Discount functions apply different discount strategies to the subtotal
- This shows how functional programming enables flexible business logic

### Program 3: Employee Salary Calculator
**Problem Statement:** Calculate employee salaries with different bonus and tax functions.

```python
def calculate_salary(base_salary, bonus_func, tax_func):
    bonus = bonus_func(base_salary)
    gross_salary = base_salary + bonus
    net_salary = tax_func(gross_salary)
    return net_salary

def performance_bonus(base):
    return base * 0.2  # 20% bonus

def holiday_bonus(base):
    return 500  # Fixed $500 bonus

def standard_tax(salary):
    return salary * 0.8  # 20% tax

def senior_tax(salary):
    if salary > 5000:
        return salary * 0.75  # 25% tax for high earners
    return salary * 0.85  # 15% tax for others

# Calculate different salary scenarios
base = 4000

salary1 = calculate_salary(base, performance_bonus, standard_tax)
salary2 = calculate_salary(base, holiday_bonus, senior_tax)
salary3 = calculate_salary(6000, performance_bonus, senior_tax)

print(f"Base ${base} with performance bonus and standard tax: ${salary1:.2f}")
print(f"Base ${base} with holiday bonus and senior tax: ${salary2:.2f}")
print(f"Base $6000 with performance bonus and senior tax: ${salary3:.2f}")
```
**Logic Explanation:**
- `calculate_salary` combines base salary with bonus and tax calculations
- Different bonus functions implement different bonus strategies
- Tax functions handle different tax brackets and rates
- Functional approach makes it easy to mix and match different policies

### Program 4: Bank Transaction Processor
**Problem Statement:** Process bank transactions with different validation and categorization functions.

```python
def process_transactions(transactions, validator, categorizer):
    processed = []
    for transaction in transactions:
        if validator(transaction):
            category = categorizer(transaction)
            processed.append({
                'amount': transaction['amount'],
                'type': transaction['type'],
                'category': category
            })
    return processed

def basic_validator(transaction):
    return transaction['amount'] > 0  # Only positive amounts

def strict_validator(transaction):
    return (transaction['amount'] > 0 and 
            transaction['type'] in ['deposit', 'withdrawal', 'transfer'])

def simple_categorizer(transaction):
    return transaction['type']

def smart_categorizer(transaction):
    amount = transaction['amount']
    t_type = transaction['type']
    
    if t_type == 'deposit':
        return 'income' if amount > 1000 else 'small_income'
    elif t_type == 'withdrawal':
        return 'major_expense' if amount > 500 else 'regular_expense'
    else:
        return 'transfer'

# Sample transactions
transactions = [
    {'amount': 1500, 'type': 'deposit'},
    {'amount': 200, 'type': 'withdrawal'},
    {'amount': 600, 'type': 'withdrawal'},
    {'amount': -50, 'type': 'deposit'},  # Invalid negative amount
    {'amount': 300, 'type': 'transfer'}
]

# Process with different combinations
basic_processed = process_transactions(transactions, basic_validator, simple_categorizer)
strict_processed = process_transactions(transactions, strict_validator, smart_categorizer)

print("Basic processing:")
for t in basic_processed:
    print(f"  ${t['amount']} ({t['type']}) -> {t['category']}")

print("\nStrict processing:")
for t in strict_processed:
    print(f"  ${t['amount']} ({t['type']}) -> {t['category']}")
```
**Logic Explanation:**
- `process_transactions` filters and categorizes transactions using provided functions
- Validator functions determine which transactions are valid
- Categorizer functions assign categories based on different logic
- This demonstrates how functional programming enables flexible data processing pipelines

### Program 5: Website Data Processor
**Problem Statement:** Process website user data with different filtering and transformation functions.

```python
def process_user_data(users, filter_func, transform_func):
    filtered_users = [user for user in users if filter_func(user)]
    transformed_data = [transform_func(user) for user in filtered_users]
    return transformed_data

def active_users_filter(user):
    return user['last_login'] > 30  # Active in last 30 days

def premium_users_filter(user):
    return user['subscription'] == 'premium'

def basic_transform(user):
    return {
        'name': user['name'],
        'email': user['email']
    }

def detailed_transform(user):
    return {
        'name': user['name'],
        'email': user['email'],
        'activity_score': user['posts'] + user['comments'] * 2,
        'engagement_level': 'high' if user['posts'] > 10 else 'medium'
    }

# Sample user data
users = [
    {'name': 'Alice', 'email': 'alice@example.com', 'last_login': 5, 
     'subscription': 'premium', 'posts': 15, 'comments': 25},
    {'name': 'Bob', 'email': 'bob@example.com', 'last_login': 45, 
     'subscription': 'basic', 'posts': 3, 'comments': 8},
    {'name': 'Charlie', 'email': 'charlie@example.com', 'last_login': 15, 
     'subscription': 'premium', 'posts': 8, 'comments': 12},
    {'name': 'Diana', 'email': 'diana@example.com', 'last_login': 60, 
     'subscription': 'basic', 'posts': 1, 'comments': 2}
]

# Process with different combinations
active_basic = process_user_data(users, active_users_filter, basic_transform)
premium_detailed = process_user_data(users, premium_users_filter, detailed_transform)

print("Active users (basic info):")
for user in active_basic:
    print(f"  {user['name']} ({user['email']})")

print("\nPremium users (detailed info):")
for user in premium_detailed:
    print(f"  {user['name']} - Score: {user['activity_score']}, Level: {user['engagement_level']}")
```
**Logic Explanation:**
- `process_user_data` first filters users based on criteria, then transforms the data
- Filter functions determine which users to include (active vs. premium)
- Transform functions shape the output data (basic vs. detailed information)
- This shows how functional programming enables flexible data processing workflows

## 9️⃣ Common Mistakes

### Mistake 1: Confusing Function Reference with Function Call
**Beginner Mistake:** Using parentheses when assigning a function to a variable.

```python
def greet(name):
    return f"Hello, {name}!"

# WRONG - This calls the function and assigns the result
wrong_greeting = greet("World")

# RIGHT - This assigns the function itself
right_greeting = greet
```

**How to Fix:** Remember that `function_name` refers to the function, while `function_name()` calls it.

### Mistake 2: Modifying Data Instead of Creating New Data
**Beginner Mistake:** Changing existing data structures instead of creating new ones.

```python
# WRONG - Modifying the original list
def add_tax_wrong(prices):
    for i in range(len(prices)):
        prices[i] *= 1.1  # Modifies original list
    return prices

# RIGHT - Creates a new list
def add_tax_right(prices):
    return [price * 1.1 for price in prices]  # Creates new list
```

**How to Fix:** Always create new data structures instead of modifying existing ones in functional programming.

### Mistake 3: Using Global Variables in Functions
**Beginner Mistake:** Relying on global state makes functions impure.

```python
# WRONG - Depends on global variable
tax_rate = 0.1

def calculate_tax_wrong(price):
    return price * tax_rate  # Depends on global state

# RIGHT - Pass dependencies as parameters
def calculate_tax_right(price, tax_rate):
    return price * tax_rate  # All dependencies explicit
```

**How to Fix:** Make functions self-contained by passing all dependencies as parameters.

### Mistake 4: Not Handling None/Missing Values
**Beginner Mistake:** Functions that don't handle edge cases properly.

```python
# WRONG - Doesn't handle None
def get_length_wrong(item):
    return len(item)  # Will fail if item is None

# RIGHT - Handles None gracefully
def get_length_right(item):
    if item is None:
        return 0
    return len(item)
```

**How to Fix:** Always consider edge cases and handle None values appropriately.

### Mistake 5: Mixing Imperative and Functional Styles
**Beginner Mistake:** Using loops and temporary variables when functional alternatives exist.

```python
# WRONG - Imperative style with loops
def process_numbers_wrong(numbers):
    result = []
    for num in numbers:
        if num > 0:
            result.append(num * 2)
    return result

# RIGHT - Functional style with comprehensions
def process_numbers_right(numbers):
    return [num * 2 for num in numbers if num > 0]
```

**How to Fix:** Prefer functional constructs like list comprehensions, map, and filter over explicit loops.

## 🔟 Summary (Revision Notes)

- **Functional Programming** treats functions as the main building blocks of code
- **Functions are First-Class Citizens** - can be assigned to variables, passed as arguments, and returned from other functions
- **Pure Functions** always give the same output for the same input without side effects
- **Immutable Data** means creating new data instead of modifying existing data
- **Higher-Order Functions** can take other functions as arguments or return functions
- **Lambda Functions** are small anonymous functions written in a single line
- **Function Composition** allows combining simple functions to create complex operations
- **Closures** are functions that remember values from their enclosing scope
- **Functional Programming Benefits**: cleaner code, fewer bugs, easier testing, better parallelization
- **Key Python Tools**: map(), filter(), reduce(), list comprehensions, lambda expressions

---

✅ Topic 1 completed. Ready for Topic 2.