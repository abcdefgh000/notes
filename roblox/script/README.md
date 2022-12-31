# roblox scripts overview

# roblox scripts common tricks

* Access the parent object to which the current script lived on
  * For example the object and the script are:
    ```
    stone1
        stone_script
    ```
    Then use this statement to get `stone1` in `stone_script`:
    ```lua
    local stone1 = stript.Parent  -- `script` is a key word! It's not the name of any object! All lower case!
    ```
