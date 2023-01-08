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

Use `table.remove()` to remove an element at the index i in the table. Be aware again that the index in Lua tables begins with 1, not 0.
```lua
local numbers = { 5, 3, 9 }
table.remove(numbers, 2)  -- This will remove the 2nd element, not the 3rd element.
-- The table `numbers` will now be { 5, 9 }.
```

Use `table.sort()` to sort a table in ascending order, but the elements in the table have to be sortable.
```lua
local numbers = { 5, 3, 9 }
table.sort(numbers)
-- The table `numbers` will now be { 3, 5, 9 }.
```


Use `table.concat()` to concatenate all the elements in a table, with a specified connection substring. The numbers can also be concatenated by this function.
```lua
local things = { "Hi", 3, "Hey" }
print(table.concat(things, "-" ))  -- This will display "Hi-3-Hey".
```
