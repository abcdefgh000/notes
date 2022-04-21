Reference: https://wiki.archlinux.org/index.php/File_permissions_and_attributes

`Read` permission is 4, `Write` permission is 2, `Execute` permission is 1. So the following permission:

```
rwxrw-r--
```

in bit form is:

```
111 110 100
```

in octal (八进制) form is:
```
7 6 4
```

in decimal (十进制) form is:

```
(7 * 8^2) + (6 * 8) + 4 = 500
```

An Octal <--> Decimal <--> Hexadecimal <--> Bit online converter: https://www.rapidtables.com/convert/number/octal-to-decimal.html
