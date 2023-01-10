# create a tool for the characters to use in the game

A `Tool` can be anything that the character can use in the game, it does not have to be a literal "tool", it can be a "weapon", "potion bottle", "decoration stuff"...

## create the `Tool` object in the `StarterPack` category

* Hover on the `StarterPack` category in the `Explorer`, press the `+` button
* Choose `InsertObject`, then choose `Tool`, in this way we have created a `Tool` type object inside `StarterPack`
* Any object in `StarterPack` will be:
  * Put into the "inventory" of a charater right away
  * The character will "own" that object and be able to "use" it
* Rename the `Tool` object, for example `sword`
* A `Tool` is just a logical container, it does not have an appearance in the game. We have to add visible `Part`(s) into this container to make the `Tool` visible. 
  * Right click the `sword`, press `+`, add a `Part` under it. So now the `sword` will look like a 3D rectangle.
* In the game editor, we can not "see" the stuff inside the `StarterPack` category, we have to move the `sword` into the `Workspace` catagory to make it visible, and then we are able to edit its appearance. Now do so.

## Edit the apperance of the `Tool`

* Move the `sword` (`Tool`) from the `StarterPack` to the `Workspace` category.
* Click the `Part`, in its `Properties` panel, change the `Part` -> `Shape` from `Block` to `Cylinder`.
* Change the size, color... of the `Part` if you want.
* Connect several `Part`s to be one object to represent a `Tool` is a more advanced topic, will interprete that in another doc
