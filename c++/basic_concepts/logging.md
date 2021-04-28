# C++ 里做 logging 的一些小技巧

## 列出一个 container 里的 elements
用类似于下面这种code：
```cpp
std::vector<std::string> filenames = ...

std::cout << "The files' names are: \n"
          << absl::StrJoin(filenames, "\n");
```
上面的 code 跑出来的效果是：
```
The files' names are:
filename1
filename2
filename3
...
```
更具体的说明 见我 关于 string operations 的 note。


