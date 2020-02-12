To `bazel build` only one file/target inside the `BUILD` file (This is super useful when debugging! So we don't have to build a log of stuff unrelevant to our changes):
```
$ bazel build //<path_to_the_file>:<file_name_without_extension>
```

The path and colon and file name format is the same as the format in the `BUILD` file. An example command:
```
$ bazel build //test/example:utils
```
Do not run this on the `BUILD` file itself, like this will not help: `$ bazel build //test/example:BUILD`
