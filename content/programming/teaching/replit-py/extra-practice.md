+++
title = "Practice"
draft = false
+++

## Additional Practice {#additional-practice}

In this page are exercises that are not part of any projects but are exercises that reinforce understanding of topics.

In your Replit Python project, let us setup a separate directory for your demonstration activities. First, open up your shell and make sure you're seeing `~/workspace`. If not type `cd ~/workspace`. Then we're creating a directory called `demonstration` by typing `mkdir demonstration`. To get into the `demonstration` directory, type `cd demonstration`.


## 2 Dimensional Lists {#2-dimensional-lists}

This exercise will help you understand how two dimensional lists work.
First, create change into the `demonstration` directory and create new Python file called `2d-array.py` by typing `touch 2d-array.py`.

Here are two functions that are provided to you. The first one `create_2d_list` creates an empty 2 dimensional list and the second `print_2d_list` will print that list out with some decorations.

```python { filename="demonstration/2d-array.py" }
from typing import Any

def create_2d_list(columns: int, rows: int, default_value: Any):
  list_2d = []
  for row in range(rows):
    list_2d.append([])
    for col in range(columns):
      list_2d[row].append(default_value)
  return list_2d

def print_2d_list(list_2d: list[list[Any]]):
  for row in range(len(list_2d)):
    for col in range(len(list_2d[row])):
      print("[", list_2d[row][col], "]", end=" ")
    print("\n")

print_2d_list(create_2d_list(5, 5, 0))
```
