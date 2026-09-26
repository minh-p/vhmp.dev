+++
title = "Space Obstacles Avoidance (WIP)"
draft = false
+++

## Space Obstacles Avoidance {#space-obstacles-avoidance}

This is a game where you command a spaceship by WASD and avoid obstacles that that can come from the edge of the screen up, down, left, right, and also out from the screen. Unlike normal "car-and-highway" game, the asteroids will be coming from different directions.


## Activity - Game Design {#activity-game-design}

From a simple imagination of the game, the student is tasked with creating a list of features they have to implement and as well as the order that they should do these tasks.

**Activity Prompt**: List out the game features you would like to make. Then, choose the game features you would really want to add. Next, organize them in the order you can get them done. Finally, for each of these features, list of the skills and knowledge you know and do not know yet in order to code these features out.

{{% details title="Solution - Game Plan, Learning List" %}}
1.  Spaceship - Sprite Creation, Key Inputs, Sprite Movement
2.  Spaceship User Interface - Health - Textbox, Sprite manipulation
3.  Asteroid - From the edge of the screen, then from in and out. - Sprite manipulation, Game Loop
4.  Visual cues - where the asteroid is going - Sprite manipulation
5.  Shop - Items that can be used to survive harder stages and a currency - sprite manipulation
{{% /details %}}

> [!WARNING]
> **How to Best Use the Solution**
>
> The solution is here as a guide. The student is encouraged to **modify** and add more than what's on here.


## Activity - Making the Spaceship {#activity-making-the-spaceship}

We're going to be making the spaceship, which the player can press WASD to move the spaceship around. First, if you haven't already, list out the pixelPAD concepts that are going to be needed.

> [!TIP]
> **What We're Training For**
>
> We're training our problem solving skills as part of the engineering process. We have identified what we would like to make in our game. Now, we're making a list of "tools" we have learned. We're simply then separating this list of "tools" to concepts we know and concepts we do not know yet.

{{% details title="Solutions - Concepts Needed Example" %}}
In order to make this spaceship that can be controlled with WASD, I as the student need to learn where I mark concepts that I understand already.

1.  [X] Sprite creation
2.  [ ] Handling keyboard inputs
{{% /details %}}


### Sprite Creation {#sprite-creation}

In pixelPAD, we know that `objects` are created from `calling` their `classes`. Each `object` can hold one sprite. The sprite can move on the screen through the manipulation of its built-in object variables.

> [!DANGER]
> **Don't Rush It** - Be sure to know prior concepts
>
> If you don't understand this sentence, it's best that you do the three activities: documentation, text box creation, and sprite creation at [/programming/teaching/pixelpad](/programming/teaching/pixelpad).

If you have already gone through the activities, or do not feel like repeating them. Check out the relevant document page on this topic at [pixelpad.io/docs](https://pixelpad.io/docs/?c=sprites).

First, create the `class` for the `sprite object` and add a `image` for the `sprite object`.

{{% details title="Solution - Sprite Creation" %}}
The `class` for the `sprite object` will be named `Player`. Any `image` is fine but I decide to change its name inside the project to `spaceship.png`.

```python { filename="Game Start" }
Player()
```

```python { filename="Player Start" }
self.sprite = sprite("spaceship.png")
```
{{% /details %}}

Now, you should see a spaceship in the middle of your screen.

> [!WARNING]
> **Image Could Not Load** - Potential Technical Issue
>
> Sometimes, pixelPAD cannot load the image from its own server because of network connectivity issues. If you look at the output, you can see the error message.


### Listening to Key Inputs {#listening-to-key-inputs}

We're adding code so that the spaceship moves up, left, down, right through the key presses WASD.

If a student doesn't understand this concept yet, they are advised to practice reading the documentation on the following two web pages and code his own solution before looking at the solution:

1.  [Objects](https://pixelpad.io/docs/?c=objects) - Sprite manipulation, position, etc.
2.  [Inputs](https://pixelpad.io/docs/?c=input) - Listening to key inputs; notice that it's used in `loop` and not `start` (understand why this is the case).
3.  [Conditionals](/programming/teaching/programming-fundamentals/conditionals/) - Read this page on if-statements.

{{% details title="Solution - WASD" %}}
**Non-exclusive movements** - Option 1

```python { filename="Player Loop" }
if key_is_pressed("a"):
    self.x = self.x - 10
if key_is_pressed("d"):
    self.x += 10
    # Equivalent to self.x = self.x + 10
if key_is_pressed("w"):
    self.y += 10
if key_is_pressed("s"):
    self.y -= 10
```

**Exclusive movements** - Option 2

We use `else-ifs` or `elif` in Python to establish an `Exclusive OR` relationship. A player cannot press `a` or `d` at the same time and have their horizontal movement canceled.

```python { filename="Player Loop" }
if key_is_pressed("a"):
    self.x = self.x - 10
elif key_is_pressed("d"):
    self.x += 10
    # Equivalent to self.x = self.x + 10

if key_is_pressed("w"):
    self.y += 10
elif key_is_pressed("s"):
    self.y -= 10
```
{{% /details %}}


## Making Obstacles (Asteroids) {#making-obstacles--asteroids}

Whenever you want to import a sprite into your game, you have to create a class that contains the instructions of how to setup the object that contains the sprite. Remember that every object created by a `PixelPad` class can hold a `sprite` that can be held on the screen.

So, we'll first create our class `Obstacle` and at the same time import the image for your asteroid.

In terms of logic, the asteroid should spawn and then move in a determined direction. The direction should be set by the scope (Class/Game) that invoked the class to create the sprite object.

Here's an example showing a creation of a single Asteroid.

```python { filename="Game Start" }
asteroid = Obstacle()
asteroid.sprite = sprite("Asteroid.png")
asteroid.x = 0
asteroid.y = 400
asteroid.direction = "South"
```

In this example an obstacle should be spawned and immediately it will be moving to the south. So the key idea is that depending on the value of the object variable `direction`, the asteroid's x and y value should be changed. For now, only work on asteroids coming from the edge of the screen. You'll be practicing working with a class's Loop in this activity.
