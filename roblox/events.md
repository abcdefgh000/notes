# events

## create an event and connect a callback function to this event

```lua
-- In-game object
local stone1 = game.Workspace.stone1

-- `Touched` is an event of the in-game object `stone1`
-- `Connect` has to be preceeded by a `:`
stone1.Touched:Connect(function()

)
```
