+++
title = "Data Types"
draft = false
weight = 20
+++

This page was created with the assistance of [GPT-5.6 Sol](https://openai.com/index/gpt-5-6/).


## Data Types {#data-types}

After learning [values]({{< relref "values" >}}) are, it's likely that you have already [chosen a programming language]({{< relref "/programming/teaching/programming-fundamentals/#what-about-the-first-programming-language" >}}).

Most general-purpose programming languages share a small set of common basic data types.

> [!NOTE]
> **General-Purpose**
>
> If you choose a programming language that's attractive to beginners, they are most definitely `general-purpose`.
> Domain-specific language (DSL) is another type of programming language. These languages cannot build any type of software (yes, even JavaScript, a general-purpose language can build an operating system that's extremely inefficient).
>
> An example DSL is CMake which is used to configure build files that create commands to compile code to binaries and link them to become an executable.

Your first language could be dynamically-typed where every [variable's]({{< relref "variables" >}}) type must be specified. For dynamically-typed languages, you still need to know the type of every single value you're looking at in your code.

{{% details title="Dynamically-typed languages (string example)" open="true" %}}
Python, Lua, JavaScript, Lisp...

```python { filename="Python" }
message = "hello"
# Variable message points to a value whose data type is a string.
```
{{% /details %}}

{{% details title="Statically-typed languages (string example)" open="true" %}}
C, C++, Rust, Java...

```C { filename="C/C++" }
char message[] = "hello";
// Variable message holds a value whose data type is an array of characters (string).
```
{{% /details %}}


### Basic Data Types {#basic-data-types}

This page will detail out 3-4 very common basic data types. Another familiar term for basic data type is called a `primitive` data type though across languages whether something is a primitive data type varies.

> [!TIP]
> **Primitive In C/C++ vs. Python**
>
> People might consider the data type `string` as a primitive data type in Python. In C/C++ we atomize this down further more down to characters (we don't have an explicit type called character in Python).

Here's an example of how strings can be regarded as "primitive" in Python but not in C/C++.

{{< tabs >}}
{{% tab "C/C++" %}}
```cpp
char a[] = "I'm an array of characters";
```
{{% /tab %}}

{{% tab "Python" %}}
```python
a = "I'm a string but my individual character are still 'strings'"
```
{{% /tab %}}
{{< /tabs >}}


### Numbers {#numbers}

A computer is able to handle different types of numbers. Any general-purpose programming language should be able to handle integers and decimals. In an unmanaged language, there are data types available depending on how much memory is needed to be reserved for a certain number.

> [!TIP]
> **Unmanaged Languages**
>
> Examples of unmanaged language include C/C++, Rust... These languages require you to manage memory yourself. They are often statically-typed.


#### Integers {#integers}

I would define these as non-decimal numbers. A typical integer can represent negative numbers as well. If an unmanaged language you can have different data types that can represent a varying ranges of numbers.

In C++, a standard `int` takes up about 4 bytes (32 bits) of memory. The range of numbers the `int` data type can represent is

```katex
-2,147,483,648 ~\mathrm{to}~ 2,147,483,647 \approx \pm 2 \times 10^9
```

What if you want to only have positive numbers? Well, you can use `unsigned int` in an unmanaged language like C/C++. First you don't need to reserve a bit that says whether a number is positive or negative. Second, the highest positive number you can now represent is twice that of the `int`. The maximum range of values are now

```katex
0 ~\mathrm{to}~ 4,294,967,295 \approx 4 \times 10^9
```


#### Decimals {#decimals}

Decimal numbers are defined as numbers that have a fractional part behind it. In the United States we are part of the majority that use the dot as our separator between the whole and fractional part.

Ten-Thousand `Comma/Dot` Two-Hundred and Six

{{< tabs >}}
{{% tab "Decimal Period" %}}
10,000.256
{{% /tab %}}

{{% tab "Decimal Comma" %}}
10.000,256
{{% /tab %}}
{{< /tabs >}}

> [!NOTE]
> **Dot or Comma**? (TRIVIA)
>
> In much of European countries and their former colonies (e.g. Vietnam and France), `,` is used as the separator between whole and fractional part while `.` is used as the separator between different orders of whole numbers.
>
> In 1958, during the creation of the programming language ALGOL, there was a heavy dispute regarding the type of decimal system that must be used. The programming language releases accounted for regional difference in the number system. This was famous historical **deadlock** where neither side of the ALGOL committee (Americans vs. Europeans) yielded.
>
> Nowadays most standard programming language uses the period decimal.

In C/C++, the two most utilized data types for decimal numbers are `double` and `float`.

<!--list-separator-->

-  Float vs. Double

    The basic idea is that a `float` represents decimal numbers but a `float` can represent decimal numbers that are twice as big. The more digits the a number has (more so the fractional part), the more memory is needed to represent the number.

    > [!DANGER]
    > **Data Type Names Can Vary**
    >
    > This distinction is not absolute for all programming languages. For example in Python, the data type `float` is implemented as a `double` in size.


### Characters and Strings {#characters-and-strings}

Unmanaged languages most likely have the data type for a single character, usually called `char`. Computers are dumb so they don't really understand any other symbols than binary representations of numbers.

In an unmanaged language like C/C++ or Rust, you are able to see that the data type `char` actually only stores number. The `char` becomes a number when a compiler is tasked to read from the translation unit and convert the character to a number according to the [ASCII chart](https://www.ascii-code.com).

> [!NOTE]
> **Translation Unit**
>
> In an unmanaged language, a translation unit is the collection of source code packaged together and processed by the compiler. In C/C++ this can be a single source file. For Rust, its fundamental translation unit is a crate.

```cpp { filename="C/C++" }
// These two lines of code are valid.
char a = 'a';
char b = 98;
```

What about a `string`? A string is simply a sequence/array/collection of characters. most all managed data-type include a built-in data type for `string`.


### Booleans {#booleans}

This allows you to express a binary (yes/no) decision. Boolean data-types can be `bool`, `boolean`...

Like characters, internally booleans are numbers. In C, a `bool` is true when it holds the number 0 for `false` and 1 or any non-zero number for `true`.

```cpp { filename="C/C++" }
bool no = false;
bool no2 = 0;
bool yes = true;
bool yes2 = 1;
bool yes3 = 123;
```

\`\`\`org


### Debrief {#debrief}

This quiz checks your understanding of basic data types, including integers, floating-point numbers, characters, strings, and booleans.


#### 1. What is the main purpose of a data type? {#1-dot-what-is-the-main-purpose-of-a-data-type}

A. To categorize different kinds of values
B. To give every variable a unique name
C. To determine which operating system runs the program
D. To determine how long a program is

{{% details title="Show Answer" %}}
**A. To categorize different kinds of values**

A data type describes what kind of value something is, such as an integer, string, or Boolean.
{{% /details %}}


#### 2. Which of the following are common basic data types? (Mark all that apply.) {#2-dot-which-of-the-following-are-common-basic-data-types--mark-all-that-apply-dot}

A. Boolean
B. Integer
C. String
D. Window

{{% details title="Show Answer" %}}
**A, B, and C**

Booleans, integers, and strings are common basic data types or basic value categories across many programming languages.

A window is normally an object provided by a graphical user interface library, not a primitive/basic data type.
{{% /details %}}


#### 3. Which value is an integer? {#3-dot-which-value-is-an-integer}

A. `3.14`
B. `"17"`
C. `-17`
D. `true`

{{% details title="Show Answer" %}}
**C. `-17`**

Integers are whole numbers without a fractional part. Integers can also be negative.
{{% /details %}}


#### 4. Which value would normally require a floating-point data type? {#4-dot-which-value-would-normally-require-a-floating-point-data-type}

A. `42`
B. `12.75`
C. `"12.75"`
D. `false`

{{% details title="Show Answer" %}}
**B. `12.75`**

The value contains a fractional part, so it would normally be represented using a floating-point data type.
{{% /details %}}


#### 5. What is the most important difference between a signed and unsigned integer? {#5-dot-what-is-the-most-important-difference-between-a-signed-and-unsigned-integer}

A. Unsigned integers cannot represent negative numbers
B. Signed integers cannot represent positive numbers
C. Unsigned integers can only contain `0` or `1`
D. Signed integers always require twice as much memory

{{% details title="Show Answer" %}}
**A. Unsigned integers cannot represent negative numbers**

An unsigned integer uses its available values for zero and positive numbers.
{{% /details %}}


#### 6. A 32-bit unsigned integer can represent approximately what maximum value? {#6-dot-a-32-bit-unsigned-integer-can-represent-approximately-what-maximum-value}

A. 255
B. 65 thousand
C. 2 billion
D. 4 billion

{{% details title="Show Answer" %}}
**D. 4 billion**

A 32-bit unsigned integer typically has a range of

```katex
0 ~\mathrm{to}~ 4,294,967,295
```
{{% /details %}}


#### 7. Which statements about floating-point numbers are true? (Mark all that apply.) {#7-dot-which-statements-about-floating-point-numbers-are-true--mark-all-that-apply-dot}

A. They can represent values with fractional parts
B. A `double` normally provides more precision than a `float` in C/C++
C. They can only represent positive numbers
D. Different languages may use the names `float` and `double` differently

{{% details title="Show Answer" %}}
**A, B, and D**

Floating-point numbers can contain fractional parts.

In C/C++, `double` normally provides greater precision than `float`.

Different programming languages may use these type names differently. For example, Python's `float` is generally implemented using double-precision floating point.
{{% /details %}}


#### 8. Consider the following C++ code. {#8-dot-consider-the-following-c-plus-plus-code-dot}

```cpp { filename="C++" }
char letter = 'A';
```

What kind of value is `letter` intended to represent?

A. Integer
B. Character
C. String
D. Boolean

{{% details title="Show Answer" %}}
**B. Character**

The `char` type is commonly used to represent a single character.
{{% /details %}}


#### 9. Why can this C++ code be valid? {#9-dot-why-can-this-c-plus-plus-code-be-valid}

```cpp { filename="C++" }
char letter = 65;
```

A. Characters are associated with numeric character codes
B. Every integer is automatically a string
C. `65` is literally stored as the letter `A` in the source file
D. C++ ignores the assigned number

{{% details title="Show Answer" %}}
**A. Characters are associated with numeric character codes**

Characters are internally represented using numbers according to a character encoding.

For example, in ASCII the value `65` represents uppercase `A`.
{{% /details %}}


#### 10. What best describes a string? {#10-dot-what-best-describes-a-string}

A. A single character
B. A sequence of characters
C. A number with a fractional part
D. A true-or-false value

{{% details title="Show Answer" %}}
**B. A sequence of characters**

A string represents a sequence or collection of characters, such as `"hello"`.
{{% /details %}}


#### 11. Which of the following are strings in Python? (Mark all that apply.) {#11-dot-which-of-the-following-are-strings-in-python--mark-all-that-apply-dot}

```python { filename="Python" }
a = "hello"
b = "A"
c = 42
d = "42"
```

A. `a`
B. `b`
C. `c`
D. `d`

{{% details title="Show Answer" %}}
**A, B, and D**

All values enclosed in quotation marks are strings here.

Even `"A"` is a string in Python. Python does not have a separate `char` type like C or C++.

`42` without quotation marks is an integer.
{{% /details %}}


#### 12. Consider these two Python values. {#12-dot-consider-these-two-python-values-dot}

```python { filename="Python" }
a = 42
b = "42"
```

What is the difference between them?

A. There is no difference
B. `a` is an integer while `b` is a string
C. `a` is a string while `b` is an integer
D. Both are floating-point numbers

{{% details title="Show Answer" %}}
**B. `a` is an integer while `b` is a string**

Quotation marks matter.

`42` represents a number.

`"42"` represents two characters: `4` followed by `2`.
{{% /details %}}


#### 13. A game needs to store how many lives the player has remaining. Which type is most appropriate? {#13-dot-a-game-needs-to-store-how-many-lives-the-player-has-remaining-dot-which-type-is-most-appropriate}

A. Boolean
B. Integer
C. String
D. Character

{{% details title="Show Answer" %}}
**B. Integer**

The number of lives is a whole-number count such as `0`, `1`, `2`, or `3`.
{{% /details %}}


#### 14. A game needs to store whether a door is currently locked. Which type is most appropriate? {#14-dot-a-game-needs-to-store-whether-a-door-is-currently-locked-dot-which-type-is-most-appropriate}

A. Boolean
B. Integer
C. String
D. Floating-point number

{{% details title="Show Answer" %}}
**A. Boolean**

The door has two relevant states:

-   Locked
-   Not locked

That makes a Boolean a natural choice.
{{% /details %}}


#### 15. Which of the following situations would most naturally use a Boolean? (Mark all that apply.) {#15-dot-which-of-the-following-situations-would-most-naturally-use-a-boolean--mark-all-that-apply-dot}

A. Whether the player is alive
B. The player's username
C. Whether an enemy has detected the player
D. The player's exact position on the map

{{% details title="Show Answer" %}}
**A and C**

Both describe two-way conditions.

The player is either alive or not alive.

The enemy has either detected the player or has not detected the player.
{{% /details %}}


#### 16. What kind of information does a Boolean primarily represent? {#16-dot-what-kind-of-information-does-a-boolean-primarily-represent}

A. A sequence of characters
B. A whole number
C. A binary condition
D. A decimal number

{{% details title="Show Answer" %}}
**C. A binary condition**

A Boolean represents two possible logical states, usually written as `true` and `false`.
{{% /details %}}


#### 17. Consider the following C++ code. {#17-dot-consider-the-following-c-plus-plus-code-dot}

```cpp { filename="C++" }
bool value = 123;
```

What will `value` become when `123` is converted to a Boolean?
A. `false`
B. `true`
C. `"123"`
D. The program must fail to compile

{{% details title="Show Answer" %}}
**B. `true`**

When an integer is converted to `bool` in C++, zero becomes `false` and a nonzero value becomes `true`.

Since `123` is nonzero, it becomes `true`.
{{% /details %}}


#### 18. Which statement about data types across programming languages is most accurate? {#18-dot-which-statement-about-data-types-across-programming-languages-is-most-accurate}

A. Every programming language has exactly the same types
B. Type names and implementations can differ between languages
C. Only statically-typed languages have data types
D. Only compiled languages have data types

{{% details title="Show Answer" %}}
**B. Type names and implementations can differ between languages**

Many languages share similar concepts such as integers, strings, and Booleans, but their exact type systems and representations can differ.
{{% /details %}}


#### 19. Why do data types still matter in a dynamically-typed language such as Python? {#19-dot-why-do-data-types-still-matter-in-a-dynamically-typed-language-such-as-python}

A. Variables must explicitly declare their type
B. Values still have types even when the variable does not specify one
C. Python does not actually have data types
D. Types only matter when the program is compiled

{{% details title="Show Answer" %}}
**B. Values still have types even when the variable does not specify one**

For example:

```python { filename="Python" }
value = 10
```

You did not explicitly declare `value` as an integer variable, but the value `10` still has the type `int`.
{{% /details %}}


#### 20. Which statement best summarizes the relationship between values and data types? {#20-dot-which-statement-best-summarizes-the-relationship-between-values-and-data-types}

A. Data types categorize different kinds of values
B. Values categorize different kinds of variables
C. Every value must be a string
D. Values only have types in C/C++

{{% details title="Show Answer" %}}
**A. Data types categorize different kinds of values**

For example:

-   `42` → integer
-   `3.14` → floating-point number
-   `"hello"` → string
-   `true` → Boolean

The data type tells us what kind of value we are working with.
{{% /details %}}


## Related {#related}

-   Data types are how you categorize different kinds of [values]({{< relref "values" >}}).
-   You should also check out [variables]({{< relref "variables" >}}).
