# Combine multiple unit test files into one Bazel BUILD target

```bazel
cc_test(
    name = "run_log_mining_unit_tests",
    srcs = [
        "//vision/data/tools/mining/miner/pcp:utils_test.cpp",
        "//vision/data/tools/mining/miner/vision:utils_test.cpp",
        "//vision/data/tools/mining/test:miner_configs_test.cpp",
        "//vision/data/tools/mining/util:common_utils_test.cpp",
        "//vision/data/tools/mining/util:filters_test.cpp",
    ],
    deps = [
        "//base/test:utils",
        "//base/test/gtest:gtest_main",
        "//external:gmock",
        "//vision/data/tools/mining/miner/pcp:utils",
        "//vision/data/tools/mining/miner/vision:utils",
        "//vision/data/tools/mining/util:common_utils",
        "//vision/data/tools/mining/util:filters",
    ],
)
```
