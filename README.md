# python-interview-questions

# Day 3 – Python Interview Preparation

## Q1. What is the difference between local and global variables in Python?

### Definition

A **local variable** is created inside a function and is normally available only within that function. 

A **global variable** is created outside functions and can be read throughout the module.

### Explanation

Python uses scope to decide where a variable can be accessed. A function can read a global variable, but assigning to a name inside a function makes that name local unless you declare it with `global`. The `global` statement allows a function to reassign a module-level variable.

### Example

```python
count = 10  # Global variable

def show_count():
    message = "The count is"  # Local variable
    print(message, count)

def increase_count():
    global count
    count += 1

show_count()
increase_count()
print(count)
```

### Output

```text
The count is 10
11
```

### Interview Tip

Explain that local names are limited to their function, while global names are defined at module level. A function may read a global name directly, but it needs `global` to reassign that name. Avoid changing globals unnecessarily because it can make code harder to understand and test.

---

## Q2. What is the difference between positional, keyword, and default arguments?

### Definition

- **Positional arguments** are matched to parameters by their position in the function call.
- **Keyword arguments** are matched by parameter name.
- **Default arguments** have a predefined value that is used when the caller omits that argument.

### Explanation

The order matters for positional arguments. Keyword arguments make calls clearer and can be supplied in a different order from the function definition. A parameter with a default value is optional when calling the function. In Python, parameters without defaults must come before parameters with defaults.

### Example

```python
def greet(name, message="Hello"):
    print(message, name)

greet("Alice")  # Positional argument; message uses its default
greet("Bob", "Hi")  # Both arguments are positional
greet(message="Welcome", name="Charlie")  # Keyword arguments
```

### Output

```text
Hello Alice
Hi Bob
Welcome Charlie
```

### Interview Tip

Be ready to identify which value is assigned to each parameter. A call can combine positional and keyword arguments, but positional arguments must come first. Default values are evaluated when the function is defined, so mutable defaults such as lists should generally be avoided.

---

## Q3. What are `*args` and `**kwargs` in Python, and when do we use them?

### Definition

*args  collects extra positional arguments into a tuple. 

**kwargs collects extra keyword arguments into a dictionary.

### Explanation

Use these parameters when a function needs to accept a flexible number of arguments. The names `args` and `kwargs` are conventions; the `*` and `**` symbols provide the behavior. They can also be used when forwarding arguments to another function.

### Example

```python
def add_numbers(*args):
    return sum(args)

def show_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print(add_numbers(1, 2, 3, 4))
show_info(name="Alice", age=25)
```

### Output

```text
10
name: Alice
age: 25
```

### Interview Tip

Remember the collection types: `args` is a tuple and `kwargs` is a dictionary. In a function signature, they are commonly written after regular parameters, with `*args` before `**kwargs`.

---

## Q4. What is the difference between `return` and `print()` in Python?

### Definition

`return` sends a value from a function back to the code that called it. `print()` displays information in the console.

### Explanation

A returned value can be stored in a variable, passed to another function, or used in an expression. Printing displays a value but does not provide it as the function's result. A function with no `return` statement returns `None` by default.

### Example

```python
def add(a, b):
    return a + b

def display_sum(a, b):
    print(a + b)

result = add(2, 3)
print(result)
print(display_sum(2, 3))
```

### Output

```text
5
5
None
```

### Interview Tip

Point out that `return` ends the function call and gives a result to the caller. `print()` is for display and, by itself, returns `None`. Use `return` when later code needs to work with the result.

---

## Q5. What is a lambda function in Python, and how is it different from a normal function?

### Definition

A **lambda function** is a small anonymous function created with the `lambda` keyword. It contains a single expression, whose value is returned automatically.

### Explanation

A regular function is defined with `def` and can contain multiple statements, a descriptive name, and documentation. A lambda is concise and is often useful for a short operation passed to another function. It should not be used for complex logic because a named `def` function is usually easier to read.

### Example

```python
square = lambda number: number * number
print(square(5))

def square_function(number):
    return number * number

print(square_function(5))
```

### Output

```text
25
25
```

### Interview Tip

Mention that a lambda can have multiple parameters but only one expression. It is often used with tools such as `sorted()` or `map()` for brief operations; use `def` when the logic needs multiple steps or a clear reusable name.
