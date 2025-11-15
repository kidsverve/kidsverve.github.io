---
layout: default
title: Python Advanced (Ages 17+)
---

# 🏆 Level 4: Python Advanced
### For Master Programmers (Ages 17+)

[← Back to Home](/)

---

## 🔧 Lesson 1: Advanced Functions

### Lambda Functions (Anonymous Functions)
```python
# Regular function
def square(x):
    return x ** 2

# Lambda equivalent
square_lambda = lambda x: x ** 2

print(square(5))         # 25
print(square_lambda(5))  # 25

# Lambda with multiple arguments
multiply = lambda x, y: x * y
print(multiply(4, 5))    # 20

# Using lambda with built-in functions
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x ** 2, numbers))
print(squared)  # [1, 4, 9, 16, 25]

evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)    # [2, 4]
```

### Map, Filter, and Reduce
```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]

# Map: Apply function to all items
squares = list(map(lambda x: x ** 2, numbers))

# Filter: Keep only items that match condition
evens = list(filter(lambda x: x % 2 == 0, numbers))

# Reduce: Combine all items into single value
sum_all = reduce(lambda x, y: x + y, numbers)
product = reduce(lambda x, y: x * y, numbers)

print(f"Squares: {squares}")
print(f"Evens: {evens}")
print(f"Sum: {sum_all}")
print(f"Product: {product}")
```

### Decorators
```python
# Simple decorator
def timing_decorator(func):
    import time
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.4f} seconds")
        return result
    return wrapper

@timing_decorator
def slow_function():
    import time
    time.sleep(1)
    return "Done!"

slow_function()

# Decorator with arguments
def repeat(times):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")  # Prints 3 times
```

### Generators
```python
# Generator function
def countdown(n):
    while n > 0:
        yield n
        n -= 1

for num in countdown(5):
    print(num)

# Generator expression
squares_gen = (x ** 2 for x in range(10))
print(list(squares_gen))

# Fibonacci generator
def fibonacci(n):
    a, b = 0, 1
    count = 0
    while count < n:
        yield a
        a, b = b, a + b
        count += 1

for num in fibonacci(10):
    print(num, end=" ")
```

---

## 🗃️ Lesson 2: Advanced Data Structures

### List Comprehensions
```python
# Basic list comprehension
squares = [x ** 2 for x in range(10)]

# With condition
evens = [x for x in range(20) if x % 2 == 0]

# Nested comprehension
matrix = [[i * j for j in range(5)] for i in range(5)]

# Dictionary comprehension
square_dict = {x: x ** 2 for x in range(10)}

# Set comprehension
unique_squares = {x ** 2 for x in [-2, -1, 0, 1, 2]}

# Flattening a list
nested = [[1, 2], [3, 4], [5, 6]]
flat = [item for sublist in nested for item in sublist]
```

### Collections Module
```python
from collections import Counter, defaultdict, deque, namedtuple

# Counter: Count occurrences
text = "hello world"
letter_count = Counter(text)
print(letter_count.most_common(3))

# defaultdict: Dictionary with default values
word_dict = defaultdict(list)
word_dict['fruits'].append('apple')
word_dict['fruits'].append('banana')

# deque: Double-ended queue
queue = deque([1, 2, 3])
queue.appendleft(0)
queue.append(4)
print(queue)

# namedtuple: Tuple with named fields
Point = namedtuple('Point', ['x', 'y'])
p = Point(10, 20)
print(f"X: {p.x}, Y: {p.y}")
```

### Advanced Dictionary Operations
```python
# Dictionary merging (Python 3.9+)
dict1 = {'a': 1, 'b': 2}
dict2 = {'c': 3, 'd': 4}
merged = dict1 | dict2

# Dictionary comprehension with condition
numbers = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
evens_only = {k: v for k, v in numbers.items() if v % 2 == 0}

# Sorting dictionaries
sorted_dict = dict(sorted(numbers.items(), key=lambda x: x[1], reverse=True))
```

---

## 🔗 Lesson 3: Working with APIs

### Making HTTP Requests
```python
import requests
import json

# GET request
def get_weather(city):
    # Example with a public API (OpenWeatherMap - requires API key)
    api_key = "your_api_key_here"
    url = f"http://api.openweathermap.org/data/2.5/weather"
    params = {
        'q': city,
        'appid': api_key,
        'units': 'metric'
    }
    
    response = requests.get(url, params=params)
    
    if response.status_code == 200:
        data = response.json()
        return data
    else:
        return None

# POST request example
def send_data():
    url = "https://jsonplaceholder.typicode.com/posts"
    data = {
        'title': 'My Post',
        'body': 'This is the content',
        'userId': 1
    }
    
    response = requests.post(url, json=data)
    print(response.json())

# Working with JSON
def save_to_json(data, filename):
    with open(filename, 'w') as f:
        json.dump(data, f, indent=4)

def load_from_json(filename):
    with open(filename, 'r') as f:
        return json.load(f)
```

### Creating a Simple REST API with Flask
```python
# Install: pip install flask
from flask import Flask, jsonify, request

app = Flask(__name__)

# In-memory database
books = [
    {'id': 1, 'title': 'Python Basics', 'author': 'John Doe'},
    {'id': 2, 'title': 'Advanced Python', 'author': 'Jane Smith'}
]

@app.route('/api/books', methods=['GET'])
def get_books():
    return jsonify(books)

@app.route('/api/books/<int:book_id>', methods=['GET'])
def get_book(book_id):
    book = next((b for b in books if b['id'] == book_id), None)
    if book:
        return jsonify(book)
    return jsonify({'error': 'Book not found'}), 404

@app.route('/api/books', methods=['POST'])
def add_book():
    new_book = {
        'id': len(books) + 1,
        'title': request.json.get('title'),
        'author': request.json.get('author')
    }
    books.append(new_book)
    return jsonify(new_book), 201

if __name__ == '__main__':
    app.run(debug=True)
```

---

## 🌐 Lesson 4: Web Scraping

### Beautiful Soup Basics
```python
# Install: pip install beautifulsoup4 requests
from bs4 import BeautifulSoup
import requests

def scrape_quotes():
    url = "http://quotes.toscrape.com/"
    response = requests.get(url)
    soup = BeautifulSoup(response.content, 'html.parser')
    
    quotes = soup.find_all('span', class_='text')
    authors = soup.find_all('small', class_='author')
    
    for quote, author in zip(quotes, authors):
        print(f"{quote.text} - {author.text}")

# More advanced scraping
def scrape_table_data(url):
    response = requests.get(url)
    soup = BeautifulSoup(response.content, 'html.parser')
    
    # Find all tables
    tables = soup.find_all('table')
    
    if tables:
        # Get first table
        table = tables[0]
        
        # Extract headers
        headers = [th.text.strip() for th in table.find_all('th')]
        
        # Extract rows
        rows = []
        for tr in table.find_all('tr')[1:]:  # Skip header row
            cells = [td.text.strip() for td in tr.find_all('td')]
            if cells:
                rows.append(cells)
        
        return headers, rows
    
    return None, None
```

---

## 📊 Lesson 5: Data Science Basics

### NumPy - Numerical Computing
```python
# Install: pip install numpy
import numpy as np

# Creating arrays
arr1 = np.array([1, 2, 3, 4, 5])
arr2 = np.zeros((3, 3))
arr3 = np.ones((2, 4))
arr4 = np.arange(0, 10, 2)
arr5 = np.linspace(0, 1, 5)

# Array operations
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(a + b)      # Element-wise addition
print(a * b)      # Element-wise multiplication
print(a.dot(b))   # Dot product

# Statistical operations
data = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])
print(f"Mean: {data.mean()}")
print(f"Median: {np.median(data)}")
print(f"Std Dev: {data.std()}")

# Matrix operations
matrix = np.array([[1, 2], [3, 4]])
print(f"Transpose:\n{matrix.T}")
print(f"Inverse:\n{np.linalg.inv(matrix)}")
```

### Pandas - Data Analysis
```python
# Install: pip install pandas
import pandas as pd

# Creating DataFrames
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David'],
    'Age': [25, 30, 35, 40],
    'City': ['New York', 'London', 'Paris', 'Tokyo'],
    'Salary': [50000, 60000, 70000, 80000]
}

df = pd.DataFrame(data)

# Basic operations
print(df.head())
print(df.describe())
print(df.info())

# Filtering
young_people = df[df['Age'] < 35]
high_earners = df[df['Salary'] > 60000]

# Sorting
sorted_df = df.sort_values('Age', ascending=False)

# Grouping
# grouped = df.groupby('City').mean()

# Reading/Writing CSV
df.to_csv('people.csv', index=False)
df_loaded = pd.read_csv('people.csv')

# Data manipulation
df['Bonus'] = df['Salary'] * 0.1
df['Total'] = df['Salary'] + df['Bonus']
```

### Matplotlib - Data Visualization
```python
# Install: pip install matplotlib
import matplotlib.pyplot as plt
import numpy as np

# Line plot
x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.figure(figsize=(10, 6))
plt.plot(x, y, label='sin(x)')
plt.title('Sine Wave')
plt.xlabel('X')
plt.ylabel('Y')
plt.legend()
plt.grid(True)
plt.savefig('sine_wave.png')
plt.show()

# Multiple plots
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))

ax1.plot(x, np.sin(x))
ax1.set_title('Sine')

ax2.plot(x, np.cos(x), color='red')
ax2.set_title('Cosine')

plt.tight_layout()
plt.show()

# Bar chart
categories = ['A', 'B', 'C', 'D']
values = [23, 45, 56, 78]

plt.bar(categories, values)
plt.title('Bar Chart Example')
plt.show()

# Scatter plot
x = np.random.randn(100)
y = np.random.randn(100)

plt.scatter(x, y, alpha=0.5)
plt.title('Scatter Plot')
plt.show()
```

---

## 🧪 Lesson 6: Testing and Debugging

### Unit Testing with unittest
```python
import unittest

def add(a, b):
    return a + b

def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b

class TestMathFunctions(unittest.TestCase):
    
    def test_add_positive_numbers(self):
        self.assertEqual(add(2, 3), 5)
    
    def test_add_negative_numbers(self):
        self.assertEqual(add(-1, -1), -2)
    
    def test_divide_normal(self):
        self.assertEqual(divide(10, 2), 5)
    
    def test_divide_by_zero(self):
        with self.assertRaises(ValueError):
            divide(10, 0)

if __name__ == '__main__':
    unittest.main()
```

### Using pytest (Modern Testing)
```python
# Install: pip install pytest
# Save as test_math.py

def add(a, b):
    return a + b

def test_add():
    assert add(2, 3) == 5
    assert add(-1, 1) == 0
    assert add(0, 0) == 0

def test_add_strings():
    assert add("hello", "world") == "helloworld"

# Run with: pytest test_math.py
```

### Logging
```python
import logging

# Basic configuration
logging.basicConfig(
    level=logging.DEBUG,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
    filename='app.log'
)

logger = logging.getLogger(__name__)

def calculate(a, b, operation):
    logger.debug(f"Calculating {a} {operation} {b}")
    
    try:
        if operation == '+':
            result = a + b
        elif operation == '-':
            result = a - b
        elif operation == '*':
            result = a * b
        elif operation == '/':
            result = a / b
        else:
            logger.error(f"Unknown operation: {operation}")
            return None
        
        logger.info(f"Result: {result}")
        return result
    
    except Exception as e:
        logger.exception(f"Error occurred: {e}")
        return None

calculate(10, 2, '+')
calculate(10, 0, '/')
```

---

## 🚀 Lesson 7: Async Programming

### Asyncio Basics
```python
import asyncio
import time

# Synchronous version
def sync_task(name, duration):
    print(f"{name} starting...")
    time.sleep(duration)
    print(f"{name} completed!")

# Async version
async def async_task(name, duration):
    print(f"{name} starting...")
    await asyncio.sleep(duration)
    print(f"{name} completed!")

async def main():
    # Run tasks concurrently
    await asyncio.gather(
        async_task("Task 1", 2),
        async_task("Task 2", 1),
        async_task("Task 3", 3)
    )

# Run async code
asyncio.run(main())

# Async web requests
import aiohttp

async def fetch_url(session, url):
    async with session.get(url) as response:
        return await response.text()

async def fetch_multiple():
    urls = [
        'https://api.github.com',
        'https://www.python.org',
        'https://stackoverflow.com'
    ]
    
    async with aiohttp.ClientSession() as session:
        tasks = [fetch_url(session, url) for url in urls]
        results = await asyncio.gather(*tasks)
        return results

# asyncio.run(fetch_multiple())
```

---

## 💾 Lesson 8: Database Operations

### SQLite Database
```python
import sqlite3

class Database:
    def __init__(self, db_name):
        self.conn = sqlite3.connect(db_name)
        self.cursor = self.conn.cursor()
    
    def create_table(self):
        self.cursor.execute('''
            CREATE TABLE IF NOT EXISTS users (
                id INTEGER PRIMARY KEY AUTOINCREMENT,
                name TEXT NOT NULL,
                email TEXT UNIQUE NOT NULL,
                age INTEGER
            )
        ''')
        self.conn.commit()
    
    def insert_user(self, name, email, age):
        try:
            self.cursor.execute(
                "INSERT INTO users (name, email, age) VALUES (?, ?, ?)",
                (name, email, age)
            )
            self.conn.commit()
            return True
        except sqlite3.IntegrityError:
            return False
    
    def get_all_users(self):
        self.cursor.execute("SELECT * FROM users")
        return self.cursor.fetchall()
    
    def get_user_by_email(self, email):
        self.cursor.execute("SELECT * FROM users WHERE email = ?", (email,))
        return self.cursor.fetchone()
    
    def update_user(self, email, new_name, new_age):
        self.cursor.execute(
            "UPDATE users SET name = ?, age = ? WHERE email = ?",
            (new_name, new_age, email)
        )
        self.conn.commit()
    
    def delete_user(self, email):
        self.cursor.execute("DELETE FROM users WHERE email = ?", (email,))
        self.conn.commit()
    
    def close(self):
        self.conn.close()

# Usage
db = Database('myapp.db')
db.create_table()
db.insert_user('Alice', 'alice@example.com', 25)
db.insert_user('Bob', 'bob@example.com', 30)
users = db.get_all_users()
print(users)
db.close()
```

---

## 🎯 Final Project: Task Management System

```python
import sqlite3
from datetime import datetime
import json

class TaskManager:
    def __init__(self, db_name='tasks.db'):
        self.conn = sqlite3.connect(db_name)
        self.cursor = self.conn.cursor()
        self.create_tables()
    
    def create_tables(self):
        self.cursor.execute('''
            CREATE TABLE IF NOT EXISTS tasks (
                id INTEGER PRIMARY KEY AUTOINCREMENT,
                title TEXT NOT NULL,
                description TEXT,
                priority TEXT CHECK(priority IN ('Low', 'Medium', 'High')),
                status TEXT CHECK(status IN ('Pending', 'In Progress', 'Completed')),
                due_date TEXT,
                created_at TEXT,
                completed_at TEXT
            )
        ''')
        self.conn.commit()
    
    def add_task(self, title, description='', priority='Medium', due_date=None):
        created_at = datetime.now().strftime('%Y-%m-%d %H:%M:%S')
        self.cursor.execute('''
            INSERT INTO tasks (title, description, priority, status, due_date, created_at)
            VALUES (?, ?, ?, 'Pending', ?, ?)
        ''', (title, description, priority, due_date, created_at))
        self.conn.commit()
        return self.cursor.lastrowid
    
    def get_all_tasks(self, status=None):
        if status:
            self.cursor.execute('SELECT * FROM tasks WHERE status = ?', (status,))
        else:
            self.cursor.execute('SELECT * FROM tasks')
        return self.cursor.fetchall()
    
    def update_task_status(self, task_id, new_status):
        completed_at = datetime.now().strftime('%Y-%m-%d %H:%M:%S') if new_status == 'Completed' else None
        self.cursor.execute(
            'UPDATE tasks SET status = ?, completed_at = ? WHERE id = ?',
            (new_status, completed_at, task_id)
        )
        self.conn.commit()
    
    def delete_task(self, task_id):
        self.cursor.execute('DELETE FROM tasks WHERE id = ?', (task_id,))
        self.conn.commit()
    
    def get_statistics(self):
        self.cursor.execute('SELECT status, COUNT(*) FROM tasks GROUP BY status')
        stats = dict(self.cursor.fetchall())
        
        self.cursor.execute('SELECT priority, COUNT(*) FROM tasks GROUP BY priority')
        priority_stats = dict(self.cursor.fetchall())
        
        return {
            'status': stats,
            'priority': priority_stats
        }
    
    def export_to_json(self, filename='tasks.json'):
        tasks = self.get_all_tasks()
        task_list = []
        
        for task in tasks:
            task_dict = {
                'id': task[0],
                'title': task[1],
                'description': task[2],
                'priority': task[3],
                'status': task[4],
                'due_date': task[5],
                'created_at': task[6],
                'completed_at': task[7]
            }
            task_list.append(task_dict)
        
        with open(filename, 'w') as f:
            json.dump(task_list, f, indent=4)
    
    def close(self):
        self.conn.close()

def main():
    tm = TaskManager()
    
    while True:
        print("\n=== Task Management System ===")
        print("1. Add Task")
        print("2. View All Tasks")
        print("3. View Pending Tasks")
        print("4. Update Task Status")
        print("5. Delete Task")
        print("6. View Statistics")
        print("7. Export to JSON")
        print("8. Exit")
        
        choice = input("\nChoose an option: ")
        
        if choice == '1':
            title = input("Title: ")
            description = input("Description: ")
            priority = input("Priority (Low/Medium/High): ") or 'Medium'
            due_date = input("Due date (YYYY-MM-DD): ") or None
            task_id = tm.add_task(title, description, priority, due_date)
            print(f"✓ Task {task_id} added!")
        
        elif choice == '2':
            tasks = tm.get_all_tasks()
            if tasks:
                for task in tasks:
                    print(f"\nID: {task[0]}")
                    print(f"Title: {task[1]}")
                    print(f"Status: {task[4]}")
                    print(f"Priority: {task[3]}")
            else:
                print("No tasks found!")
        
        elif choice == '3':
            tasks = tm.get_all_tasks('Pending')
            if tasks:
                for task in tasks:
                    print(f"{task[0]}. {task[1]} [{task[3]}]")
            else:
                print("No pending tasks!")
        
        elif choice == '4':
            task_id = int(input("Task ID: "))
            print("1. Pending  2. In Progress  3. Completed")
            status_choice = input("New status: ")
            status_map = {'1': 'Pending', '2': 'In Progress', '3': 'Completed'}
            if status_choice in status_map:
                tm.update_task_status(task_id, status_map[status_choice])
                print("✓ Status updated!")
        
        elif choice == '5':
            task_id = int(input("Task ID to delete: "))
            tm.delete_task(task_id)
            print("✓ Task deleted!")
        
        elif choice == '6':
            stats = tm.get_statistics()
            print("\nStatus Statistics:")
            for status, count in stats['status'].items():
                print(f"  {status}: {count}")
            print("\nPriority Statistics:")
            for priority, count in stats['priority'].items():
                print(f"  {priority}: {count}")
        
        elif choice == '7':
            filename = input("Filename (default: tasks.json): ") or 'tasks.json'
            tm.export_to_json(filename)
            print(f"✓ Exported to {filename}!")
        
        elif choice == '8':
            tm.close()
            print("Goodbye!")
            break

if __name__ == '__main__':
    main()
```

---

## 📚 What You Mastered!

✅ Advanced functions (lambda, decorators, generators)  
✅ Advanced data structures and comprehensions  
✅ Working with APIs and web scraping  
✅ Data science libraries (NumPy, Pandas, Matplotlib)  
✅ Testing and debugging best practices  
✅ Async programming with asyncio  
✅ Database operations with SQLite  
✅ Building complete, production-ready applications  

---

## 🎓 Next Steps

Congratulations on completing the advanced level! 🎉

### Continue Your Journey:
- **Contribute to Open Source**: Find projects on GitHub
- **Build Your Portfolio**: Create real-world applications
- **Learn Frameworks**: Django, FastAPI, PyTorch, TensorFlow
- **Specialize**: Web Development, Data Science, Machine Learning, DevOps
- **Get Certified**: Python certifications from recognized organizations

### Recommended Resources:
- [Real Python](https://realpython.com/)
- [Python Documentation](https://docs.python.org/)
- [Python Package Index (PyPI)](https://pypi.org/)
- [GitHub Trending Python](https://github.com/trending/python)

[← Back to Home](/)
