## loop_invariants

此仓库用于在 issues 中记录自己使用「循环不变量」视角整理的算法题解。

循环不变量，即 loop invariant，是循环迭代能够正确解决问题的「关键所在」。

每一个使用循环迭代解决问题的程序，都有一个或显式或隐式的「loop invariant」。

循环迭代能解决问题的核心：保证每一次子循环中的「loop invariant」得到正确、恰当也稳妥的维护。

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

严格来说，「循环不变量」是一个断言，就是 `assert checkWithCondition(someVar)`。但在实际工业化的编程时，`checkWithCondition` 的实现往往会有碍性能，在我个人的经验里，`checkWithCondition(someVar)` 中的 `someVar` 更为关键。当我们找到循环所需要的一个或多个 `someVar`，并精准的初始化，稳妥的在每一次循环的开始或结束都正确更新，确保循环之前、之中、之后都始终满足 `checkWithCondition(someVar)` 时，基本就大功告成。

因此，「循环不变量」在我这里，侧重于 `someVar` 寻找，并仔细维护，使其隐式的满足 `checkWithCondition(someVar)`。

> In [computer science](https://en.wikipedia.org/wiki/Computer_science), a **loop invariant** is a property of a [program](https://en.wikipedia.org/wiki/Computer_program) [loop](https://en.wikipedia.org/wiki/Control_flow#Loops) that is true before (and after) each iteration. It is a [logical assertion](https://en.wikipedia.org/wiki/Logical_assertion), sometimes checked within the code by an [assertion](https://en.wikipedia.org/wiki/Assertion_(software_development)) ，call. Knowing its invariant(s) is essential in understanding the effect of a loop.

引自 [Loop invariant - Wikipedia](https://en.wikipedia.org/wiki/Loop_invariant)

