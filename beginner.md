---
layout: default
title: Python Beginner (Ages 9-12)
---

# 🚀 Level 2: Python Beginner
### For Aspiring Coders (Ages 9-12)

[← Back to Home](/)

---

## 📦 Lesson 1: Variables - Storing Information

Variables are like labeled boxes where you store information.

```python
# Creating variables
name = "Emma"
age = 10
height = 4.5
is_student = True

# Using variables
print("My name is", name)
print("I am", age, "years old")
print("My height is", height, "feet")
```

### Variable Rules:
- Names can have letters, numbers, and underscores
- Must start with a letter or underscore
- No spaces allowed
- Case sensitive (`Name` and `name` are different)

### 🎯 Practice
```python
# Create variables about yourself
favorite_color = "blue"
favorite_number = 7
pets = 2

print("My favorite color is", favorite_color)
print("My lucky number is", favorite_number)
print("I have", pets, "pets")
```

---

## 🎤 Lesson 2: Getting Input from Users

Let's make programs interactive!

```python
# Ask for user's name
name = input("What is your name? ")
print("Hello,", name + "!")

# Ask for age
age = input("How old are you? ")
print("Wow! You are", age, "years old!")
```

### Making a Conversation Bot
```python
name = input("What's your name? ")
color = input("What's your favorite color? ")
food = input("What's your favorite food? ")

print("\nNice to meet you,", name + "!")
print("I also like the color", color)
print("Yum!", food, "sounds delicious!")
```

### 🎯 Challenge: Age Calculator
```python
name = input("What's your name? ")
age = input("How old are you? ")
age = int(age)  # Convert to number

next_year = age + 1
in_5_years = age + 5

print(name + ", next year you'll be", next_year)
print("In 5 years, you'll be", in_5_years)
```

---

## 🔀 Lesson 3: Making Decisions (If-Else)

Help your program make choices!

```python
age = int(input("How old are you? "))

if age < 13:
    print("You're a kid!")
elif age < 20:
    print("You're a teenager!")
else:
    print("You're an adult!")
```

### Comparison Operators:
- `==` equal to
- `!=` not equal to
- `>` greater than
- `<` less than
- `>=` greater than or equal
- `<=` less than or equal

### Number Guessing Game
```python
secret_number = 7

guess = int(input("Guess a number between 1 and 10: "))

if guess == secret_number:
    print("🎉 Correct! You win!")
elif guess < secret_number:
    print("Too low! Try again.")
else:
    print("Too high! Try again.")
```

### 🎯 Challenge: Grade Calculator
```python
score = int(input("Enter your test score: "))

if score >= 90:
    print("Grade: A - Excellent! 🌟")
elif score >= 80:
    print("Grade: B - Great job! 👍")
elif score >= 70:
    print("Grade: C - Good work! ✓")
elif score >= 60:
    print("Grade: D - Keep trying! 📚")
else:
    print("Grade: F - Study more! 💪")
```

---

## 🔁 Lesson 4: Loops - Repeating Actions

### For Loops (When you know how many times)

```python
# Count to 10
for i in range(1, 11):
    print(i)

# Print a message 5 times
for i in range(5):
    print("Python is fun!")

# Count by 2s
for i in range(0, 20, 2):
    print(i)
```

### Looping Through Words
```python
word = "PYTHON"

for letter in word:
    print(letter)
```

### While Loops (Keep going until something happens)

```python
# Countdown
countdown = 10

while countdown > 0:
    print(countdown)
    countdown = countdown - 1

print("Blast off! 🚀")
```

### 🎯 Practice: Multiplication Table
```python
number = int(input("Which multiplication table? "))

for i in range(1, 11):
    result = number * i
    print(f"{number} x {i} = {result}")
```

---

## 📝 Lesson 5: Lists - Collections of Items

Lists store multiple items in order.

```python
# Create a list
fruits = ["apple", "banana", "orange", "grape"]

# Print the list
print(fruits)

# Access items (starts at 0)
print(fruits[0])  # First item: apple
print(fruits[1])  # Second item: banana
print(fruits[-1]) # Last item: grape

# Add items
fruits.append("mango")
print(fruits)

# Remove items
fruits.remove("banana")
print(fruits)

# Length of list
print("We have", len(fruits), "fruits")
```

### Looping Through Lists
```python
animals = ["dog", "cat", "bird", "fish", "hamster"]

for animal in animals:
    print("I love my", animal)

# With index numbers
for i in range(len(animals)):
    print(f"{i+1}. {animals[i]}")
```

### 🎯 Challenge: To-Do List
```python
tasks = []

print("=== My To-Do List ===")

# Add 3 tasks
for i in range(3):
    task = input(f"Enter task #{i+1}: ")
    tasks.append(task)

print("\n=== Your Tasks ===")
for i, task in enumerate(tasks, 1):
    print(f"{i}. {task}")
```

---

## 🎲 Lesson 6: Random Numbers - Adding Surprise!

```python
import random

# Random number between 1 and 6 (like a dice)
dice = random.randint(1, 6)
print("You rolled a", dice)

# Random choice from a list
colors = ["red", "blue", "green", "yellow"]
random_color = random.choice(colors)
print("Your color is", random_color)

# Shuffle a list
cards = ["A", "K", "Q", "J", "10"]
random.shuffle(cards)
print(cards)
```

### 🎮 Dice Rolling Game
```python
import random

print("=== Dice Rolling Game ===")
input("Press Enter to roll the dice...")

player_roll = random.randint(1, 6)
computer_roll = random.randint(1, 6)

print(f"You rolled: {player_roll}")
print(f"Computer rolled: {computer_roll}")

if player_roll > computer_roll:
    print("🎉 You win!")
elif player_roll < computer_roll:
    print("😢 Computer wins!")
else:
    print("🤝 It's a tie!")
```

---

## ⚙️ Lesson 7: Functions - Reusable Code

Functions are like recipes - write once, use many times!

```python
# Define a function
def greet():
    print("Hello!")
    print("Welcome to Python!")

# Call the function
greet()
greet()  # Can call it many times
```

### Functions with Parameters
```python
def greet_person(name):
    print(f"Hello, {name}!")
    print("Nice to meet you!")

greet_person("Alice")
greet_person("Bob")
greet_person("Charlie")
```

### Functions that Return Values
```python
def add_numbers(a, b):
    result = a + b
    return result

answer = add_numbers(5, 3)
print("5 + 3 =", answer)

# Calculate area of rectangle
def rectangle_area(length, width):
    area = length * width
    return area

my_area = rectangle_area(10, 5)
print("Area:", my_area)
```

### 🎯 Practice: Temperature Converter
```python
def celsius_to_fahrenheit(celsius):
    fahrenheit = (celsius * 9/5) + 32
    return fahrenheit

def fahrenheit_to_celsius(fahrenheit):
    celsius = (fahrenheit - 32) * 5/9
    return celsius

# Test it
temp_c = 25
temp_f = celsius_to_fahrenheit(temp_c)
print(f"{temp_c}°C = {temp_f}°F")

temp_f = 77
temp_c = fahrenheit_to_celsius(temp_f)
print(f"{temp_f}°F = {temp_c}°C")
```

---

## 🎮 Final Project: Complete Number Guessing Game

```python
import random

def play_game():
    print("=== Number Guessing Game ===")
    print("I'm thinking of a number between 1 and 100")
    
    secret = random.randint(1, 100)
    attempts = 0
    max_attempts = 7
    
    while attempts < max_attempts:
        attempts += 1
        remaining = max_attempts - attempts + 1
        
        guess = int(input(f"\nAttempt {attempts}/{max_attempts} - Your guess: "))
        
        if guess == secret:
            print(f"🎉 Congratulations! You found it in {attempts} attempts!")
            return
        elif guess < secret:
            print(f"Too low! {remaining} attempts remaining.")
        else:
            print(f"Too high! {remaining} attempts remaining.")
    
    print(f"\n😢 Game Over! The number was {secret}")

# Play the game
play_game()

# Ask to play again
play_again = input("\nPlay again? (yes/no): ")
if play_again.lower() == "yes":
    play_game()
```

---

## 📚 What You Learned!

✅ Variables and data types  
✅ User input and output  
✅ If-else statements and conditions  
✅ For and while loops  
✅ Lists and basic operations  
✅ Random numbers  
✅ Functions and parameters  

---

## 🚀 Ready for the Next Level?

Awesome work! You've mastered the basics! 🎉

**Next Step:** [Level 3: Intermediate (Ages 13-16)](/intermediate.html)

[← Back to Home](/)
