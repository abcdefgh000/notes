# Regex meta-characters

## Wildcards
* `.`
  * 代表 任意 1个 字母，数字 或 符号

* `?`
  * 代表 它前面紧贴的 character 0到1 次
  * 例如：`10?` 可以是 1 或 10

* `+`
  * 代表 它前面紧贴的 character 1到无数 次
  * 例如：`10+` 可以是 10, 100, 1000, 10000...

* `*`
  * 代表 它前面紧贴的 character 0到无数 次
  * 例如：`10*` 可以是 1, 10, 100, 1000, 10000...

* `|`
  * 意思是 `OR`
  * 例如：`1|10` 即 1 或 10

## Anchors
* `^`
  * Matches the adjacent chars at the beginning of a string
  * 例如：`^1a`：
    * 可以 match：1a, 1a5, 1aT67X8...，
    * 不能 match：1b, 2a, 10a...

* `$`
  * Matches the adjacent chars at the end of a string
  * 例如：`$1a`：
    * 可以 match：1a, 01a, UI90oPx1a...，
    * 不能 match：1b, 2a, XY10a...

## Groups
* `()`
  * 用途1：Matches the enclosed chars in exact order, anywhere in a string
    * 例如：`(1a)` Matches: 1a, B1a, 1aT, tY1aXUI9...
  * 用途2：Group other expressions
    * 例如：`([0-9]|[a-z])` 意思是 任何 一位数字 或 一个小写字母

* `[]`
  * 用途1：Matches the enclosed chars in ANY order, anywhere in a string
    * 例如：`[1ab]` Matches: 1ab, b1a, 1abT, tY1baXUI9...
  * 用途2：和 `-` 一起表达一个范围的字符。见下文

* `-`
  * Creates a range of characters within brackets `[]` to match, anywhere in a string
    * 例如：[0-9] 表示 0到9之中的任何一个 1位数字

## Escape

* `\`
  * To match a metacharacter, escape it with a backslash `\`
  * 例如：`\+` matches a literal "+" character
