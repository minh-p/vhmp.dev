+++
title = "Functions"
draft = false
+++

## Functions {#functions}

> [!TIP]
> **What are Functions (Simple)**
>
> `Functions` allow us to write less code while generating the same amount of instructions to a computer. Different instructions can be generated depending on the `arguments` you give to the `function`.

`Functions` reduce the amount of code you have to write while allowing variations in the same type of action. For example, you could write a function that handles the withdrawal of money. You just need to let the function know how much money to withdraw. This is quite useful instead of writing different arbitrary units of code for different amounts of money in different places.


### Arguments {#arguments}

We pass values to a `function` for it to perform its action. For example, if you made a function draw a square, you could pass in its side length or its x-y coordinates as three `required` arguments. A common function in many programming languages is the `print` function. In most programming languages, you can send in an `arugment` of the data-type `string` to the print function.

{{< tabs >}}
{{% tab Python %}}
```python
print("I'm a string")
```
{{% /tab %}}

{{% tab Lua %}}
```lua
print("I'm a string")
```
{{% /tab %}}

{{% tab JavaScript %}}
```cpp
console.log("I'm a string");
```
{{% /tab %}}

{{% tab C %}}
```c
#include <stdio.h>

int main() {
    printf("I'm a string!\n");
    return 0;
}
```
{{% /tab %}}

{{% tab "C++" %}}
In C++, we `insert` the string into the `output stream`. In this case, we `insert` a string into the standard output.

```cpp
#include <iostream>

int main() {
    std::cout << "I'm a string" << std::endl;
    return 0;
}
```

The symbol `<<` is an the `insertion` operator that's `overloaded` by the C++ standard library. Unlike built-in operators which are `translated` by the compiler, `overloaded operators` are declared and defined by a function.

Here's the declaration of the function `operator<<`.

```cpp
template<
    class CharT,
    class Traits,
    class Allocator
    >
std::basic_ostream<CharT, Traits>&
operator<<(
           std::basic_ostream<CharT, Traits>& os,
           const std::basic_string<CharT, Traits, Allocator>& str
           );
```

For this example, you can mentally reduce it to:

```cpp
std::ostream& operator<<(std::ostream& os, const std::string& str);
```
{{% /tab %}}
{{< /tabs >}}

We do not _argue_ with the function. The word `argument` means `something from which another thing may be deduced`. It originally appeared in mathematics going as early as the 14th Century. The field of Computer Science much depended on the well thought out field of Mathematics. In mathematics, it is a `mathematical quantity from which another quantity may be deduced, or on which its calculation depends`.


### Parameters {#parameters}

Think `parameters` as the variables that holds your `arguments`. When you make a function, you will have to declare `parameters` that will refer to `arguments`. `Parameters` are how you work with the function's `arguments` while defining your `function`.

In this example, we create a function that returns the sum of two integer arguments. These examples in different programming languages also uses `type-hinting` for the featured `dynamically-typed languages`. `a` and `b` are your `parameters`.

{{< tabs >}}
{{% tab Python %}}
```python
def sum(a: int, b: int):
    return a + b
```
{{% /tab %}}

{{% tab Lua %}}
```lua
function sum(a: number, b: number)
   return a + b
end
```
{{% /tab %}}

{{% tab "C/C++" %}}
```cpp
int sum(int a, int b) {
    return a + b;
}
```
{{% /tab %}}
{{< /tabs >}}


### Optional and Required Arguments {#optional-and-required-arguments}

In many languages, especially dynamically-typed languages, there's usually a way to make optional and required arguments. If not, you'll have to stick with `overloading` your `functions`.

> [!NOTE]
> **Overloading**
>
> A programmer can `overload` a function in a programming language that supports it by creating different functions of the same name but different parameters' types or different amounts of parameters.
>
> E.g. In Java, you can only `overload` a method. In Java 8, there's an `Optional type`.

Otherwise, languages usually have an `optional type` in their standard library. Most primitively (if a language allows it), you can use a `null pointer`. The examples below are very dense because they are language-specific. Feel free to peruse other languages besides the one you are learning from.

{{< tabs >}}
{{% tab Python %}}
Python supports ****default arguments**** directly. This is usually the simplest way to make an argument optional.

```python
def greet(name="World", punctuation="!"):
    print("Hello, " + name + punctuation)

greet()
greet("Alice")
greet("Alice", "?")
```

This prints:

```text
Hello, World!
Hello, Alice!
Hello, Alice?
```

When the absence of a value has a special meaning, Python commonly uses `None`.

```python
def greet(name: str | None = None):
    if name is None:
        name = "World"

    print("Hello, " + name)

greet()
greet("Alice")
```

Here, the type

```python
str | None
```

means that `name` may contain either a string or `None`.

Python also has `@overload` for static type checking, but it is normally used when different argument combinations produce different type signatures. It is usually unnecessary just to make an ordinary argument optional.

```python
def greet(name="World"):
    print("Hello, " + name)
```

is therefore generally preferable to trying to simulate function overloading.
{{% /tab %}}

{{% tab Lua %}}
Lua handles function arguments differently from Python and C++.

****Every ordinary function parameter in Lua is effectively optional.****

If an argument is not provided, its corresponding parameter receives `nil`.

```lua
local function greet(name, punctuation)
    print(name)
    print(punctuation)
end

greet()
```

This behaves approximately as though Lua had called:

```lua
greet(nil, nil)
```

Because of this, Lua does not need special syntax for optional parameters.

You usually check for `nil` and provide the default yourself.

```lua
local function greet(name, punctuation)
    if name == nil then
        name = "World"
    end

    if punctuation == nil then
        punctuation = "!"
    end

    print("Hello, " .. name .. punctuation)
end

greet()
greet("Alice")
greet("Alice", "?")
```

This prints:

```text
Hello, World!
Hello, Alice!
Hello, Alice?
```

For values where `false` is not meaningful, Lua programmers will also commonly use `or`:

```lua
local function greet(name, punctuation)
    name = name or "World"
    punctuation = punctuation or "!"

    print("Hello, " .. name .. punctuation)
end
```

However, remember that Lua considers both `nil` and `false` to be false values.

For example, this can be wrong:

```lua
local function configure(enabled)
    enabled = enabled or true
end
```

If someone deliberately calls

```lua
configure(false)
```

then `enabled or true` produces `true`.

When `false` is a legitimate argument, explicitly check for `nil` instead:

```lua
local function configure(enabled)
    if enabled == nil then
        enabled = true
    end

    print(enabled)
end

configure()       -- true
configure(false)  -- false
```

Lua also permits extra arguments:

```lua
local function greet(name)
    print("Hello, " .. (name or "World"))
end

greet("Alice", 10, true)
```

If the function does not use `...`, those additional arguments are simply not assigned to named parameters.

To deliberately accept an arbitrary number of arguments, Lua uses ****varargs****:

```lua
local function printAll(...)
    for index, value in ipairs({...}) do
        print(index, value)
    end
end

printAll("Alice", 10, true)
```

So in Lua, "optional arguments" are not a separate language feature. They naturally result from Lua assigning `nil` to parameters whose arguments were omitted.
{{% /tab %}}

{{% tab C %}}
C does ****not**** have default arguments.

A function such as

```c
void greet(const char *name);
```

must normally be called with exactly the arguments required by its declaration.

One common C technique is to use a sentinel value such as `NULL` to represent an omitted value:

```c
#include <stdio.h>

void greet(const char *name)
{
    if (name == NULL) {
        name = "World";
    }

    printf("Hello, %s!\n", name);
}

int main(void)
{
    greet(NULL);
    greet("Alice");
}
```

Another common technique is to provide separate functions:

```c
#include <stdio.h>

void greet(const char *name)
{
    printf("Hello, %s!\n", name);
}

void greet_default(void)
{
    greet("World");
}

int main(void)
{
    greet_default();
    greet("Alice");
}
```

C also supports variadic functions using `...`, such as `printf`:

```c
printf("%s is %d years old\n", "Alice", 15);
```

However, variadic arguments are generally ****not**** a replacement for ordinary optional parameters. They sacrifice type information and require the function to have some way to determine how many arguments were supplied and what their types are.

For ordinary APIs, explicit parameters, sentinel values, configuration structures, or additional helper functions are usually clearer.
{{% /tab %}}

{{% tab "C++" %}}
C++ directly supports ****default arguments****.

For simple optional parameters, this is usually the clearest solution.

```cpp
#include <iostream>
#include <string_view>

void greet(
    std::string_view name = "World",
    std::string_view punctuation = "!"
)
{
    std::cout << "Hello, " << name << punctuation << '\n';
}

int main()
{
    greet();
    greet("Alice");
    greet("Alice", "?");
}
```

This prints:

```text
Hello, World!
Hello, Alice!
Hello, Alice?
```

C++ also supports ****function overloading****.

An overload is useful when different forms of an operation deserve separate interfaces rather than merely different default values.

```cpp
#include <iostream>
#include <string_view>

void greet()
{
    std::cout << "Hello, World!\n";
}

void greet(std::string_view name)
{
    std::cout << "Hello, " << name << "!\n";
}

int main()
{
    greet();
    greet("Alice");
}
```

For a simple example like this, a default argument is usually less repetitive:

```cpp
void greet(std::string_view name = "World");
```

C++ also provides `std::optional` when ****the presence or absence of a value is itself meaningful****.

```cpp
#include <iostream>
#include <optional>
#include <string>

void greet(const std::optional<std::string>& name = std::nullopt)
{
    if (name) {
        std::cout << "Hello, " << *name << "!\n";
    } else {
        std::cout << "Hello, mysterious stranger!\n";
    }
}

int main()
{
    greet();
    greet("Alice");
}
```

Here, `std::nullopt` means that no name was supplied.

A useful rule of thumb is:

-   Use a ****default argument**** when there is an obvious normal default.
-   Use an ****overload**** when different forms of the operation deserve distinct interfaces.
-   Use `std::optional<T>` when "there is no value" is meaningful information that should be represented explicitly.
{{% /tab %}}
{{< /tabs >}}


### Where Function Lies In Your Programming Journey {#where-function-lies-in-your-programming-journey}

We created programming language to make sending instructions to the computer simpler. As you progress further in your computer science studies, you'll be required to learn assembly languages (after experiencing an unmanaged language like C/C++) which is the level of abstraction before going down further to computer instruction sets which are ultimately represented as binary code that correspond to different central processing units like x86, Arm, and RISC-V.

As you get further down, the tools you learned early in more abstracted languages might change in its form but the semantics (the idea) transfer. E.g. in assembly languages, the idea of a function is broken down into subroutines and the direct management and usage of addresses to handle `parameters`.
