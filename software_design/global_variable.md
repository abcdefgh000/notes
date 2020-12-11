# Global Variable

## Global Flag
一个 Global Flag 其实就是一层额外的 if-else。不要感觉它比 if-else 更高端或者更干净。

理论上，每加入一个新的 global flag，**所有和这个flag相关的code的test case 的个数都要至少翻倍**（如果这个flag是bool flag的话 就要翻倍，如果是其它的有超过2个可能值的数据类型，这个test case的理论增加倍数可能会更高）。
* 只有一个和现有code都“正交”的flag才不会增加 test cases 的个数，但这样的flag是不太可能的
* 显然没有程序员会这么淳朴，真的去写翻倍的 test cases。所以尽量别加 global flag

真的不得不定义 global flag 的话：
* Global Flag 的含义必须 明确，唯一，一致 (Consistent)。它的名称可以比较长，宁愿啰嗦点，也要把它的含义说得细致，限制得死
  * 不能让不同的程序员看到这同一个flag 能想到不同的作用
  * 必须绝对杜绝一个flag 随着时间的增加，随着用它的程序员的增加，在不同的地方起不同的作用，稍微有点区别的作用也不行（而且这可能比完全不同的作用更危险）
  * **总结：一个flag的含义的蔓延会导致灾难性后果，任何对这个flag的新的使用，或者对它的任何一个老的使用的修改，都可能遭遇不可控的无数bug；对这个flag写任何 unit test 也会遭到无尽挫折**
* 一个 flag 被用到的code场合，也最好是同一类场合。这也是从另一个方面 对上述风险进行一种预防



