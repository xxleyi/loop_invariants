## loop invariants

此仓库用于在 issues 中记录自己使用「循环不变式」视角整理的算法题解。当然，所依据的算法思想是不可缺少的。但我题解中会大概率不说，少说。默认读者已经有所了解。

换言之，此仓库的题解特色是：立足于各种算法思想之上，系统记录、整理使用「循环不变式」的题解方案。

循环不变式，即 loop invariant，是保证循环迭代能够正确解决问题的「关键所在」。

每一个使用循环迭代解决问题的程序，都有一个或显式或隐式的「loop invariant」。

循环迭代能解决问题的核心：**确保每一次子循环中的「loop invariant」**。

时刻记住：**循环不变式虽然是求解问题的关键，但循环不变式本身并不等同于问题答案**。

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

准确的说，「循环不变式」是一个断言，就是 `assert checkWithCondition(someVar)`。但在实际工业化的编程实现中，`checkWithCondition` 的实现往往会有碍性能，相比之下，`checkWithCondition(someVar)` 中的 `someVar` 显得尤为关键。当我们找到「循环不变式」所需要的一个或多个 `someVar`，并在循环开始之前正确初始化，在每一次循环的开始或结束正确更新「循环不变式」相关的变量以确保「循环不变式」始终满足 `checkWithCondition(someVar)` 。在此前提之下，`循环终止 + 「循环不变式」`将使问题的正确解浮出水面。

「循环不变式」的视角下，关键还是寻找相关的变量 `someVar` 以及 `checkWithCondition`。后者在大部分时候都不必直接体现在代码中，但解题者应该了然于胸，并正确的初始化以及更新相关变量，隐式的实现 `checkWithCondition(someVar) == true`。当然，在不影响性能且对暴露报错有良好助益时，完全可以显式的将「循环不变式」的断言放于代码的关键位置。`react` 源码中的 `invariant` 函数就被广泛的用来断言「循环不变式」。

> In [computer science](https://en.wikipedia.org/wiki/Computer_science), a **loop invariant** is a property of a [program](https://en.wikipedia.org/wiki/Computer_program) [loop](https://en.wikipedia.org/wiki/Control_flow#Loops) that is true before (and after) each iteration. It is a [logical assertion](https://en.wikipedia.org/wiki/Logical_assertion), sometimes checked within the code by an [assertion](https://en.wikipedia.org/wiki/Assertion_(software_development)) call. **Knowing its invariant(s) is essential in understanding the effect of a loop**.
> 
> In [formal program verification](https://en.wikipedia.org/wiki/Formal_verification), particularly the [Floyd-Hoare approach](https://en.wikipedia.org/wiki/Hoare_logic), loop invariants are expressed by formal [predicate logic](https://en.wikipedia.org/wiki/Predicate_logic) and used to prove properties of loops and by extension [algorithms](https://en.wikipedia.org/wiki/Algorithm) that employ loops (usually [correctness](https://en.wikipedia.org/wiki/Correctness_(computer_science)) properties). **The loop invariants will be true on entry into a loop and following each iteration, so that on exit from the loop both the loop invariants and the loop termination condition can be guaranteed**.
> 
> From a programming methodology viewpoint, **the loop invariant can be viewed as a more abstract specification of the loop**, which characterizes the deeper purpose of the loop beyond the details of this implementation. A survey article [[1]](https://en.wikipedia.org/wiki/Loop_invariant#cite_note-1) covers fundamental algorithms from many areas of computer science (searching, sorting, optimization, arithmetic etc.), characterizing each of them from the viewpoint of its invariant.
> 
> Because of the similarity of loops and [recursive](https://en.wikipedia.org/wiki/Recursion) programs, proving partial correctness of loops with invariants is very similar to proving correctness of recursive programs via [induction](https://en.wikipedia.org/wiki/Structural_induction). In fact, **the loop invariant is often the same as the inductive hypothesis to be proved for a recursive program equivalent to a given loop**.


引自 [Loop invariant - Wikipedia](https://en.wikipedia.org/wiki/Loop_invariant)

----

说一千道一万，此「循环不变式」的关键还是要「践行不止」，尝试用它去解决算法问题，因为各种原因没能力解决的话，尝试用它去拆解答案。总之，就是在实践中不断感受「循环不变式」在「正确解决算法问题」时发挥的核心作用。


----

还有另外一个**重要**问题：既然站在「循环不变式」视角求解问题，那**动态规划、二分、贪心、回溯**这类算法思想呢？难道不需要了吗？**需要**，当然需要，而且非常重要。

**「算法思想」赋予我们解决实际问题的思路和能力，而「循环不变式」保证我们可以正确无误的解决问题**。

一方面，如果没有解决问题的思路和能力，就根本谈不上正确无误的解决问题，这表明「算法思想」居于核心地位；另一方面，在有了解题思路之后，如果因为细节处理不到位而前功尽弃，是不是更「憋屈」，也更显「无能」？

所以，一个是**有思路解决问题**，一个是**可以正确解决问题**，你觉得哪个重要？当然是缺一不可。
