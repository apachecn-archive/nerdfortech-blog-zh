# SwiftUI 动画序列

> 原文：<https://medium.com/nerd-for-tech/swiftui-animation-sequence-7a0cf364773a?source=collection_archive---------0----------------------->

![](img/e08833669f2fa7469c0be0bf3bab5d85.png)

照片由[杰弗里·布兰德杰斯](https://unsplash.com/@jeffreyfotografie?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/s/photos/sequence?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄

在用 SwiftUI 做了几个动画之后，我意识到在不同的时间或顺序对多个属性和视图使用`withAnimation()`修改器是多么困难。此外，当以一种非常特殊的方式移动视图时,`withAnimation()`可能缺乏清晰性、可扩展性，有时缺乏组织性。这就是为什么我要向你展示我写的`AnimationSequence`框架，它包装了`SwiftUI.Animation`的美丽，并稍微整理了一下我们的代码。让我们深入研究一下。

## 1 —当前情景

这是我通常在谷歌或 YouTube 上寻找如何按顺序制作视图动画的教程时发现的。我会解释这个片段中发生了什么，但首先，让我们来看看，好吗？

当涉及到一系列动画时的第一种方法。

好吧，这是什么？让我们看看这段代码发生了什么，为什么在进行更新或扩展时会如此痛苦和昂贵。代码片段是:

*   跟踪告诉视图何时被动画化的布尔值。
*   对每个视图使用单独的布尔值，我们希望以不同的方式(或在不同的时刻)制作动画。
*   对我们想要制作动画的不同属性使用布尔。
*   在三元运算符中使用布尔运算来设置不同的值，具体取决于它是开还是关。
*   以及基于先前的持续时间延迟动画。

想象一下，现在，我们需要改变任何动画的持续时间，或者我们想要水平移动一些视图而不是垂直移动，或者我们想要给其中一个动画添加延迟，或者只是简单地将动画分组在一起。尽管上面的代码建议的方法对于较小的例子来说还不错，但是在处理更复杂的场景时，它将花费大量的重构成本，并且可能令人头疼。

## 2-添加动画状态

为了让我们的地形准备好，让我们首先添加一个动画状态，在这个状态中，我们跟踪发生在我们的视图上的一切，比如颜色、偏移、位置、边界、比例等等。在这一步中，我们将清理 ContentView，并在为每个特定属性设置哪个值时具有更大的灵活性。在我们继续之前，先声明一点:*这是我解决这个问题的方法，它远非完美或最好的解决方案，它只是我发现使用它更有趣。*

引入 AnimationState 使我们的视图更清晰。

正如我们在上面的片段中看到的，引入`AnimationState`去除了许多气味，使我们的`View`看起来更干净，然而，制作视图动画仍然是一项相当大的工作，跟踪动画持续时间并决定这些动画的顺序，我有信心说这是一项痛苦的任务，考虑到这个动画只包括上下移动三个圆圈，然后改变它们的颜色。

## 3 —让我们最终看到动画序列

在对问题、当前情况进行了大量介绍，并稍微清理了一下舞台之后，让我们来谈谈这篇文章的内容——如何编写一个好的动画序列，而不必太在意延迟、动画顺序或实际动画定义之外的疯狂细节，例如——将此视图向上移动 20 像素，更改此视图的背景颜色，将另一个视图的比例增加到 2，等等。
说我们可以描绘一个不存在的动画序列码(因为我们还没有写出来),它看起来干净又方便——当然，是 Swift 语法中的虚构代码和人类可能的代码。

AnimationSequence 的一个有趣的期望语法。

从这个想象的片段中，我们可以突出几件事:

*   代码看起来比以前更干净，因为我们去掉了不必要的延迟计算。
*   我们为所有连接的动画设置了默认的持续时间`0.5`和缓解时间`.default`。// 1.
*   我们为添加到序列中的每个块赋予特定的动画值。// 2.
*   为了完成我们的序列定义并开始制作动画，我们调用了函数`start()`。

## 4 —编写解决方案

正如您可能已经想到的，我们要求`AnimationSequence`遵循一种构建器模式，在这种模式下，每次我们调用 append 函数时，它都会返回自身。它还应该接收可选值`duration`、`delay`、`easing`和一个`non-optional trailing closure`，以及我们希望稍后在实际的`withAnimation()`块中执行的代码块。让我们看看建筑商。

基本的动画序列生成器。

为了保存所有的动画值，让我给你介绍一下`AnimationConfig`结构，它包含持续时间、延迟、缓动和阻塞/关闭。

存储动画行为的 AnimationConfig 结构。

现在，我们准备写`start()`函数了。基于我们添加的所有动画，它通过调度每个带有时间偏移的动画来创建一个序列，这意味着前一个动画的持续时间是我们拥有的每个动画的当前相同过程的延迟。例如，假设我们有一个初始的`timeOffset=0`，当第一个动画 **A** 到来时，timeOffset 将它的值增加`A.duration + A.delay`，因此在几秒钟后调度下一个动画 B `timeOffset`。

所有动画序列魔法发生的核心功能。

## 5 —将所有东西放在一起

在花了相当多的时间阅读代码之后(如果你没有跳过的话)，我把 AnimationSequence 的整个实现交给你，它与我们到目前为止看到的代码片段没有太大的不同，它只是一段更完整的代码，我添加了一些调试标志，异步任务，一个`onFinish`回调，我把代码分成一些文件，并做了一些总体清理。

[](https://github.com/cristhianleonli/AnimationSequence) [## cristianleonli/动画序列

### SwiftUI 工具，通过隐藏动画调度细节，允许更容易地构建复杂的动画序列…

github.com](https://github.com/cristhianleonli/AnimationSequence) 

非常感谢您的阅读。我希望你喜欢这段代码，如果它对你有用，不要害羞👏或者给我留言，告诉我你有多喜欢这篇文章。下次见。