+++
title = "pixelPAD"
draft = false
+++

## What is pixelPAD? {#what-is-pixelpad}

pixelPAD is a closed-source game development platform and education tool, that's free to use.

> [!NOTE]
> **Resources**
>
> The student should be exposed to the documentation page first before anything. This is located at [pixelpad.io/docs](https:pixelpad.io/docs).
>
> There are also tutorials created by the platform that the student can peruse on his/her own time. These are videos located at [pixelpad.io/learn](https:pixelpad.io/learn). Keep in mind the videos might not play if you had an ad-blocker or pop-up blocker enabled.

<!--quoteend-->

> [!DANGER]
> **PixelPad Docs Issue**
>
> As of 09/02/26, there are some errors in the documentation page such as outdated examples. Most notably are the names of the sprite creation functions removed "new" in front of the sprite type.


## Intended Audience {#intended-audience}

This page is intended for both the teacher and the students to read. Activities should be mainly driven by the teacher but students should be given a chance to read if he would like and want to. A sample syllabus for my generic syllabus.


## Learning Progression {#learning-progression}

{{% steps %}}
1.  Look over [documentation page](https:pixelpad.io/docs) that defines terms of pixelPAD. Do the quiz below.
2.  Create a text box. In that process learn classes creation, class instantiation of object, the "self" keyword, and reading from the documentation understand a function signature.
3.  Create a sprite by reading from the documentation page.
4.  Begin on a simple but multi-day to long-term project.
{{% /steps %}}


## Each Learning Session {#each-learning-session}

The student must be tested on all concepts first before advancement.
Assessment should be done on a separate PAD while keeping the long-term project clean.

For a 1 hour session, time should be allocated approximately:

1.  Assessment through small coding exercises - 15 minutes
2.  Project supervision, instruction alternating - 45 minutes


## Documentation Home Page Quiz {#documentation-home-page-quiz}

The quiz was created with the assistance of [OpenAI GPT-5.6](https:openai.com/index/gpt-5-6/).


### 1. What programming language does pixelPAD use? {#1-dot-what-programming-language-does-pixelpad-use}

-   A. Java
-   B. Python
-   C. C++
-   D. JavaScript

{{% details "Show answer" %}}
**Answer: B. Python**

PixelPAD 2D uses Python to program projects and applications.
{{% /details %}}


### 2. Why do coders use an engine? {#2-dot-why-do-coders-use-an-engine}

-   A. To avoid rebuilding common project functionality from the ground up
-   B. To store only sound files
-   C. To replace Python with another language
-   D. To allow multiple rooms to run at once

{{% details "Show answer" %}}
**Answer: A.**

An engine handles much of the underlying work needed by a project so that
developers do not have to build everything from scratch every time.
{{% /details %}}


### 3. What is an Asset in pixelPAD? {#3-dot-what-is-an-asset-in-pixelpad}

-   A. Only an image used by the game
-   B. Only a Class or Room
-   C. Any piece of information placed in the project
-   D. Only a file uploaded from outside PixelPAD

{{% details "Show answer" %}}
**Answer: C.**

Assets include Classes, Rooms, Sprites, Sounds, and Functions.
{{% /details %}}


### 4. What is the difference between `Start` and `Loop` in a Class? {#4-dot-what-is-the-difference-between-start-and-loop-in-a-class}

-   A. `Start` repeats while `Loop` runs once
-   B. `Start` runs when the script starts, while `Loop` repeatedly runs while
    the object is active
-   C. `Start` creates Rooms while `Loop` creates Sprites
-   D. They always perform the same task

{{% details "Show answer" %}}
**Answer: B.**

`Start` runs when the script starts. `Loop` runs many times per second while
the object is active.
{{% /details %}}


### 5. What best describes a Room? {#5-dot-what-best-describes-a-room}

-   A. A collection of sound files
-   B. A scene containing objects working together
-   C. A Python function available to every script
-   D. A single Sprite

{{% details "Show answer" %}}
**Answer: B.**

A Room can be thought of as a scene. Its room script primarily creates and
connects objects to produce a particular scenario.
{{% /details %}}


### 6. How many Rooms can be active at the same time? {#6-dot-how-many-rooms-can-be-active-at-the-same-time}

-   A. One
-   B. Two
-   C. Four
-   D. Any number

{{% details "Show answer" %}}
**Answer: A. One**

PixelPAD allows only one Room to be active at a time.
{{% /details %}}


### 7. What is a Sprite? {#7-dot-what-is-a-sprite}

-   A. A sound effect
-   B. A Python Class
-   C. A two-dimensional bitmap or image
-   D. A Room script

{{% details "Show answer" %}}
**Answer: C.**

A Sprite is a two-dimensional bitmap or image, most commonly used as a visual
element in a 2D project.
{{% /details %}}


### 8. Which formats are listed as supported Sound assets {#8-dot-which-formats-are-listed-as-supported-sound-assets}

-   A. PNG, JPG, and GIF
-   B. MP3, MIDI, and WAV
-   C. MP4, AVI, and MOV
-   D. TXT, JSON, and XML

{{% details "Show answer" %}}
**Answer: B.**

PixelPAD lists MP3, MIDI, and WAV as supported sound formats.
{{% /details %}}


### 9. Why would you place code in the Functions section? {#9-dot-why-would-you-place-code-in-the-functions-section}

-   A. To make reusable code available to other scripts
-   B. To restrict the code to a single Object
-   C. To turn the code into a Sprite
-   D. To activate multiple Rooms

{{% details "Show answer" %}}
**Answer: A.**

The Functions section is intended for code that needs to be reused. Functions
placed there can be used from other scripts in the project.

Python classes that are not attached to Objects can also be created there.
{{% /details %}}


### 10. How do you access the Asset Library for Sprites and Sounds? {#10-dot-how-do-you-access-the-asset-library-for-sprites-and-sounds}

-   A. Write a Python `import` statement
-   B. Open the `Loop` section
-   C. Click the plus (+) button in the Assets panel
-   D. Activate another Room

{{% details "Show answer" %}}
**Answer: C.**

The Asset Library is accessed using the plus (+) button in the Assets panel
for Sprites and Sounds. It contains free-to-use assets and also allows you to
upload your own.
{{% /details %}}


## Activity - Creating a Text Box {#activity-creating-a-text-box}

The goal of this activity is to display a text box on the pixelPAD screen.


### Prerequisites {#prerequisites}

-   Basic Internet Literacy, Navigation


### Concepts {#concepts}

-   Functions
-   Variables
-   Documentation Referencing


### Coach Strategy {#coach-strategy}

Creation of a text box is heavy in instructions. The [best for engagement]({{< relref "teaching-programming.md#best-for-engagement" >}}) strategy should be used.


### Guide and Solution {#guide-and-solution}

{{% details title="Sample activity guide w/ documentation referencing" open="true" %}}
{{% steps %}}
1.  I open up [pixelPAD's documentation page](https:pixelpad.io/docs). I then press "Ctrl+F" to search for "text" or "text box".
2.  I take my time to read everything I can find about text and not just finding the correct page specifically about text or creating a text box.
3.  I find the function in the documentation that creates the text box. I note down its name and its required and optional arguments.
4.  I look at the examples.
5.  (Student) I form questions about confusing thing to later ask the tutor/coach/instructor.
6.  (Coach) Demonstrate creating a text box very slowly.
7.  (Student) Repeat steps 1-5 and try to redo what the coach did.
{{% /steps %}}
{{% /details %}}

{{% details title="Solution" %}}
{{% steps %}}
1.  In `Game Start` use the function `text` to create a new text box.
2.  The function signature is `text(text :string, x :number, y :number) -> sprite`. So I need to give it the required arguments: (1) text content the string data type, (2) x coordinate as an int data type, (3) y coordinate as an int data type.
3.  Because the default text is black, it is not visible in a black background. I will change it to another color like white by assigning the object variable `color` of the created text object with the string that makes up a hex-color value.
{{% /steps %}}

```python { filename="Game Start" }
my_text = text("Hello There", 0, 0)
my_text.color = "#fff"
# Blue
my_text.color = "#0000FF"
```
{{% /details %}}


### Debrief {#debrief}

Created with assistance of [OpenAI GPT-5.6](https:openai.com/index/gpt-5-6/).


#### 1. Which function is used to create a text box in PixelPAD? {#1-dot-which-function-is-used-to-create-a-text-box-in-pixelpad}

-   A. `sprite`
-   B. `text`
-   C. `textbox`
-   D. `label`

{{% details title="Answer" %}}
**B.**

The `text` function is used to create a text box.

```python { filename="Game Start" }
my_text = text("Hello There", 0, 0)
```
{{% /details %}}


#### 2. Which statements about this line are true? Mark all that apply. {#2-dot-which-statements-about-this-line-are-true-mark-all-that-apply-dot}

```python { filename="Game Start" }
my_text = text("Hello There", 0, 0)
```

-   A. `text` is a function call.
-   B. `"Hello There"` is the displayed text.
-   C. `0, 0` specify the position.
-   D. `my_text` refers to the returned object.
-   E. `my_text` is only a string.

{{% details title="Answer" %}}
**A, B, C, D**

The `text` function returns a sprite object, and that object is assigned to `my_text`.
{{% /details %}}


#### 3. What does the `text` function return? {#3-dot-what-does-the-text-function-return}

-   A. A string
-   B. A number
-   C. A sprite object
-   D. A color

{{% details title="Answer" %}}
**C.**

The function signature ends with:

`text(text :string, x :number, y :number) -> sprite`

The `-> sprite` portion tells us that the function returns a sprite object.
{{% /details %}}


#### 4. Why might a newly created text object not be visible? {#4-dot-why-might-a-newly-created-text-object-not-be-visible}

-   A. The `text` function does not display objects.
-   B. The text may be black on a black background.
-   C. Text objects only appear at `(100, 100)`.
-   D. A sprite image must be added first.

{{% details title="Answer" %}}
**B.**

The default text color is black. If the background is also black, the text exists but may not be visible.
{{% /details %}}


#### 5. Which line changes `my_text` to white? {#5-dot-which-line-changes-my-text-to-white}

-   A. `my_text = "#fff"`
-   B. `color.my_text = "#fff"`
-   C. `my_text.color = "#fff"`
-   D. `text.color("#fff")`

{{% details title="Answer" %}}
**C.**

The `color` object variable can be assigned a hexadecimal color value.

```python { filename="Game Start" }
my_text.color = "#fff"
```
{{% /details %}}


#### 6. In `my_text.color = "#0000FF"`, which statements are true? Mark all that apply. {#6-dot-in-my-text-dot-color-0000ff-which-statements-are-true-mark-all-that-apply-dot}

-   A. `my_text` refers to an object.
-   B. `color` is an object variable.
-   C. `"#0000FF"` is the new value assigned to `color`.
-   D. `color` is the name of the `text` function.
-   E. The statement modifies an existing object.

{{% details title="Answer" %}}
**A, B, C, E**

`my_text.color` accesses the `color` variable belonging to the object referred to by `my_text`. The assignment changes that object's `color` value to `"#0000FF"`.
{{% /details %}}


#### 7. What color does `#0000FF` represent? {#7-dot-what-color-does-0000ff-represent}

-   A. Red
-   B. Green
-   C. Blue
-   D. White

{{% details title="Answer" %}}
**C.**

`#0000FF` is a hexadecimal color value representing blue.

```python { filename="Game Start" }
my_text.color = "#0000FF"
```
{{% /details %}}


#### 8. Which pieces of information can be learned from this function signature? Mark all that apply. {#8-dot-which-pieces-of-information-can-be-learned-from-this-function-signature-mark-all-that-apply-dot}

`text(text :string, x :number, y :number) -> sprite`

-   A. The function's name
-   B. The names of its arguments
-   C. The expected data types of its arguments
-   D. The type of value it returns
-   E. The exact color the text will have

{{% details title="Answer" %}}
**A, B, C, D**

The signature tells us the function name, its arguments, their expected data types, and the return type. It does not tell us the exact color of the resulting text.
{{% /details %}}


#### 9. Which code correctly creates `Hello World` at `(100, 200)` and then makes it white? {#9-dot-which-code-correctly-creates-hello-world-at--100-200--and-then-makes-it-white}

-   A. `text("Hello World", "#fff", 100, 200)`
-   B. `my_text = text(100, 200, "Hello World")`
-   C. `my_text = text("Hello World", 100, 200)` followed by `my_text.color = "#fff"`
-   D. `my_text.color = text("Hello World", 100, 200)`

{{% details title="Answer" %}}
**C.**

First create the text object with the required arguments, then modify its `color` variable.

```python { filename="Game Start" }
my_text = text("Hello World", 100, 200)
my_text.color = "#fff"
```
{{% /details %}}


#### 10. If you forget how to use the `text` function, what is the best first step? {#10-dot-if-you-forget-how-to-use-the-text-function-what-is-the-best-first-step}

-   A. Guess different arguments until something works.
-   B. Search the PixelPAD documentation for information about text.
-   C. Ask someone to write the whole solution immediately.
-   D. Start a new project.

{{% details title="Answer" %}}
**B.**

Search the PixelPAD documentation and use it to reconstruct the solution.

A useful process is:

1.  Search for terms related to what you want to create.
2.  Read the relevant documentation.
3.  Find the function signature.
4.  Identify required and optional arguments.
5.  Study the examples.
6.  Try using the function yourself.
7.  Form specific questions about anything that remains confusing.

The goal is to practice learning from documentation, not only memorizing the solution.
{{% /details %}}


## Activity - Creating a Sprite {#activity-creating-a-sprite}

This activity teaches the student how to make a sprite in pixelPAD.


### Prerequisites {#prerequisites}

-   Basic Internet Literacy, Website Navigation


### Concepts {#concepts}

-   Variables
-   Functions
-   Documentation Referencing


### Coach Strategy {#coach-strategy}

Creation of a text box is heavy in instructions. The [best for engagement]({{< relref "teaching-programming.md#best-for-engagement" >}}) strategy should be used.


### Guide and Solution {#guide-and-solution}

{{% details title="Sample activity guide w/ documentation referencing" open="true" %}}
{{% steps %}}
1.  I open up [pixelPAD's documentation page](https:pixelpad.io/docs). I then press "Ctrl+F" to search for "sprite".
2.  I take my time to read everything I can find about sprite and not just finding the correct page specifically about creating a sprite.
3.  I find the function in the documentation that creates the sprite. I note down its name and its required and optional arguments.
4.  I look at the examples.
5.  (Student) I form questions about confusing thing to later ask the tutor/coach/instructor.
6.  (Coach) Demonstrate creating a text box very slowly.
7.  (Student) Repeat steps 1-5 and try to redo what the coach did.
{{% /steps %}}
{{% /details %}}

{{% details title="Sample Solution" %}}
{{% steps %}}
1.  Create a class `Sprite` that will create an object that draws our sprite on the screen.
2.  Look at the left-side panel and click the `+` button next Sprite and choose an image. Name it `"sprite_image.png"`.
3.  Inside the class `Sprite`, we will assign a sprite object to the object variable `sprite` of `self`. The sprite object is created by using the function `sprite`.
4.  To tell the class `Sprite` to actually generate our object, we _call_ it inside `Game Start`.
{{% /steps %}}

```python { filename="Sprite Start" }
self.sprite = sprite("sprite_image.png")
```

```python { filename="Game Start" }
variable_holding_object = Sprite()
```

> [!WARNING]
> **Warning** - `sprite` vs. `Sprite`
>
> The word `sprite` or capitalized `Sprite` holds different meanings in the course of this activity. Students can get confused.
>
> 1.  `self.sprite` shows a `sprite` that is an object variable of `self`.
> 2.  `sprite("sprite_image.png")` is a _call_ to the function `sprite` that will **return** to us a `sprite object`.
> 3.  `sprite object` is the data-type of the value assigned to the object variable `sprite` as in `self.sprite`.
{{% /details %}}


### Debrief {#debrief}

Created with assistance of [OpenAI GPT-5.6](https:openai.com/index/gpt-5-6/).


#### 1. What is the purpose of the `Sprite` class in this activity? {#1-dot-what-is-the-purpose-of-the-sprite-class-in-this-activity}

-   A. To store only the image file.
-   B. To create an object that can display the sprite.
-   C. To replace the `sprite` function.
-   D. To change the project's room.

{{% details title="Answer" %}}
**B.**

The `Sprite` class is used to create an object that contains the code needed to display the sprite.
{{% /details %}}


#### 2. Which statements about the following line are true? Mark all that apply. {#2-dot-which-statements-about-the-following-line-are-true-mark-all-that-apply-dot}

```python { filename="Sprite Start" }
self.sprite = sprite("sprite_image.png")
```

-   A. `sprite` is a function being called.
-   B. `"sprite_image.png"` identifies the image asset to use.
-   C. The `sprite` function returns a sprite object.
-   D. `self.sprite` stores the returned sprite object.
-   E. `Sprite` is being called to create an instance of the class.

{{% details title="Answer" %}}
**A, B, C, D**

The lowercase `sprite` function is called with the image asset name. It returns a sprite object, which is assigned to `self.sprite`.

`Sprite`, with a capital `S`, is not being called in this line.
{{% /details %}}


#### 3. Which function is used to create a sprite object from an image asset? {#3-dot-which-function-is-used-to-create-a-sprite-object-from-an-image-asset}

-   A. `Sprite`
-   B. `image`
-   C. `sprite`
-   D. `asset`

{{% details title="Answer" %}}
**C.**

The lowercase `sprite` function creates and returns a sprite object.

```python { filename="Sprite Start" }
self.sprite = sprite("sprite_image.png")
```
{{% /details %}}


#### 4. What argument is passed to `sprite` in this example? {#4-dot-what-argument-is-passed-to-sprite-in-this-example}

```python { filename="Sprite Start" }
self.sprite = sprite("sprite_image.png")
```

-   A. The name of the `Sprite` class.
-   B. The name of the image asset.
-   C. The position of the sprite.
-   D. The color of the sprite.

{{% details title="Answer" %}}
**B.**

`"sprite_image.png"` is the name of the image asset that the sprite object should use.
{{% /details %}}


#### 5. What does `self.sprite` represent? {#5-dot-what-does-self-dot-sprite-represent}

-   A. The `sprite` function itself.
-   B. The image file stored on the computer.
-   C. An object variable that stores the returned sprite object.
-   D. The `Sprite` class.

{{% details title="Answer" %}}
**C.**

`self.sprite` is an object variable belonging to `self`. The sprite object returned by the `sprite` function is assigned to it.

```python { filename="Sprite Start" }
self.sprite = sprite("sprite_image.png")
```
{{% /details %}}


#### 6. Which statements correctly distinguish `Sprite`, `sprite`, and `self.sprite`? Mark all that apply. {#6-dot-which-statements-correctly-distinguish-sprite-sprite-and-self-dot-sprite-mark-all-that-apply-dot}

-   A. `Sprite` is the class created in this activity.
-   B. `sprite` is a function used to create a sprite object.
-   C. `self.sprite` is an object variable.
-   D. `Sprite` and `sprite` always refer to the same thing.
-   E. Capitalization matters when distinguishing `Sprite` from `sprite`.

{{% details title="Answer" %}}
**A, B, C, E**

The three names have different roles:

1.  `Sprite` is the class.
2.  `sprite` is the function.
3.  `self.sprite` is an object variable that stores the sprite object returned by the function.

Because Python is case-sensitive, `Sprite` and `sprite` are different names.
{{% /details %}}


#### 7. What does the following line do? {#7-dot-what-does-the-following-line-do}

```python { filename="Game Start" }
variable_holding_object = Sprite()
```

-   A. It loads the image asset directly.
-   B. It calls the `sprite` function.
-   C. It creates an object from the `Sprite` class and stores it in a variable.
-   D. It creates a new `Sprite` class.

{{% details title="Answer" %}}
**C.**

`Sprite()` calls the `Sprite` class to create an object from that class.

The returned object is assigned to `variable_holding_object`.

```python { filename="Game Start" }
variable_holding_object = Sprite()
```
{{% /details %}}


#### 8. Which steps are involved in displaying the sprite in this activity? Mark all that apply. {#8-dot-which-steps-are-involved-in-displaying-the-sprite-in-this-activity-mark-all-that-apply-dot}

-   A. Add an image to the Sprite assets.
-   B. Use `sprite("sprite_image.png")` to create a sprite object.
-   C. Store the returned sprite object in `self.sprite`.
-   D. Call `Sprite()` in `Game Start`.
-   E. Call `text()` to load the image.

{{% details title="Answer" %}}
**A, B, C, D**

The activity connects several steps:

1.  Add the image asset.
2.  Create a sprite object from the image using `sprite`.
3.  Store that object in `self.sprite`.
4.  Create an instance of the `Sprite` class from `Game Start`.

The `text` function is not used to create the sprite.
{{% /details %}}


#### 9. Which code correctly creates the sprite object inside `Sprite Start`? {#9-dot-which-code-correctly-creates-the-sprite-object-inside-sprite-start}

-   A. `Sprite("sprite_image.png")`
-   B. `self.sprite = Sprite("sprite_image.png")`
-   C. `self.sprite = sprite("sprite_image.png")`
-   D. `sprite = self.Sprite("sprite_image.png")`

{{% details title="Answer" %}}
**C.**

The lowercase `sprite` function creates the sprite object, and the returned object is stored in `self.sprite`.

```python { filename="Sprite Start" }
self.sprite = sprite("sprite_image.png")
```
{{% /details %}}


#### 10. If you forget how to create a sprite, what is the best first step? {#10-dot-if-you-forget-how-to-create-a-sprite-what-is-the-best-first-step}

-   A. Guess function names until one works.
-   B. Search the PixelPAD documentation for information about sprites.
-   C. Ask someone to write the entire solution immediately.
-   D. Recreate the project from the beginning.

{{% details title="Answer" %}}
**B.**

Search the PixelPAD documentation and use it to reconstruct the solution.

A useful process is:

1.  Search for terms such as `sprite`.
2.  Read the relevant documentation.
3.  Find the function used to create a sprite.
4.  Identify its required and optional arguments.
5.  Study the examples.
6.  Try using the function yourself.
7.  Form specific questions about anything that remains confusing.

The goal is to practice learning unfamiliar features from documentation rather than only memorizing the finished code.
{{% /details %}}


## Related {#related}

These beginner concepts reference the [programming fundamentals roadmap]({{< relref "_index" >}}).

For insights about my teaching approach, check out the [teaching philosophy]({{< relref "teaching-programming" >}}).
