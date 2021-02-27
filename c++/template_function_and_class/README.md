# Template

Template 的 code 本身是 **“不存在”** 的。之所以这么说，是因为 template code 是在 compile time 的时候，如果 code call 了 这个 template function 或者 template class，compiler 才会根据 这个 template 的定义 来 **生成** 相应的 template function code 或者 template class code。如果这个 template 根本就没有被call，则和这个template 有关的任何东西都不会出现在 compiled code 里，甚至如果 定义这个 template 的 code 里有任何 syntax error，compiler 都不会发现，compile 都可以成功完成。
