---
layout: default
title: Practice Exercises
---

# ✍️ Practice Exercises
### Challenge Yourself at Every Level

[← Back to Home](/)

---

## 🌟 Basics Exercises (Ages 5-8)

### Exercise 1: Print Your Story
```python
# Complete this program to tell a story about yourself
print("My name is _____")
print("I am _____ years old")
print("My favorite color is _____")
print("I love to play _____")
```

### Exercise 2: Simple Math
```python
# Solve these math problems with Python
print(5 + 3)    # What is 5 + 3?
print(10 - 4)   # What is 10 - 4?
print(3 * 4)    # What is 3 × 4?
print(20 / 5)   # What is 20 ÷ 5?
```

### Exercise 3: Draw a House
```python
import turtle

t = turtle.Turtle()

# Draw the house body (a square)
# Your code here

# Draw the roof (a triangle)
# Your code here

turtle.done()
```

### Exercise 4: Color Pattern
```python
import turtle

t = turtle.Turtle()
colors = ["red", "blue", "green", "yellow"]

# Draw 4 lines, each with a different color
# Your code here

turtle.done()
```

---

## 🚀 Beginner Exercises (Ages 9-12)

### Exercise 1: Even or Odd Checker
```python
# Write a program that asks for a number and tells if it's even or odd
# Your code here
```

**Solution:**
```python
number = int(input("Enter a number: "))
if number % 2 == 0:
    print("Even!")
else:
    print("Odd!")
```

### Exercise 2: Multiplication Table
```python
# Create a multiplication table from 1 to 10 for any number
# Ask the user for a number, then print its multiplication table
# Your code here
```

### Exercise 3: List Operations
```python
# Create a program that:
# 1. Creates a list of your 5 favorite foods
# 2. Prints them all
# 3. Adds a new food
# 4. Removes one food
# 5. Prints the final list

# Your code here
```

### Exercise 4: Simple Calculator
```python
def calculator():
    # Write a calculator that can:
    # - Add two numbers
    # - Subtract two numbers
    # - Multiply two numbers
    # - Divide two numbers
    # Ask the user which operation they want
    
    # Your code here
    pass

calculator()
```

**Solution:**
```python
def calculator():
    print("Simple Calculator")
    print("1. Add")
    print("2. Subtract")
    print("3. Multiply")
    print("4. Divide")
    
    choice = input("Choose operation (1-4): ")
    num1 = float(input("First number: "))
    num2 = float(input("Second number: "))
    
    if choice == '1':
        print(f"Result: {num1 + num2}")
    elif choice == '2':
        print(f"Result: {num1 - num2}")
    elif choice == '3':
        print(f"Result: {num1 * num2}")
    elif choice == '4':
        if num2 != 0:
            print(f"Result: {num1 / num2}")
        else:
            print("Can't divide by zero!")

calculator()
```

### Exercise 5: Password Validator
```python
# Create a program that checks if a password is strong enough:
# - At least 8 characters long
# - Contains at least one number
# - Contains at least one uppercase letter

def is_strong_password(password):
    # Your code here
    pass

# Test your function
test_passwords = ["weak", "Strong123", "noNumbers", "SHORT1"]
for pwd in test_passwords:
    print(f"{pwd}: {is_strong_password(pwd)}")
```

### Exercise 6: FizzBuzz
```python
# Write a program that prints numbers from 1 to 100
# But for multiples of 3, print "Fizz" instead
# For multiples of 5, print "Buzz"
# For multiples of both 3 and 5, print "FizzBuzz"

# Your code here
```

---

## 💎 Intermediate Exercises (Ages 13-16)

### Exercise 1: Dictionary Challenge
```python
# Create a student grade management system
# Use a dictionary to store student names and their grades
# Functions needed:
# - add_student(name, grade)
# - get_average()
# - get_highest_grade()
# - get_lowest_grade()

students = {}

# Your code here
```

**Solution:**
```python
students = {}

def add_student(name, grade):
    students[name] = grade
    print(f"Added {name} with grade {grade}")

def get_average():
    if students:
        return sum(students.values()) / len(students)
    return 0

def get_highest_grade():
    if students:
        return max(students.values())
    return None

def get_lowest_grade():
    if students:
        return min(students.values())
    return None

# Test
add_student("Alice", 95)
add_student("Bob", 87)
add_student("Charlie", 92)

print(f"Average: {get_average()}")
print(f"Highest: {get_highest_grade()}")
print(f"Lowest: {get_lowest_grade()}")
```

### Exercise 2: File Word Counter
```python
# Create a program that:
# 1. Reads a text file
# 2. Counts the number of words
# 3. Finds the most common word
# 4. Saves the statistics to a new file

def analyze_file(filename):
    # Your code here
    pass

# Test it
analyze_file("sample.txt")
```

### Exercise 3: Class Creation - Library System
```python
# Create a Book class with:
# - title, author, isbn, is_available (attributes)
# - borrow() method - marks book as unavailable
# - return_book() method - marks book as available
# - info() method - prints book information

class Book:
    # Your code here
    pass

# Create a Library class that:
# - Stores multiple books
# - Can add books
# - Can search for books by title
# - Can list all available books

class Library:
    # Your code here
    pass

# Test your classes
```

**Solution:**
```python
class Book:
    def __init__(self, title, author, isbn):
        self.title = title
        self.author = author
        self.isbn = isbn
        self.is_available = True
    
    def borrow(self):
        if self.is_available:
            self.is_available = False
            return True
        return False
    
    def return_book(self):
        self.is_available = True
    
    def info(self):
        status = "Available" if self.is_available else "Borrowed"
        print(f"{self.title} by {self.author} - {status}")

class Library:
    def __init__(self):
        self.books = []
    
    def add_book(self, book):
        self.books.append(book)
    
    def search_by_title(self, title):
        for book in self.books:
            if title.lower() in book.title.lower():
                return book
        return None
    
    def list_available(self):
        available = [book for book in self.books if book.is_available]
        for book in available:
            book.info()

# Test
library = Library()
library.add_book(Book("Python Basics", "John Doe", "123"))
library.add_book(Book("Advanced Python", "Jane Smith", "456"))
library.list_available()
```

### Exercise 4: Recursive Functions
```python
# Implement these recursive functions:

def factorial(n):
    # Calculate n! recursively
    # Example: factorial(5) = 5 * 4 * 3 * 2 * 1 = 120
    pass

def fibonacci(n):
    # Return the nth Fibonacci number
    # Sequence: 0, 1, 1, 2, 3, 5, 8, 13...
    pass

def sum_digits(n):
    # Sum all digits in a number recursively
    # Example: sum_digits(123) = 1 + 2 + 3 = 6
    pass

# Test your functions
print(factorial(5))
print(fibonacci(7))
print(sum_digits(123))
```

### Exercise 5: Data Processing
```python
# Given a list of dictionaries representing products:
products = [
    {"name": "Laptop", "price": 1000, "category": "Electronics"},
    {"name": "Phone", "price": 500, "category": "Electronics"},
    {"name": "Shirt", "price": 30, "category": "Clothing"},
    {"name": "Shoes", "price": 80, "category": "Clothing"},
    {"name": "Watch", "price": 200, "category": "Accessories"}
]

# Write functions to:
# 1. Get all products under a certain price
# 2. Get products by category
# 3. Calculate total value of all products
# 4. Find the most expensive product
# 5. Get average price by category

# Your code here
```

---

## 🏆 Advanced Exercises (Ages 17+)

### Exercise 1: Decorator Challenge
```python
# Create a decorator that:
# 1. Logs when a function is called
# 2. Logs the arguments passed
# 3. Logs the return value
# 4. Logs how long the function took to execute

import time
from functools import wraps

def log_function(func):
    # Your code here
    pass

@log_function
def calculate_sum(numbers):
    return sum(numbers)

# Test
calculate_sum([1, 2, 3, 4, 5])
```

**Solution:**
```python
import time
from functools import wraps

def log_function(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        print(f"Arguments: {args}, {kwargs}")
        
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        
        print(f"Return value: {result}")
        print(f"Execution time: {end_time - start_time:.4f} seconds")
        
        return result
    return wrapper

@log_function
def calculate_sum(numbers):
    time.sleep(0.5)  # Simulate work
    return sum(numbers)

calculate_sum([1, 2, 3, 4, 5])
```

### Exercise 2: API Integration
```python
# Create a GitHub user info fetcher that:
# 1. Takes a GitHub username as input
# 2. Fetches user data from GitHub API
# 3. Displays: name, bio, followers, public repos
# 4. Handles errors gracefully

import requests

def get_github_user(username):
    # Your code here
    pass

# Test
get_github_user("torvalds")
```

### Exercise 3: Data Analysis Challenge
```python
# Using pandas, analyze this sales data:
# Create a CSV with columns: Date, Product, Quantity, Price
# Write code to:
# 1. Load the data
# 2. Calculate total revenue per product
# 3. Find the best-selling product
# 4. Calculate revenue by month
# 5. Create a bar chart of revenue by product

import pandas as pd
import matplotlib.pyplot as plt

# Your code here
```

### Exercise 4: Custom Context Manager
```python
# Create a context manager that:
# 1. Opens a file
# 2. Logs when file operations start and end
# 3. Ensures file is closed even if an error occurs

class FileLogger:
    def __init__(self, filename, mode):
        # Your code here
        pass
    
    def __enter__(self):
        # Your code here
        pass
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        # Your code here
        pass

# Test
with FileLogger('test.txt', 'w') as f:
    f.write("Hello, World!")
```

### Exercise 5: Algorithm Challenge - Binary Search
```python
# Implement binary search algorithm
# Input: sorted list and target value
# Output: index of target (or -1 if not found)

def binary_search(arr, target):
    # Your code here
    pass

# Test
numbers = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
print(binary_search(numbers, 7))   # Should return 3
print(binary_search(numbers, 10))  # Should return -1
```

**Solution:**
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = (left + right) // 2
        
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1

# Test
numbers = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
print(binary_search(numbers, 7))   # 3
print(binary_search(numbers, 10))  # -1
```

### Exercise 6: Web Scraper with Error Handling
```python
# Create a web scraper that:
# 1. Scrapes quotes from http://quotes.toscrape.com/
# 2. Extracts quotes, authors, and tags
# 3. Saves to a JSON file
# 4. Handles network errors
# 5. Implements retry logic

from bs4 import BeautifulSoup
import requests
import json
import time

def scrape_quotes(max_pages=3):
    # Your code here
    pass

scrape_quotes()
```

### Exercise 7: Async Task Manager
```python
# Create an async program that:
# 1. Fetches data from multiple URLs concurrently
# 2. Processes each response
# 3. Saves results to separate files
# 4. Reports total time taken

import asyncio
import aiohttp

async def fetch_and_save(url, filename):
    # Your code here
    pass

async def main():
    urls = [
        ('https://api.github.com', 'github.json'),
        ('https://jsonplaceholder.typicode.com/posts', 'posts.json'),
    ]
    
    # Your code here
    pass

# asyncio.run(main())
```

---

## 🎯 Challenge Projects

### Project 1: Password Manager
Build a secure password manager with:
- Master password protection
- Encryption for stored passwords
- Add/retrieve/delete passwords
- Password strength checker
- Auto-generate strong passwords

### Project 2: Weather Dashboard
Create a weather app that:
- Fetches weather data from an API
- Displays current weather and forecast
- Saves favorite locations
- Shows historical data
- Creates visualizations

### Project 3: Personal Finance Tracker
Build an app to:
- Track income and expenses
- Categorize transactions
- Generate monthly reports
- Create charts and graphs
- Export data to CSV/PDF

### Project 4: Mini Social Network
Create a simple social network with:
- User registration and login
- Post creation and editing
- Follow/unfollow users
- Like and comment on posts
- Timeline/feed display

---

## 💡 Tips for Success

1. **Start Small**: Begin with easier exercises and work your way up
2. **Debug Actively**: Use print statements to understand what's happening
3. **Read Error Messages**: They tell you exactly what went wrong
4. **Test Your Code**: Try different inputs to ensure it works
5. **Refactor**: After it works, make it better and cleaner
6. **Compare Solutions**: After solving, look at the provided solution
7. **Ask Questions**: Don't hesitate to seek help when stuck

---

## 📖 More Resources

- [Practice Python](http://www.practicepython.org/)
- [LeetCode](https://leetcode.com/)
- [HackerRank](https://www.hackerrank.com/domains/python)
- [Codewars](https://www.codewars.com/)
- [Project Euler](https://projecteuler.net/)

[← Back to Home](/)
