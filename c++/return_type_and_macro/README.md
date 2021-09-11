# 关于 Return 的一些原则

* caller 应该 主要靠 return status 来了解出错的 类型，而不是靠 error message 的具体内容。error message 只是 对于 status 的进一步的细化说明

* test 一般来说不要 depend on error message 的具体内容/措辞
