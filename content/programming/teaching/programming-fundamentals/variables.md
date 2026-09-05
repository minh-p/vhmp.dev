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
