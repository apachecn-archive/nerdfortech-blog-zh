# SQL 简化版—涵盖大多数 SQL 概念的 10 个高级实践问题和解决方案

> 原文：<https://medium.com/nerd-for-tech/sql-simplified-10-advanced-practice-problems-and-solutions-covering-most-sql-concepts-61fb96e7ec5a?source=collection_archive---------1----------------------->

有效地使用 SQL 是任何数据科学家的关键技能，也是面试中最受考验的技能之一。在我们自己提高这一技能的尝试中，我们发现了 Mrinal Gupta **(** [**原文链接于此**](https://towardsdatascience.com/10-problems-to-practice-almost-all-sql-concepts-37545e7c5219) **)** 的一篇非常有用的文章，这篇文章涵盖了 10 个高质量的问题，涉及了面试中测试的大多数 SQL 概念。在这篇文章之后，无论我们尝试了多难的练习题，与那 10 道题相比都相形见绌，令人惊讶的是我们的能力突然提高了！为了从上述文章中获得最大收益，我们必须做 3 个准备步骤:

![](img/726a78bdfe345a5b91a2c8f562fe3b72.png)

来自 [Pexels](https://www.pexels.com/photo/person-in-blue-denim-jeans-using-macbook-3987114/?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels) 的 [Anna Shvets](https://www.pexels.com/@shvetsa?utm_content=attributionCopyText&utm_medium=referral&utm_source=pexels) 的照片

1.  准备实践数据(在最初的文章中，训练数据并不容易获得。我们不得不手工制作 SQL 表并输入数据来尝试我们的测试查询)。
2.  写下我们一步一步的思考过程(有些回答问题乍一看很吓人。花了很长时间才搞清楚他们背后的一步一步的思维过程)。
3.  过时的关键字替换(原始文章中使用的一些 SQL 关键字可能由于版本变化而过时。我们必须找到当前版本的替代品)。

在这篇文章中，我们分享了我们的准备步骤(10 个关键问题),以获得更顺利的学习体验。我们希望您能像我们一样从中受益！

***Q1。给定下面两个表，写一个查询，显示某部门员工平均工资与公司平均工资的比较结果(高/低/相同)。***

首先，让我们创建必要的表。

现在我们已经设置好了表，让我们进行初始连接。

**第一步。**加入

现在，这两个表使用共享的“employee_id”列连接在一起:

**第二步。**现在我们已经连接了两个表，考虑最终表所需的中间列。选择和设计这些。

通过这一步，我们实现了一些目标。通过使用 DATE_FORMAT 关键字，我们允许窗口函数按月进行平均。为了清楚起见，我们给这些陈述起了别名。下面是上述语句的输出。如果这看起来有点不清楚，我们建议快速谷歌一下什么是窗口函数，因为它们会在接下来的问题中大量出现。

第三步。让我们将现有代码转换为子查询&管道，再转换为空白的最终查询。

我们使用 WITH 关键字创建临时表，因为这允许我们查询别名。下面是上面代码的输出:

**第四步。**这样，剩下的就是为我们的最终展示做相关的选择&特征工程。我们将使用 DISTINCT 关键字从结果集中删除重复的列，并使用 CASE WHEN 子句设置我们的条件。

现在我们可以显示某部门员工平均工资与公司平均工资的对比结果(较高/较低/相同)。

***Q2。*** ***编写一个 SQL 查询，报告学生(student_id，student_name)在所有考试中“安静”的情况。“安静”的学生是指至少参加了一次考试，既没有高分也没有低分的学生。***

***方案二:***

首先，让我们创建必要的表。

**第一步。**加入(我们做内部加入，因为对没有考试的孩子不感兴趣)

现在，这些表在 student_id 上被连接起来。

**第二步。**接下来，我们创建所有需要的中间列。

第三步。将以前的查询转换为子查询，以便我们可以访问中间列。

第四步。考虑最终输出&使用相关的【选择】&【过滤】产生。

***Q3。编写一个查询来显示连续行数超过 3 或
且人数超过 100(含)的记录。***

***方案三:***

首先，让我们创建必要的表。

**第一步。**制作一个可识别 100+条纹的列。

**第二步。**选择其他相关的中间列&组成子查询，以便我们可以访问它们。

**步骤 3。**然后，我们制作一个表格，从 t1 开始计算每个条纹的条纹大小。

第四步。我们只过滤掉 3+ streak_size 的条纹。

**第 5 步。**让我们把这个内部连接到 t1，这样我们就得到入围 streak_num 的所有条目。

**第 6 步。**然后根据最终输出的需要进行相关选择。

***Q4。编写一个 SQL 查询来查找有多少用户访问了银行但没有进行任何交易，有多少用户访问了银行并进行一次交易等等。***

首先，让我们创建必要的表。

**第一步。**让我们从按用户 id 查找每天的访问次数开始。

**第二步。**然后我们通过 user_id 计算每天的交易数量。

**步骤 3。让我们做一个左连接，这样我们就可以保持总访问量&一起争论数据。**

**第四步。**我们只选择日期列，num_visits 列&用 0 替换 null num_trans。

**第五步。**让我们将之前的结果转换成一个子查询，然后使用另一个查询 t2 进行适当的分类。我们将不得不使用 t2 的递归子句来正确地使它起作用。

**第 6 步。**适当加入 t1 & t2，就有了我们想要的输出！

***Q5。编写 SQL 查询，为 2019 年 1 月 1 日至 2019 年 12 月 31 日期间的每个连续天数间隔生成 period_state 报告。***

让我们从做桌子开始吧。

第一步。让我们做一个专栏，记录 2019 年的每一次连胜。添加状态 1 只是为了表示成功状态。

第二步。让我们找到每一个连胜的开始&结束日期。

第三步。让我们重复失败状态的过程。

第四步。让我们使用 UNION ALL & order by date 合并 t1 & t2。

第五步。让我们用成功的&失败时替换 1 & 0 的用例，我们得到了我们想要的输出！

***Q6。编写一个 SQL 查询来报告一周中每天每个类别中订购了多少台。***

首先，创建模式和表:

**第一步。用右连接来连接表，因为每一项都没有顺序。**

如果您查看结果表的输入值，我们会看到“T-Shirt”没有值，但是表中的所有商品都在那里。

**第 2.1 步。**让我们创建一个临时表，连接 orders 和 items 表中的必要列，并在一周的第一天，星期一进行测试。

对于输出，我们应该可以看到星期一所有项目的总和。

**第 2.2 步。太好了，现在我们知道这是可行的，让我们获取一周中的所有日子。**

输出:

**第三步。**以上输出有什么问题？我们不希望看到多个 item_categories 出现，所以让我们在 item_category 列上使用 DISTINCT。

现在，我们可以看到在一周的每一天，每个类别中有多少个单位被订购。

***Q7。编写一个 SQL 查询来查找每个部门中工资最高的三名员工。对于上面的表，您的 SQL 查询应该返回下面的行(行的顺序无关紧要)。***

首先让我们创建模式和表:

**第一步。我们需要将两个表连接到各自的 id 上。**

我们有以下结果要处理。我们关心连接表中的哪些数据？

**第二步。嗯，我们需要员工姓名、部门名称和薪水**

**步骤 3。太好了，这样我们就有了最终需要的信息。让我们将现有代码转换成一个子查询，并设置一个只返回前 3 个值的条件。**

在 IT 部门，马克斯的工资最高，兰迪和乔并列第二，威尔的工资第三高。销售部只有两个员工，亨利的工资最高，而萨姆的工资第二高。

***Q8。编写一个 SQL 查询来计算 7 天内(当天+ 6 天前)客户支付金额的移动平均值。***

首先让我们创建我们需要的模式和“客户”表。

**第一步。**让我们首先用 SUM 合计金额，并按 visited_on 分组，以便查看时间窗口

所以现在我们可以看到每天访问的客户数量。

**第二步。我们需要找到滚动平均值。我们想知道这段时间的总量，以及平均量。10 天中的每 7 天相当于每天 4 种可能性。**

**第三步。**为了在这个语句中选择 visited_on，我们需要使我们的第一个查询成为一个临时表，就像这个一样。

现在，我们可以看到客户在 7 天内(当天+ 6 天前)支付的移动平均值和总金额。

***Q9。编写一个查询，找出这些点之间的最短距离，四舍五入到 2 位小数。***

首先让我们创建表格:

第一步。首先让我们使用一个交叉连接，这是一种生成第一个表的每一行与第二个表的每一行的配对组合的连接。

第二步。既然我们已经处理好了交叉连接，让我们找出每个坐标之间的最短距离。

第三步。从输出中我们可以清楚地看到最短距离是 1，但是为了保持简洁，我们将通过按 ASC 排序并限制 1 来完成这个问题，因此只显示最短距离。

上面的查询将输出 1，这是我们所期望的。

***Q10。编写一个 SQL 查询来查找至少连续出现三次的所有数字。***

第一步。由于我们对获取连续的数字感兴趣，以查看哪些数字在一行中出现了 3 次，我们将使用 LAG 函数从前一行获取数据，并引导下一行。

请注意，prev 的第一行为 null，因为应该从中获取值(num)的行并不存在。“下一个”的情况正好相反。

**第二步。**让我们将 SELECT 语句变成子查询，以启用窗口函数条件。

**第三步。**让我们使用 DISTINCT 返回满足我们条件的数字(正如我们看到的，它只是上一个查询中的 1)来完成这个任务。

我们希望您喜欢我们的文章，并对 SQL 更有信心。对于接下来的步骤，我们建议自由设计一些中高难度的数据科学 SQL 面试问题。Stratascratch 在他们的免费专栏中有几个这样的问题(至少在撰写本文的时候)。然后在那之后，考虑你可以应用你新发现的 SQL 技能的项目。再次感谢您参与我们的工作。我们很高兴知道它帮助了别人，比如我们过去的自己！

真诚的，邓肯·安德森。
阿马尔的[LinkedIn](https://www.linkedin.com/in/ammar-masood-khan/)邓肯的 [LinkedIn](https://www.linkedin.com/in/duncan-kg-anderson/)