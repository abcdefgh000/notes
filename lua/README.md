# basic syntax of Lua

## variable and function

```lua
-- Local variables
local zombie1 = game.Workspace.zombie1
local reflectance = 0.4

-- Function definition
local function SetupZombie(zombie)
  zombie.Reflectance = reflectance
  print("Succeeded setting up a zombie!")
  return zombie.name
end

-- Calling the function
local zombie_name = SetupZombie(zombie1)
```

## if, and, or
```lua
if x == 1 then
  -- do sth
elseif x == 2 then
  -- do sth
else
  -- do sth
end
```
```lua
if animal.name == "Dog" and animal.age <= 3 then
  print("Small dog")
end
```
```lua
if animal.name == "Cat" or animal.name == "Lion" then
  print("Feline")
end
```

## while
```lua
while number < 5 do
  -- do sth
  number = number + 1
end
```
```lua
while true do
  -- do sth hopefully it can break some time
end
```

## repeat (not used very often)
```lua
repeat 
  -- do sth
  number = number + 2
until number < 5
```

## data structures

### table

#### define a table

A table can contain different data types, that is different than many other languages:
```lua
local my_numbers = { 1, 2, 3 }
local my_ingredients = { "egg", "sugar", "flour" }
local my_stuff = { 1, 2.5, "hi" }
```

The index of a table in Lua starts with 1, not 0, that is different than many other languages:
```lua
local numbers = { 10, 20, 30 }
local first_number = numbers[1]  -- This is 10. There is no `numbers[0]`.
```
