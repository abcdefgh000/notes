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

-- Connect an existing function to an event
local function TouchedUtilFunction()
  print("Util function: Touched!")
end
-- Attention: inside `Connect()`, do not use `()` after the function name
stone1.Touched:Connect(TouchedUtilFunction)
```
