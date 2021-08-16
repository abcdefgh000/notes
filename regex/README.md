# Regex Overview

A regex usually comes within this form: `/abc/`, where the search pattern 被 2个 `/` 包围起来。

## Flags
在 regex 的 第二个 `/` 的后面，we can specify a flag with these values (we can also combine them each other):
* `g` (global)
  * Does not return after the first match, restarting the subsequent searches from the end of the previous match
* `m` (multi-line)
  * When enabled `^` and `$` will match the start and end of a line, instead of the whole string
* `i` (insensitive)
  * Makes the whole expression case-insensitive (for instance `/aBc/i` would match `AbC`)


# Regex metacharacters

## Wildcards
### Repetition operators
有3种：
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

还有一种 特殊的 符号：`{}`，有的地方提到它，有的没有提到，不知道是不是在某些 Regex 体系下它不可用？？？
* `{}`
  * `ab{3}`: Matches a string that has `a` followed by 3 `b`
  * `ab{3,}`: Matches a string that has `a` followed by 3 or more `b`
  * `ab{1,6}`: Matches a string that has `a` followed by 1 to 6 `c`
  * `a(bc){2,4}`: Matches a string that has `a` followed by 2 to 4 `bc`


### OR
* `|`
  * 意思是 `OR`
  * 例如：`1|10` 即 1 或 10

## Anchors
* `^`
  * Matches the adjacent chars at the beginning of a string
  * 例如：`^1a`：
    * 可以 match：1a, 1a5, 1aT67X8...，

* `$`
  * Matches the adjacent chars at the end of a string
  * 例如：`$1a`：
    * 可以 match：1a, 01a, UI90oPx1a...，

* `^foo$`
  * Exact match to `foo`

* `foo`
  * Match 任何 stirng that has substring `foo` (anywhere in it).


## Groups
* `()`
  * **metacharacter 在 `()` 里不会被视为 字面意义上的字符，还是会保持它们的 metacharacter 的 特殊意义**（但是 `-` 在 `()` 里就表示字面的 "-" 的意思！详见下文），例如：
    * `(a+)` 是 "a" 重复 1 到 N 次
    * `(a|b)` 是 "a" OR "b"，`(ab|cd)` 是 "ab" OR "cd"
  * **特别注意！`-` 在 `()` 里就表示 字面的 "-" 的意思！** 例如：
    * `(a-z0-9)` 会 match 字符串 "a-z0-9"，它不会 match "a0" 或者 "a" 或者 "0"
    * `(a-z|0-9)` 会 match 字符串 "a-z" 或者 "0-9"，它不会 match 字符串 "a-z|0-9"，因为 `|` 在 `()` 里还是表示 OR 的意思，不是字面的 "|"
  * 用途1：表示一个 **capturing group**
    * 例如：
      * `(1a)` Matches: 1a, B1a, 1aT, tY1aXUI9...
      * `(1a)+` Matches: 1a, 1a1a, 1a1a1a, 1a1aB, X1a1a1aTY...
  * 用途2：Group expressions 以 改变 或 突出 执行优先级
    * 例如：`(|('|"))` 表示 **无** 或 单引号 或 双引号
      * **特别注意！上面的例子里 如何表达 “无” 的做法**

* `[]`
  * `[]` 表示一个 **character class**，在这个 class 里 **取且仅取一个 char**。例如：
    * `[ab]` 是 a 或 b
  * **metacharacter 在 `[]` 里 都会被视为 字面意义上的字符！比如：
    * `+` 在 `[]` 里就是一个 加号！不是 “1次或多次” 的意思了**。例如：
      * `[a+]` 是 "a" 或者 加号，但不会 match "aa" 或 "aaa" 之类的
    * () 在 [] 里 也只是 "括号" 的意思，而不再有 特殊含义，例如：
      * `[(ab)]` 会 match "(" 或 "a" 或 "b" 或 ")"，不会 match "ab" 等




        * | 在 [] 里也只是 竖直线 的意思 <=== test！！！
      * `[a-z0-9]` 是 a-z 中的一个 char **或者** 0-9 中的一个 char <==== 自己写 unit test 测一下！！！
      * 到底是 a 和 b 都要有，还是只能有一个？？？？[a-zA-Z] 到底是什么意思？？？？在 RE2 和 外网的 regex 都试试看！写 unit test！！！
    * 写案例：

* `-`
  * Creates a range of characters within brackets `[]` to match, anywhere in a string
    * 例如：[0-9] 表示 0到9之中的任何一个 1位数字

## Escape

* `\`
  * 用途1：To match a **metacharacter**, escape it with a backslash `\`
    * 例如：`\+` matches a literal "+" character，如果没有这个 `\` 在前面，`+` 就会被视为一个 metacharacter 而非一个 加号
  * 用途2：和某些字母组合在一起，有特殊作用，比如：
    * `\s` 表示 空格 space
    * `\d` 表示 一个 一位数字
    * `\w` 表示 一个 alphanumeric char 或 underscore
    * `\n` 表示 new line
    * `\t` 表示 Tab 
    * `\r` 表示 回车

# Regex expressions 的 组合
## Concatenation
如果 regex expression `e1` matches `a`，regex expression `e2` matches `b`，则 `e1e2` matches `ab`

## Alternation
如果 regex expression `e1` matches `a`，regex expression `e2` matches `b`，则 `e1 | e2` 就是 `a` OR `b`

# Regex expressions 的 优先级（precedence）

The operator precedence, 从最强到最弱：
1. Explicit parentheses can be used to force different meanings, just as in arithmetic expressions
2. Repetition operators
3. Concatenation
4. Alternation

Some examples:
* `ab|cd` is equivalent to `(ab)|(cd)`
* `ab*` is equivalent to `a(b*)`


# References
* https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285
