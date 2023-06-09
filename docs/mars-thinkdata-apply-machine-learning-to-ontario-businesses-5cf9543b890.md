# MaRS & ThinkData 将机器学习应用于安大略企业

> 原文：<https://medium.com/nerd-for-tech/mars-thinkdata-apply-machine-learning-to-ontario-businesses-5cf9543b890?source=collection_archive---------16----------------------->

随着我们在数据时代的前进，寻找数据的公司正在寻找数据。这是好事。使用新的数据源具有不可否认的价值，但是在提取该价值之前，来自任何组织内部和外部的各种数据集需要能够在整个数据目录中以标准的方式引用给定的实体，例如特定的公司。

这似乎是一个小障碍；大多数人看到“GM”和“通用汽车”就知道它们是相关的。但是，为此创建一个可扩展的、编程式的解决方案要复杂得多，需要考虑到每一种变化和排列。

ThinkData Works 的 DataLabs 团队的首席数据科学家 Hoyoung Jang 表示:“教机器理解不同数据集中的实体是如何表示的以及它们之间的关系是一项极具挑战性的工作。”ThinkData Works 是一家专门研究数据管理技术的公司，特别是那些处理多样性的技术。

链接记录的问题不是任何一家公司独有的。尤其是在使用替代和外部数据时，信息记录的方式总是有差异；每个组织、部门甚至个人都有不同的做事方式。孤立的数据、人为错误和多个数据源只是将“ACME Corporation”这样的地址记录为 Acme 公司、Acme 公司、Acme 加拿大、AMCE 多伦多等的几种方式。这种不一致通常存在于一个数据集内，并且几乎肯定存在于两个数据集之间，即使源是相同的。为此，数据团队需要[实体解析](https://blog.thinkdataworks.com/entity-resolution-for-master-data-management)。

![](img/0f564c062c4e77ca786522c4ae5bf3e5.png)

这些表情符号都来自同一个母表情符号，但表达方式却如此不同。

## 这是数据多样性的问题

[MaRS Data Catalyst](https://www.marsdd.com/service/data-catalyst/) 的团队着手创建一个关于初创企业和扩大规模的全景图；为了做到这一点，他们需要将主要来源的数据整合在一起，如创新经济生态系统中的数据合作伙伴、火星收集的调查、像 [Crunchbase](https://blog.thinkdataworks.com/press/thinkdata-announces-data-partnership-with-crunchbase) 这样的数据提供商，以及任何可用的第三方数据。从本质上来说，某家公司的每一项数据都必须与一个唯一的标识符相关联，以便能够跟踪特定公司随着时间的变化。

尤其是对于初创公司，可能会发生很多变化:地址、公司名称、产品支点，所有这些都需要随着时间的推移并跨多个来源进行跟踪。很乱，不是处理‘大数据’的问题，是数据种类的问题。

![](img/1e5623df6dec14b6fbc310fe6260d0d1.png)

“围绕实体匹配，我们尝试了一些相当标准的 Python 库。我们还会把现有的名字列表简化，然后比较这些简化的版本。”MaRS Data Catalyst 的高级数据经理 Joseph Lalonde 反思了他们过去的手动流程。他们的解决方案都跟不上他们希望流入解决方案的数据量，这阻碍了团队的发展。

玛氏团队“会制定规则来消除公司间的歧义，但不可避免地，有些会被遗漏。ThinkData Works 的 DataLabs 团队的首席软件开发人员 Zeshan Mahmood 指出:“这些不准确的地方会引起注意，他们不得不重新编写一个新的规则，并重新开始。”。“即使他们有很棒的团队，这也非常耗时。”

## 贯穿不同数据的共同线索

ThinkData Works 的实体解析工具包 [er](https://www.thinkdataworks.com/products/entity-resolution) ，是一个机器智能记录链接解决方案，可以随数据伸缩。ThinkData 是一家总部位于多伦多的公司，也是玛氏合作伙伴网络的一部分，也是一家[玛氏 IAF](http://www.marsiaf.com/) 投资组合公司——他们的数据管理解决方案是在 Data Catalyst 将点连接起来的关键。

ThinkData 的 Jang 指出了这个难题中最复杂的一块。“大多数实体解析解决方案缺乏伸缩能力，而这在处理大数据时是非常关键的。”创建实体解析问题的可伸缩解决方案是 ThinkData 创建 er 的主要目标。

“我们首先尝试对数据中存在的实体类型进行分类。好处有三:分辨率更一致，因为它给定了上下文；分类有助于提炼、丰富和标准化每个实体类型的信息；它提供了跨数据集的有意义的实体关系。”

![](img/954d65d480cb5514b8322ef36808b803.png)

对于 Data Catalyst 团队来说，结果是更快、更可靠的结果，不会因为新数据而变慢，所有这些都由专门的数据科学家和工程师团队完全管理和支持。

“ThinkData 的数据工程师解决这个问题为我们节省了大量时间，而且就复杂程度而言，它肯定更复杂，”Lalonde 说。“随着时间的推移，我们看到 ThinkData Works 提供了明显的改进。还有更多的反馈机制——Python 库永远不会有这种响应能力和客户服务水平。”

## 聪明地工作，而不是努力

该团队已经能够在不对其工作流程造成重大中断的情况下实施 er。Lalonde 指出，“因为它是程序化的，所以我们可以将它整合到我们其余的数据流中。它不是某种工具，你必须跳进去跳出来才能让它工作，它整合起来没有摩擦。”

使用来自完全不同来源的数据集，Data Catalyst 团队现在可以跨数十万行可靠地将实体联系在一起。随着实体匹配部分的解决，他们能够将时间集中在使用数据上，而不是争论它。

“感觉它会变得越来越好，似乎我们扔给它的公司数量并不重要。”好处是立竿见影的，回报只会越来越大。

"我们用得越多，它就能为我们节省越多的时间."

**关于火星数据催化剂**
火星数据催化剂将分析和严谨的研究相结合，以促进社会经济影响。他们通过报告、见解和创新产品帮助企业、政府机构和学术界共享和使用数据。从培养数据透明度到让公民为未来的工作做好准备，MaRS Data Catalyst 相信，获取高价值信息可以让安大略成为一个更好的生活、工作和学习场所。

**关于 ThinkData Works**
发现、管理和利用推动企业发展的数据。ThinkData Works 提供灵活的企业数据目录，旨在确保数据生命周期每个阶段的数据质量和法规合规性。要了解更多信息，请访问 [ThinkData Works](https://www.thinkdataworks.com/) 并通过 [Twitter](https://twitter.com/thinkdataworks) 和 [LinkedIn](https://www.linkedin.com/company/thinkdata-works/) 与我们联系。

*原载于*[*https://blog.thinkdataworks.com*](https://blog.thinkdataworks.com/mars-thinkdata-apply-machine-learning-to-ontario-businesses)*。*