# Combine multiple unit test files into one Bazel BUILD target

```bazel
cc_test(
    name = "run_all_unit_tests",
    srcs = [
        "//folder1/folder11:xxx_test.cpp",
        "//folder1/folder12:yyyyyyyy_test.cpp",
        "//folder2/folder21:folder211:zzzz_test.cpp",
    ],
    deps = [  # <====== here we put the combination of all the deps of all the above unit test files
        "...",
        "............",
        ".......",
        ...
    ],
)
```
then we only need to run this one line command to run all the above unit test files:
```
bazel run //folderA/folderB:run_all_unit_tests
```
