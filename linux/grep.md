# grep

## Linux 里 如何在一个 文本文件里 找一个关键字，并查看它所在的那一行前后几行的内容

For BSD or GNU grep you can use -B num to set how many lines before the match and -A num for the number of lines after the match.
```
grep -B 3 -A 2 foo README.txt
```

If you want the same number of lines before and after you can use -C num.
```
grep -C 3 foo README.txt
```
This will show 3 lines before and 3 lines after.

Ref: [How to grep a file and show several surrouding lines](https://stackoverflow.com/questions/9081/grep-a-file-but-show-several-surrounding-lines)
