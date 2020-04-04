## loop invariants

此仓库用于在 issues 中记录自己使用「循环不变量」视角整理的算法题解。

循环不变量，即 loop invariant，是循环迭代能够正确解决问题的「关键所在」。

每一个使用循环迭代解决问题的程序，都有一个或显式或隐式的「loop invariant」。

循环迭代能解决问题的核心：**确保每一次子循环中的「loop invariant」**。

时刻记住：**循环不变量虽然是求解问题的关键，但循环不变量本身并不等同于问题答案**。

很好的读物：[Loop Invariants](https://www.cs.miami.edu/home/burt/learning/Math120.1/Notes/LoopInvar.html)

```
   ...
   // the Loop Invariant must be true here
   while ( TEST CONDITION ) {
      // top of the loop
      ...
      // bottom of the loop
      // the Loop Invariant must be true here
   }
   // Termination + Loop Invariant = Goal
   ...
```

准确的说，「循环不变量」是一个断言，就是 `assert checkWithCondition(someVar)`。但在实际工业化的编程实现中，`checkWithCondition` 的实现往往会有碍性能，相比之下，`checkWithCondition(someVar)` 中的 `someVar` 显得尤为关键。当我们找到「循环不变量」所需要的一个或多个 `someVar`，并在循环开始之前正确初始化，在每一次循环的开始或结束正确更新「循环不变量」相关的变量以确保「循环不变量」始终满足 `checkWithCondition(someVar)` 。在此前提之下，`循环终止 + 「循环不变量」`将使问题的正确解浮出水面。

「循环不变量」的视角下，关键还是寻找相关的变量 `someVar` 以及 `checkWithCondition`。后者在大部分时候都不必直接体现在代码中，但解题者应该了然于胸，并正确的初始化以及更新相关变量，隐式的实现 `checkWithCondition(someVar) == true`。当然，在不影响性能且对暴露报错有良好助益时，完全可以显式的将「循环不变量」的断言放于代码的关键位置。`react` 源码中的 `invariant` 函数就被广泛的用来断言「循环不变量」。

> In [computer science](https://en.wikipedia.org/wiki/Computer_science), a **loop invariant** is a property of a [program](https://en.wikipedia.org/wiki/Computer_program) [loop](https://en.wikipedia.org/wiki/Control_flow#Loops) that is true before (and after) each iteration. It is a [logical assertion](https://en.wikipedia.org/wiki/Logical_assertion), sometimes checked within the code by an [assertion](https://en.wikipedia.org/wiki/Assertion_(software_development)) call. **Knowing its invariant(s) is essential in understanding the effect of a loop.**

引自 [Loop invariant - Wikipedia](https://en.wikipedia.org/wiki/Loop_invariant)

