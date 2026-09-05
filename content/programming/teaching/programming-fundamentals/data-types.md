+++
title = "Data Types"
draft = false
weight = 20
+++

This page was created with the assistance of [GPT-5.5 Sol](https:openai.com/index/gpt-5-6/).


## Data Types {#data-types}

After learning [values]({{< relref "values" >}}) are, it's likely that you have already [chosen a programming language]({{< relref "programming-fundamentals.md#what-about-the-first-programming-language" >}}).

Most general-purpose programming languages share a small set of common basic data types.

> [!NOTE]
> **General-Purpose**
>
> If you choose a programming language that's attractive to beginners, they are most definitely `general-purpose`.
> Domain-specific language (DSL) is another type of programming language. These languages cannot build any type of software (yes, even JavaScript, a general-purpose language can build an operating system that's extremely inefficient).
>
> An example DSL is CMake which is used to configure build files that create commands to compile code to binaries and link them to become an executable.

Your first language could be dynamically-typed where every [variable's]({{< relref "programming-fundamentals.md#variable" >}}) type must be specified. For dynamically-typed languages, you still need to know the type of every single value you're looking at in your code.

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


### About "Primitive" Data Types {#about-primitive-data-types}

Here are some common basic data types. Another familiar term for basic data type is primitive though across languages whether something is a primitive data type varies.

> [!TIP]
> **Primitive In C/C++ vs. Python**
>
> People might consider the data type `string` as a primitive data type in Python. In C/C++ we atomize this down further to character (we don't have an explicit type called character in Python).

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

In an unmanaged language like C/C++ or Rust, you are able to see that the data type `char` actually only stores number. The `char` becomes a number when a compiler is tasked to read from the translation unit and convert the character to a number according to the [ASCII chart](https:www.ascii-code.com).

> [!NOTE]
> **Translation Unit**
>
> In an unmanaged language, a translation unit is the collection of source code packaged together and processed by the compiler. In C/C++ this can be a single source file. For Rust, its fundamental translation unit is a crate.

```cpp { filename="C/C++" }
// These two lines of code are valid.
char a = 'a';
char b = 98;
```

What about a `string`? A string is simply a sequence/array/collection of characters. Almost all managed data-type include a built-in data type for `string`.


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


## Related {#related}

-   Data types are how you categorize different kinds of [values]({{< relref "values" >}}).
-   You should also check out [variables]({{< relref "programming-fundamentals.md#variable" >}}).
