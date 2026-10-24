+++
title = "Rock Paper Scissors (WIP)"
draft = false
+++

## Rock Paper Scissors {#rock-paper-scissors}

You're creating a multi-player rock-paper scissors game. Assume that in this game there are only two players. You're making a turn-based game.

Here's some code to begin. By the way, do we use server or local script?

```lua { filename="ServerScriptService/Game" }
Players = game:GetService("Players")
players = Players:GetPlayers()

-- Wait until there are two players
while #players < 2 do
   task.wait(1)
end

--[[
   TODO: variables player1, player2. Use the variable players
   player1 = ...
   player2 = ...
]]

ReplicatedStorage = game:GetService("ReplicatedStorage")
-- Creating a remote event directly
submitRF = Instance.new("RemoteFunction")
submitRF.Name = "SubmitRPS"
submitRF.Parent = ReplicatedStorage

player1Score = 0
player2Score = 0

VALID_CHOICES = {
   "rock",
   "paper",
   "scissors"
}

--[[
   Returns true if given argument is a valid choice of rock/paper/scissors

   choice: the possible valid choice as a string

   Returns true if is valid choice and false otherwise
]]
function isValidChoice(choice: string): boolean
   for _, reference in VALID_CHOICES do
      if reference == choice then
         return true
      end
   end
   return false
end

--[[
   This function returns the winner out of the two choices

   player1Choice/player2Choice: either "rock", "paper", or "scissors"

   Returns player who won or nil of they have the same choice
]]
function getWinner(player1Choice: string, player2Choice: string): Player?
   assert(isValidChoice(player1Choice), `Choice of {player1.Name} (player2) is invalid.`)
   assert(isValidChoice(player2Choice), `Choice of {player2.Name} (player1) is invalid.`)

   -- TODO: Form if-statements and return the player that won
   -- Replace return nil with your custom logic if needed
   return nil
end

-- The game keeps going until one player leaves
while player1 and player2 do
   local player1Choice: string = submitRF:InvokeClient()
   local player2Choice: string = submitRF:InvokeClient()

   -- TODO: Form an if-statement to increase player1Score or player2Score
   -- Use the getWinner function that you made

   print(player1.Name .. "'s score:", player1Score)
   print(player2.Name .. "'s score:", player2Score)
   task.wait(5)
end
```

```lua { filename="StarterPlayer/StarterPlayerScripts/UI" }
ReplicatedStorage = game:GetService("ReplicatedStorage")
submitRF = ReplicatedStorage:WaitForChild("SubmitRPS")

Random = Random.new()

VALID_CHOICES = {
   "rock",
   "paper",
   "scissors"
}

submitRF.OnClientInvoke = function(player: Player)
   local randomIndex = Random:NextInteger(1, 3)
   -- TODO: variable randomChoice use randomIndex
   -- Get value from VALID_CHOICES
   local randomChoice = ...
   return randomChoice
end
```
