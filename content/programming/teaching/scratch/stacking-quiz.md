+++
title = "Stacking Game"
draft = false
+++

## Stacking Game {#stacking-game}

This is a simple project that's made in scratch where the user needs to stack up rectangular blocks up in the sky. This project requires code to be put into one sprite and programming structures such as:

1.  variables - setting and changing
2.  forever loop
3.  repeat and repeat until
4.  if-statements and boolean expressions as condition

{{% details title="Stacking Project Full Solution (Teacher Only While In Session)" %}}
{{< figure src="/ox-hugo/stacking-project.png" >}}
{{% /details %}}


## Debrief {#debrief}

Quiz is another word for debrief. This quiz tests your understanding of the programming structures used in this project.

Use questions 1–6 as fundamental understanding, 7–10 for events and clones, and 11–12 for applying multiple programming concepts together.

| Activity                 | Duration  | Purpose                           |
|--------------------------|-----------|-----------------------------------|
| Quiz **without** Scratch | 10–12 min | Test understanding and recall     |
| Quiz **with** Scratch    | 10–15 min | Experiment and verify predictions |
| Review answers           | 5–8 min   | Explain misconceptions            |
| Let's Add Something More | 25–35 min | Apply knowledge creatively        |


### 1. What does this block do? {#1-dot-what-does-this-block-do}

```scratch
set [speed v] to (10)
```

-   A. Adds 10 to the current speed
-   B. Changes speed to exactly 10
-   C. Multiplies speed by 10
-   D. Moves the sprite 10 steps

{{% details title="Answer (Multiple Choice)" %}}
B. Changes speed to exactly 10.

The `set` block replaces the current value of a variable with a new value.
{{% /details %}}


### 2. What will the value of score be after these blocks execute? {#2-dot-what-will-the-value-of-score-be-after-these-blocks-execute}

```scratch
set [score v] to (0)
change [score v] by (1)
change [score v] by (1)
change [score v] by (1)
```

-   A. 0
-   B. 1
-   C. 3
-   D. 4

{{% details title="Answer (Multiple Choice)" %}}
C. 3.

The score starts at 0 and increases by 1 three times.
{{% /details %}}


### 3. Which statements about this loop are correct? {#3-dot-which-statements-about-this-loop-are-correct}

```scratch
repeat (8)
    change y by (34)
end
```

-   A. The sprite moves upward 8 times.
-   B. The sprite's y-coordinate increases by 272 in total.
-   C. The sprite's x-coordinate increases by 34.
-   D. The instructions inside the loop execute exactly 8 times.

{{% details title="Answer (Select All)" %}}
A, B, and D.

Each repetition increases y by 34, so the total change is 8 × 34 = 272. The x-coordinate is unchanged.
{{% /details %}}


### 4. What happens when the space key is pressed? {#4-dot-what-happens-when-the-space-key-is-pressed}

```scratch
repeat until <key [space v] pressed?>
    move (10) steps
end
```

-   A. The sprite begins moving faster.
-   B. The sprite stops repeating the movement.
-   C. The sprite moves exactly 10 more times.
-   D. The entire Scratch project stops.

{{% details title="Answer (Multiple Choice)" %}}
B. The sprite stops repeating the movement.

The loop continues while the condition is false. Once the space key is pressed, the loop ends.
{{% /details %}}


### 5. Which condition makes the sprite move when the space key is NOT pressed? {#5-dot-which-condition-makes-the-sprite-move-when-the-space-key-is-not-pressed}

A.

```scratch
<key [space v] pressed?>
```

B.

```scratch
<not <key [space v] pressed?>>
```

C.

```scratch
<touching [edge v]?>
```

D.

```scratch
<mouse down?>
```

{{% details title="Answer (Multiple Choice)" %}}
B.

The `not` operator reverses a Boolean condition. When the space key is not pressed, the inner condition is false, making the whole condition true.
{{% /details %}}


### 6. What happens when the sprite touches the edge? {#6-dot-what-happens-when-the-sprite-touches-the-edge}

```scratch
move (10) steps
if on edge, bounce
```

-   A. The sprite disappears.
-   B. The sprite stops permanently.
-   C. The sprite changes direction to bounce away.
-   D. The sprite returns to the center of the stage.

{{% details title="Answer (Multiple Choice)" %}}
C. The sprite changes direction to bounce away.

The `if on edge, bounce` block adjusts the sprite's direction when it touches the stage boundary.
{{% /details %}}


### 7. Which events can start a Scratch script? {#7-dot-which-events-can-start-a-scratch-script}

A.

```scratch
when green flag clicked
```

B.

```scratch
when I receive [lost v]
```

C.

```scratch
when I start as a clone
```

D.

```scratch
set [score v] to (0)
```

{{% details title="Answer (Select All)" %}}
A, B, and C.

These are event blocks that can begin scripts. Setting a variable changes data but does not start a script by itself.
{{% /details %}}


### 8. What does broadcasting a message do? {#8-dot-what-does-broadcasting-a-message-do}

```scratch
broadcast [lost v]
```

-   A. Sends a message that can trigger other scripts.
-   B. Deletes all clones immediately.
-   C. Changes the score to zero.
-   D. Ends every running script.

{{% details title="Answer (Multiple Choice)" %}}
A. Sends a message that can trigger other scripts.

Scripts beginning with `when I receive [lost v]` can respond to this broadcast.
{{% /details %}}


### 9. What happens when this script executes? {#9-dot-what-happens-when-this-script-executes}

```scratch
when I receive [lost v]
hide
delete this clone
```

-   A. Every sprite in the project is deleted.
-   B. The sprite becomes visible.
-   C. The current clone hides and deletes itself.
-   D. The game restarts automatically.

{{% details title="Answer (Multiple Choice)" %}}
C, if this script is running on a clone.

The `hide` block makes the current sprite instance invisible. The `delete this clone` block removes the current clone. If the original sprite runs the script, it hides, but the original sprite is not deleted.
{{% /details %}}


### 10. What is the purpose of creating a clone in this stacking game? {#10-dot-what-is-the-purpose-of-creating-a-clone-in-this-stacking-game}

```scratch
create clone of [myself v]
change y by (34)
```

-   A. Create another copy of the sprite while moving the original upward.
-   B. Move every existing sprite upward by 34.
-   C. Replace the original sprite with a new costume.
-   D. Create a completely new Scratch variable.

{{% details title="Answer (Multiple Choice)" %}}
A.

A clone is another instance of the sprite. After creating it, the original sprite continues executing and moves upward by 34.
{{% /details %}}


### 11. Which statements about this condition are correct? {#11-dot-which-statements-about-this-condition-are-correct}

```scratch
if <not <touching color [#ff0000]?>> then
    broadcast [lost v]
end
```

-   A. The broadcast happens when the sprite is not touching red.
-   B. The broadcast happens every time the sprite touches red.
-   C. The `not` operator reverses the result of the touching-color test.
-   D. The broadcast happens only if the entire condition is true.

{{% details title="Answer (Select All)" %}}
A, C, and D.

The touching-color test checks whether the sprite touches the specified color. The `not` operator reverses that result, so the broadcast executes when the sprite is not touching red.
{{% /details %}}


### 12. What happens to speed after this program runs? {#12-dot-what-happens-to-speed-after-this-program-runs}

```scratch
set [speed v] to (10)
repeat (4)
    change [speed v] by (1)
end
```

-   A. 10
-   B. 11
-   C. 14
-   D. 40

{{% details title="Answer (Multiple Choice)" %}}
C. 14.

The variable starts at 10. The loop increases it by 1 four times, resulting in 10 + 4 = 14.
{{% /details %}}
