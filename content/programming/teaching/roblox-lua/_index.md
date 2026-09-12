+++
title = "Luau"
draft = false
+++

## Luau (Roblox Luau) {#luau--roblox-luau}

Roblox games uses a fork (customized version) of Lua 5.1. While students can reference the official Lua documentation, some concepts commonly used in Roblox do not exist in the official releases of Lua

As usual, the index page includes the common Roblox features associated with Roblox Scripting. The latter parts nested inside describes some of the projects students have taken part of and is used to document all types of projects.


## Types of Scripts {#types-of-scripts}

There are three types of scripts in Roblox as of right: scripts, local scripts, and module scripts. The normal scripts are not actually "normal", they are code a developer writes to affect changes to the **server**. The local scripts include code that affects only a single player, other players other than the player that owns the local script do not see the changes to the game world.

> [!TIP]
> **Server vs. Client** - First-Person Shooter Example
>
> The normal Script contains code written for the server while the Local Script contains code written for a single player.
>
> In many games (not just in Roblox), the usage of fake-arms are employed. After all, if the player's arms are controlled by the Server in first-person, the arms movement will feature massive delay. Fake arms, or "viewmodels" are created in a Local Script that constantly sets the coordinate frame (CFrame) to that of the camera's CFrame offset by some amount.
