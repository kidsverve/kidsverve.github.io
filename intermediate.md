---
layout: default
title: Python Intermediate (Ages 13-16)
---

# 💎 Level 3: Python Intermediate
### For Confident Programmers (Ages 13-16)

[← Back to Home](/)

---

## 📖 Lesson 1: String Manipulation

Strings are powerful! Let's explore advanced string operations.

```python
# String methods
text = "Hello, Python World!"

print(text.upper())          # HELLO, PYTHON WORLD!
print(text.lower())          # hello, python world!
print(text.capitalize())     # Hello, python world!
print(text.title())          # Hello, Python World!

# Checking string content
print(text.startswith("Hello"))  # True
print(text.endswith("!"))        # True
print("Python" in text)          # True

# Finding and replacing
print(text.find("Python"))       # 7 (index position)
print(text.replace("World", "Universe"))

# Splitting and joining
words = text.split()
print(words)                     # ['Hello,', 'Python', 'World!']

new_text = "-".join(words)
print(new_text)                  # Hello,-Python-World!
```

### String Formatting
```python
name = "Alex"
age = 15
score = 95.5

# f-strings (modern way)
print(f"My name is {name}, I'm {age} years old")
print(f"Score: {score:.1f}%")  # One decimal place

# format() method
print("My name is {}, I'm {} years old".format(name, age))

# Multiple lines
message = f"""
Hello {name}!
You are {age} years old.
Your score is {score}%.
"""
print(message)
```

### 🎯 Challenge: Text Analyzer
```python
def analyze_text(text):
    print(f"Text: {text}")
    print(f"Length: {len(text)} characters")
    print(f"Words: {len(text.split())} words")
    print(f"Uppercase letters: {sum(1 for c in text if c.isupper())}")
    print(f"Lowercase letters: {sum(1 for c in text if c.islower())}")
    print(f"Digits: {sum(1 for c in text if c.isdigit())}")

analyze_text("Python 3.11 is Awesome!")
```

---

## 📚 Lesson 2: Dictionaries - Key-Value Pairs

Dictionaries store data in key-value pairs.

```python
# Creating a dictionary
student = {
    "name": "Emma",
    "age": 14,
    "grade": "9th",
    "gpa": 3.8,
    "subjects": ["Math", "Science", "English"]
}

# Accessing values
print(student["name"])
print(student.get("age"))

# Adding/updating values
student["email"] = "emma@school.com"
student["age"] = 15

# Removing values
del student["gpa"]
removed = student.pop("grade")

# Checking if key exists
if "email" in student:
    print("Email:", student["email"])

# Looping through dictionaries
for key, value in student.items():
    print(f"{key}: {value}")
```

### Nested Dictionaries
```python
school = {
    "student1": {
        "name": "Alice",
        "grade": 95,
        "subjects": ["Math", "Physics"]
    },
    "student2": {
        "name": "Bob",
        "grade": 88,
        "subjects": ["English", "History"]
    }
}

print(school["student1"]["name"])
print(school["student2"]["subjects"][0])
```

### 🎯 Project: Contact Book
```python
contacts = {}

def add_contact():
    name = input("Name: ")
    phone = input("Phone: ")
    email = input("Email: ")
    contacts[name] = {"phone": phone, "email": email}
    print(f"✓ {name} added!")

def search_contact():
    name = input("Search name: ")
    if name in contacts:
        print(f"Phone: {contacts[name]['phone']}")
        print(f"Email: {contacts[name]['email']}")
    else:
        print("Contact not found!")

def list_contacts():
    if contacts:
        for name, info in contacts.items():
            print(f"{name}: {info['phone']}, {info['email']}")
    else:
        print("No contacts yet!")

# Simple menu
while True:
    print("\n1. Add  2. Search  3. List  4. Quit")
    choice = input("Choose: ")
    
    if choice == "1":
        add_contact()
    elif choice == "2":
        search_contact()
    elif choice == "3":
        list_contacts()
    elif choice == "4":
        break
```

---

## 🗂️ Lesson 3: Sets and Tuples

### Sets (Unique Items, No Order)
```python
# Creating sets
fruits = {"apple", "banana", "orange", "apple"}
print(fruits)  # {'apple', 'banana', 'orange'} - duplicates removed

# Set operations
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

print(set1.union(set2))         # {1, 2, 3, 4, 5, 6}
print(set1.intersection(set2))  # {3, 4}
print(set1.difference(set2))    # {1, 2}

# Adding and removing
fruits.add("grape")
fruits.remove("banana")
```

### Tuples (Immutable Lists)
```python
# Creating tuples
coordinates = (10, 20)
rgb_color = (255, 128, 0)

# Unpacking tuples
x, y = coordinates
r, g, b = rgb_color
print(f"X: {x}, Y: {y}")

# Tuples are immutable (can't change)
# coordinates[0] = 15  # This would cause an error!

# Multiple return values from functions
def get_stats():
    return (100, 85, 92)  # min, max, average

min_val, max_val, avg_val = get_stats()
```

---

## 📁 Lesson 4: File Operations

Reading and writing files is essential!

### Writing to Files
```python
# Write to a file
with open("diary.txt", "w") as file:
    file.write("Dear Diary,\n")
    file.write("Today I learned Python file operations!\n")
    file.write("It's really cool!\n")

# Append to a file
with open("diary.txt", "a") as file:
    file.write("I can't wait to learn more!\n")
```

### Reading from Files
```python
# Read entire file
with open("diary.txt", "r") as file:
    content = file.read()
    print(content)

# Read line by line
with open("diary.txt", "r") as file:
    for line in file:
        print(line.strip())  # strip() removes newline

# Read all lines into a list
with open("diary.txt", "r") as file:
    lines = file.readlines()
    print(lines)
```

### 🎯 Project: Simple Note-Taking App
```python
def save_note():
    note = input("Enter your note: ")
    with open("notes.txt", "a") as file:
        from datetime import datetime
        timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        file.write(f"[{timestamp}] {note}\n")
    print("✓ Note saved!")

def view_notes():
    try:
        with open("notes.txt", "r") as file:
            notes = file.readlines()
            if notes:
                print("\n=== Your Notes ===")
                for note in notes:
                    print(note.strip())
            else:
                print("No notes yet!")
    except FileNotFoundError:
        print("No notes file found!")

# Menu
while True:
    print("\n1. Add Note  2. View Notes  3. Exit")
    choice = input("Choose: ")
    
    if choice == "1":
        save_note()
    elif choice == "2":
        view_notes()
    elif choice == "3":
        break
```

---

## 🎯 Lesson 5: Object-Oriented Programming (OOP)

Classes let you create your own data types!

### Creating Classes
```python
class Dog:
    def __init__(self, name, age, breed):
        self.name = name
        self.age = age
        self.breed = breed
    
    def bark(self):
        print(f"{self.name} says Woof!")
    
    def birthday(self):
        self.age += 1
        print(f"Happy Birthday {self.name}! Now {self.age} years old!")
    
    def info(self):
        print(f"{self.name} is a {self.age} year old {self.breed}")

# Create objects
dog1 = Dog("Buddy", 3, "Golden Retriever")
dog2 = Dog("Max", 5, "Labrador")

# Use methods
dog1.bark()
dog1.info()
dog1.birthday()
```

### More Complex Example: Bank Account
```python
class BankAccount:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance
        self.transactions = []
    
    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            self.transactions.append(f"Deposit: +${amount}")
            print(f"✓ Deposited ${amount}. New balance: ${self.balance}")
        else:
            print("Invalid amount!")
    
    def withdraw(self, amount):
        if amount > 0 and amount <= self.balance:
            self.balance -= amount
            self.transactions.append(f"Withdrawal: -${amount}")
            print(f"✓ Withdrew ${amount}. New balance: ${self.balance}")
        else:
            print("Insufficient funds or invalid amount!")
    
    def get_balance(self):
        print(f"{self.owner}'s balance: ${self.balance}")
        return self.balance
    
    def transaction_history(self):
        print(f"\n=== {self.owner}'s Transactions ===")
        for transaction in self.transactions:
            print(transaction)

# Using the class
account = BankAccount("Alice", 100)
account.deposit(50)
account.withdraw(30)
account.get_balance()
account.transaction_history()
```

### Inheritance
```python
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        pass  # To be overridden

class Cat(Animal):
    def speak(self):
        return f"{self.name} says Meow!"

class Dog(Animal):
    def speak(self):
        return f"{self.name} says Woof!"

# Create instances
cat = Cat("Whiskers")
dog = Dog("Buddy")

print(cat.speak())
print(dog.speak())
```

---

## ⚠️ Lesson 6: Error Handling

Handle errors gracefully!

```python
# Try-except blocks
def safe_divide(a, b):
    try:
        result = a / b
        print(f"{a} / {b} = {result}")
    except ZeroDivisionError:
        print("Error: Can't divide by zero!")
    except TypeError:
        print("Error: Please provide numbers!")

safe_divide(10, 2)   # Works
safe_divide(10, 0)   # Handles error
safe_divide(10, "a") # Handles error
```

### Multiple Exception Types
```python
def get_number_from_user():
    while True:
        try:
            num = int(input("Enter a number: "))
            return num
        except ValueError:
            print("That's not a valid number! Try again.")

number = get_number_from_user()
print(f"You entered: {number}")
```

### Finally Block
```python
def read_file_safely(filename):
    try:
        file = open(filename, "r")
        content = file.read()
        print(content)
    except FileNotFoundError:
        print(f"Error: {filename} not found!")
    except Exception as e:
        print(f"An error occurred: {e}")
    finally:
        try:
            file.close()
            print("File closed.")
        except:
            pass
```

---

## 📦 Lesson 7: Modules and Packages

Organize code into reusable modules!

### Creating Your Own Module
```python
# Save this as math_tools.py
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b

def factorial(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial(n - 1)

PI = 3.14159

# In another file, import and use:
# import math_tools
# print(math_tools.add(5, 3))
# print(math_tools.PI)
```

### Common Built-in Modules
```python
# Math module
import math
print(math.sqrt(16))
print(math.pi)
print(math.ceil(4.3))
print(math.floor(4.7))

# Random module
import random
print(random.randint(1, 100))
print(random.choice(['a', 'b', 'c']))

# Datetime module
from datetime import datetime, timedelta
now = datetime.now()
print(now.strftime("%Y-%m-%d %H:%M:%S"))

tomorrow = now + timedelta(days=1)
print(f"Tomorrow: {tomorrow.date()}")

# OS module
import os
print(os.getcwd())  # Current directory
# os.mkdir("new_folder")  # Create folder
```

---

## 🎮 Final Project: Quiz Game with Scoring

```python
import random
import json

class QuizGame:
    def __init__(self):
        self.questions = [
            {
                "question": "What is the capital of France?",
                "options": ["London", "Berlin", "Paris", "Madrid"],
                "answer": 2
            },
            {
                "question": "What is 2 + 2?",
                "options": ["3", "4", "5", "6"],
                "answer": 1
            },
            {
                "question": "Which planet is known as the Red Planet?",
                "options": ["Venus", "Mars", "Jupiter", "Saturn"],
                "answer": 1
            },
            {
                "question": "What is the largest ocean?",
                "options": ["Atlantic", "Indian", "Arctic", "Pacific"],
                "answer": 3
            }
        ]
        self.score = 0
        self.player_name = ""
    
    def start_game(self):
        print("=== Welcome to the Quiz Game! ===")
        self.player_name = input("Enter your name: ")
        print(f"\nHello {self.player_name}! Let's begin!\n")
        
        random.shuffle(self.questions)
        
        for i, q in enumerate(self.questions, 1):
            self.ask_question(q, i)
        
        self.show_results()
    
    def ask_question(self, question, num):
        print(f"Question {num}: {question['question']}")
        
        for i, option in enumerate(question['options']):
            print(f"  {i + 1}. {option}")
        
        try:
            answer = int(input("Your answer (1-4): "))
            
            if answer - 1 == question['answer']:
                print("✓ Correct!\n")
                self.score += 1
            else:
                correct_answer = question['options'][question['answer']]
                print(f"✗ Wrong! The correct answer was: {correct_answer}\n")
        except (ValueError, IndexError):
            print("✗ Invalid input! No points.\n")
    
    def show_results(self):
        total = len(self.questions)
        percentage = (self.score / total) * 100
        
        print("=" * 40)
        print(f"{self.player_name}'s Results")
        print("=" * 40)
        print(f"Score: {self.score}/{total}")
        print(f"Percentage: {percentage:.1f}%")
        
        if percentage >= 90:
            print("Grade: A - Excellent! 🌟")
        elif percentage >= 80:
            print("Grade: B - Great job! 👍")
        elif percentage >= 70:
            print("Grade: C - Good effort! ✓")
        else:
            print("Grade: D - Keep practicing! 📚")
        
        self.save_score()
    
    def save_score(self):
        try:
            with open("scores.txt", "a") as file:
                from datetime import datetime
                timestamp = datetime.now().strftime("%Y-%m-%d %H:%M")
                file.write(f"{timestamp} - {self.player_name}: {self.score}/{len(self.questions)}\n")
        except Exception as e:
            print(f"Could not save score: {e}")

# Run the game
if __name__ == "__main__":
    game = QuizGame()
    game.start_game()
    
    play_again = input("\nPlay again? (yes/no): ")
    while play_again.lower() == "yes":
        game = QuizGame()
        game.start_game()
        play_again = input("\nPlay again? (yes/no): ")
```

---

## 📚 What You Learned!

✅ Advanced string manipulation  
✅ Dictionaries, sets, and tuples  
✅ File reading and writing  
✅ Object-oriented programming  
✅ Error handling (try-except)  
✅ Modules and imports  
✅ Building complete applications  

---

## 🚀 Ready for Advanced Topics?

Congratulations! You're now an intermediate Python programmer! 🎉

**Next Step:** [Level 4: Advanced (Ages 17+)](/advanced.html)

[← Back to Home](/)
