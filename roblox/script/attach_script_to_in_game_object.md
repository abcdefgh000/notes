# attach a script to an in-game object

## commonly used statements

* Access the parent object to which the current script lived on.

  For example if the object and its associated script are:
  ```
  stone1
      stone_script
  ```
  Then use this statement to get `stone1` in `stone_script`:
  ```lua
  -- The `script` in this statement is a key word! It's not the name of any object! 
  -- (All lower case!)
  -- `Parent` is also a key word.
  local stone1 = stript.Parent
  ```



