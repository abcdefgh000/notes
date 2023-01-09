# destroy parts in the `Workspace` (game scene)

Use the method `Part:Destroy()`:

```lua
local house_parts = { game.Workspace.left_wall, game.Workspace.right_wall, 
                      game.Workspace.back_wall, game.Workspace.roof, }

for index, part in pairs(house_parts) do
  part:Destroy()
end
```

Notice that in the game scene, the above destroying events follow physical rules! So if both left and right wall are destoyed first and the root is only supported by the back wall, the roof will lean and fall front-wards until its front end touches the ground.
