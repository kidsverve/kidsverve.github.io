---
layout: default
title: Python Basics (Ages 5-8)
---

# 🌟 Level 1: Python Basics
### For Young Explorers (Ages 5-8)

[← Back to Home](/)

---

## 🎨 Lesson 1: What is Python?

Python is like a magic wand! You type special words, and the computer does what you say.

**Why is it called Python?**
It's named after a funny TV show, not the snake! 🐍

---

## 👋 Lesson 2: Say Hello!

Let's make the computer talk!

```python
print("Hello!")
print("My name is Alex")
print("I love Python!")
```

**Try This:**
- Change the words inside the quotes
- Print your name
- Print your favorite color

### 🎯 Challenge
Make the computer say three things about you!

---

## 🔢 Lesson 3: Numbers and Counting

Python is great at math! Let's play with numbers.

```python
# Counting
print(1)
print(2)
print(3)

# Adding numbers
print(2 + 3)
print(5 + 5)

# Subtracting
print(10 - 4)

# Multiplying
print(3 * 4)
```

**Fun Facts:**
- `+` means add
- `-` means subtract  
- `*` means multiply
- `/` means divide

### 🎯 Challenge
```python
# How old will you be in 5 years?
print(7 + 5)  # If you're 7 years old now
```

---

## 🎨 Lesson 4: Drawing with Turtle

Let's draw pictures! Python has a turtle that draws for us.

```python
import turtle

# Create a turtle
t = turtle.Turtle()

# Draw a line
t.forward(100)

# Turn right
t.right(90)

# Draw another line
t.forward(100)

# Keep the window open
turtle.done()
```

### Draw a Square!
```python
import turtle

t = turtle.Turtle()

# Draw 4 sides
t.forward(100)
t.right(90)
t.forward(100)
t.right(90)
t.forward(100)
t.right(90)
t.forward(100)

turtle.done()
```

### Draw a Star! ⭐
```python
import turtle

t = turtle.Turtle()
t.color("gold")

# Draw 5 points
for i in range(5):
    t.forward(100)
    t.right(144)

turtle.done()
```

### 🎯 Challenges
1. Draw a triangle
2. Change the turtle's color: `t.color("blue")`
3. Make the turtle go faster: `t.speed(5)`
4. Draw a circle: `t.circle(50)`

---

## 🌈 Lesson 5: Colors and Fun!

Make your turtle colorful!

```python
import turtle

t = turtle.Turtle()

# Rainbow square
colors = ["red", "orange", "yellow", "green", "blue", "purple"]

for color in colors:
    t.color(color)
    t.forward(100)
    t.right(60)

turtle.done()
```

### Make a Spiral! 🌀
```python
import turtle

t = turtle.Turtle()
t.speed(10)

colors = ["red", "blue", "green", "yellow", "purple", "orange"]

for i in range(100):
    t.color(colors[i % 6])
    t.forward(i * 2)
    t.right(30)

turtle.done()
```

---

## 🎮 Lesson 6: Your First Game!

Let's make the turtle move with keyboard keys!

```python
import turtle

# Setup
screen = turtle.Screen()
screen.title("Move the Turtle!")
t = turtle.Turtle()
t.shape("turtle")

# Functions to move
def move_up():
    t.setheading(90)
    t.forward(20)

def move_down():
    t.setheading(270)
    t.forward(20)

def move_left():
    t.setheading(180)
    t.forward(20)

def move_right():
    t.setheading(0)
    t.forward(20)

# Listen for keys
screen.listen()
screen.onkey(move_up, "Up")
screen.onkey(move_down, "Down")
screen.onkey(move_left, "Left")
screen.onkey(move_right, "Right")

turtle.done()
```

**Use arrow keys to move the turtle!**

---

## 📝 What You Learned!

✅ How to print messages  
✅ How to do math with Python  
✅ How to draw with turtle graphics  
✅ How to use colors  
✅ How to make simple interactive programs  

---

## 🎯 Practice Projects

### Project 1: About Me
```python
print("My name is ________")
print("I am __ years old")
print("My favorite animal is ________")
print("I love to ________")
```

### Project 2: Draw Your House
```python
import turtle

t = turtle.Turtle()

# Draw a square house
for i in range(4):
    t.forward(100)
    t.right(90)

# Draw a triangle roof
t.forward(100)
t.left(120)
t.forward(100)
t.left(120)
t.forward(100)

turtle.done()
```

### Project 3: Colorful Shapes
Create a picture using different colored shapes!

---

## 🚀 Ready for More?

Great job! You're a Python beginner now! 🎉

**Next Step:** [Level 2: Beginner (Ages 9-12)](/beginner.html)

[← Back to Home](/)
