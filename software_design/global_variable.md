# Global Variable

## Global Flag
一个 Global Flag 其实就是一层额外的 if-else。不要感觉它比 if-else 更高端或者更干净。每加入一个新的 flag，理论上，所有和这个flag相关的code的test case 的个数 都要翻倍（如果这个flag是bool flag的话，如果是其）

Global Flag 的含义必须 明确，唯一，一致 (Consistent)。它的名称可以比较长，宁愿啰嗦点，也要把它的含义说得细致，限制得死。

一个 Global Flag 被用到的地方最好是同一类地方，起到的作用必须是同一类作用
* 不能让不同的程序员看到这同一个flag想到不同的作用。必须绝对杜绝一个flag在不同的地方起不同的作用，稍微有点区别的作用也不行，而且这可能比完全不同的作用更危险

