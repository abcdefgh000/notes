# create a tool for the characters in `StarterPack` to use in the game

## create the `Tool` object in the `StarterPack` category
A `Tool` can be anything that the character can use in the game, it does not have to be a literal "tool", it can be a "weapon", "potion bottle", "decoration stuff"...

Steps to create a `Tool`:
* Hover on the `StarterPack` category in the `Explorer`, press the `+` button
* Choose `InsertObject`, then choose `Tool`, in this way we have created a `Tool` type object inside `StarterPack`
* Any object in `StarterPack` will be:
  * Put into the "inventory" of a charater right away
  * The character will "own" that object and be able to "use" it
* Rename the `Tool` object, for example `sword`
* A `Tool` is just a logical container, it does not have an appearance in the game. We have to add visible `Part`(s) into this container to make the `Tool` visible. 
