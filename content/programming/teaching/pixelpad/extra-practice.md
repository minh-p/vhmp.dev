+++
title = "Practice"
draft = false
+++

## Additional Practice {#additional-practice}

In this page are exercise prompts and solutions to practice concepts. They are project-agnostic, which means that exercises do not correspond to any long-term project. Rather, students are given initial instructions to setup their exercise and their job will be finish any section marked `TODO`.


## Sprite Creation and Movement With Inputs {#sprite-creation-and-movement-with-inputs}


### Create an Apple (Easy) {#create-an-apple--easy}

First, create a new `sprite` by clicking on the `+` and find apple. Name this sprite `Apple.png`. Then, create a class and name it `Apple`. Remember that classes creates objects according to the code you give in `Start` and `Loop`. Each object can hold only one single `sprite`. A `sprite` is just an image. While a `sprite object` is a coding object returned by the function `sprite`. The function `sprite`, the `sprite object`, and a `sprite` are three different things.

{{< figure src="/ox-hugo/apple-setup.png" >}}

Then, we're first going to be coding in `Game Start`. Go ahead and tell the class `Apple` to create an object. Do you remember how to do it? If not, don't look at the solution before reviewing the [create a sprite activity]({{< relref "/programming/teaching/pixelpad/#activity-creating-a-sprite" >}}).

{{% details title="Solution - Calling class Apple" %}}
```python { filename="Game Start" }
apple = Apple()
```

Note that you don't have to make a variable to keep track of the object the class `Apple` creates.

Here's an alternative solution that doesn't create a variable.

```python { filename="Game Start" }
Apple()
```
{{% /details %}}

Next, we're going to code the class `Apple`. Right now, we're only telling the class `Apple` to run the code inside `Apple Start` and `Apple Loop`, which there's nothing in there.

Here are a few review questions to get you started.

1.  What's the difference between the code that you put inside `Start` versus the code you put inside `Loop`?

    {{% details title="Solution - Start vs. Loop" %}}
    The code you put inside `Loop` will run multiple times. Specifically, pixelPad will try to run it 60 times a second. This means you can redraw things on the screen 60 times a second. The code you put inside `Start` will only run one time.
    {{% /details %}}
2.  Inside `Apple Start` and `Apple Loop`, what is the variable that keeps track of the object the class `Apple` is creating?

    {{% details title="Solution - Variable Refering to Object Created By the Class Apple" %}}
    This variable is called `self`.
    {{% /details %}}
3.  What are some variables that are inside an object created by a pixelPAD class and how do you access and change them?

    {{% details title="Solution - Variables inside pixelpad objects" %}}
    These variables, or more specifically built-in object variables can be found at the bottom of the pixelPad documentation page on objects.

    <https://pixelpad.io/docs/?c=objects>

    Some of them are: x, y, z, sprite, scaleX, scaleY, skewX...

    Let us say we want to change the variable sprite, we have to first access the object being created by the class through the variable `self`.

    ```python { filename="Apple Start" }
    self.sprite = ...
    ```

    The `...` means you still have to write something there for the code to work but this solution is not including it. What you have to write here you'll be tasked of in the next question.
    {{% /details %}}
4.  What is a `value`? What keeps track of a `value` in Python? What `value` do you assign to the object variable `sprite`? What `function` creates that value?

    {{% details title="Solution - Working with variable sprite" %}}
    Here, we're assigning a `sprite object` to the variable `sprite` of the object the class `Apple` is creating. The `sprite object` is created with the function `sprite`. The function `sprite` needs at minimum a `string value` which is the name of the `sprite` for it to create and return a `sprite object`.

    ```python { filename="Apple Start" }
    self.sprite = sprite("Image.png")
    ```
    {{% /details %}}

With this, you should be able to put an apple on the screen.

{{% details title="Full Solution" %}}
```python { filename="Game Start" }
Apple()
```

```python { filename="Apple Start" }
self.sprite = sprite("Apple.png")
```
{{% /details %}}

Here's an additional challenge:

How would you assign the `sprite object` to the variable `sprite` of the object created by the class `Apple` without writing any code in `Apple Start` or `Apple Loop`?

{{% details title="Solution - Without Apple Start and Apple Loop" %}}
You can set the variable `sprite` anywhere if you have access to the `variable` that keeps track of the `object` created by the class `Apple`.

```python { filename="Game Start" }
apple = Apple()
apple.sprite = sprite("Apple.png")
```
{{% /details %}}


### Positioning Fruits (Easy) {#positioning-fruits--easy}

We're continuing from the [previous exercise](#create-an-apple--easy) where we created our apple. Make sure you understand the extra challenge problem (the last question).

Go and add in two more fruits: a banana and orange. Name the sprites `Orange.png` and `Banana.png`. Then together with the apple, make them appear in the middle of the screen. Go check out the [previous exercise](#create-an-apple--easy) if you haven't already.

Put the code that assign the `sprite object` to the variable `sprite` inside `Apple Start`, `Orange Start`, and `Banana Start` and not inside `Game Start` (like that of the code of the extra challenge problem of the previous exercise).

{{% details title="Solution - Orange Start" %}}
```python { filename="Orange Start" }
self.sprite = sprite("Orange.png")
```
{{% /details %}}

{{% details title="Solution - Banana Start" %}}
```python { filename="Banana Start" }
self.sprite = sprite("Banana.png")
```
{{% /details %}}

Make sure use all three classes to create three different objects. Make it so that only the banana appears on the center of the screen even though the orange and apple is also on there.

{{% details title="Solution - Game Start" %}}
```python { filename="Game Start" }
Apple()
Orange()
Banana()
```

This also works, as long as the `banana object` is created last.

```python { filename="Game Start" }
Orange()
Apple()
Banana()
```
{{% /details %}}

Now, only inside `Game Start`, position the apple, orange, and banana so they do not position on top of each other. You'll have to create three variables and use the object variables `x` and `y`.

{{% details title="Solution - Positioning Apple" %}}
```python { filename="Game Start" }
apple = Apple()
Orange()
Banana()

# can be different numbers for x and y
apple.x = 100
apple.y = 200
```
{{% /details %}}

{{% details title="Full Solution - Game Start" %}}
```python { filename="Game Start" }
apple = Apple()
orange = Orange()
banana = Banana()

# can be different numbers for x and y
apple.x = 100
apple.y = 200

banana.x = -100
banana.y = -200

# The following 2 lines are unnecessary
orange.x = 0
orange.y = 0
```
{{% /details %}}

Additionally, here's a version of `Game Start` that's going to randomly position these fruits. You can just view it and study as new materials.

{{% details title="Randomizing Fruit Positions" %}}
```python { filename="Game Start" }
# Importing code from a built-in Python file called random
# to use the function randint by writing random.randint(min, max)
import random

apple = Apple()
orange = Orange()
banana = Banana()

# Positioning fruits randomly
# x: -400 to 400
# y: -500 to 500
apple.x = random.randint(-400, 400)
apple.y = random.randint(-250, 250)

orange.x = random.randint(-400, 400)
orange.y = random.randint(-250, 250)

banana.x = random.randint(-400, 400)
banana.y = random.randint(-250, 250)
```
{{% /details %}}
