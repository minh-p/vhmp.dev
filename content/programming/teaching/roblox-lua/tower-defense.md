+++
title = "Tower Defense (WIP)"
draft = false
+++

## Tower Defense {#tower-defense}

A very popular type of Roblox game is the Tower Defense genre. A very basic setup of this type of game includes the following elements:

1.  A lobby where player can buy and store units into their inventory using a permanent currency (like Gold).
2.  The actual game place where player can use the troops to defend their home base using a temporary currency (like Silver).

A project like this is very complex. This page will list the most important mechanics like the shop, inventory, and placing down units, making the player units attack enemy units, and make enemy units spawn and path find across the map.


### Requirements {#requirements}

This project is complex. You should understand everything in the [programming fundamentals roadmap]({{< relref "/programming/teaching/programming-fundamentals/#roadmap" >}}) up until maps and dictionaries.


### Player Data {#player-data}

We have to store certain player information like the units they own and as well as the unit they have equipped. All of which we'll use the `DataStore` in order to store these data. There's also the `MemoryStore` but we won't use that for this page because `MemoryStore` should only be used for data that needs to be shared between servers that has an expiration date as opposed to the `DataStore`. Also, remember that `data management` must be done in a `Server Script`, so you're going to have to work with `Remote Functions` to send data to the server and back. The reason why I recommend a `Remote Function` is because it's a `2-way` communication pathway where both the `server` and `client` can understand if their request was successful. You can also just use `Remote Events` if you're adamant about a `1-way` communication of sending and receiving request without sending back any information.


#### Working With Data Store {#working-with-data-store}

While the simplest data structure that can be considered is a table list of `strings`, the way they each are handled should differ from each other.

First, we're lucky that Roblox accepts tables&mdash;either specifically a list or a map&mdash;directly for its data store. So whenever we have a table we can just use [GlobalDataStore:UpdateAsync](https://create.roblox.com/docs/en-us/reference/engine/classes/GlobalDataStore#UpdateAsync) and send in the table as the second argument to the `transform function`.

Here's an example of storing a table inside a data store. Ideally, you should attempt to code this out before looking at this solution. In this example, the player's data is saved when they leave the game out of any reason. We're using the approach where the player's data is only truly saved when they leave the game instead of burdening data store every single request. So the server has to save data somewhere on its own &rarr; you can use a table that stores pairs where the key is the player's name and the value is another table that stores other information.

You choose the key you want for your `DataStore`, it has to be permanent and unique for all players, one such value is the player's user id.

{{% details title="Saving Player Data When They Leave" %}}
```lua { filename="ServerScriptService/PlayerData" }
DataStoreService = game:GetService("DataStoreService")
inventoryStore = DataStoreService:GetDataStore("Inventory")

playerData = {}

Players = game:GetService("Players")

function savePlayerInventory(player: Player)
   -- Check if player's data is recorded
   -- This condition only works when a player joined first time and did not buy or equip units
   if not playerData[player.Name] or not playerData[player.Name].inventory then
      return
   end

   local inventoryData = playerData[player.Name].inventory
   -- Inventory is a table list of strings
   inventoryStore:UpdateAsync(player.UserId, function() return inventoryData end)
end

Players.PlayerRemoving:Connect(savePlayerInventory)
```
{{% /details %}}

> [!TIP]
> **DataStore and Rate Limit**
>
> Your job as a Roblox developer is to ensure the integrity of the player's data while making sure that requests to data store is sustainable at a higher player's load. If you see warnings about `data store` request limits then, consider holding the player's data on the server as they play and only saving to data store when they leave.


#### What Data Structure {#what-data-structure}

Here are some recommendations about the data structure.

For the available shop items, you should put them into a module script serving as a place to search up the unit's image, name, and price.

For the player's inventory, you should store them as a table of strings that's sorted lexicographically (alphabetical order) and implement a binary search algorithm so that confirming whether a player owns the unit takes `O(Log N)` instead of `O(N)` algorithmic complexity.

As for the player's currently equipped units, because they are fixed to a small number, we're not going to deal with binary searches. Additionally, because the player has the liberty to have gaps in their hot bar, removing items from the table must accommodate gaps. Therefore you should use a table map (also called dictionary).
