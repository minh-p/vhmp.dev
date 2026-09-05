+++
title = "Namespaces"
draft = false
weight = 30
+++

## Namespaces {#namespaces}

> [!WARNING]
> **Warning**
>
> This is a more complex topic that can be skipped over for the first time you learn a programming language. It becomes important if you're learning the historical trend of how unmanaged languages are designed which includes especially C, C++, Rust...

Namespaces prevent naming conflict and they categorize different and names (synonymously labels, or `identifiers`).

We generalize [variables]({{< relref "variables" >}}) to introduce the term `identifiers`. A variable is a type of identifier. An identifier syntactic form of a name of a code element like function, variables, classes... In C++ variables without a specified `namespace` is inside the `global namespace`. Standard C does use the term "namespace" but it is a different meaning than C++; `namespace` in C is just a categorization of identifier while `C++ namespaces` can group any identifiers together in a way that a programmer define instead of as mechanic of the compiler.

> [!TIP]
> **Importance**
>
> The concept of name management is important in any programming language to prevent conflict and categorize identifiers. In C++ specifically, we manage this through `namespaces` as the important mechanic where the programmer can group identifiers by themselves. Other more recently made programming languages like Rust, Python, and JavaScript uses `modules`. `Modules` file-scopes identifiers.


## Related {#related}

A related concept is called [scope]({{< relref "scope" >}}) which in many programming languages work in tandem with namespaces to handle identification (looking up things by name).
