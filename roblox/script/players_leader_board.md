# creates a leader board for players

## requirements
* Whenever a new player joins the game, add and display him in the leader board immediately.
* When a player's mouse clicks a specific object (e.g. a stone) in the game scene, add the score of that player once.

## steps

### In the script of the `Workspace`

Add the following code:

```lua
-- Creates a leader board for players.
game.Players.PlayerAdded:Connect(function(added_player)
	local leader_board = Instance.new("Folder", added_player)
    -- The leader board has to be named exactly as "leaderstats",
	-- or Roblox won't be able to recognize it!
	leader_board.Name = "leaderstats"

	-- Adds a column into the leader board
	local player_score = Instance.new("IntValue", leader_board)
	player_score.Name = "Score"
	player_score.Value = 0

	local player_health = Instance.new("IntValue", leader_board)
	player_health.Name = "Health"
	player_health.Value = 100
end)
```

### Add a `ClickDetector` to the object to click
1. Hover the object to click in the `Workspace` panel
2. Press the `+` button
3. Choose the `ClickDetector`

So it will look like this:
```
stone1   +
    ClickDetector
    stone1_script
```

### In the script of the object to click

Add the following code:

```lua
script.Parent.ClickDetector.MouseClick:Connect(function(clicked_player)
	local player_score = clicked_player.leaderstats.Score
	player_score.Value = player_score.Value + 1
end)
```

