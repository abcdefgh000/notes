# String Operations

## 用 自定义的 间隔符 把一个 container 里的 elements 串起来
```cpp
absl::StrJoin(<container>, "\n")
```
上面 code 里的 container 可以是 vector，set... 这个 code 运行出来的效果是：
```
element1
element2
element3
...
```
