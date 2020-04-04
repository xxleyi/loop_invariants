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
