# 遇见生态区 PHP 的企业级框架

> 原文：<https://medium.com/nerd-for-tech/meet-ecotone-enterprise-ready-framework-for-php-bc40f4c5c1d3?source=collection_archive---------10----------------------->

![](img/d36502ff4c225d638228f9f51bda2950.png)

我听说过很多次，PHP 不允许企业级解决方案。我是 PHP 开发人员，我曾经相信这是真的。

让我们想象一下想要以稳定可靠的方式运行其系统的团队。
以电子商务业务为例，它允许用户销售和购买产品。

# 见见“欧米茄”队

团队“ ***【欧米茄】*** ”已经开始用“*注册服务*”实现，该注册服务填充用户模型，存储它并发送带有激活链接“欢迎消息”邮件。然后，他们创建了产品模型，其中存储了新创建产品，供买家选择。最后，他们创建了一个订单模型，用于存储购买产品的信息。
无论何时下单，都有对友好团队开发的两个外部应用程序的 HTTP API 调用。第一个是给买家开发票的计费平台，第二个是知道产品运送到哪里的运送平台。

![](img/4d266a547375ece5191163e1305cab44.png)

# “我们来制作一个状态，已发送/未发送”

产品发布后的第二天，“欧米茄”团队开始收到来自用户的投诉。
部分用户没有收到带有激活链接的邮件，无法重新注册。
团队发现用户注册时没有第二个名字，因此电子邮件模板渲染失败。
由于交易已经提交，用户被存储在数据库中，但是邮件没有被发送。

团队知道他们必须用不同的设计来防止将来出现这种情况。
他们考虑为通知和后台流程设置状态，但是他们知道最终解决方案仍然是在同一流程中保存数据库事务和发送电子邮件。所以他们认为这是把问题转移到了另一个地方。在这种情况下，他们决定引入消息代理— [RabbitMQ](https://www.rabbitmq.com/) 和事件。
每当注册完成时，“注册完成”事件就会发布到 RabbitMQ。
寄件消费者抓到了，发了邮件。

# “我们需要运行同步”

过了一段时间，“欧米茄”小组面临了另一个问题。很少有用户没有收到他们已经支付的产品。
经过深入研究，他们在旧日志中发现，他们确实存储了订单，并正确地通知了计费平台，但是在下订单时，运输平台出现故障。这导致了一种情况，当订单被下，发票被制作，但是运输平台没有被指示发送产品。

解决这个问题的第一个想法是创建同步流程，该流程将定期调用运输平台和计费平台，以确保它们“*同步*”。
然而，他们知道这种解决方案只是暂时的，因为当新的集成出现时，他们将需要为每个集成实现它。
*欧米茄*认定引进订单被下单事件是一个好的开始。如果他们为该事件创建一个消费者，问题可能会再次出现。因为单个消费者将提取消息并呼叫计费和运输。
他们提出的解决方案是创建两个消费者，并将此事件发布给他们每个人。所以计费和发货 API 调用是分开处理的。

# "队列被卡住"

管理员可以向用户提供 10%的折扣。
无论何时提供折扣，都会向用户发送带有促销代码的电子邮件。

新用户再次停止接收“*欢迎消息*”。
团队发现，由于队列被阻止发送“促销代码”邮件。
消费者试图处理它，无论何时失败，消息都被返回到队列并再次被消费。这阻止了所有较新的通知被发送，并且没有“*欢迎消息*，用户不能激活他们的帐户登录。
团队知道这种问题可能会发生，他们需要提供一个允许发送电子邮件的解决方案。他们引入了死信队列，每当消息失败时，它被移动到单独的队列中，以便以后调查，并感谢其他邮件可以被发送。

![](img/8c44eae760070c28e3225b433debcf5c.png)

# 漫长的道路，但有可能…

在他们的系统平稳运行之前，Omega 团队不得不面对许多其他问题。
他们与其他团队共享知识和库，因为他们知道从头开始这个过程会花费很多时间。

在 PHP 中构建企业级解决方案是可能的。PHP 为此做好了准备，然而我们美国开发者需要工具，因为构建自己的工具可能会成为第二份工作。
*生态区*为您解决了那些问题，因此您可以专注于代码的业务部分。
如果你想轻松构建更健壮的系统，请阅读[教程](https://docs.ecotone.tech/tutorial-php-ddd-cqrs-event-sourcing.)来学习如何在你现有的系统中应用*生态区*。