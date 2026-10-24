+++
title = "Practice"
draft = false
+++

## Additional Practice {#additional-practice}

This page includes small exercises of many concepts that's detached from any specific long-term project.


## Selection Sort {#selection-sort}


### Sorting Numbers (Selection Sort) {#sorting-numbers--selection-sort}

Make a function that sorts an array of integers using two for-loops. There are three kinds of loops you could use (bubble sort, insertion sort, selection sort). For now, just do selection sort.

For selection sort you're sorting from the left to the right side of the list. The outer loop is the loop that will put a number in the right position at a certain index while the inner for-loop gets the smallest number out of the numbers that's left.

Sort the list in-place (don't make a copy that's sorted):

```lua { filename="ServerScriptService/SelectionSortNumbers" }
numbers = {1, 5, 6, 2, 1, 4}

-- TODO:

-- The code below checks if the loop was done properly.
expectedNumbers = {1, 1, 2, 4, 5, 6}

for i = 1, #expectedNumbers do
   assert(numbers[i] == expectedNumbers[i], "Not sorted properly")
end
```

{{% details title="Hint (If You've Spent 20 Minutes Already" %}}
```lua { filename="ServerScriptService/SelectionSort" }
for i = 1, #numbers do
   local smallest = numbers[i]
   for j = i, #numbers do
      -- TODO: Make the inner for loop assign the actuall smallest number
      -- to the variable smallest when the outer for loop finishes
   end

   if smallest ~= numbers[i] then
      -- TODO: Swap numbers[i] with smallest
   end
end
```
{{% /details %}}

{{% details title="Full Solution (Look at when you run out of time)" %}}
```lua { filename="ServerScriptService/SelectionSort" }
for i = 1, #numbers do
   local smallest = numbers[i]
   local smallestIndex = i
   for j = i, #numbers do
      -- DONE: Make the inner for loop assign the actuall smallest number
      -- to the variable smallest when the inner for loop finishes
      if numbers[i] < smallest then
         smallest = numbers[i]
         smallestIndex = i
      end
   end

   if smallest ~= numbers[i] then
      -- DONE: Swap numbers[i] with smallest
      local originalValue = numbers[i]
      numbers[i] = smallest
      numbers[smallestIndex] = originalValue
   end
end
```
{{% /details %}}


### Sorting Player Names (Selection Sort) {#sorting-player-names--selection-sort}

You can compare strings. Whether the first string is "larger" than the second string depends if a character in the first string at the same index is after the character in the alphabet in the second string at the same index.

```lua
RunService = game:GetService("RunService")
Players = game:GetService("Players")

--[[
   Get actual player names if the code is running in an actual game
   Or, provide some fake player names if we're testing in Roblox
   Studio

   Returns a table list of strings which are the player names
]]
function getPlayerNames(): {string}
   if RunService:IsStudio() then
      return {
         "david.baszucki",
         "Roblox",
         "Builderman",
         "Shedletsky"

      }
   end

   local playerNames = {}
   for _, player in Players:GetPlayers() do
      table.insert(playerNames, player.Name)
   end
   return playerNames
end

-- TODO: Put your code in a function called selectionSort
--[[
   Perform a selection sort on any table list of things that are
   comparable.

   list: table of things that are comparable

   Returns the provided list but sorted
]]
function selectionSort(list: {any}): {any}
   -- TODO: selection sort
   -- Use selection sort of the previous exercise but just return it sorted

   return list
end

-- The code here will check if it's correct
sorted = selectionSort(getPlayerNames())
expected = {
   "Builderman",
   "Roblox",
   "Shedletsky",
   "david.baszucki"
}

for i = 1, #expected do
   assert(expected[i] == sorted[i], "Not sorted properly")
end
```

{{% details title="Full Solution" %}}
```lua { filename="ServerScriptService/SortingPlayerNames" }
function selectionSort(list: {any}): {any}
   -- DONE: selection sort
   -- Use selection sort of the previous exercise but just return it sorted

   for i = 1, #list do
      local smallest = list[i]
      local smallestIndex = i
      for j = i, #list do
         -- DONE: Make the inner for loop assign the actuall smallest number
         -- to the variable smallest when the inner for loop finishes
         if list[i] < smallest then
            smallest = list[i]
            smallestIndex = i
         end
      end

      if smallest ~= list[i] then
         -- DONE: Swap list[i] with smallest
         local originalValue = list[i]
         list[i] = smallest
         list[smallestIndex] = originalValue
      end
   end

   return list
end
```
{{% /details %}}
