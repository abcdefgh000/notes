## Build a single file

To `bazel build` only one file/target inside the `BUILD` file (This is super useful when debugging! So we don't have to build a log of stuff unrelevant to our changes):

### Run bazel build from the root folder
```
$ bazel build //folder_tier1/folder_tier2:<file_name_without_extension>
```
The path and colon and file name format is the same as the format in the `BUILD` file. An example command:

Do not run this on the `BUILD` file itself, like this will not help: `$ bazel build //folder_tier1/folder_tier2:BUILD`

### Run bazel build directly at the folder which the file is at
We can also go to the folder directly and do the bazel build inside that folder like this, then we do not need `//` or `:`:
```
$ cd folder_tier1
$ cd folder_tier2
$ bazel build ./utils
```

### Run bazel build in a parent folder
Attention: must use `/` instead of `:` in this case:
```
$ cd folder_tier1
$ bazel build ./folder_tier2/utils
```

## Build all the files in a folder
```
$ bazel build //folder_tier1/...
```
or like
```
$ bazel build //folder_tier1/folder_tier2/...
```

## Sometimes a bazel build passed on local machine, but fails on the CI machine, then try the following
On CI Clang Fastbuild, it has the `--config=clang` and `compilcation_mode=fastbuild`, so we can do this on local machine to get the same CI result as the CI machine:
```
$ bazel build --config=clang --compilcation_mode=fastbuild //folder_tier1/...
```

The same for CI GPU Fastbuild:
```
$ bazel build --config=cuda --compilcation_mode=fastbuild //folder_tier1/...
```
