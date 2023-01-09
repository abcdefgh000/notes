# rain drops falling down from random positions in the "sky"

In the `Workspace` script, write this:

```lua
-- Creates one rain drop.
local function CreateOneRainDrop()
	wait()
	
	local rain_drop = Instance.new("Part", game.Workspace)
	-- Specifies the 3D size of the object: (width, height, length)
	rain_drop.Size = Vector3.new(0.1, 0.3, 0.1)
	rain_drop.Anchored = false
	rain_drop.Transparency = 0.6
	
	-- `tick()` is the timestamp of "now".
	math.randomseed(tick())
	local origin_x = math.random(0, 30)
	local origin_y = 100
	local origin_z = math.random(0, 30)
	-- Specifies the 3D position of the object: (width, height, length)
	rain_drop.Position = Vector3.new(origin_x, origin_y, origin_z)
end

-- Creates rain drops in a batche.
local function CreateRainDropBatch(rain_drop_number_in_a_batch)
    local rain_drop_count = 0
	while rain_drop_count < rain_drop_number_in_a_batch do
		CreateOneRainDrop()
		rain_drop_count = rain_drop_count + 1
    end
end


-- Main function.
local batch_count = 0
while batch_count < 100 do
	CreateRainDropBatch(5)
	batch_count = batch_count + 1
end
```
