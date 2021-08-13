# Regex meta-characters

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

### OR
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
  * 用途1：表示一个 **capturing group**
    * 例如：
      * `(1a)` Matches: 1a, B1a, 1aT, tY1aXUI9... 《=== 自己写 unit test！看会 match 后面这些 非 1a 的么？？？
      * `(1a)+` Matches: 1a, 1a1a, 1a1a1a... <=== 还能 match eee1aiii 么？我自己写个 unit test！！！
      * `(a-z0-9)` 表示 a-z 中 取一个 char，并且紧贴着后面 再在 0-9 之中 取一个 char，比如 b8 会被 match 上 <==== 我自己写个 unit test ！！！！！《==== 可能是 不对的！！！
      * a-z0-9 -- Can be captured by (a-z0-9) and then can be referenced in a replacement and/or later in the expression. 《== 按这个 更正！！！
      * (a-z0-9) -- Explicit capture of a-z0-9. No ranges.  《==== 按这个更正！！！(a-z0-9) will match the exact string "a-z0-9"
        * 就是说，- 符号 在 () 里是没有意义的是么？必须在 [] 里 - 才算是个 metacharacter？？？<=== test!!
      * metacharacter 在 `()` 里不会被视为 字面意义上的字符，还是会保持它们的 metacharacter 的 特殊意义！<=== 写 unit test！！！
        * 比如 `(\s+)` 是 空格 重复 1 到 N 次 <==== 写 unit test！！！
        * `(a-z|0-9)` 会如何？里面的 | 会是 OR 还是 一般意义上的 竖直线？？<==== test!!!
  * 用途2：Group other expressions
    * 例如：`([0-9]|[a-z])` 意思是 任何 一位数字 或 一个小写字母

* `[]`
  * 表示一个 **character class**，在这个 class 里 **取且仅取一个 char**。
    * 例如：
      * `[ab]` 是 a 或 b <=== 我自己写个unit test 看一下！！！
      * metacharacter 在 `[]` 里 都会被视为 字面意义上的字符！比如：`+` 在 `[]` 里就是一个 加号！不是 “1次或多次” 的意思了！<==== 写 unit test！！！
        * 比如 `[\s+]?` 是 空格 或者 加号，重复 0 到 1 次 <==== 写 unit test！！！
        * () 在 [] 里 也只是 括号的意思 <=== test！！！
        * | 在 [] 里也只是 竖直线 的意思 <=== test！！！
      * `[a-z0-9]` 是 a-z 中的一个 char **或者** 0-9 中的一个 char <==== 自己写 unit test 测一下！！！
      * 到底是 a 和 b 都要有，还是只能有一个？？？？[a-zA-Z] 到底是什么意思？？？？在 RE2 和 外网的 regex 都试试看！写 unit test！！！
    * 写案例：(|('|")) 表示 “无”，记录下如何表示 “无”！！！！！<======

* `-`
  * Creates a range of characters within brackets `[]` to match, anywhere in a string
    * 例如：[0-9] 表示 0到9之中的任何一个 1位数字

## Escape

* `\`
  * 用途1：To match a **metacharacter**, escape it with a backslash `\`
    * 例如：`\+` matches a literal "+" character，如果没有这个 `\` 在前面，`+` 就会被视为一个 metacharacter 而非一个 加号
  * 用途2：和某些字母组合在一起，有特殊作用，比如：
    * `\n` 表示 new line
    * `\s` 表示 空格 space
    * `\t` 表示 Tab 

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

