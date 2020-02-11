## For MAC: .bash_profile

* Make terminal to show colors
  ```
  export CLICOLOR=1
  export LSCOLORS=GxFxCxDxBxegedabagaced
  ```

* Show Git branch in prompt
  ```
  parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
  }
  export PS1="\u@\h \w\[\033[32m\]\$(parse_git_branch)\[\033[00m\] $ "
  ```
  * inside the above `export PS1="..."`:
    * `u` is to display the current user name on linuxe
    * `h` is to display the current machine name
    * `w` is to display the current full path, if changed to `W`, then it will only display the current folder name without parent folders' names


## Overview
To make the changes to take effect immediately, run:
```
$ source ~/.bash_profile [or .bashrc]
```
