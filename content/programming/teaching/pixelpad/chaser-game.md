+++
title = "Chaser Game (WIP)"
draft = false
+++

This is a shorter project that introduces a student to animations in pixelPAD. The student will learn how to work with animations such as an idle animation when the player stands still a running/walking animation when the player is pressing a movement key. Alongside animations, the student will review and practice sprite creation and manipulation of pixelPAD object variables.


## Game Premise {#game-premise}

The game features a player that can run left, right, up, and down. Additionally, there's a chaser that will intend to do the player harm. The chaser will run to the player and decrease the player's health when touched.

Here are a list of requirements:

1.  Player walking left, right, up down with running animations and an idle animation when the player is not moving.
2.  The chaser will move to the player also with animations playing with different movements.

> [!TIP]
> **Check the Documentation**
>
> At this point, the student should be able to make a list of functions they will need. These functions are described and located at the pixelPAD's official documentation.
>
> <https://pixelpad.io/docs>


## Creating Objects and Procuring Sprites {#creating-objects-and-procuring-sprites}

Overall, there are two objects that should be active inside the game at all times. The first is the player character and the second is the chaser. We have two different things inside the game. How pixelPAD works is that with two different things, we'll need two different classes.

As such, go ahead and create two classes: Player and Chaser.
![](/ox-hugo/classes-created.png)

Then, use these classes to create two default pixelPAD objects.

{{% details title="Solution - Creating Player and Chaser objects" %}}
To create a Python object from a class, type the class name and then the parentheses.

```python { filename="Game Start" }
Player()
Chaser()
```

We're going to change some attributes (object variables) of these objects later. Therefore, create two variables to keep track of these two objects.

```python { filename="Game Start" }
player = Player()
chaser = Chaser()
```

Additionally, we can make these two variables object variables so that in any classes (that's not the `Game class` of course) you can access the two pixelPAD objects that represent the player and the chaser.

```python { filename="Game Start" }
self.player = Player()
self.chaser = Chaser()
```

The following is not part of the solution but simply what you could do by creating object variables inside the `Game class`.

```python { filename="RandomClass Start" }
game.chaser.visible = False
game.player.scaleX = 2
# The player is now safe and somehow two times bigger.
```
{{% /details %}}

Now, we're going to get some sprites. We need four sprites.

1.  Player Idle
2.  Player Running
3.  Chaser Idle
4.  Chaser Running

Name accordingly like a programmer should&mdash;without spaces and special symbols. Here is an example of the player running sprite as well as other sprites.

{{< figure src="/ox-hugo/sprites-procured.png" >}}

> [!NOTE]
> **Animations vs. Static Sprites**
>
> An animation is a single png file with rows and columns of image files. In the screenshot above, `Player_Idle.png` has **1 row** and **9 columns**.


## The Player Object {#the-player-object}

We're going to be working on the `Player` class first which should give some good practice before tackling the more difficult `Chaser` class.


### Moving the Chaser Away {#moving-the-chaser-away}

Right now, there are two objects inside the game. They have a default image titled `Empty Image`. They are also on top of each other at (0, 0). We're going to move the chaser to the right of the player by modifying the object variable `x` of the player object.

{{% details title="Solution - Moving Chaser Rightward" %}}
As a reminder, to modify an object variable, you first need to a way to access the variable that keeps track of that object. You can see the usage of the `.` notation.

```python
self.player = Player()
self.chaser = Chaser()

self.chaser.x = 200
```
{{% /details %}}


### Creating and Testing Animations {#creating-and-testing-animations}

Previously, when we were working with static images, we simply tell the object variable `sprite` to keep track of the `sprite object`.

```python { filename="Player Start" }
self.sprite = sprite("Player.png")
```

This is different now that we're working with animations.

> [!TIP]
> **Check Documentation For Animations**
>
> Check out the documentation page for animations:
> <https://pixelpad.io/docs/?c=animation>

Go and create the player animation. Play the animation as well. You should practice your documentation referencing skill and look at the arguments (values sent to functions) required by the necessary functions.

{{% details title="Solution - Player Idle Animation" %}}
We're going to use two functions:

1.  animation
2.  set_animation

We're creating an object variable for the idle animation to later use it inside `Player Loop`.

```python { filename="Player Start" }
# My player idle animation sprite sheet has 1 row and 9 columns
idle_sprite_sheet = sprite("Player_Idle.png", 1, 9)
# Creating an animation of 9 frames per second,
# starting from the first frame to the 9th frame (indexed 0-8).
self.idle_animation = animation(idle_sprite_sheet, 9, 0, 8)

# Test out the idle animation
set_animation(self, self.idle_animation)
```

Additionally, some sprite sheet are too small or big, so scale things up or down. Checkout the `scaleX` and `scaleY` object variables for more information  <https://pixelpad.io/docs/?c=objects>.

```python { filename="Player Start" }
# ...
self.scaleX = 4
self.scaleY = 4
```
{{% /details %}}

Create the animation for the running animation as well. Once again, make sure get the number of columns and rows correct, then the frames per second, ending / starting frame accordingly.

{{% details title="Solution - Creating Running Animation" %}}
```python { filename="Player Start" }
# ...
run_sprite_sheet = sprite("Player_Run.png", 1, 8)
self.run_animation = create_animation(run_sprite_sheet, 8, 0, 7)
# Test out the animation to see if you got the rows and columns
# as well as the first and final frame correct
set_animation(self, self.run_animation)
# ...
```
{{% /details %}}


### Input-Based Player Movement Logic {#input-based-player-movement-logic}

Now, remove any lines of code you have that set the player's animation.

We're first going to work on input-based player movement logic. Disregarding the player's current appearance (animation), use if-statements to create conditions and actions that move the player up, down, left, right with the W, A, S, D keys.

> [!TIP]
> **Check Documentation For Inputs**
>
> Check specifically the function `key_is_pressed`.
> <https://pixelpad.io/docs/?c=input>

Also, try to make the player move left and right by negating `scaleX`. You'll see it work if the `empty image` is horizontally reflected. Or if you have the animation set (as you didn't remove the `set_animation` lines) then it would be clearer to see that.

Here are some hints. First, playing animation is a computer intensive resource. As well, it will not look nice if the animation keeps repeating from the beginning. Imagine watching a movie but it keeps rewind by 10 seconds with multiple rewinds happening at the same time. Second, setting up if-statements is going to be quite a challenge because by default if the player is not pressing anything, an idle animation should be playing and otherwise the run animation if the movement keys are pressed.

{{% details title="Hints - Playing Animations Only When Necessary" %}}
Create two variables. One that keeps track of the current state and one that is deliberately stale which won't be changed until an animation has been played.

```python { filename="Player Start" }
self.state = "idle"
self.old_state = "idle"
```

The default state can be idle and only set the state to `"run"` when the player is pressing the related keys. Constantly reassigning variables, even if to the same value, is more efficient than playing animations multiple times.

```python { filename="Player Loop" }
self.state = "idle"

if key_is_pressed("w"):
    self.state = "run"
    # ...
elif key_is_pressed("s"):
    self.state = "run"
    # ...
# ...
```
{{% /details %}}

{{% details title="Solution - Movement Without Animations" %}}
Put this code inside the `Player Loop` as whether the player is pressing a certain key needs to be pressed continuously.

```python { filename="Player Start" }
self.state = "idle"
self.old_state = "idle"
```

```python { filename="Player Loop" }
if self.state != self.old_state:
    if self.state == "idle":
        set_animation(self, self.idle_animation)
    elif self.state == "run":
        set_animation(self, self.run_animation)
    self.old_state = self.state

self.state = "idle"

if key_is_pressed("a"):
    self.state = "run"
    self.x -= 5
    self.scaleX = -4
elif key_is_pressed("d"):
    self.state = "run"
    self.x +=5
    self.scaleX = 4

if key_is_pressed("w"):
    self.state = "run"
    self.y += 5
elif key_is_pressed("s"):
    self.state = "run"
    self.y -= 5
```

When you press play, you'll still see `Empty Image`. So, we'll still need to set an initial animation first. We'll just use the idle animation.

```python { filename="Player Start" }
# ...
set_animation(self, self.idle_animation)
```
{{% /details %}}
