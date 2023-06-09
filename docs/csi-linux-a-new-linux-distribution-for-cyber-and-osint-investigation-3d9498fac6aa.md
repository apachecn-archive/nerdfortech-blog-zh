# CSI Linux:用于网络和犯罪调查的新 Linux 发行版

> 原文：<https://medium.com/nerd-for-tech/csi-linux-a-new-linux-distribution-for-cyber-and-osint-investigation-3d9498fac6aa?source=collection_archive---------0----------------------->

由 [anshul vyas](https://www.instagram.com/_ansh_vyas/) 撰写

![](img/fb0299caeea7ca0930d9fb32ba6c1715.png)

# **简介**

为了应对日益严重的网络犯罪问题，政府和企业正在投入更多资源创建网络调查实验室，以调查在线犯罪。因此，软件工具对调查过程至关重要。因此，网络取证、事件响应和竞争情报专业人员开发了 CSI Linux，这是一种针对网络取证的操作系统。收集和安装各种应用程序以检查和分析犯罪是非常耗时的。因此，需要一个只附带必要工具的包罗万象的系统。

# CSI Linux:基于 Linux 的操作系统

这个多功能操作系统是专门为网络调查人员设计的。有了 CSI Linux，您不必担心软件包的安装和配置，因为预先安装了大量工具来进行在线调查、分析恶意软件和防范安全威胁。CSI Linux 解决以下问题:在线调查:社交媒体帐户、网站信息、OSINT、事件响应:入侵检测/预防和恶意软件分析。

对于 CSI Linux 来说，要运行虚拟机映像和下载安装程序，您需要超过 50gb 的可用空间，因此如果您不喜欢这个最低要求，它可能不适合您。还需要至少 8GB 的内存。CSI Linux Investigator 包括三个独立的平台:Analyst、Gateway 和 SIEM，它们提供了任务的个性化和模块化。

# 如何设置 CSI Linux 2021.1 虚拟设备(VM)

该版本已更新至 Ubuntu 20.04 LTS 版，以获得长期支持。CSI Gateway 已经退役，该项目已更名为 CSI TorVPN，占用空间更少，启动速度比 2020 版本更快。对应用程序和新应用程序进行了许多增强。当你打开它时，所有的流量都将被一个 Tor“VPN”适配器封装。旧的 CSI 网关可以与 Whonix 一起使用，这样你就可以通过位于 whonix.org 的 Whonix 网站提供的 Whonix 网关发送你的所有流量。

# 系统需求

1.  系统应该支持虚拟化。
2.  文件下载和安装需要 64 GB 的可用空间。
3.  需要 6 GB 内存。
4.  虚拟机通常预分配了 4 GB。
5.  工具和更新更新

# 装置

1.  从这个链接下载并安装 VirtualBox 或扩展包:【https://www.virtualbox.org/wiki/Downloads 
2.  您将在下面看到 CSI Linux 2021.1VM.ova 文件。从下载部分下载。

A.使用 BitTorrent 程序打开 Torrent 或 Magnetlink 文件。BitTorrents 下载。OVA 文件。

B.一旦它被下载，请考虑把它作为种子留在你的种子客户端，这样其他人也可以找到它并下载它。

3.只需检查。ova 文件是否已经下载。

4.双击鼠标左键，您应该会看到 VirtualBox 在屏幕上弹出安装信息。ova 文件。

5.选择一个具有足够磁盘空间的位置来安装虚拟设备非常重要。如果您的系统在 C:驱动器上没有足够的空间，您可能需要将其安装在 D:驱动器或外部驱动器上。

![](img/e9c06a8eba0283b22ceb0a6907ced851.png)

6.检查设置以确保它们符合您的需求。例如，如果您有很多 RAM，您可以增加 RAM 的数量或添加更多的虚拟 CPU。不要超过您的主操作系统的物理可用容量。

![](img/d42fef9e5f1be087b33be78e43b0ab11.png)![](img/f34e9e3b18f26ba9ff5b7cea64958142.png)

7.请左键单击“导入”。

8.点击左边的同意，然后等待，直到 CSI Linux 已经安装，这可能需要几分钟。

![](img/bcaa438d6ccfdf502eb09b43d8c164b4.png)![](img/6fd10bee8560faccdc5551a27e732c3f.png)

9.安装成功后，您可能会在 VirtualBox 中看到 CSI Linux 2021.1 作为一个系统。

![](img/8e9358cbbbaa2fcb8fdf642402b5435a.png)

10.双击 CSI Linux 2021.1 虚拟机。

11.当虚拟机在新窗口中启动时，输入用户名和密码。
用户名:csi
密码:csi

![](img/4e6b7d12c02f0c7351de4d197b2c9981.png)

12.填写凭证后，点击“登录”。

13.现在你会看到 CSI Linux 界面。

![](img/0013be5f1a87f6a2d26c61c93b308cb4.png)

# CSI Linux 分析师

除了调查和分析工具之外，分析师版还提供了创建网络报告的工具。你可以使用社交媒体搜索和 Maltego 等程序收集嫌疑人的所有社交足迹。

# CSI Linux 网关

顾名思义，网关网络将所有分析师流量连接到 Tor 网络，以确保互联网上的安全性和匿名性。大多数网络工具允许你与黑暗网络互动。如果嫌疑人属于使用 Gateway Linux 的黑客或盗版团体，您可以隐藏您的位置，并增加一层安全性。

# CSI Linux SIEM

此版本的 SIEM 主要用于检测入侵和响应事件。如果您的系统受到威胁，可以使用 SIEM 工具(如 anchorage、Kibana 和 Elasticsearch)来检查整个系统的漏洞。它们也可以独立使用，用于对威胁进行深入分析。

# 特征

来作为网络和犯罪调查的天堂，因为预装的新工具是可怕的。

![](img/1d5e270ff429b8cabd235f4a0267611e.png)![](img/1c595865a3d925b1b86281cddf656df9.png)![](img/424f2aeda578b0bb2e242596fc743267.png)![](img/701302fbe1400bc86c699aedf667fb90.png)![](img/95096719658417b931fc727b69aa96d9.png)