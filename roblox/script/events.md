# events

## create an event and connect a callback function to this event

```lua
-- In-game object
local stone1 = game.Workspace.stone1

-- `Touched` is an event of the in-game object `stone1`
-- `Connect` has to be preceeded by a `:`
stone1.Touched:Connect(function()
  print("One-off function: Touched!")
end)
```
```lua
-- Connect an existing function to an event
local function TouchedUtilFunction()
  print("Util function: Touched!")
end

-- Attention: inside `Connect()`, do not use `()` after the function name
stone1.Touched:Connect(TouchedUtilFunction)
```

## utilize the parameter that is offered (detected) by the event

For example, in the `ObjectBrower` of `Roblox Studio`, the event `Touched` is shown like this:
```
Touched

event Touched(Instance otherPart)
Member of BasePart
```

So `Instance otherPart` means this event `Touched` can detect and offer you the (opponent) object that is touching the current object FOR FREE. So if the current object is `stone1` and a `ball1` just touched `stone1`, then `otherPart` is `ball1`.

To access and use the `otherPart` in the call back function connected to the event, here is an example: 
```lua
local stone1 = game.Workspace.stone1

-- `touching_object` is just an arbitrary name for the above `otherPart`,
-- it can be named anything by the user
stone1.Touched:Connect(function(touching_object)
  -- This will print the name of the `touching_object` to the console
  print(touching_object)
  
  -- For a player-object in the game, any part of the player-object can hit the `stone1`,
  -- like `left_leg`, `right_arm`... can all be the `touching_object`.
  -- So we have to find the "Humanoid" field in the player-object to really access and manipulate
  -- the "human body part" in the following way.
  -- We should check if the `touching_object` has a parent humanoid first instead of directly
  -- trying to access the humanoid, because anything can touch the `stone1`, for example an apple,
  -- and the apple does not have a parent humonoid.
  --
  -- Added another criterion of `Health > 0` to avoid dying multiple times (a humanoid can die multiple
  -- times before its health is set to 0 since it has multiple body parts that all can touch the death item).
  if the_touching_object.Parent:FindFirstChild("Humanoid") and the_touching_object.Parent.Humanoid.Health > 0 then
    the_touching_object.Parent.Humanoid.Health = 0
    print("Killed " .. the_touching_object.Parent.Name)
  end
end)
```
