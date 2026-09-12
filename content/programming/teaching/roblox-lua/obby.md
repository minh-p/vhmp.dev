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


#### Kill Brick {#kill-brick}

Kill Brick simply sets the health of the player to zero when the player touches it.

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

Unlike the Kill Brick, the fire brick deals damages over time and is much more complex. We have to make cool-down system.

Burn Brick #1
Simply decrease the health instead of setting it to 0.

{{% details title="Solution" %}}
```lua
part = script.Parent

function burn(otherPart)
    -- First, we confirm if the otherPart is a body part
    local character = otherPart.Parent
    local humanoid = character:FindFirstChild("Humanoid")
    if not humanoid then return end

    humanoid.Health -= 5
    -- Code above is same as:
    -- humanoid.Health = humanoid.Health - 5
end

part.Touched:Connect(burn)
```
{{% /details %}}

Burn Brick #2 - Countdown system attempted

{{% details title="Solution" %}}
```lua
-- the function os.time() returns seconds since January 1st of 1970.
savedTime = os.time()

function burn(otherPart)
    -- First we once again confirm if otherPart is a body part
    local character = otherPart.Parent
    local humanoid = character:FindFirstChild("Humanoid")
    if not humanoid then return end

    -- Cooldown of 1 second
    if os.time() - savedTime > 1 then
        humanoid.Health -= 5
    end
end
```
{{% /details %}}

Bug: In the first version, we thought the burning effect worked because multiple body parts was causing the burn.
In the next version we have to begin integrating the event TouchEnded to deal damage gradually until the player stops touching the part

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
