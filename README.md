# labno4
# Part 1: Defining Functions

# Basic Function
def add_numbers(a, b):
    return a + b

add_lambda = lambda a, b: a + b

# Testing Basic Function
print(add_numbers(3, 5))  # Output: 8
print(add_lambda(3, 5))  # Output: 8

# Flexible Function
def join_words(*words):
    return ' '.join(words)

join_lambda = lambda *words: ' '.join(words)

# Testing Flexible Function
print(join_words("Hello", "world", "!"))  # Output: "Hello world !"
print(join_lambda("Hello", "world", "!"))  # Output: "Hello world !"

# Recursive Function
def countdown(n):
    if n < 0:
        return
    print(n)
    countdown(n-1)

# Testing Recursive Function
countdown(5)  # Output: 5 4 3 2 1 0

# Normal Function Usage
def greet(name):
    return f"Hello, {name}!"

# Testing Normal Function Usage
print(greet("Alice"))  # Output: "Hello, Alice!"

# Function with Default Arguments
def repeat_phrase(phrase, times=2):
    return phrase * times

# Testing Function with Default Arguments
print(repeat_phrase("Hi! "))  # Output: "Hi! Hi! "
print(repeat_phrase("Hi! ", 3))  # Output: "Hi! Hi! Hi! "

# Higher-Order Function
def apply_function(func, value):
    return func(value)

# Testing Higher-Order Function
print(apply_function(lambda x: x.upper(), "hello"))  # Output: "HELLO"

# Part 2: Errors and Exceptions

# Handling Errors
def safe_divide(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        return "Error: Cannot divide by zero"

# Testing Handling Errors
print(safe_divide(4, 2))  # Output: 2.0
print(safe_divide(4, 0))  # Output: "Error: Cannot divide by zero"

# Custom Exceptions
def check_age(age):
    if not isinstance(age, int) or age < 0:
        raise ValueError("Age must be a positive integer")

# Testing Custom Exceptions
try:
    check_age(-1)
except ValueError as e:
    print(e)  # Output: "Age must be a positive integer"

# Handling Multiple Exceptions
def parse_int(value):
    try:
        return int(value)
    except ValueError:
        return "Error: Cannot convert to integer"

# Testing Handling Multiple Exceptions
print(parse_int("123"))  # Output: 123
print(parse_int("abc"))  # Output: "Error: Cannot convert to integer"

# Finally Block
def safe_divide(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        return "Error: Cannot divide by zero"
    finally:
        print("Division attempted")

# Testing Finally Block
print(safe_divide(4, 2))  # Output: 2.0, followed by "Division attempted"
print(safe_divide(4, 0))  # Output: "Error: Cannot divide by zero", followed by "Division attempted"

# Part 3: Iterators

# Using Built-in Iterators
numbers = [5, 4, 3, 2, 1]
it = iter(numbers)
print(next(it))  # Output: 5
print(next(it))  # Output: 4
print(next(it))  # Output: 3
print(next(it))  # Output: 2
print(next(it))  # Output: 1

# Using Generator Expressions
words = ["hello", "world"]
uppercase_words = (word.upper() for word in words)

for word in uppercase_words:
    print(word)
# Output:
# HELLO
# WORLD

# Custom Iterator Class
class Countdown:
    def __init__(self, start):
        self.current = start

    def __iter__(self):
        return self

    def __next__(self):
        if self.current < 0:
            raise StopIteration
        current = self.current
        self.current -= 1
        return current

# Testing Custom Iterator Class
countdown = Countdown(5)
for number in countdown:
    print(number)
# Output:
# 5
# 4
# 3
# 2
# 1
# 0

# Using itertools
import itertools

colors = ["red", "blue", "green"]
color_cycle = itertools.cycle(colors)

for _ in range(6):
    print(next(color_cycle))
# Output:
# red
# blue
# green
# red
# blue
# green
