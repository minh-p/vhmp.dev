+++
title = "Conditionals"
draft = false
+++

## Conditionals {#conditionals}

Programming languages make it convenient to tell the computer perform an action given a condition. Most general purpose languages have if-statements are switch-cases.

> [!NOTE]
> **Condition Definition**
>
> A condition is something that is needed before something else can happen.

In many programming languages, the condition is a boolean expression.

> [!NOTE]
> **Boolean Expression**
>
> The term `boolean expression` is used to describe some code that gets evaluated until at its simplest form becoming a boolean true or false.

<!--quoteend-->

> [!NOTE]
> **Evaluation**
>
> In an interpreted language like Python, Lua, JavaScript, the interpreter evaluates expressions. An a compiled language, the CPU directly evaluates the program's expressions.


### If-Statements {#if-statements}

Here are example of if-statements in different programming languages in the context of returning early from a function that checks for valid arguments.

{{< tabs >}}
{{% tab "Python" %}}
```python
def need_int(a):
    if not isinstance(a, int):
        return
    return a+1
```
{{% /tab %}}

{{% tab "Luau" %}}
```lua
function need_num(a)
   if typeof(a) ~= "number" then
      return
   end
   return a + 1
end
```
{{% /tab %}}

{{% tab "C++" %}}
```cpp
int needInt(int * int_ptr) {
    // Checking type of pointer using dynamic cast.
    if (int_ptr != nullptr && dynamic_cast<int*>(int_ptr)) {
        return 0;
    }
}
```
{{% /tab %}}
{{< /tabs >}}


### Switch Statements (Or Equivalents) {#switch-statements--or-equivalents}

Switch statements might not exist in newer programming languages. This sections shows the switch-case statements in C++ but it's not enough as exclusive learning materials. There are also imitations of a switch-case in Python and Lua. In this example, we're making a simple game menu.

{{< tabs >}}
{{% tab "C++" %}}
```cpp
int choice = 2;

switch (choice) {
 case 1:
     std::cout << "Start game\n";
     break;

 case 2:
     std::cout << "Open settings\n";
     break;

 case 3:
     std::cout << "Quit game\n";
     break;

 default:
     std::cout << "Invalid choice\n";
     break;
 }
```
{{% /tab %}}

{{% tab "Python 3.10+" %}}
```python
choice = 2

match choice:
    case 1:
        print("Start game")
    case 2:
        print("Open settings")
    case 3:
        print("Quit game")
    case _:
        print("Invalid choice")
```
{{% /tab %}}

{{% tab "Bad Lua" %}}
Don't use this. This is not conventional Lua practice.

```lua
local choice = 2

local actions = {
   [1] = function()
      print("Start")
   end,

   [2] = function()
      print("Settings")
   end,

   [3] = function()
      print("Quit")
   end
}

local action = actions[choice]

if action then
   action()
else
   print("Invalid choice")
end
```
{{% /tab %}}
{{< /tabs >}}
