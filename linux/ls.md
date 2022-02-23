# ls

## ls 的 output
* 特别注意！ls 出来的 date time **是 last modified date time! 不是 creation date time!** 

## Count number of files in a directory
```
$ ls  /some/dir  | wc  -l
1234
```
1234 is the total number of files and sub dirs in this dir.

For more options/granuality of the counting, see this article: https://linuxhandbook.com/count-files-directory-linux/
