+++
title = "Stack (WIP)"
draft = false
+++

## What is a Stack? {#what-is-a-stack}

Stack is an abstract data type that collects data.
The basic operation contract for this project details: O(1) for push, pop, peek.
The student will decide the backing data structure on his own. Possible options are: singly linked list, dynamic array.

> [!TIP]
> **What kind of Stack?**
>
> In this project, we're making a Stack abstract data type that stores only integers.


## Prerequisites {#prerequisites}

The student has to know how to write a class that will own a data structure that deals with allocation on the free store or heap. They should obviously know pointers and follow the rule of three. If they wish to implement the move assignment operator or the move constructor then that would be fulfill the move of 5 and make memory more efficient.


## Instructions {#instructions}

Here's a list of instructions to implement this project.

{{% steps %}}
1.  Project Setup - `compile.sh`, `main.cpp`, `Stack.hpp`, `stack.cpp`, `replit.nix`
2.  Write constructor(s) with member initialization
3.  Rule of 3 - Write the needed declarations to satisfy the rule of three and implement them
4.  Testing - Setup Google Test and write some tests
5.  Implement the Rule of Three Declarations
6.  Implement `push()`, `pop()`, `peek()`, and `resize()`
{{% /steps %}}


## 1. Project Setup {#1-dot-project-setup}


### Replit {#replit}

There isn't any web platform that can host C++ that I know of besides Replit. The best tools are the tools that you own. Most of my students at [TheCoderSchool, Irvine](https://https//www.thecoderschool.com/locations/irvine/) use a chromebook, so we opt to use Replit.

> [!WARNING]
> **Skip If Needed**
>
> You can skip this section if you are not using a chromebook. The specific setup on Windows, MacOS, or Linux are not discussed. But this tutorial will work if you have the GNU compiler installed for C++. This means should have access to the program `g++` on the path of your shell. This tutorial also only supports a POSIX shell like `sh`, `bash`, or `zsh`. You have to search for equivalent commands for `powershell` on Windows. In terms of programs to install, you should install the GNU Compiler Collections and Google Test on your system.

New Replit projects uses nix for package management. So don't reuse an old Replit application. The specifics is recorded in the Replit App Configuration or the [Advanced Configuration page](https://docs.replit.com/features/project-setup/configuration).

> [!TIP]
> **Creating an Empty Replit Project** - 09/05/2026
>
> If you click the `New` button, Replit will show you an AI command prompt. This is not what we want. Instead, find the `Import` button which should be underneath it. On the `Import` page, select the `Empty` option.

We are going to install the GNU compiler for C++ which will allow us access to the program `g++`. Create `replit.nix` at the project's root. Inside, paste this code in so that we install the GNU Compiler Collection and Google Test.

```nix { filename="replit.nix" }
{ pkgs } :
{
  deps = with pkgs; [
    libgcc
    gtest
  ];
}
```

> [!TIP]
> **What is Project Root**?
>
> A `project root` is the directory (synonymous with folder) where every file is stored. The directory that contains the project root will contain other files and directories external to your project.

<!--quoteend-->

> [!TIP]
> **Did editing replit.nix work?**
>
> To confirm whether the GNU compiler for C++ and GoogleTest is installed, open up Replit's `shell` and type `g++`. If you receive an error that says command-not-found, you should retry copy-and-paste from what I have.


### Creating Translation Units {#creating-translation-units}

Next, we are going to create the translation units needed for this project. In C++, these are simply your individual `cpp` files but also the header files `hpp`. Make the empty files `stack.cpp`, `Stack.hpp`, `main.cpp`.

> [!NOTE]
> **Translation Unit**
>
> This term refers to the packaging of source code into a unit that is evaluated by the compiler. Translation units are different across programming languages. The translation unit of C and C++ is each file that is evaluated after the preprocessor has finished doing its job of copying content from include files. In another programming language like Rust, the translation unit we work with is modules, something you encountered in a managed language like Python or JavaScript.


### Our First Executable {#our-first-executable}

REPLIT uses Bash for its shell which is a shell derived from the POSIX standard. We're going to create an `sh` file called `compile.sh` in the project root.

```sh { filename="compile.sh" }
g++ main.cpp stack.cpp -o main
```

To run the shell file, type this on the command line:

```sh
sh ./compile.sh
```

> [!TIP]
> **Why compile.sh**
>
> Instead of typing in the long command every time we need to recompile. We just put the command in `compile.sh` as a shorter way to compile our project.

Right now, there's going to be an error saying that there's no entry to the program because there's no `main` function.

As for tests, we're going to create a separate `sh` file later.


#### Basic Source Code Setup {#basic-source-code-setup}

I suggest you type these out over direct copy-and-paste as it helps you remember the syntax.

```cpp { filename="main.cpp" }
#include "Stack.hpp"

int main() {
    return 0;
}
```

```cpp { filename="Stack.hpp" }
class Stack {
};
```

```cpp { filename="stack.cpp" }
#include "Stack.hpp"

// Nothing here yet
```

Now, run our `compile.sh` file again using the Replit shell.

```sh
sh ./compile.sh
```

You should get a binary now in your project root called `main`, which is going to do nothing if you run it. Use the Replit shell and run it by just providing the path to the binary.

```sh
./main
```

> [!TIP]
> **What about header files**?
>
> Notice that our compilation command in `compile.sh` only deals with the `cpp` files. We don't have to do additional setup because the `hpp` files are in the same directory as the `cpp` files. You should research more about what the `preprocessor` does. Because we "included" the header files, the content of the header files are copied inside the `cpp` file after the `preprocessor` runs. Remember that the `translation unit` of C/C++ is one `cpp` file after `preprocessing`, the linker will automatically link the declarations with where the specific programming element is defined.


## 2. Writing a Constructor For Stack {#2-dot-writing-a-constructor-for-stack}

This part is relatively simple. We declare the constructor `Stack.hpp` and define it in `stack.cpp`. You also need to think about what data members are needed for Stack ADT. Every ADT needs a backing data structure, in this project we'll be using a `dynamic array`. Therefore, inside the class, we'll need to have our first data member which is going to be a integer pointer holding the address of the first integer inside the contiguous heap-allocated array.

> [!NOTE]
>
> **Dynamic Array and Related Terms**
>
> A `dynamic array` is an array that change in size. What changing in size means is that the array will not be stored inside the object of class Stack. Instead, we have a data member which is a pointer which allows access to the heap allocated array. You can visualize this as having two containers of computer memory connected one-way by a pointer.
>
> The adjective `contiguous` describes a collection whose elements' memory addresses are next to each other. Contiguous memory is preferred by your CPU because of efficient cache operations &rarr; a concept called `cache locality` which you can further research on.

We also have to consider any other necessary data members that's useful to be holding on. When we heap allocate an array of an arbitrary type, there's no way to get a hold of the size besides keeping the `capacity` of our heap allocated array. Besides our `capacity`, we should consider the `logical length` of the `dynamic array`.

> [!TIP]
> **Additional data members needed**
>
> Besides the `dynamic array`, we also need to keep track of the current `capacity` and the current `logical length`.

<!--quoteend-->

> [!NOTE]
>
> **Getting Length** - An unsolvable problem for arrays and strings
>
> Our memory slots, whose amount is measured in the unit bits, is by itself an array. You have to tell the computer when to stop reading the next slot of memory.
>
> `Strings` - In C/C++, you will learn that the logical length for a string of 5 characters e.g. `"Hello"` is actually 6. There's an invisible null terminator that you have that's automatically appended to any array of characters (string)s you make. The null terminator character `\0` tells us when the string ends.
>
> This is why we `keep length` not `get length later`.

{{% details title="Solution" %}}
```cpp { filename="Stack.hpp" }
class Stack {
    // These data members are private by default
    int size;
    int *data;
    int length;
public:
    Stack(int size);
};
```

```cpp { filename="stack.cpp" }
#include "Stack.hpp"

Stack::Stack(int size): size{size}, data{new int[size]}, length{0} {}
```
{{% /details %}}

> [!DANGER]
> **You Must Try and Struggle** - Don't Look at Solution Yet
>
> Don't look at the solutions yet. Unless you're confident that you got it right. Keep trying and confirm your implementation on your own. Your **enemy** is the **lack of time management**, especially in your academic courses.


## 3. Our Rule of Three {#3-dot-our-rule-of-three}

`Rule of Three` requires that for any class that has a pointer as its data member, the programmer has to implement the `destructor`, `copy constructor`, and `copy assignment operator`.


### Destructor {#destructor}

Implement your destructor. How are you going to `free` your `dynamic array` when the Stack object is destructed?

{{% details title="Solution" %}}
```cpp { filename="Stack.hpp" }
class Stack {
    //...
    ~Stack();
    //...
};
```

```cpp { filename="stack.cpp" }
Stack::~Stack() {
    delete[] data;
}
```
{{% /details %}}


### Copy Constructor {#copy-constructor}

When constructing from an existing Stack object, we have to allocate our `dynamic array` and copy integers over. Because this is a constructor, you should allocate your `dynamic array` with the member initialization list. You can copy integers by iterating over the Stack object we're copying.

{{% details title="Solution" %}}
```cpp { filename="Stack.hpp" }
class Stack {
    Stack(int size);
    Stack(const Stack& other);
};
```

```cpp { filename="stack.cpp" }
//...
Stack::Stack(const Stack& other): size{other.size}, data{new int[other.size]}, length{other.length} {
    for (int i = 0; i < other.length; ++i) {
        data[i] = other.data[i];
    }
}
//...
```
{{% /details %}}


### Copy Assignment Operator {#copy-assignment-operator}

The `copy assignment operator` decides what happens when you're assigning an existing Stack object to a variable that already held another existing Stack object. Also remember that there's no longer any member initialization because this is not a constructor.

```cpp
Stack A{10};
Stack B{20};

A = B;
```

You should also handle the case where self-assignment happens.

```cpp
Stack A{10};
A = A; // Nothing should happen
```

{{% details title="Solution" %}}
```cpp { filename="Stack.hpp" }
class Stack {
    Stack& operator=(const Stack& other);
};
```

```cpp { filename="stack.cpp" }
Stack& Stack::operator=(const Stack& other) {
    // self-assignment guard
    if (this == &other) {
        return *this;
    }

    delete[] data;
    data = new int[other.size];

    for (int i = 0; i < other.size; ++i) {
        data[i] = other.data[i];
    }

    return *this;
}
```
{{% /details %}}

> [!NOTE]
> **Trivia** - Is `operator=` an identifier?
>
> You may have heard people or some sources use the word `identifier`. The answer to this trivia is **No**. An identifier is a syntactic form of a name. Simplified, you could think of it as type of name. Whenever you see a member function whose name does not conform to that of a standard identifier (think what name would be valid for a variable) then usually they are built-in and do something special. You can still use them normally e.g. inside a class:
>
> ```cpp
> class A {
>     A& operator=(const A& other) {
>         // ...
>         return *this;
>     }
>     void hey() {
>         operator=(Stack a{}); // should be valid
>     }
> };
> ```

<!--quoteend-->

> [!WARNING]
> **WARNING** - self-assignment guard implementation
>
> ````cpp
> if (*this == other) {
>     return;
> }
> ````
>
> What's wrong about this condition? What is the correct condition instead?
>
> **Hint:** Are you comparing values for equivalence or memory addresses for equality?
