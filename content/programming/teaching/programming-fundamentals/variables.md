+++
title = "Variables"
draft = false
weight = 30
+++

## Variables {#variables}

Think of variables as a tracker of values. Typically, we say that we `create` a variable and we `assign` a value to that variable. We also often can say that we `intialize` a variable with a `value` if we want to be specific and say that memory is allocated to a variable and it will automatically keep track of a specific `value`.

To use a variable, you have to make sure it is declared (and most likely defined in the same process).


### Prerequisites {#prerequisites}

If you didn't understand the paragraph above then, do some searches to understand the vocabulary. Most likely however, you haven't read the previous two concepts:

-   [Values]({{< relref "values" >}})
-   [Data Types]({{< relref "data-types" >}})


### Modifiers {#modifiers}

Variables in many programming languages can be created differently by being `modified`.


#### Scope {#scope}

Different kinds of variables can be created. In both dynamically-typed and statically-typed languages, there's often a way to make a variable `global` or `local` to a specific kind of scope.

> [!NOTE]
> **Dynamically-typed vs. Statically-typed**
>
> Dynamically-typed languages figure out what type of data your variable hold automatically while statically-typed languages require you to specify what the type is.

Variables referring to an integer in some different programming languages.

{{< tabs >}}
{{% tab Python %}}
```python
my_number = 10

def hello():
    global my_number
    # global operator makes
    # variable global.
    my_number = 20

hello()
print(my_number) # We expect 20 now
```
{{% /tab %}}

{{% tab Lua %}}
```lua
-- Outside of any scope (function, loops, if-statements...)
myNumber = 10

function foo()
    local myLocal = 20
end

print(myNumber) -- Legal
print(myLocal) -- Gives nil. Not what we intended
```
{{% /tab %}}

{{% tab JavaScript %}}
```javascript
// block-scoped
if (true) {
    let myNumber = 1
}

console.log(myNumber) // will error

// function-scope
function bar() {
    if (true) {
        var hey = 10
    }
    print(hey) // does not error because of var
}
```
{{% /tab %}}

{{% tab "C++" %}}
There's no examples because this is the cool kids club. (What discussed is too extensive).

Variables are automatically block-scoped or scoped to the file as a global.
{{% /tab %}}
{{< /tabs >}}


### Debrief {#debrief}

This quiz checks your understanding of variables, assignment, initialization, scope, and how variables behave across different programming languages.

Questions are ordered approximately from easiest to hardest.


#### 1. What is the main purpose of a variable? {#1-dot-what-is-the-main-purpose-of-a-variable}

A. To track or refer to a value
B. To permanently store an entire program
C. To determine which operating system is running
D. To automatically print values

{{% details title="Show Answer" %}}
**A. To track or refer to a value**

A variable gives a program a way to keep track of a value so that the value can be used or changed later.
{{% /details %}}


#### 2. Which statement best describes assignment? {#2-dot-which-statement-best-describes-assignment}

A. Giving a value to a variable
B. Creating a new programming language
C. Printing a variable
D. Removing the variable from the program

{{% details title="Show Answer" %}}
**A. Giving a value to a variable**

Assignment associates a value with a variable.
{{% /details %}}


#### 3. After the second assignment, what value does `score` refer to? {#3-dot-after-the-second-assignment-what-value-does-score-refer-to}

{{< tabs >}}
{{% tab Python %}}
```python
score = 10
score = 20
```
{{% /tab %}}

{{% tab Lua %}}
```lua
score = 10
score = 20
```
{{% /tab %}}

{{% tab JavaScript %}}
```javascript
let score = 10
score = 20
```
{{% /tab %}}

{{% tab "C++" %}}
```cpp
int score = 10;
score = 20;
```
{{% /tab %}}
{{< /tabs >}}

A. `10`
B. `20`
C. `30`
D. Both `10` and `20`

{{% details title="Show Answer" %}}
**B. `20`**

The second assignment changes the value associated with `score`.

Although the syntax differs between languages, the general idea of reassignment is the same.
{{% /details %}}


#### 4. Which word describes giving a variable its first value when it is created? {#4-dot-which-word-describes-giving-a-variable-its-first-value-when-it-is-created}

A. Iteration
B. Initialization
C. Comparison
D. Invocation

{{% details title="Show Answer" %}}
**B. Initialization**

Initialization gives a variable its initial value when the variable is created.
{{% /details %}}


#### 5. In each example, what is the initial value of `score`? {#5-dot-in-each-example-what-is-the-initial-value-of-score}

{{< tabs >}}
{{% tab Python %}}
```python
score = 10
```
{{% /tab %}}

{{% tab Lua %}}
```lua
local score = 10
```
{{% /tab %}}

{{% tab JavaScript %}}
```javascript
let score = 10
```
{{% /tab %}}

{{% tab "C++" %}}
```cpp
int score = 10;
```
{{% /tab %}}
{{< /tabs >}}

A. `0`
B. `1`
C. `10`
D. The variable has no value

{{% details title="Show Answer" %}}
**C. `10`**

In every example, `score` begins with the value `10`.

The syntax used to create the variable differs, but the general concept is the same.
{{% /details %}}


#### 6. What does the scope of a variable determine? {#6-dot-what-does-the-scope-of-a-variable-determine}

A. Its exact numerical value
B. Where its name can be used in the program
C. How quickly it changes
D. What operating system the program requires

{{% details title="Show Answer" %}}
**B. Where its name can be used in the program**

Scope determines where a variable's name is visible and accessible.
{{% /details %}}


#### 7. What best describes a local variable? {#7-dot-what-best-describes-a-local-variable}

A. A variable available everywhere in the program
B. A variable restricted to some particular scope
C. A variable that can only contain integers
D. A variable stored on another computer

{{% details title="Show Answer" %}}
**B. A variable restricted to some particular scope**

A local variable is available only within some limited region of a program, such as a function or block.
{{% /details %}}


#### 8. What best describes a global variable? {#8-dot-what-best-describes-a-global-variable}

A. A variable declared in a broad program scope
B. A variable that can only contain strings
C. A variable that cannot change
D. A variable that only exists inside a loop

{{% details title="Show Answer" %}}
**A. A variable declared in a broad program scope**

A global variable has a broader scope than a local variable and can often be accessed from multiple parts of a program.
{{% /details %}}


#### 9. Which statements about variables are true? (Mark all that apply.) {#9-dot-which-statements-about-variables-are-true--mark-all-that-apply-dot}

A. Variables can keep track of values
B. Variables can often be assigned new values
C. Variables can exist in different scopes
D. Every variable must be global

{{% details title="Show Answer" %}}
**A, B, and C**

Variables can track values, can often be reassigned, and can exist in different scopes.

Not every variable is global.
{{% /details %}}


#### 10. In each example, which variable is local to the function? {#10-dot-in-each-example-which-variable-is-local-to-the-function}

{{< tabs >}}
{{% tab Python %}}
```python
outside = 10

def foo():
    inside = 20
```
{{% /tab %}}

{{% tab Lua %}}
```lua
outside = 10

function foo()
    local inside = 20
end
```
{{% /tab %}}

{{% tab JavaScript %}}
```javascript
let outside = 10

function foo() {
    let inside = 20
}
```
{{% /tab %}}

{{% tab "C++" %}}
```cpp
int outside = 10;

void foo() {
    int inside = 20;
}
```
{{% /tab %}}
{{< /tabs >}}

A. `outside`
B. `inside`
C. Both variables
D. Neither variable

{{% details title="Show Answer" %}}
**B. `inside`**

In each example, `inside` is created inside the function and belongs to that function's local scope.

`outside` is declared outside the function.
{{% /details %}}


#### 11. What should happen if code tries to access the local variable after leaving its scope? {#11-dot-what-should-happen-if-code-tries-to-access-the-local-variable-after-leaving-its-scope}

{{< tabs >}}
{{% tab Python %}}
```python
def foo():
    inside = 20

foo()
print(inside)
```
{{% /tab %}}

{{% tab Lua %}}
```lua
function foo()
    local inside = 20
end

foo()
print(inside)
```
{{% /tab %}}

{{% tab JavaScript %}}
```javascript
function foo() {
    let inside = 20
}

foo()
console.log(inside)
```
{{% /tab %}}

{{% tab "C++" %}}
```cpp
void foo() {
    int inside = 20;
}

int main() {
    foo();
    // inside cannot be named here
}
```
{{% /tab %}}
{{< /tabs >}}

A. The local variable automatically becomes global
B. The local variable is not accessible through that local name
C. The variable always becomes `0`
D. The variable becomes a string

{{% details title="Show Answer" %}}
**B. The local variable is not accessible through that local name**

The exact result differs between languages.

Python and JavaScript will report an error when that nonexistent name is accessed.

Lua commonly looks for a global named `inside` and produces `nil` if none exists.

In C++, using `inside` there would fail during compilation because the name is outside its scope.
{{% /details %}}


#### 12. Which of the following can affect scope? (Mark all that apply.) {#12-dot-which-of-the-following-can-affect-scope--mark-all-that-apply-dot}

A. Functions
B. Blocks
C. Loops
D. Conditional statements

{{% details title="Show Answer" %}}
**A, B, C, and D**

Depending on the language, functions, blocks, loops, and conditional statements can introduce or affect scopes.

The exact rules differ between languages.
{{% /details %}}


#### 13. What is one major difference between dynamically-typed and statically-typed languages? {#13-dot-what-is-one-major-difference-between-dynamically-typed-and-statically-typed-languages}

A. Dynamically-typed languages do not have data types
B. Statically-typed languages determine variable types statically
C. Statically-typed languages cannot use strings
D. Dynamically-typed languages cannot use functions

{{% details title="Show Answer" %}}
**B. Statically-typed languages determine variable types statically**

A dynamically-typed language associates types with values at runtime.

A statically-typed language determines types as part of static analysis, usually before the program runs.
{{% /details %}}


#### 14. Which tabs contain dynamically-typed languages? (Mark all that apply.) {#14-dot-which-tabs-contain-dynamically-typed-languages--mark-all-that-apply-dot}

{{< tabs >}}
{{% tab Python %}}
```python
score = 10
```
{{% /tab %}}

{{% tab Lua %}}
```lua
score = 10
```
{{% /tab %}}

{{% tab JavaScript %}}
```javascript
let score = 10
```
{{% /tab %}}

{{% tab "C++" %}}
```cpp
int score = 10;
```
{{% /tab %}}
{{< /tabs >}}

A. Python
B. Lua
C. JavaScript
D. C++

{{% details title="Show Answer" %}}
**A, B, and C**

Python, Lua, and JavaScript are dynamically typed.

C++ is statically typed.
{{% /details %}}


#### 15. In each example, what value will `number` have after `change()` is called? {#15-dot-in-each-example-what-value-will-number-have-after-change-is-called}

{{< tabs >}}
{{% tab Python %}}
```python
number = 10

def change():
    global number
    number = 20

change()
```
{{% /tab %}}

{{% tab Lua %}}
```lua
number = 10

function change()
    number = 20
end

change()
```
{{% /tab %}}

{{% tab JavaScript %}}
```javascript
let number = 10

function change() {
    number = 20
}

change()
```
{{% /tab %}}

{{% tab "C++" %}}
```cpp
int number = 10;

void change() {
    number = 20;
}

int main() {
    change();
}
```
{{% /tab %}}
{{< /tabs >}}

A. `10`
B. `20`
C. `30`
D. The variable disappears

{{% details title="Show Answer" %}}
**B. `20`**

In each example, the function modifies a variable declared outside the function.

The syntax and lookup rules differ between languages, but the resulting value is `20` in all four examples.
{{% /details %}}


#### 16. `Python` What does the `global` statement do? {#16-dot-python-what-does-the-global-statement-do}

```python
global number
```

A. Converts `number` into an integer
B. Tells Python that assignments should refer to the global binding
C. Makes `number` constant
D. Creates a new function

{{% details title="Show Answer" %}}
**B. Tells Python that assignments should refer to the global binding**

Inside a function, assigning to a name normally makes that name local unless Python is told otherwise.

`global number` tells Python that assignments to `number` refer to the global binding.
{{% /details %}}


#### 17. `Lua` What does `local` do in this declaration? {#17-dot-lua-what-does-local-do-in-this-declaration}

```lua
local score = 10
```

A. Makes `score` global
B. Creates `score` in a local scope
C. Makes `score` constant
D. Changes `score` into a string

{{% details title="Show Answer" %}}
**B. Creates `score` in a local scope**

Lua uses the `local` keyword to create a local variable.

Without `local`, assignment to a previously undeclared name commonly refers to a global.
{{% /details %}}


#### 18. `JavaScript` Consider the following code. {#18-dot-javascript-consider-the-following-code-dot}

```javascript
if (true) {
    let score = 10
}

console.log(score)
```

What happens?

A. It prints `10`
B. It prints `true`
C. Accessing `score` outside the block causes an error
D. `score` becomes global

{{% details title="Show Answer" %}}
**C. Accessing `score` outside the block causes an error**

`let` is block-scoped.

The variable exists within the surrounding `{ ... }` block and cannot be accessed using that name afterward.
{{% /details %}}


#### 19. `JavaScript` Why can `score` be accessed after the `if` block here? {#19-dot-javascript-why-can-score-be-accessed-after-the-if-block-here}

```javascript
function foo() {
    if (true) {
        var score = 10
    }

    console.log(score)
}
```

A. `var` is function-scoped
B. Every JavaScript variable is global
C. `if` statements do not create blocks
D. Numbers ignore scope

{{% details title="Show Answer" %}}
**A. `var` is function-scoped**

A declaration using `var` belongs to the surrounding function scope rather than the smaller `if` block.

This differs from `let`.
{{% /details %}}


#### 20. `C++` Which description of this statement is most accurate? {#20-dot-c-plus-plus-which-description-of-this-statement-is-most-accurate}

```cpp
int score = 10;
```

A. `score` is declared as an `int` and initialized with `10`
B. `score` is assigned without being declared
C. `10` is the variable
D. The statement gives `score` no value

{{% details title="Show Answer" %}}
**A. `score` is declared as an `int` and initialized with `10`**

`int` specifies the type.

`score` is the variable's name.

`10` is its initial value.
{{% /details %}}


#### 21. `C++` What is the important difference between these two cases? {#21-dot-c-plus-plus-what-is-the-important-difference-between-these-two-cases}

```cpp
int a = 10;

int b;
b = 10;
```

A. There is no conceptual difference
B. `a` is initialized with `10`, while `b` is defined first and assigned `10` afterward
C. `a` is global and `b` is local
D. `b` is initialized twice

{{% details title="Show Answer" %}}
**B. `a` is initialized with `10`, while `b` is defined first and assigned `10` afterward**

These are different operations.

```cpp
int a = 10;
```

creates `a` with its initial value.

```cpp
int b;
b = 10;
```

first defines `b` and then performs assignment.
{{% /details %}}


#### 22. `C++` What happens in this code? {#22-dot-c-plus-plus-what-happens-in-this-code}

```cpp
int score = 10;

{
    int score = 20;
}
```

A. The second declaration permanently replaces the first variable
B. The inner `score` is a separate variable that shadows the outer `score`
C. C++ forbids two variables with the same name anywhere
D. Both declarations name the same object

{{% details title="Show Answer" %}}
**B. The inner `score` is a separate variable that shadows the outer `score`**

Inside the inner block, the name `score` refers to the variable initialized with `20`.

After leaving that block, the outer `score` becomes visible again.
{{% /details %}}


#### 23. `C++` What is the value of `value` afterward? {#23-dot-c-plus-plus-what-is-the-value-of-value-afterward}

```cpp
int value = 10;
int& reference = value;

reference = 20;
```

A. `10`
B. `20`
C. `0`
D. Undefined

{{% details title="Show Answer" %}}
**B. `20`**

`reference` is a reference to `value`.

Assigning through the reference modifies the original object.
{{% /details %}}


#### 24. `C++` What is the value of `value` afterward? {#24-dot-c-plus-plus-what-is-the-value-of-value-afterward}

```cpp
int value = 10;
int* pointer = &value;

*pointer = 30;
```

A. `10`
B. `20`
C. `30`
D. The pointer modifies only a copy

{{% details title="Show Answer" %}}
**C. `30`**

`&value` obtains the address of `value`.

`pointer` stores that address.

Dereferencing the pointer with `*pointer` accesses the original object, so assigning `30` changes `value`.
{{% /details %}}


#### 25. `C++` Why is this code dangerous? {#25-dot-c-plus-plus-why-is-this-code-dangerous}

```cpp
int* getNumber() {
    int value = 10;
    return &value;
}
```

A. Integers cannot be used inside functions
B. `value`'s lifetime ends when the function returns
C. Pointers cannot point to integers
D. Local variables automatically become global

{{% details title="Show Answer" %}}
**B. `value`'s lifetime ends when the function returns**

`value` is a local object with automatic storage duration.

When `getNumber()` returns, `value` is destroyed.

The returned pointer therefore points to an object that no longer exists.

This is called a **dangling pointer**.
{{% /details %}}


#### 26. `C++` Which statement best distinguishes scope from lifetime? {#26-dot-c-plus-plus-which-statement-best-distinguishes-scope-from-lifetime}

A. Scope concerns where a name can be used; lifetime concerns when an object exists
B. Scope and lifetime always mean exactly the same thing
C. Scope determines an object's data type
D. Lifetime only applies to dynamically allocated objects

{{% details title="Show Answer" %}}
**A. Scope concerns where a name can be used; lifetime concerns when an object exists**

**Scope** concerns the visibility of a name in source code.

**Lifetime** concerns the period during execution in which an object exists.

These concepts become particularly important when working with references, pointers, dynamic allocation, and object ownership.
{{% /details %}}
