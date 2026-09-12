+++
title = "Luau"
draft = false
+++

## Luau (Roblox Luau) {#luau--roblox-luau}

Roblox games uses a fork (customized version) of Lua 5.1. While students can reference the official Lua documentation, some concepts commonly used in Roblox do not exist in the official releases of Lua

As usual, the index page includes the common Roblox features associated with Roblox Scripting. The latter parts nested inside describes some of the projects students have taken part of and is used to document all types of projects.

This page records the basic setup when it comes to begin coding on Roblox. My writings on [programming fundamentals]({{< relref "/programming/teaching/programming-fundamentals" >}}) should be referenced. I include examples in Lua whenever possible.

One of the things you need to do as you get better at Roblox is the ability to be able to look up things from the [official reference page](https://create.roblox.com/docs) on your own.


### Types of Scripts {#types-of-scripts}

There are three types of scripts in Roblox as of right: scripts, local scripts, and module scripts. The normal scripts are not actually "normal", they are code a developer writes to affect changes to the **server**. The local scripts include code that affects only a single player, other players other than the player that owns the local script do not see the changes to the game world.

> [!TIP]
> **Server vs. Client** - First-Person Shooter Example
>
> The normal Script contains code written for the server while the Local Script contains code written for a single player.
>
> In many games (not just in Roblox), the usage of fake-arms are employed. After all, if the player's arms are controlled by the Server in first-person, the arms movement will feature massive delay. Fake arms, or "viewmodels" are created in a Local Script that constantly sets the coordinate frame (CFrame) to that of the camera's CFrame offset by some amount.


#### Where to Use Each Type of Script {#where-to-use-each-type-of-script}

Both the `script` and the `local script` can be put into an object placed inside the `workspace`. This is how models work in Roblox.

For general game mechanics that transcend any model, the Roblox developer is utilize other places.

<!--list-separator-->

-  Script

    The normal `script` otherwise called the server script should be usually placed inside `ServerScriptService`. If the script is not meant to be running, it can be placed inside `ServerStorage`.

    > [!NOTE]
    > **ServerStorage** - Additional Usage
    >
    > The server storage can store other assets like models, sounds... or anything that's handled by the server exclusively first. The player cannot access any of the asset inside `ServerStorage`.

<!--list-separator-->

-  Local Script

    `Local script` can be placed inside a `GuiObject` inside `StarterGui` as code handling each player's graphical interface. `StarterPlayerScripts` is the most common place to put a `local script` which is created and runs every time a player joins the game. `StarterCharacterScripts` is also a valid option if the player wishes for a local script to run every time the player character reloads.


### Events - Something You See Often {#events-something-you-see-often}

Roblox uses the programming pattern called the `Observer Pattern` where a process `listens` and `notifies` state changes. The result is that whenever an specific `event` happens, like when something touches a `BasePart`, then a function that the Roblox Developer writes for that event will be called.

> [!NOTE]
> **State Changes**
>
> In a computer program `states` are values that the computer look at constantly to decide what to do. Think of a light switch. If the light switch is off, then the room's ambiance should be dark.

<!--quoteend-->

> [!WARNING]
> **Know Prerequisites**
>
> If you have difficulty understanding the writing so far, make sure you know what a `function` and a `loop` is first.


#### How are Listeners Implemented {#how-are-listeners-implemented}

This is not something that you have to worry about. However, you might understand events more if you visualize that `listeners` are a separate thing that waits for a certain condition to occur. Here's pseudo-code of what a `listener` might be.

```nil
while game is running:
  if event_condition:
    for every function we are given:
       function(necessary arguments for this event)
```


#### How to Use the Listeners {#how-to-use-the-listeners}

All we need to do is to give the listener the functions we would like to be called when the event condition occurs. Roblox also describes this in its [official documentation page on events](https://create.roblox.com/docs/scripting/events). We're showcasing the `Touched` event which is listed in this [official reference page](https://create.roblox.com/docs/reference/engine/classes/BasePart#Touched), which I recommend reading as it's a skill you're going to have develop called `documentation referencing`.

```lua { filename="ServerScriptService/Script" }
-- Creating a part in workspace and positioning it
-- at (x, y, z) = (0, 10 0)
part = Instance.new("Part")
part.Name = "Touchable"
part.Parent = workspace
part.Position = Vector3.new(0, 10, 0)

-- The function we're giving to the Touched
-- Event as argument
function onTouch(basePartTouched)
   print(basePartTouched:GetFullName())
end

-- Passing the our function to the Connect function
-- The Connect function is inside every event in Roblox
part.Touched:Connect(onTouch)
```

Notice that `Touched` is an event that exists inside the part. `Touched` itself is also a table. We then use the `Connect` function that is inside the `Touched` event. Every `event` needs an argument which is the `function` that should be called when the event occurs. Every `event` can handle and keep track of multiple `functions`. You can assign many `functions` to a single `event`.

> [!TIP]
> **What a object in Roblox Is**
>
> Every single game object in Roblox you see is actually a table that has been modified with a `metatable`. This game object table is modified so that it can access its `children` which are other game objects it stores. It can also access its properties and other non-properties.
>
> All of this is possible through the `.` operator to access something inside another thing.

A common coding pattern in Roblox code is the usage of lambdas (alias `in-line functions`). Lambdas are anonymous functions (functions without a name). Here's the same code that uses a `lambda` instead of a `named function`.

```lua { filename="ServerScriptService/Script" }
-- Creating a part in workspace and positioning it
-- at (x, y, z) = (0, 10 0)
part = Instance.new("Part")
part.Name = "Touchable"
part.Parent = workspace
part.Position = Vector3.new(0, 10, 0)

-- Passing a lambda to the Connect function
-- The Connect function is inside every event in Roblox
part.Touched:Connect(function(basePartTouched)
      print(basePartTouched:GetFullName())
end)
```
