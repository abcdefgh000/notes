# C++ 里什么时候会发生 copy

## Overview
这是一个特别重要，也不容易的问题。大体来说，如果用到了 `=` 即 assignment operator，则一般是发生了copy，只是说 也许 copy的是value，也许copy的是 pointer 即 address，copy address会便宜很多，但也是一种copy。例外有：
* 一个 reference = 一个东西的时候，这里的 `=` 并没有copy任何东西（包括也没有copy address），因为 reference只是一个 alias

