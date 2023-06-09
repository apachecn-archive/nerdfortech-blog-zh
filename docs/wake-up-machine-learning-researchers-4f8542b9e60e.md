# 唤醒机器学习研究者！

> 原文：<https://medium.com/nerd-for-tech/wake-up-machine-learning-researchers-4f8542b9e60e?source=collection_archive---------17----------------------->

![](img/642ce849182ca297d332833353c9a5d1.png)

来源:首席财务官

> “在新冠肺炎·疫情袭击事件发生后，许多研究表明使用机器学习模型从医学图像中诊断新冠肺炎。但是，剑桥大学研究人员最近的一项系统综述表明，这种方法“缺陷太多”，而且“不适合”用于患者！”

如果你来自**数据科学/ ML(机器学习)**背景，你一定经常听说 ML 具有检测“某某”疾病的**潜力**。还发表了许多研究论文，其中在医学数据有限的情况下，与耗时或需要专家的传统方法相比，ML 模型在疾病检测中显示出**更高的准确性**。

类似地，在**新冠肺炎疫情**之后，由于缺乏对新型冠状病毒的完美测试，研究人员开始试验 ML 的**功效，以从现有的医学数据中检测新冠肺炎，如胸片(CXR)和计算机断层扫描(ct)图像。**

> **与金标准 RT-PCR 相比，ML 模型取得了令人鼓舞的结果，但也有少数模型承诺了更好的诊断准确性！**

这些结果看起来很有希望，直到最近对所有这些研究论文进行了系统的审查，时间是从 2020 年 1 月 1 日到 2020 年 10 月 3 日。由剑桥大学领导的一组研究人员开始详细分析所有这些研究，这些方法面临的挑战，以及避免缺陷的补救措施！

根据最初的搜索标准和质量筛选，超过 **r 2212 篇论文被视为**，只有 **62 篇论文通过流程保留**，其中 **37 篇是深度学习论文，23 篇是传统机器学习论文，2 篇是混合论文！**

但是为什么数字这么低呢？**才 62？**

大部分深度学习论文都没有提到以下几件事:

1.  **最终型号是怎么选出来的？**
2.  **图像的预处理方法**
3.  **训练方法**细节(优化器、损失函数、学习率)

而且，大部分机器学习论文都没有涵盖以下内容:

1.  **特征缩减**技术
2.  **模型验证**技术

> **这基本上显示了全球在 ML 领域(尤其是医疗保健领域)所做研究的质量，其中大多数研究人员对发表研究论文更感兴趣，很少有人关注所用数据模型的实时实施和粒度&！**

正如剑桥大学应用数学和理论物理系的迈克尔·罗伯茨博士所说，

> “然而，任何机器学习算法都取决于它接受训练的数据”

那么，当谈到实时使用时，模型质量差的原因是什么呢？

*   >数据质量差
*   > ML 方法质量差
*   >研究设计的可重复性差且存在偏差

很少有研究人员使用儿童的**图像作为他们的“非新冠肺炎”样本**！然而，与成人相比，儿童更不容易感染这种疾病，这在训练数据中增加了一个**高偏差！**

这项由剑桥研究人员进行的系统调查还断言，**如果人们基于一家医院建立 ML 模型，它甚至可能不适用于最近城镇的医院数据！**

尽管 ML 模型存在许多缺陷，研究人员仍然对 ML 的潜力持积极态度，但它需要关键的修改和来自医疗行业的外部验证！

**寓意:在你研究之前重新研究，不要急于发表你的“最先进的”模型！**

参考资料:[https://www.nature.com/articles/s42256-021-00307-0](https://www.nature.com/articles/s42256-021-00307-0)