+++
title = "Lists (Arrays)"
draft = false
+++

## Lists (Arrays) {#lists--arrays}

`Lists` are a collection of things. The term `list` is most commonly used for a collection that is indexed continuously which can store values of many data-types. The term `array` is most commonly used for a collection that is indexed continuously but only stores values of a single data-type.

Examples here feature a list (array) of strings in various languages.

{{< tabs >}}
{{% tab Python %}}
```python
strings = ["Hello", "World"]
print(strings[0]) #--> Hello
print(strings[1]) #--> World
print(len(strings)) #--> 2
```
{{% /tab %}}

{{% tab Lua %}}
```lua
-- Global var
strings = {"Hello", "World"}
print(strings[1]) --> Hello
print(strings[2]) --> World
print(#strings) --> 2
```
{{% /tab %}}

{{% tab C %}}
```c
#include <stdio.h>
int main() {
    // Auto appends null terminator
    char str[] = "Hello World";
    // sizeof is builtin
    printf("%zu\n", sizeof(str)); // Gives 6
    return 0;
}
```
{{% /tab %}}

{{% tab "C++" %}}
```cpp
#include <iostream>
#include <string>
int main() {
    std::string str = "Hello";
    // Gives 6 including null terminator.
    std::cout << str.size() << std::endl;
    return 0;
}
```
{{% /tab %}}
{{< /tabs >}}
