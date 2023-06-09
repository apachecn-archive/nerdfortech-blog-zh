# 如果你能自己制作，为什么要买一个 Alexa？

> 原文：<https://medium.com/nerd-for-tech/why-buy-an-alexa-if-you-can-make-your-own-4223a33abd9a?source=collection_archive---------7----------------------->

在获益的同时保护您的隐私！

![](img/f2bcd0b44ea7249962d2fd8fb6f53ac9.png)

市场上的个人助理，如[谷歌主页](https://www.cnet.com/how-to/everything-you-want-to-know-about-google-home/)和[亚马逊 Alexa](https://en.wikipedia.org/wiki/Amazon_Alexa) 提供了很多物有所值的功能，但(真的)是在黑盒子里工作的。不知道您的数据是如何处理的不确定性是许多其他人真正关心的问题，这可能导致像我这样的用户避免购买此类产品。

在这篇文章中，我将与你分享我如何使用 Raspberry Pi 和 Python 的请求库来构建我自己的语音激活个人助理。因为你会知道引擎盖下发生的一切，隐私问题和缺乏可定制性就不再是问题了。

**在您的台式机/笔记本电脑上配置您的助手**

在我们配置 Raspberry Pi 计算机之前，我们可以使用我们的开发环境开始助手的工作。我们将从创建一个 Python 脚本 **assistant.py** 开始，为我们定义一个描述我们的助手及其功能的类。我们要做的第一件事是导入相关的包，以确保助手可以接收和解析音频命令，并使用文本到语音(TTS)引擎进行回复。

我们可以首先使用 pyttx3 包来配置 TTS 引擎。

在此之后，我们需要为助手定义一个方法来监听其环境并解析任何类似语音的音频。如果助手的名字被检测到，助手将在其后发送命令给另一个方法，该方法根据命令执行不同的助手功能。由于[全局解释器锁](https://realpython.com/python-gil/)，Python 不支持多线程，但是我们可以使用回调函数来解决这个问题。

现在我们可以定义方法 **take_command** 来检测命令中的关键词或短语，以确定用户的意图。你也可以训练一个 NLP 语言模型来做同样的事情，但是这个项目展示是为没有机器学习经验的人准备的。尽管这样做也没关系，因为这将使助手更加健壮。

我们现在可以开始为助手的不同功能定义方法。自从我每天使用维基百科，我的助手就可以不用手来帮我做这件事了。我通过使用 Python 的维基百科库做到了这一点。

除此之外，我还希望我的助手从 API 中检索天气数据。我们可以使用 Python 的请求库来做到这一点。

有许多 API 可以用来增加您的助手的功能。以下是我实现的一些功能，您可以自己尝试一下，但是您不应该局限于这个列表:

*   使用 Wolfram Alpha 解决数学问题
*   告知日期和时间
*   根据一天中的时间问候用户并进行自我介绍
*   讲笑话
*   停工
*   阅读最新新闻
*   推荐食谱来尝试

定义好方法后，你的助手就准备好了！从**助手**类中创建一个对象，并调用它的 **listen_background** 方法。

**我们如何才能更进一步？**

目前，助手受到您的开发环境提供的硬件的限制。使用 Raspberry Pi 计算机(RPi)等硬件，我们可以通过使用其通用输入/输出(GPIO)引脚与现实世界中的传感器和执行器进行交互，来做更多有趣的事情。在本文的这一部分，我将介绍在 RPi 计算机上运行您的助手所需的步骤。

**你需要什么**

*   树莓派电脑
*   USB 麦克风
*   带有 HDMI/USB 输入的扬声器

**要采取的步骤**

1.  将麦克风和扬声器连接到 RPi。
2.  将您的脚本从开发环境上传到 RPi。你可以使用物理连接或 Google Drive 等云服务来实现这一点。
3.  安装相关的软件包。因为 RPi 附带了 Raspberry Pi OS(基于 Debian)，所以还需要几个步骤来确保 pyttsx3 可以正常工作。打开终端并运行以下命令:`sudo apt-get install python-espeak && sudo apt-get update && sudo apt-get install espeak`
4.  在 RPi 上运行脚本。

恭喜你！您已经制作了自己的声控个人助理！如果你对我做过的其他项目感兴趣，或者想要联系我，这里是我的 [Github](https://github.com/Iscaraca) 和 [LinkedIn](https://www.linkedin.com/in/isaac-chen-jing-de/) 账户。