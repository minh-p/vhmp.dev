+++
title = "Snake (WIP)"
draft = false
+++

## Snake {#snake}

This project is divided into two parts. First, we'll be making the `model` of the game which handles the logic first before looking at how the game looks like (called `view`). Because this is a large project there are going to be a lot of prerequisites which is going to be mentioned when the time comes.


### Prerequisites {#prerequisites}

While making the `model`, we'll create a 2 dimensional list of characters. The student will have to learn to work with 2 dimensional arrays which includes traversal, indexing, etc. In short, make sure you understand the very basic regarding [arrays]({{< relref "/programming/teaching/programming-fundamentals/lists-arrays/" >}}).

When we begin working on the `view`, we'll be using `Pygame` which requires some prior knowledge about classes and objects.


### Project Setup - Directories and Files {#project-setup-directories-and-files}

We'll be creating `modules` in order to organize our code. In your project root, make sure to have `replit.nix` installing important packages. While working on the `model`, you don't need anything except Python yet. When we get to work on the `view(s)`, we'll have to install Pygame.

```nix { filename="replit.nix" }
{pkgs}: {
  deps = [
    (pkgs.python3.withPackages (ps: with ps; [ pygame pytest ]))
  ];
}
```

> [!NOTE]
> **Nix**
>
> You don't have to learn about `nix`, which is a domain-specific language for generating declarative system states. Briefly, this is a nix module that accepts `pkgs` as an argument. `pkgs` is an `attribute set` that stores the `pakcages` of the project's configured `nix channel`. A module can give back an `attribute set` as a result (hence the curly braces). The attribute `deps` is a list that will store packages accessible from the argument `pkgs`. In this example, we use the function `withPackages` to expand specific `packages` from a `package set`.

After your `replit.nix` is configured, we'll talk about how we're going to organize our files. Because the amount of Replit we can create is limited, we're going to create a directory inside the Replit's project root and make that the root of our snake project.

> [!TIP]
> **Root and Project(s)**
> A project's root is however you define it. The paragraph above is confusing because I'm writing about two types of projects. The `Replit project` is the application that you created. The `Snake project` is the project which you're going to store inside the directory `snake`.
>
> **Directory** the technical term for folders.

Setup your project like this:

```sh
.
├── replit.nix
└── snake
    ├── game.py
    ├── models
    │   └── engine.py
    ├── tests
    │   └── engine_tests.py
    └── views
```

`snake`, `models`, `views`, and `tests` are `directories` while the rest are files with their extensions: `.nix`, `.py`.


### Project Setup - Tests {#project-setup-tests}

A good programmer write very good tests. A programming project that doesn't have tests will grow difficultly if there isn't a way to ensure the integrity of the entire project as features are added. Writing tests is also a good way to understand more about the solution to the problem you're writing code for. A good test considers situations where things could go wrong such as on the boundary of situations you expect. It's the only practical way to assert the expectations of your project.

We're writing out first set of tests inside the file `engine_tests.py`. We're going to be using a the module `unittest` which is provided as part of Python's `standard library`.

> [!TIP]
> **Standard Library**
>
> A programming language's library includes code that comes installed with the language by default. The standard library of every programming language is different. While Python contains a library for unit-testing called `unittest`, other languages like `C/C++` requires the installation and linking of an external **C/C++** library for unit-testing.

We'll write our first tests:

```python
# Import the module unittest
import unittest

# This is the function we're testing as part of our Hello test case.
def get_hello_world():
  return "Hello World"

# Test Cases are created with a class that inherits from the class TestCase
class TestHello(unittest.TestCase):
  # For every test, we create a function that is inside a class.
  # In Python, these types of function are called "methods"
  # Methods have the parameter self which refers to the object
  # which is being modified by the method.
  def test_assert_hello(self):
    # We're using the method called "assertEqual"
    # This method is from the class TestCase of the
    # unittest module that our test case class inherits from.
    self.assertEqual("Hello World", get_hello_world())

# This condition checks if the file is being run directly
# Through the python command. If the condition is false,
# then it would mean that the file is being imported as a module
if __name__ == "__main__":
  unittest.main()
```
