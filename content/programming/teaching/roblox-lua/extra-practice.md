+++
title = "Practice"
draft = false
+++

## Additional Practice {#additional-practice}

This page includes small exercises of many concepts that's detached from any specific long-term project.


## For-Loops {#for-loops}

There are two types of for-loops in Roblox: the numeric and general for loop. The `numeric for-loop` allows the programmer to get the indices of the table array and additionally specify what indices he uses. The `generic for-loop` on the other hand gives two variables: one keeps track of the indices, and the other one the values. However, the generic for loop will run for all the values inside the table array. Some of the exercises below will include solutions for both kinds of for-loops.


### Printing Even Numbers {#printing-even-numbers}

Make a function called `printEvens` which takes in a list of arbitrary values (the values can be of any type). Then, print the even numbers into the output.

{{% details title="Hint 1 - Function signature" %}}
The function `printEvens` should only accept a single value which is list of anything. The function signature should be the following:

```lua { filename="ServerScriptService/Script" }
function printEvens(list: {any}): nil
end
```
{{% /details %}}

{{% details title="Hint 2 - Functions and Operators Needed" %}}
The function `typeof` allows you to get the type of the value.

```lua { filename="Example - typeof" }
print(typeof(10)) --> Prints "number"
print(typeof("Hello")) --> Prints "string"
print(typeof(workspace.Part)) --> Prints "Instance"
```

The modulo operator `%` allows you to get the remainder of the right value dividing the left value.

```lua { filename="Example - evenness condition" }
x = 10
if x % 2 == 0 then
   print(tostring(x) .. " is of course even")
end
```
{{% /details %}}

Part of this exercise is a challenge for you research the tools you need to use. Find the Roblox tutorial/documentation pages on the for-loops.

{{% details title="Hint 3 - Important Document Pages on For-Loops" %}}
-   The numeric for-loop: <https://create.roblox.com/docs/en-us/tutorials/fundamentals/coding-4/intro-to-for-loops>
-   The generic for-loop (ipairs, array): <https://create.roblox.com/docs/en-us/tutorials/fundamentals/coding-5/pairs-and-ipairs#arrays-and-ipairs>
{{% /details %}}

{{% details title="Numeric For-Loop Solutions" %}}
```lua { filename="Solution" }
function printEvens(list: {any}): nil
   for i = 1, #list do
      local value = list[i]
      if typeof(value) == "number" then
         if value % 2 == 0 then
            print(value)
         end
      end
   end
end

printEvens({1, 2, 3, false, "hello", workspace})
```

```lua { filename="Alternative Solution with the conjunction logical operator =and=." }
function printEvens(list: {any}): nil
   for i = 1, #list do
      local value = list[i]
      if typeof(value) == "number" and value % 2 == 0 then
         print(value)
      end
   end
end

printEvens({1, 2, 3, false, "hello", workspace})
```
{{% /details %}}

{{% details title="Generic For-Loop Solutions" %}}
```lua { filename="Solution" }
function printEvens(list: {any}): nil
   for _, value in list do
      if typeof(value) == "number" then
         if value % 2 == 0 then
            print(value)
         end
      end
   end
end

printEvens({1, 2, 3, false, "hello", workspace})
```

```lua { filename="Alternative Solution with the conjunction logical operator =and=." }
function printEvens(list: {any}): nil
   for _, value in list do
      if typeof(value) == "number" and value % 2 == 0 then
         print(value)
      end
   end
end

printEvens({1, 2, 3, false, "hello", workspace})
```
{{% /details %}}


### Concatenating Strings From List {#concatenating-strings-from-list}

Make a `function` called `bulkConcat` that takes in a list of strings. This function should return one single string which `concatenates` all of the strings inside the list.

The function also takes in a `second value`, which is a string that's going to separate different strings `concatenated` together.

Put the following line of code **after** your solution. The game yielding no errors would prove that your function works.

```lua
assert(bulkConcat({"hello", "hey", "what"}, " ") == "hello hey what")
```

{{% details title="Helpful Examples" %}}
Example: concatenating a string

```lua
string1 = "Hello"
string2 = " World"
print(string1 .. string2) --> Prints "Hello World"
```

Example: concatenating a string2

```lua
string1 = "Hello"
string1 = string1 .. "Hello2"
string1 = string1 .. "Hello3"
print(string1) --> Print "HelloHello2Hello3"
```

Related Example: Sum of numbers inside a list

```lua
local totalNumber = 0
local numbers = {1, 2, 3}
for index, number in numbers do
   totalNumber = totalNumber + number
end
```
{{% /details %}}

{{% details title="Hint - Function Signature" %}}
Your function signature should look like this with type hinting:

```lua { filename="ServerScriptService/Script" }
function bulkConcat(strings: {string}, separator: string)
end
```
{{% /details %}}

{{% details title="Solution - Numeric For-Loop" %}}
```lua
function bulkConcat(strings: {string}, separator: string)
   result = ""
   for i = 1, #strings do
      local value = strings[i]
      result = result .. value
      if i < #strings then
         result = result .. separator
      end
   end
   return result
end

assert(bulkConcat({"hello", "hey", "what"}, " ") == "hello hey what")
```
{{% /details %}}

{{% details title="Solution - Generic For-Loop" %}}
```lua
function bulkConcat(strings: {string}, separator: string)
   result = ""
   for index, value in strings do
      result = result .. value
      if index < #strings then
         result = result .. separator
      end
   end
   return result
end

assert(bulkConcat({"hello", "hey", "what"}, " ") == "hello hey what")
```
{{% /details %}}


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
