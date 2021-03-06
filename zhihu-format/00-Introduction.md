从零开始的简单函数式C++（〇）前言&目录
========================================

## 目录

为了方便整理和查找，我把整个系列的目录和每一篇里涉及到的主要内容放在这里，供大家使用。

* [从零开始的简单函数式C++（〇）前言](https://zhuanlan.zhihu.com/p/44772722)
* [从零开始的简单函数式C++（一）pair](https://zhuanlan.zhihu.com/p/44774845)，主要涉及内容：pair
* [从零开始的简单函数式C++（二）tuple](https://zhuanlan.zhihu.com/p/44774845)，主要涉及内容：tuple，tuple 的展开，tuple 的逐项应用，tuple 版本的 head，tail，init，last
* [从零开始的简单函数式C++（三）vector](https://zhuanlan.zhihu.com/p/45208774)，主要涉及内容：vector
* [从零开始的简单函数式C++（四）lambda 函数](https://zhuanlan.zhihu.com/p/45430715)，主要涉及内容：lambda 函数，Y-组合子（不动点组合子）
* [从零开始的简单函数式C++（五）函数式编程工具箱](https://zhuanlan.zhihu.com/p/45750387)，主要涉及内容：map（for_each，transform），filter（copy_if，remove_if），reduce（accumulate）
* [从零开始的简单函数式C++（六）更多的函数](https://zhuanlan.zhihu.com/p/46737243)，主要涉及内容：函数的部分应用，tuple_apply，函数类型识别 function_traits

## 写在最前

在阅读这个简单的教程之前，请务必记住这样一句话：

> 源码之前，了无秘密。

这句话出自侯捷先生所著《STL源码剖析》的扉页。虽然我们现在总是宣传，要多用库函数，要熟悉官方所给的框架，要用官方的风格去思考去写代码，但是又有多少人真正地知道每一个函数的作用，又有多少人了解了一个框架他背后设计的故事，又有多少人真正的想过这门编程语言是为了解决什么问题而这样设计的。

因为，源码之前，了无秘密。

## 讲什么

如标题所示，这个教程主要是讲解如何用现代的 C++ 以及所配套的 STL 来“函数式”地编程。具体而言，本教程会讲解以下内容：

* STL 中的主要工具：元组 `pair`，`tuple`，向量 `vector`
* C++11 引入的 lambda 函数
* 假装在函数式编程的三板斧：`filter`，`map`，`reduce`
* 是否需要引入 lazy 求值
* 简单的函数操作
* 递归与状态变换
* 基础的模板元编程（编译时计算）

当然，如果真的执着于函数式编程的话，C++ 是显然不能满足绝大多数人的要求的，比如不能轻松地进行模式匹配，也没有较为简单地惰性求值。这时候不如推荐一些纯粹的函数式语言例如 Haskell 或者 scheme。相反，如果只是单纯的想改变自己粗糙的平凡的代码，想变得高大上或者觉得这样写很屌很有意思，请出门左转先治好自己的中二病再说。

## 注意

这份教程是一份典型的实用主义教程，很大程度上我只会简单的把事实摆出来，其背后的原理需要自己去想去理解。本教程从设计上来讲总共有 7 节，每节阅读约消耗 30-45 分钟，但是能否随学随用很大程度上依赖阅读之后的有效代码量的多少了。需要额外注意的是，由于讲解的内容涉及到了大量的 C++11 及其更新版本的性质，所以请使用至少 GCC 4.8 或不低于该编译器的同等水平其他编译器。

另外，为什么选择 C++ 而不是现在更流行的 python 呢？这里有我自己的一点考虑，个人认为如果平时 python 用的很多，或者任何一门语言用的很多，自然而言地对这门语言中那些从函数式借鉴来的精华耳濡目染，深有体会，更无需他人指点，只需要借助一本 cppreference 就能轻松地将自己的代码转换成现代风格的 C++。毕竟这世上的编程语言五花八门，而实实在在的编程思想早已深入骨髓。

说这么多，让我们现在就，从零开始，去写简单易懂的函数式的 C++。

## 其他需要说明的

这个东西还挂在了 github 上，欢迎大家加入催更大军 emmm