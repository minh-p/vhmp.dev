+++
title = "First-Person Shooter (WIP)"
draft = false
+++

## Project Description {#project-description}

This project features the creation of an average first person shooter on Roblox. The first-person shooter system contains many individual parts that are going to be completed one step at a time.


## Viewmodel As an Idea {#viewmodel-as-an-idea}

A viewmodel is a game programming technique where the body part of a player is rendered on the player side instead of the server. This means that there has to be another view model that is going to render on the player.

In a Roblox game like Arsenal, you can see the body arms as standard blocky R6 limbs while the outward appearance seen by the other players are that of R15. The point is that the player has their fake arms.


## Creating Fake Arms {#creating-fake-arms}

A standard fake arm or viewmodel requires a root part which is similar to that of a Humanoid Root Part of the player, a Humanoid object, and as well as the left arm, right arm, and then gun.

The notes will not be going over how to make the specific view model as you can just get one from the tool box without any scripts or create one from a YouTube tutorial.

One helpful plugin that helps this could be RigEdit Lite.

You should also then be able animate the viewmodel. As such make your equipped animation where the end result should look like a Minecraft zombie. Make sure to publish this animation object and get the animation Id which you should copy and then paste into the `AnimationContent` property of an `Animation` object. Put this `Animation` object inside the `ReplicatedStorage`.


## Playing Animations {#playing-animations}

First, let's go over animations as we want to see our arms. Normally when you stand up and have your arms by your side with your head tilted up normal to the horizon, you won't see your arms. As such, with your equipped animation you can script the animation playing.

We're going to test out your animation by creating a script which later we're going to disable and delete. But for now, it's a good opportunity for you to practice creating animations.

Name the fake arms you just created `Viewmodel` and put it inside the workspace.

```lua { filename="ServerScriptService/AnimationTest (Server/Normal/Non-Local Script)" }
local equippedAnimation = game:GetService("ReplicatedStorage").Animation
local viewmodel = workspace.Viewmodel
local viewmodelAnimator = viewmodel.Humanoid.Animator
local equippedTrack = viewmodelAnimator:LoadAnimation(equippedAnimation)

equippedTrack.Looped = true
equippedTrack:Play()
```

Select `Run` instead of `Test` and press the play icon with your camera looking at the viewmodel you have inside your workspace.

> [!TIP]
> **Anchor and Primary Part**
>
> Make sure to anchor the root part of the viewmodel. As well, make the viewmodel's primary part to be the root part.

You should see the animation of the viewmodel play.


## Attaching the Viewmodel to the Player Camera {#attaching-the-viewmodel-to-the-player-camera}

Now, disable the script that we just used to test the animation and create a local script inside `StarterPlayerScripts`, which is the place to put any local script that we do not want to be in the workspace.

As well, move your viewmodel into `ReplicatedStorage`.

Here's the code that you're going to put inside the local script

```lua { filename="StarterPlayerScripts/Viewmodel (Local Script)" }
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local viewmodelSrc = ReplicatedStorage.Viewmodel
local equippedAnimation = ReplicatedStorage.Animation

-- TODO 1: Clone the viewmodel and parent it to the workspace

-- TODO 2: Play the Equipped animation on the clone

-- TODO 3: Use RunService.RenderStepped to constantly set the clone's CFrame
```

{{% details title="TODO 1 - clone viewmodel" %}}
```lua { filename="StarterPlayerScripts/Viewmodel (Local Script)" }
--...
-- TODO 1: Clone the viewmodel and parent it to the workspace
local viewmodelClone = viewmodelSrc:Clone()
viewmodelClone.Parent = workspace
--...
```
{{% /details %}}

{{% details title="TODO 2 - play the Equipped animation on the clone" %}}
```lua { filename="StarterPlayerScripts/Viewmodel (Local Script)" }
--...
-- TODO 2: Play the Equipped animation on the clone
local animator = viewmodelClone.Humanoid.Animator
local equippedTrack = animator:LoadAnimation(equippedAnimation)
equippedTrack.Looped = true
equippedTrack:Play()
--...
```
{{% /details %}}

{{% details title="TODO 3 - attach viewmodel to player's camera" %}}
```lua { title="StarterPlayerScripts/Viewmodel (Local Script)" }
local RunService = game:GetService("RunService")
local camera = workspace.CurrentCamera

local function attachCamera()
   viewmodelClone.PrimaryPart.CFrame = camera.CFrame
end

RunService.RenderStepped:Connect(attachCamera)
```
{{% /details %}}


## Fixing Collision (WIP) {#fixing-collision--wip}

Because we have the Humanoid inside the viewmodel. By default, it overrides the collision of the arms causing it to collide with the player's body parts.

This section is a work in progress.
