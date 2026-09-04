+++
title = "Fundamentals"
draft = false
weight = 30
+++

## Roadmap {#roadmap}

This is the roadmap of programming fundamentals taught to students.

```mermaid
flowchart TB

    subgraph R1[" "]
        direction LR
        A["Values"] --> B["Data Types"] --> C["Variables"] --> D["Operators"] --> E["Expressions"]
    end

    subgraph R2[" "]
        direction RL
        F["Input"] --> G["Output"] --> H["Booleans"] --> I["Comparisons"] --> J["Conditionals"]
    end

    subgraph R3[" "]
        direction LR
        K["Loops"] --> L["Strings"] --> M["Lists / Arrays"] --> N["Indexing"] --> O["Maps / Dictionaries"]
    end

    subgraph R4[" "]
        direction RL
        P["Functions"] --> Q["Parameters"] --> R["Arguments"] --> S["Return Values"] --> T["Scope"]
    end

    subgraph R5[" "]
        direction LR
        U["Decomposition"] --> V["Tracing"] --> W["Debugging"] --> X["Testing"] --> Y["Algorithms"]
    end

    R1 --> R2
    R2 --> R3
    R3 --> R4
    R4 --> R5

    style R1 fill:none,stroke:none
    style R2 fill:none,stroke:none
    style R3 fill:none,stroke:none
    style R4 fill:none,stroke:none
    style R5 fill:none,stroke:none

    click A "/programming/teaching/programming-fundamentals/values/" "Pieces of information that programs can work with."
    click B "/programming/teaching/programming-fundamentals/data-types/" "Categories of values such as numbers, text, and booleans."
    click C "/programming/teaching/programming-fundamentals/variables/" "Names used to store and refer to values."
    click D "/programming/teaching/programming-fundamentals/operators/" "Symbols that perform operations on values."
    click E "/programming/teaching/programming-fundamentals/expressions/" "Combinations of values and operators that produce new values."

    click F "/programming/teaching/programming-fundamentals/input/" "How a program receives information from outside itself."
    click G "/programming/teaching/programming-fundamentals/output/" "How a program communicates information and results."
    click H "/programming/teaching/programming-fundamentals/booleans/" "True and false values used to represent logical states."
    click I "/programming/teaching/programming-fundamentals/comparisons/" "Operations that compare values and produce boolean results."
    click J "/programming/teaching/programming-fundamentals/conditionals/" "Choosing which instructions execute based on a condition."

    click K "/programming/teaching/programming-fundamentals/loops/" "Repeating instructions while or until a condition is met."
    click L "/programming/teaching/programming-fundamentals/strings/" "Sequences of characters used to represent and manipulate text."
    click M "/programming/teaching/programming-fundamentals/lists-arrays/" "Ordered collections containing multiple values."
    click N "/programming/teaching/programming-fundamentals/indexing/" "Accessing elements of a sequence by their position."
    click O "/programming/teaching/programming-fundamentals/maps-dictionaries/" "Associating keys with corresponding values."

    click P "/programming/teaching/programming-fundamentals/functions/" "Reusable sections of code that perform a particular task."
    click Q "/programming/teaching/programming-fundamentals/parameters/" "Names that describe the inputs accepted by a function."
    click R "/programming/teaching/programming-fundamentals/arguments/" "Actual values supplied when a function is called."
    click S "/programming/teaching/programming-fundamentals/return-values/" "Values sent from a function back to its caller."
    click T "/programming/teaching/programming-fundamentals/scope/" "The region of a program where a name can be accessed."

    click U "/programming/teaching/programming-fundamentals/decomposition/" "Breaking a large problem into smaller manageable parts."
    click V "/programming/teaching/programming-fundamentals/tracing/" "Following execution step by step to understand program state."
    click W "/programming/teaching/programming-fundamentals/debugging/" "Finding, understanding, and correcting program errors."
    click X "/programming/teaching/programming-fundamentals/testing/" "Checking that programs behave correctly across different cases."
    click Y "/programming/teaching/programming-fundamentals/algorithms/" "Precise step-by-step procedures for solving computational problems."
```


## What About the First Programming Language? {#what-about-the-first-programming-language}

> [!NOTE]
> **Summary**
>
> The first programming language matters less than what comes after it.
>
> A student's first language should make programming approachable and give them enough motivation to build things. Python, Lua, JavaScript, Java, and even C or C++ can all serve that purpose in different situations.
>
> What matters more is that the student does not let one language define their entire understanding of programming. As they progress, they should encounter different programming models, type systems, data structures, memory models, and ways of organizing software.
>
> The recommendations below are therefore based on what I think provides the best foundation for general programming education, not on the idea that one language is universally superior.

The youngest students I have use Scratch before they develop their typing skills. When they are used to the keyboard, I would immediately switch them to Python or Lua.

Many students might choose Python as their first programming language because of its easy-to-remember syntax while following many conventions that transfer well to other programming languages. A student could also start with Java, especially if they want earlier exposure to static typing, classes, and the style of programming commonly used in large software projects but do not want to deal with manual memory management. Some young students choose Lua because they would like to work with Roblox. If the student wants to make a small website, JavaScript could be given a go. Or, as a trial by fire, a student could go directly to C or C++ (which I wouldn't recommend).

> [!TIP]
> **Python** for a general student, and Lua for a student who wants to directly make Roblox games. For a student who wants to directly make a website, I suggest JavaScript.

{{% details title="Huy's Personal Experience" %}}
I first learned programming through the Roblox Lua language to make some small Roblox games. I was partly motivated by wanting Robux to buy cosmetics and game passes or even make real money. Now that I'm older, I realize that my interests have moved far beyond Roblox. I could have stuck with Python because, compared to Lua or JavaScript, Python would have given me a more transferable foundation for the languages and computer science concepts I later encountered in C++.
{{% /details %}}


### Prefer Python For General Programming Education {#prefer-python-for-general-programming-education}

If a student wants to pursue computer science or software engineering seriously, I prefer languages whose concepts transfer easily to other mainstream languages. A beginner should not only learn syntax, but also develop mental models of variables, types, functions, data structures, objects, references, and program organization that remain useful when they eventually move to languages such as Java, C++, or Rust.


#### Lua {#lua}

This language has its weird quirks like indexing starting at 1 instead of 0 compared to most other languages.

Lua also uses tables in places where other languages distinguish arrays, maps (dictionaries), objects, and classes. As perhaps the worst transgression, even object-oriented behavior is built by extending ordinary tables with metatables.

In terms of broader educational and career prospects, I would eventually transition a student from Lua to Python as long as they are willing to leave behind making Roblox games. When they are ready for a more explicit (trading simplicity for control) language, they could then move to Java, C, or C++.

> [!DANGER]
> **Roblox Isn't the Best** (Might Be the Worst)
>
> I don't think students should approach Roblox development expecting to make money. Students can make games to learn basic problem solving in coding, but making a commercially successful game requires substantially more than learning how to script. Financially, eventually making one's own game outside of a game platform like Roblox or even one's own game engine guarantees maximal profits compared to 15-29% roughly of the revenue Roblox earns.
>
> Lua's tables combine several concepts that other languages conventionally distinguish, such as arrays, maps, objects, and class-like structures. A student who later moves to another language will therefore have to learn to distinguish concepts that Lua allowed them to treat as one general-purpose structure.
>
> Roblox can be a good motivation for learning programming, but it should not become the boundary of a young student's programming education.
>
> {{< youtube "_gXlauRB1EQ?start=575" >}}


#### JavaScript {#javascript}

JavaScript can be a reasonable first programming language, but it is a poor language to learn programming exclusively through. Its unusual semantics (the rules determining what code means and how it behaves), browser-oriented history, and high-level abstractions can leave beginners with an incomplete mental model of how programming languages and computers generally work.

{{% details title="Unusual Semantics of JavaScript" open="true" %}}
```javascript
"5" + 1       // "51"
"5" - 1       // 4

[] == false   // true
typeof null   // "object"
```

These behaviors are manageable once someone understands JavaScript, but they are not rules I particularly want a beginner internalizing while they are still developing their understanding of values, types, and comparison.
{{% /details %}}
