## Handbook for commands

* Get a file in another commit or branch into the current branch
  ```
  git checkout <commit SHA> -- ./folder_name/file_name.pbtxt
  ```

* Merge everything from another local branch A to our current local branch B: inside branch B, run this command
  ```
  git merge A
  ```

* Create a new local branch and at the same time link+update to a remote target branch, no matter the remote target branch is older or newer than the remote master branch
  ```
  git checkout <remote target branch name>
  ```
