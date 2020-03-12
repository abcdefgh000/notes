## Test a stand alone function in a python library file

The python library to be tested:
```py
# //folder1/folder2/utils.py

def increment_count_in_dict(dictionary, key):
    dictionary[key] = dictionary.get(key, 0) + 1
```

Bazel BUILD file for the python test file:
```bazel
package(default_visibility = ["//visibility:public"])
load("@python_deps//:requirements.bzl", "requirement")

py_test(
    name = "utils_test",
    srcs = ["utils_test.py"],
    deps = [
        "//folder1/folder2:utils",
        requirement("pytest"),
    ],
)
```

Python unit test file:
```py
import logging
import pytest
import sys
import unittest

from folder1.folder2.utils import (
    increment_count_in_dict,
)

class TestCommonLib(unittest.TestCase):
    def test_increment_count_in_dict_add_new_key_success(self):
        dictionary = {'key1': 2}
        key = 'key2'
        increment_count_in_dict(dictionary, key)
        self.assertEqual(dictionary, {'key1': 2, 'key2': 1})

    def test_increment_count_in_dict_increment_old_key_success(self):
        dictionary = {'key1': 2}
        key = 'key1'
        increment_count_in_dict(dictionary, key)
        self.assertEqual(dictionary, {'key1': 3})


if __name__ == '__main__':
    logging.basicConfig(level=logging.INFO)
    sys.exit(pytest.main([__file__, '--color=yes', '--verbose', '--verbose']))
```
