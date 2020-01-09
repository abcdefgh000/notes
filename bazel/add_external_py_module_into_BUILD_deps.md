To add an external python module (like `xgboost`) into the `deps` section in the `BUILD` file:
* Add a line on the top of the `BUILD` file:
  ```
  load("@python_deps//:requirements.bzl", "requirement")
  ```
* Add this into the `deps` section:
  ```
  deps = [
      requirement("xgboost"),
      ...
  ]
  ```
