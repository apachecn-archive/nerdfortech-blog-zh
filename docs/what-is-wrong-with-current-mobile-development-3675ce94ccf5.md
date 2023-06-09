# 现在的移动开发出了什么问题？

> 原文：<https://medium.com/nerd-for-tech/what-is-wrong-with-current-mobile-development-3675ce94ccf5?source=collection_archive---------3----------------------->

## 移动应用中的反应式编程——一次旅行

## 当 web 和混合开发架构蓬勃发展时，由于架构师从头开始创建它们，原生移动开发——Android 和 iOS——坐在板凳上

## 介绍

几年前，当我第一次被介绍到[脸书的 *React.js*](https://reactjs.org/tutorial/tutorial.html#overview) (以及 [*Redux*](https://redux.js.org/tutorials/essentials/part-1-overview-concepts#what-is-redux) )进行 web 开发时，我有点震惊，我承认——这与我习惯的 *Android* 开发毫无关系。
没过多久，我又一次感到震惊，甚至充满了愤怒——为什么在 *JavaScript* 中会有这种*反应式*、结构化、坚实的 *web* 开发库，而 *Android/iOS* 开发经验仍然……嗯……**陈旧**。

> 从这一点开始，我将专门谈论 *Android* ，但我向你保证——iOS 是*不*更好，哦不

![](img/b64f0853aac18f1bc1305cca66da3308.png)

伟大的建筑造就伟大的美。土耳其伊斯坦布尔。

## 愤怒和羞耻

这篇文章是许多文章中的第一篇。它的主要目的是让移动开发人员**清醒过来**——直到不久前还被一个纯粹的实用程序库( [*JQuery*](https://jquery.com/) )所主宰的 web 开发，已经遥遥领先于我们。事实上，Web 开发是如此领先于移动开发，以至于*反应本地的*一个 *JavaScript/TypeScript* 环境，威胁接管*编译的*、*静态类型的*、*平滑的 UX* 移动开发。当前的移动环境太过时了，以至于整个世界都开始牺牲用户体验来开发更便宜、更容易和更快的产品。如果你问我，这是一个非常糟糕的笑话。我既是一名网络开发人员，也是一名移动开发人员，但我仍然对这种趋势感到不快。

> 编辑:在完成这个系列的时候，Android 终于发布了一个稳定版本的 [JetpackCompose](https://developer.android.com/jetpack/compose) ，它基本上模仿了 React 的功能组件。再加上[协同例程](https://kotlinlang.org/docs/coroutines-overview.html)和[科特林-Redux](https://reduxkotlin.org/) ，这是一个强大的“包”，经过一些努力，可以一起用来解决我在这里介绍的许多问题。
> 虽然所有这些都是真的(并且您应该熟悉上面的技术)，但是我们将在本系列中学习的概念现在****甚至**比以往更加相关**——编写移动应用程序的“标准”方式越来越接近提到的概念。****

# ****我们将在这些文章中讨论什么****

****我们将快速概述一种*反应式*方法，特别是一种 *React-Redux* 式的移动开发方法。
我们将从*为什么*开始，继续*什么*并以一点点*如何*结束。接下来的章节将在技术上更深入，帮助我们形成一个完整的*[](https://proandroiddev.com/getting-started-with-mvi-architecture-on-android-b2c280b7023)**[*通量*](/@grover.vinayak0611/what-is-flux-architecture-why-facebook-used-it-and-the-comparison-with-mvc-architecture-49c01ed5d2e1) 架构。这将是一次漫长而有趣的旅行🚂。
这些文章是为每一个(移动、网络)开发者准备的，并且将展示一个完整的工作架构。它目前只适用于 *Android* ，但是有一个纯粹的 *Kotlin* 内核，并且打算/可以为 [*Kotlin 多平台*](https://blog.jetbrains.com/kotlin/2020/08/kotlin-multiplatform-mobile-goes-alpha/#:~:text=Kotlin%20Multiplatform%20Mobile%20(KMM)%20is,both%20iOS%20and%20Android%20applications.&text=It%20includes%20the%20new%20KMM,code%20in%20the%20same%20IDE.) *(* 如果有人想加入我的旅程，请随时联系我)。
所以……来了*为什么*、*什么*和*如何。********

# ******为什么(目前的方法还不够吗)？******

******当前创建移动应用程序的*风格*的问题就在于此——这是一种*风格* —远不止是一种架构。它没有结构。它只是一堆 UI 对象、实用程序、服务和库，它们甚至没有一个严格、统一的协议来相互通信。******

******我将列出我在 **Android** 开发中遇到的 **3** **问题**(在众多问题中)，并用一些代码来解释我自己:
一个非常简单的**应用**、的例子，由 **1 个屏幕**和 **1 个文本**组成，显示手机的当前状态**AirplaneMode**—【T23 你觉得会很整洁吗？简单？准备哭吧。******

## ******UI 结构不清晰******

******第一个**第一个**第三个**问题**我和*安卓*开发的问题，就是缺乏清晰的 UI 结构。直到今天，[开发者仍然不理解](https://www.reddit.com/r/androiddev/comments/5t3s5r/help_me_understand_when_to_use_fragments_vs/)*活动、*片段和*视图*之间的“正确”不同用法——原因。见鬼，我甚至不确定 *Android* 的开发者是否知道😅；这只是几十年代码进化的结果，真的——是我们坐下来从头开始重新思考整个事情的时候了。******

******所以让我们从我们的 **1 屏幕 1 文本 AirplaneMode** 例子开始。我们应该用什么？一个*视图*？嗯……但是我们需要监听 *AirplaneMode* 的状态变化——这对于一个*视图*来说太复杂了，难以管理。一个*片段*然后呢？嗯……但是它[甚至没有 *registerReceiver* 方法](https://stackoverflow.com/questions/32379106/how-to-registerreceiver-in-fragment/32379299)，它不得不使用它的*活动*来实现。
好吧！所以我们会用一个*活动*！让我们准备好监听 *AirplaneMode* 的变化:******

******使用 AirplaneMode 广播接收器的活动******

******很好，现在我们有了一个能够监听 *AirplaneMode* 状态变化的*活动*。但是一个*活动*基本上是一个屏幕，所以如果我们希望我们应用程序中的另一个屏幕具有相同的逻辑，我们必须为此创建一些基类*和*。很快，我们的基地*班*就会做*很多*的事情，对吧？而且……我们已经打破了一个非常重要的原则——[*关注点分离*](https://en.wikipedia.org/wiki/Separation_of_concerns)；我们的应用程序中甚至还没有文本😖。
你可以和我争论，说你可以做得更好——但这是安卓的“标准”方法，尽管听起来很可悲——除非你是一名高级开发人员，否则你会这么做。******

> ******顺便说一下，如果你真的想知道为什么有 3 个 UI 组件(但我建议*不再重要了)，*视图*是实际的 UI 构建块，*活动*是*上下文*持有者/供应商，它们[直接与 *Android* *OS* 的*进程*](https://developer.android.com/guide/components/activities/process-lifecycle) *和片段*相关🙄这太过分了。
> 为什么*活动*在实践中被用来直接呈现和处理 UI 令我困惑，但我猜这可能与官方教程用来展示*活动*中 UI 相关代码的事实有关，开发人员把那些例子看得太字面了。*******

## ******过于复杂的生命周期******

******我在 *Android* 开发中遇到的**第二个问题**是其 UI 组件过于复杂的生命周期；事实上他们每个人都有不同的想法。有许多生命周期回调不一定是坏事，但是当不绝对清楚做什么和什么时候做时，它很快就会变得一团糟。你们都明白(并且记得)在*活动*的*onStart/on stop*vs .*on resume/on pause*vs .*on create/on destroy*中*注册/注销* a *BroadcastReceiver* 的区别吗？那么处理与一个*视图*的大小相关的动画呢——你花了多长时间才明白一个*视图*的 *onFinishInflate* 回调是在视图被测量之前*被调用的，所以在它被调用的时候，*视图*的大小为 0？*******

*****回到我们的例子——这次是使用*视图*和适当的生命周期处理。记住，如果我们使用*视图*或*片段*，这个例子看起来会*完全不同，因为它们有不同的生命周期！
我们要做的是添加 UI 相关代码(`TextView`)并将`super` 调用放入我们的生命周期回调中——为什么？因为这就是安卓系统的工作方式😓。
请注意，我们在 **3** 不同的地方更新了*文本*！******

*****用文本视图显示手机的 AirplaneMode 状态的活动*****

*****很好，现在我们有了 **1 屏幕**和 **1 文本**，显示手机的**airplanemode**的状态，使用 **3 UI 调用**和 **4 回调**(生命周期-方法)。我们完成了吗？！？！嗯……不！*****

## *****复数数据流*****

*****我遇到的第三个**问题**是，应用程序中的数据如何流动。超级复杂。你需要*包、intent*(它也可以保存*包*)、*广播接收器*和*自定义设置器。*有*很多*地方你要*设置*它们，*注册*它们，*回调*检索它们什么的。而且都有不同的名称，甚至不同的做法。
例如，一个*视图*是最基本的 UI 组件，但是它没有内置的方法来为它提供*数据*。有一个完整的(官方)库( [*数据绑定*](https://developer.android.com/topic/libraries/data-binding) )就是为了这个。它需要定制的 xml 代码和大量的开销。
让我再说一遍来强调: *Android* 发布了一个库，只是为了将*数据*传递给它最基本的 UI 组件😖。*****

*****回到我们的例子，我们将添加与`savedInstanceState` 相关的代码，这是一个`Bundle`，一个*活动*使用它来从*状态*中恢复丢失，例如屏幕旋转(是的，屏幕旋转实际上重启了整个*活动*)和内存丢失(当*活动*回到前台时)。*****

*****显示 AirplaneMode 状态的活动，具有适当的生命周期和状态管理*****

*****现在我们终于有了一个完整的 **1 屏幕 1 文本**和 **AirplaneMode** 。
是的，这是在 *Android* 中编写 UI 代码的正确、标准的方式。
是的，通常情况下，你会把*广播接收器*放在一个基类*中*并省略*保存实例*的东西，只依靠*许多*你已经设置了 UI 的地方来克服这些情况。但这仍然是正确的方式。悲伤的方式。*****

*****你喜欢吗？你哭了吗？我知道我做到了😤。
这是人们能想象到的最简单的*屏幕*——从这里开始只会变得更加复杂；Android 团队并没有修复这个有根本问题的架构，而是发布了越来越多的工具和库，每一个都帮助(修补)了上面代码的某个特定区域/方面。如今，你需要成为一名高级开发人员，才能创建一个简单的 Android 应用程序，拥有所有‘现代’的工具和库，没有错误。难怪世界正在向本土反应转变。糟糕。*****

# *****摘要*****

*****嗯，我希望我成功地叫醒了你，或者至少进入了你的梦里😵。这仅仅是个开始。现在我们必须明白对此能做些什么。什么方法可以更好地为我们服务，更重要的是，更好地为应用程序的用户服务——因为这毕竟是最重要的。*****

*****所以…这就是*的原因。* 感谢您的阅读，欢迎在下方留下您的评论！现在让我们接着来看**🙃*。********