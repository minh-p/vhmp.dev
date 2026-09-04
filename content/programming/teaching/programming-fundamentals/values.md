+++
title = "Values"
draft = false
weight = 10
+++

This page was created with the assistance of [GPT-5.5 Sol](https:openai.com/index/gpt-5-6/).


## Values {#values}

This is the first programming concept that student learns. The prerequisites are omitted. Any difficulty in understanding would come from a lack of vocabulary due to age or the lack of engagement of innate intuition.


### Why Values Are the First Thing You Understand {#why-values-are-the-first-thing-you-understand}

There is no way to directly represent what a value is in any programming language. One might say that in programming language X, I can make a variable that is assigned a value. While that is functionally accurate, a value is more so an idea of the kind of information a computer can store, pass around, choose, change, remove, etc.

> [!TIP]
> **A Computer Program Simply Manages Values**
>
> What is a `computer program?`
>
> A Google search would say, `"a sequence or set of instructions in a programming language for a computer to execute"`.
>
> We can **simplify** this definition down closer to simply `"telling the computer how to manage values"`.


### Activity - Control a Drawing Robot {#activity-control-a-drawing-robot}

This activity introduces the idea that a computer can control a machine by sending values to different parts of the machine.

The student will control a simple drawing robot using only the values `0` and `1`.


#### Prerequisites {#prerequisites}

-   Be able to distinguish the values `0` and `1`.
-   Be able to follow a sequence of instructions from top to bottom.


#### Concepts {#concepts}

-   Values
-   Binary Values
-   Input (Reading Values)
-   Output (Sending Values)


#### Coach Strategy {#coach-strategy}

Do not introduce programming syntax during this activity.

The goal is for the student to develop the intuition that different parts of a computer or machine can _receive_, _read_, and _respond to_ values.

Avoid explaining how the electronics inside the robot work unless the student specifically asks. It is enough to say that the robot has been built so that its controller responds differently to `0` and `1`.

The student should spend most of the activity predicting what the robot will do before being shown the result.


#### Guide and Solution {#guide-and-solution}

{{% details title="The Drawing Robot" open="true" %}}
Our robot has two wheels and a pen.

Each wheel has its own motor.

The computer controlling the robot can send one value to each motor.

| Value | Motor |
|-------|-------|
| `0`   | Off   |
| `1`   | On    |

The robot therefore receives two values:

```text
LEFT MOTOR     RIGHT MOTOR
     1              1
```

The first value is sent to the left motor.

The second value is sent to the right motor.

When both motors receive `1`, both wheels turn and the robot moves forward.

```text
LEFT      RIGHT

  1         1
  │         │
  ▼         ▼
 ON        ON
   \       /
    \     /
     ROBOT
       │
       ▼
    FORWARD
```
{{% /details %}}

{{% details title="Predict the Robot's Movement" %}}
{{% steps %}}
1.  Give the left motor the value `0` and the right motor the value `0`.

    Ask the student:

    _What do you think the robot will do?_

    Both motors are off, so the robot stops.

2.  Give both motors the value `1`.
    ```text
    LEFT     RIGHT
      1        1
    ```
    Both motors turn on, so the robot moves forward.

3.  Give the motors:
    ```text
    LEFT     RIGHT
      0        1
    ```
    Only the right wheel moves.

    The robot turns toward the left.

4.  Reverse the values:
    ```text
    LEFT     RIGHT
      1        0
    ```
    Only the left wheel moves.

    The robot turns toward the right.

5.  Ask the student to complete the following table before revealing the answers.

    | Left | Right | Robot Movement |
    |------|-------|----------------|
    | 0    | 0     | ?              |
    | 1    | 1     | ?              |
    | 0    | 1     | ?              |
    | 1    | 0     | ?              |
{{% /steps %}}

The completed table is:

| Left | Right | Robot Movement |
|------|-------|----------------|
| 0    | 0     | Stop           |
| 1    | 1     | Forward        |
| 0    | 1     | Turn Left      |
| 1    | 0     | Turn Right     |

Two very simple values are already enough to describe several different actions because the values are being sent to different places.
{{% /details %}}

{{% details title="Give the Robot a Pen" %}}
Now imagine that the robot has a pen attached underneath it.

The pen controller also receives either `0` or `1`.

For this part of the robot:

| Value | Pen      |
|-------|----------|
| `0`   | Pen Up   |
| `1`   | Pen Down |

Notice that `1` does not mean _motor on_ everywhere.

For a motor:

```text
1 → Motor On
```

For the pen:

```text
1 → Pen Down
```

The value is read by a particular part of the robot, and that part determines what the value means.

The computer can now send three values at once:

```text
LEFT MOTOR     RIGHT MOTOR     PEN
     1              1           1
```

The robot reads them as:

```text
Left motor on
Right motor on
Pen down
```

The robot therefore moves forward while drawing.
{{% /details %}}

{{% details title="Make a Drawing" %}}
The student will now act as the computer controlling the robot.

For each step, read the three values and determine what the robot does.

| Step | Left Motor | Right Motor | Pen |
|------|------------|-------------|-----|
| 1    | 1          | 1           | 1   |
| 2    | 1          | 1           | 1   |
| 3    | 0          | 1           | 1   |
| 4    | 1          | 1           | 1   |
| 5    | 0          | 0           | 0   |

{{% steps %}}
1.  Read the three values in the first row.
2.  Determine what each part of the robot does.
3.  Move an imaginary robot, toy, or marker according to those values.
4.  Continue to the next row.
5.  Before each step, predict what will happen.
{{% /steps %}}

The sequence can be interpreted as:

```text
Step 1
1  1  1
│  │  │
│  │  └── Pen Down
│  └───── Right Motor On
└──────── Left Motor On

Robot moves forward and draws.
```

```text
Step 2
1  1  1

Robot continues forward and continues drawing.
```

```text
Step 3
0  1  1

The left motor stops.
The right motor continues.
The robot turns left while drawing.
```

```text
Step 4
1  1  1

The robot moves forward again while drawing.
```

```text
Step 5
0  0  0

Both motors stop.
The pen is lifted.
```
{{% /details %}}

{{% details title="What Just Happened?" %}}
The computer did not need to directly understand ideas such as:

```text
Move the robot forward.

Turn the robot.

Draw a line.
```

Instead, different parts of the robot were given values.

```text
Computer
   │
   ├── 1 ──> Left Motor
   │
   ├── 1 ──> Right Motor
   │
   └── 1 ──> Pen Controller
```

Each part reads the value it receives and responds to it.

By sending different values at different times, the computer can cause the robot to perform a much more complicated action such as making a drawing.
{{% /details %}}


#### Debrief {#debrief}

<!--list-separator-->

-  1. What values did we use to control the robot?

    -   A. `0` and `1`
    -   B. `1` and `2`
    -   C. `ON` and `OFF`
    -   D. `LEFT` and `RIGHT`

    {{% details title="Answer" %}}
    **A.**

    The computer sent the values `0` and `1`.

    Words such as _on_, _off_, _left_, and _right_ describe how parts of the robot responded to those values.
    {{% /details %}}

<!--list-separator-->

-  2. What happens when both motors receive `1`?

    -   A. The robot stops.
    -   B. The robot moves forward.
    -   C. The pen is lifted.
    -   D. Nothing can be determined.

    {{% details title="Answer" %}}
    **B.**

    Each motor interprets `1` as _motor on_.

    Therefore:

    ```text
    LEFT     RIGHT
      1        1
      │        │
      ▼        ▼
     ON       ON
    ```

    Both wheels move and the robot travels forward.
    {{% /details %}}

<!--list-separator-->

-  3. What happens when both motors receive `0`?

    -   A. The robot moves forward.
    -   B. The robot turns left.
    -   C. The robot stops.
    -   D. The robot draws.

    {{% details title="Answer" %}}
    **C.**

    Both motors interpret `0` as _motor off_, so neither wheel moves.
    {{% /details %}}

<!--list-separator-->

-  4. Does the value `1` always mean "motor on"?

    -   A. Yes.
    -   B. No.

    {{% details title="Answer" %}}
    **B.**

    The meaning depends on which part receives the value.

    In this activity:

    ```text
    Motor receives 1 → Motor On

    Pen receives 1   → Pen Down
    ```

    The value itself is the same. Different parts of the robot are designed to interpret it differently.
    {{% /details %}}

<!--list-separator-->

-  5. Consider these values:

    ```text
    LEFT MOTOR     RIGHT MOTOR     PEN
         0              1           1
    ```

    What does the robot do?

    -   A. Stops and lifts the pen.
    -   B. Moves forward without drawing.
    -   C. Turns left while drawing.
    -   D. Turns right without drawing.

    {{% details title="Answer" %}}
    **C.**

    The left motor is off, the right motor is on, and the pen is down.

    Therefore the robot turns left while continuing to draw.
    {{% /details %}}

<!--list-separator-->

-  6. Which statement best describes what the computer did during this activity?

    -   A. It physically pushed the robot.
    -   B. It sent values to different parts of the robot.
    -   C. It only stored values without using them.
    -   D. It drew the picture itself.

    {{% details title="Answer" %}}
    **B.**

    The computer sent values to different parts of the robot.

    Those parts read the values and responded according to what the values meant to them.
    {{% /details %}}

<!--list-separator-->

-  7. What is the main idea demonstrated by this activity?

    -   A. Computers can only work with two values.
    -   B. A value always means the same thing everywhere.
    -   C. A computer can manage values by sending them to parts of a system that read and respond to them.
    -   D. Every computer must control a robot.

    {{% details title="Answer" %}}
    **C.**

    The important idea is not that every computer controls motors.

    The activity demonstrates a more general pattern:

    ```text
    value
      │
      ▼
    sent somewhere
      │
      ▼
    read by something
      │
      ▼
    response
    ```

    Computer programs can store values, read values, change values, create new values, and send values to other parts of a system.
    {{% /details %}}
