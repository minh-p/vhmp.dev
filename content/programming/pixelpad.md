+++
title = "PixelPad"
draft = false
+++

[PixelPad](https://pixelpad.io/) is a simple 2D game engine for beginners to coding. It's completely free to use.

Python is the programming language that students have to learn.
For any extensive information, check out the PixelPad's official [documentation page](https://pixelpad.io/docs).


## Classes and Objects {#classes-and-objects}

The left panel shows "Classes", "Room", "Sprites", and "Function".

The first class that always exist is called "Game". The class Game will be used by PixelPad's code (which we do not write). A **class**'s purpose is to create an object. Inside each class are two coding environments: "Start" and "Loop".


### Start and Loop {#start-and-loop}

The code put inside "Start" is run when the object is created by calling the class.

Example: you create a class called "Player". You tell the class "Player" to create the object with code that describes the player.

```python
# Game Start
Player()
```

```python
# Player Start
## Nothing yet
```


### Game {#game}

The Game class is always provided. We do not ever call the Game class. Somewhere in the PixelPad's Python code, the Game class is used to create the Game object.


## Variables {#variables}

Variable is the first concept that must be understood.

A **variable** stores some value. In programming languages, you must give variable a valid name. A **value** is of a certain data type.


## Data Types {#data-types}

In Python or any other programming language, every value is of a data type. Below are some basic data types.


### String {#string}

Strings - a group of characters.

```python
name = "hello"
```


#### Character {#character}

A character is any letter or punctuation like the ones you see on your keyboard.


### Numbers {#numbers}


#### Integers {#integers}

These are numbers that are not a decimal.

```python
my_number = 72
```


#### Decimals {#decimals}

Data types that represent decimal numbers include: float and double.
The different between these data types is double can represent more of a decimal number.

In Python the data type float is implemented like a double.

```python
my_decimal_number = 65.2503
```


## Functions {#functions}

Function is a group of code (in a programming language) that can be reused. A function must be given a name. To use a defined function we type the function name and put the parentheses:

```python
# Defining the function
def my_function():
    # do something
    pass # the pass keyword allows an empty function

#Using the function
my_function()
```

The result of the function can be different with the same lines of code.


## Sprite Creation {#sprite-creation}

Create a class called "Player" and add a sprite.

```python
my_player = Player()
my_player.sprite = sprite("image_name.png")
```
