# 什么是机器学习模型解释？

> 原文：<https://medium.com/nerd-for-tech/what-is-machine-learning-model-interpretation-9556c3c247e6?source=collection_archive---------0----------------------->

如今，随着机器学习模型在行业中的使用越来越多，找到最合适的模型并不是一件容易的事情。准确度、精确度或召回率可能不代表模型在现实世界中的有用性。因此，为了找到最合适的模型，一个新的热门话题是机器学习模型的解释。

![](img/67f360d3c2520f873085694beff4741a.png)

保持冷静，现在你可以相信你的 ML 模型了！(unsplach.com)

机器学习模型的领域解释是一个新的热门话题，它讨论模型如何工作以及如何表示输出。它依赖于模型的可信度这一事实。换句话说，这个话题回答了问题*“为什么我需要信任这个模型？”*和*“如何预测模型的产量？”*。

在本文中，我们将解释该领域的主要概念，以及如何超越旧的度量标准准确性、精确度或召回率。在我们开始之前，我需要提一下，本文的参考文献是和熊[1]写的一篇论文。

# **解释算法**

解释算法用于揭示模型如何做出决策。它突出显示数据，以显示它对特殊输出的有效性。例如，在狼图片中，雪如何有效地将图像分类为狼，而不是狗。

# **模型可解释性**

模型解释指的是“作为一个人，如何理解一个模型做决策？”以及“如何预测模型的结果？”。很明显，为了找到模型的可解释性，我们需要使用解释算法。使用解释方法有助于我们更好地理解模型是如何工作的，以及它是如何输出结果的。

# **值得信赖的**

这里的可信度意味着我们可以应用于模型解释的信任程度。或者换句话说，可以说，可信赖性显示了模型解释结果是如何正确的并且在一般情况下被应用。

# **此消彼长**

一方面，完全可信的模型通常是不能解决现实世界问题的简单模型，但是另一方面，可信模型的输出是已知的，并且没有不可预测的输出。由于这个事实，使用更可信的模型或使用具有更好性能的模型总是一种折衷。

# **描述解释算法的属性**

有各种属性来描述解释算法的不同视图。每一个都用来突出解释算法的一个方面。它们分类如下

*   *人类可以理解的:*如信息量、合理性、满意度
*   *可信度:*可靠性，健壮性、Trus、保真度和透明性
*   *基本原理:*偶然性、透明性
*   *模型验证:*公平性、可转移性、隐私性
*   等等

名为“底层基本原理”的类别回答了“模型如何被参数化以生成输出？”。正如你所看到的，一些属性在不止一个类别中，这意味着它可以突出不止一个类别的解释算法。

# **不同类别的解释算法**

有不同类型的解释算法用于不同的领域。有些可能用于不止一个领域，有些可能只适用于一个领域。

*   有些方法将模型视为黑箱，它只是将输出与不同的输入进行比较。
*   其他一些人发现每个模型的潜在过程，即他们试图在分类/预测问题中跟踪模型的参数，如决策树。
*   最后一类试图为一个模型找到一个封闭形式的解决方案，例如制定一个模型的过程(SVM 或线性回归模型)。

这里我们可以提到一些解释算法的类别。当然，还有更多不同的算法分类。如果你想进一步了解这些方法，你可以阅读参考论文。

感谢你阅读这篇文章，祝你有美好的一天！

# 参考

[1]李，x，熊，h，李，x，吴，x，张，x，刘，边，j，窦，2022 . [*可解释深度学习:解释、可解释、可信赖、超越*](https://doi.org/10.48550/arXiv.2103.10689) 。