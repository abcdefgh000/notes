# spreadsheet tricks

* 把一个字符串的 最后一个 `/` 以及之后的东西都去掉 (remove the last slash and everything after it)
  ```
  =REGEXEXTRACT(A1, "(.+)/")
  ```
