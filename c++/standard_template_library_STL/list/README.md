# List in C++ Overview
## List和Vector的区别
* 最核心的区别：list是非连续存储的，是 node, pointer, node, pointer... 这样的结构；vector是连续存储的，像array一样。这个区别导致了以下的所有区别
* list可以在头部或中间或尾部 加元素，vector只能在尾部 加元素
* vector可以通过 vector[i] 来访问元素，list不行
