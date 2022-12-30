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

## if, loop
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
