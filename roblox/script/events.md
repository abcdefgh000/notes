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

-- `touching_object` is just an arbitrary name, it can be named anything by the user
stone1.Touched:Connect(function(touching_object)
  -- This will print the name of the `touching_object` to the console
  print(touching_object)
  
  -- For a player-object in the game, any part of the player-object can hit the `stone1`,
  -- like `left_leg`, `right_arm`... can all be the `touching_object`.
  -- So we have to find the "Humanoid" field in the player-object to really access and manipulate
  -- the "human body part" in the following way:
  if touching_object.Parent:FindFirstChild("Humanoid") then
  end
end)
```
