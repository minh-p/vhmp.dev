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
