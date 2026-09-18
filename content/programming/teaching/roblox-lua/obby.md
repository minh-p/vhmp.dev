+++
title = "Obby (WIP)"
draft = false
+++

## Obby {#obby}

An obby is a classic obstacle game in Roblox. This project focuses on coding certain common components of an Obby from scratch.


### List of Common Mechanics {#list-of-common-mechanics}

Some common mechanics include

1.  Damage Brick - Kill Brick, Fire Brick
2.  Path Pattern - A correct path is illuminated before disappearing for a couple of seconds
3.  Stages System - Spawn locations
4.  Progress Saving - Saving The stage the player is on through DataStore.


### Damage Brick {#damage-brick}

When the player touches a damage brick, their health will decrease. We're going to be using the `Touched` event for both this and two different bricks.


#### Prerequisites {#prerequisites}

Knowledge of [functions]({{< relref "/programming/teaching/programming-fundamentals/functions/" >}}) is required as well as [conditionals]({{< relref "/programming/teaching/programming-fundamentals/conditionals" >}}).


#### Kill Brick {#kill-brick}

Kill Brick simply sets the health of the player to zero when the player touches it.

<!--list-separator-->

-  Instructions

    {{% steps %}}
    1.  Create a `script` inside the kill brick.
    2.  Create a variable for your kill brick.
    3.  Create an empty named function
    4.  Call the `Connect` function of the `Touched` event inside the kill brick
    5.  Implement the empty named function
    {{% /steps %}}

    <!--list-separator-->

    -  Implementing the empty named function

        Here are the specific sub-steps of step 5.

        {{% steps %}}
        1.  Make sure the part touching our kill brick is a body part.
        2.  Set the `Health` property of the character model's `Humanoid`.
        {{% /steps %}}

<!--list-separator-->

-  Implementation Hints, Solutions

    <!--list-separator-->

    -  Step 1 - Activity Setup

        Simply create a Part in `workspace` and insert a `script` inside the Part.

        > [!TIP]
        > **Script or Local Script**
        >
        > In Roblox, we only use a `local script` for graphical interface elements, things the player should only see or experience, and the events of the character's humanoid.

    <!--list-separator-->

    -  Step 2 - Making Variable For Kill Brick

        We're creating a `variable` so think of a name. e.g. `killbrick`, `part`.

        Remember how variable initialization/assignment work in Lua. On the right side of `=`, how can you access the kill brick? Remember that the script we're writing in is inside the kill brick.

        {{% details title="Solution" %}}
        ```lua { filename="workspace/KillBrick/Script" }
        killBrick = script.Parent
        ```
        {{% /details %}}

    <!--list-separator-->

    -  Step 3 - Making an Empty Function

        Choose a name for your `function`. Look at the [documentation reference page](https://create.roblox.com/docs/en-us/reference/engine/classes/BasePart#Touched) for the `Touched` event, what parameter(s) do we need?

        {{% details title="Solution" %}}
        ```lua { filename="workspace/KillBrick/Script" }
        function processKill(otherPart: BasePart)
        end
        ```
        {{% /details %}}

    <!--list-separator-->

    -  Step 4 - Passing Empty Function to Connect Function

        Access the `Touched` event inside the `KillBrick`, then call the `Connect` function and pass in our empty function in as argument.

        {{% details title="Solution" %}}
        ```lua { filename="workspace/KillBrick/Script" }
        killBrick = script.Parent -- From Step 2

        -- Step 3
        function processKill(otherPart: BasePart)
        end

        killBrick.Touched:Connect(processKill)
        ```
        {{% /details %}}

    <!--list-separator-->

    -  Step 5 - Implementing the Empty Function

        First, we have to make sure that the argument we received is an actual body part because the `Touched` event [occurs for any base part](https://create.roblox.com/docs/en-us/reference/engine/classes/BasePart#Touched) that moved to touch. In order to do this, we check if there's a `Humanoid` inside the `Parent` of the body part. If there isn't, then `return` from the function early.

        > [!TIP]
        > **Parent of Body Part**
        >
        > The parent of every body part is the character model.

        <!--quoteend-->

        > [!TIP]
        > **Use FindFirstChild**
        >
        > Use the function `FindFirstChild` in order to safely access a `child` (nested object) of another object. `FindFirstChild` requires a `string` as argument which is the name of the child that should be attempted to access. `FindFirstChild` returns `nil` if it could not find the child of given name or it gives the actual `child` back.
        >
        > Check out the [reference documentation page on `FindFirstChild`](https://create.roblox.com/docs/en-us/reference/engine/classes/Instance#FindFirstChild).

        {{% details title="Solution - Making Sure It's a Body Part" %}}
        ```lua { filename="workspace/KillBrick/Script" }
        function processKill(otherPart: BasePart)
           local potentialCharacter = otherPart.Parent
           local potentialHumanoid = potentialCharacter:FindFirstChild("Humanoid")
           if not potentialHumanoid then return end
           -- Equivalent: if potentialHumanoid == nil then return end
        end
        ```
        {{% /details %}}

        Then, we simply set the `Health` property of the character's `humanoid` to 0.

        {{% details title="Solution - Setting Property Health" %}}
        ```lua { filename="workspace/KillBrick/Script" }
        function processKill(otherPart: BasePart)
           local potentialCharacter = otherPart.Parent
           local potentialHumanoid = potentialCharacter:FindFirstChild("Humanoid")
           if not potentialHumanoid then return end
           -- Equivalent: if potentialHumanoid == nil then return end

           potentialHumanoid.Health = 0
        end
        ```
        {{% /details %}}

<!--list-separator-->

-  Complete Solution

    Before you look at the complete solution, make sure to struggle first.

    {{% details Solution %}}
    ```lua { filename="workspace/KillBrick/Script" }
    part = script.Parent

    function burn(otherPart)
        -- First, we confirm if the otherPart is a body part
        local character = otherPart.Parent
        local humanoid = character:FindFirstChild("Humanoid")
        if not humanoid then return end

        humanoid.Health = 0
    end

    part.Touched:Connect(burn)
    ```
    {{% /details %}}


#### Fire Brick {#fire-brick}

Unlike the `Kill Brick`, the fire brick is much more complicated because we're dealing with gradual damage over time. Coming from the finished code of the `Kill Brick`, instead of setting `Health` to zero, you might have thought that instead of setting the `Health` to 0, you could just decrease it.

> [!WARNING]
> **Finish KillBrick First**
>
> This section assumes that you have the code for the `KillBrick` already. Don't rush it and sacrifice your learning experience.

{{% details title="Naive Solution" %}}
```lua { filename="workspace/FireBrick/Script" }
firePart = script.Parent

function burn(otherPart: BasePart)
   -- making sure it's a body part
   local pCharacter = otherPart.Parent
   local pHumanoid = pCharacter:FindFirstChild("Humanoid")
   if not pHumanoid then return end

   -- Old: pHumanoid.Health = 0
   pHumanoid.Health -= 5
end

firePart.Touched:Connect(processDamage)
```
{{% /details %}}

You'll quickly see that when you touch the part, there might be more than just 5 damages. This is because body part engaged the event and so the `burn` function is called multiple times. Then, worse is the fact that there's no burning effect which we expected.

Part of the engineering process, you want to list out your problems and think about a potential solution for each of them. Ask yourself what you would like this piece of code to do instead. A strategy is to list out things you think Roblox (might) have which you can use.

{{% details title="Solution - Engineering Sub-activity" %}}
**Problems** - **Potential Solution**

1.  Multiple body-parts triggering event - A `debounce` mechanic is needed.
2.  Doesn't burn until body part stops touching - Use `TouchEnded` event and something to process characters still touching the fire brick
{{% /details %}}

This guide assumes that you have reached a conclusion similar to the solution above. In turn, I expect the student to know these concepts:

1.  [Functions]({{< relref "/programming/teaching/programming-fundamentals/functions" >}})
2.  [Conditionals]({{< relref "/programming/teaching/programming-fundamentals/conditionals" >}})
3.  [Maps]({{< relref "/programming/teaching/programming-fundamentals/maps/" >}}) (also called dictionaries)

<!--list-separator-->

-  charsTouching - Our Table (Map)

    > [!TIP]
    > **How to Approach the Guide**
    >
    > Try to implement the code on your own first before looking at the solutions.

    First, create a variable and assign an empty table to it. This guide is going to refer to this table as `charsTouching`. Expanded, it's characters touching.

    {{% details title="Solution - Making an empty table" %}}
    ```lua { filename="workspace/FireBrick/Script" }
    charsTouching = {}
    ```
    {{% /details %}}

    Our table is going to hold keys which are going to the characters' name. The name of every player's character model is the same as the player's username. The value for each key is going to be table that holds (1) the player character and (2) the last time the burn effect was applied which we get from the function [os.time](https://create.roblox.com/docs/en-us/reference/engine/libraries/os#time).

    {{% details title="Solution - Table Entry Example" %}}
    ```lua { filename="Pseudo-code" }
    charsTouching = {
       ["player1"] = {<Character>, <number>}
    }
    ```
    {{% /details %}}

<!--list-separator-->

-  Setting Up the Code Skeleton

    `Code Skeleton` is no way an official term in computer science. We first though write a simple structure of our code which includes two functions for the events `Touched`, `TouchEnded`, and as well [Heartbeat of RunService](https://create.roblox.com/docs/en-us/reference/engine/classes/RunService#Heartbeat).

    {{% details title="Solution - Code Skeleton" %}}
    ```lua { filename="workspace/FireBrick/Script" }
    RunService = game:GetService("RunService")
    fireBrick = script.Parent
    charsTouching = {}

    function subscribe(otherPart: BasePart)
    end

    function unsubscribe(otherPart: BasePart)
    end

    function processBurn(deltaTime: number)
       -- We won't use the parameter deltaTime.
    end

    fireBrick.Touched:Connect(subscribe)
    fireBrick.TouchEnded:Connect(unsubscribe)
    RunService.Heartbeat:Connect(processBurn)
    ```
    {{% /details %}}

<!--list-separator-->

-  Complete Solution

    {{% details title="Solution" %}}
    ```lua
    charactersTouching = {
        -- ["Player1"] = {12312512, true, <Character>}, -- touching is still occuring.
        -- ["Player2"] = {123451243, false, <Character>}, -- touch stops about to be removed from the table
        -- ["Player3"] = nil -- not actually in the table anymore
    }

    part = script.Parent

    function isCharacter(otherPart: BasePart)
        local potentialCharacter = otherPart.Parent
        local humanoid = potentialCharacter:FindFirstChild("Humanoid")
        if humanoid then return potentialCharacter end
        return false
    end

    function startBurn(otherPart: BasePart)
        local character = isCharacter(otherPart)
        if not character then return end
        if charactersTouching[otherPart] then return end
        charactersTouching[otherPart] = {os.time(), true, character}
    end

    function stopBurn(otherPart: BasePart)
        local character = isCharacter(otherPart)
        if not character then return end
        charactersTouching[character.Name][2] = false
    end

    function burnOnStandBy()
        for characterName, data in charactersTouching do
            if not data[2] or not data[3] then
                charactersTouching[characterName] = nil
                continue
            end
            if os.time() - data[1] > 1 then
                data[3].Humanoid.Health -= 5
            end
        end
    end

    part.Touched:Connect(startBurn)
    part.Touched:Connect(stopBurn)
    part.Heartbeat:Connect(burnOnStandby)
    ```
    {{% /details %}}
