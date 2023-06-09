# 如何在 Polkadot 平台上创建一个 dApp？

> 原文：<https://medium.com/nerd-for-tech/how-to-create-a-dapp-on-the-polkadot-platform-dbd843951607?source=collection_archive---------2----------------------->

![](img/e5e2c909b7b12a88260be46120409822.png)

随着区块链议定书数量的增加，我们必须了解它们的目的以及它们将解决现有区块链一代的哪些缺点。互操作性是大多数第一代和第二代区块链协议所缺乏的特性之一。由于它们各自为政的体系结构，它们无法与其他区块链平台通信，也无法处理跨链交换。

这就是波尔卡多特着手解决互联性问题的地方。Polkadot 是区块链高速公路，致力于提供互操作性，弥合不同区块链网络之间的差距，这些网络以独特的共识机制运行。

Polkadot 是一个可互操作的链，它基于与第一个不同的共识机制，帮助在另一个区块链上托管一个区块链的 dApps。Polkadot 是最好的区块链平台之一，它有助于托管具有所有这些优势的可互操作的分散式应用。

本文将帮助您理解在 Polkadot 平台上构建一个 [Web3 应用程序](https://www.leewayhertz.com/web3-development-company/)的过程。

# 关于波尔卡多特的建筑

![](img/f357a3de568dcc8f86e61cb8228b7cfd.png)

波尔卡多特是异质区块链碎片或副链在单一网络中的混合体。这些链通过链接到 Polkadot 中继链而受到安全监控，并且它们可以在 Polkadot 网桥的帮助下轻松地与外部网络进行交互。Polkadot 的体系结构中有以下组件来执行副链一致性角色:

# 继电器链

中继是 Polkadot 整个架构的症结所在。它侧重于网络的跨链互操作性、一致性和安全性。

# 副链

副链是独立的区块链，可以针对特定的用例调节它们的功能。对于与中继链的联系连接，副链被允许租用一个插槽，并且当他们决定去的时候也可以付费，因为他们随身带着他们的令牌。

# 波尔卡多桥

Polkadot 网桥是特殊的区块链组件，有助于两个不同的区块链或两个不同的外部网络之间的交互。

# 提名者

提名者通过选择可信的验证者和标记点来保护接力链。

# 验证器

Polkadot 验证器通过与其他验证器一起参与共识来关注中继链的安全性，验证来自标桩点和整理器的证据。

# 校对程序

它们为验证者提供证据，并且通过从用户处获取分片事务来维护分片是可信的。

# 渔船

他们从根本上参与了 Polkadot 网络的监控和监督，并提醒验证者注意任何不良功能。任何一个副链，一个完整的节点或者一个整理器都可以充当渔夫。

# 负责 Polkadot 治理的组件:

# 理事会成员

委员会成员代表被动的利益相关者，被赋予执行公投和否决恶意公投的责任。

# 技术委员会

技术委员会肩负着建设波尔卡多特的责任，该委员会可以在提议的紧急公投中联系议会成员。

现在我们已经熟悉了 Polkadot 网络的基本组件，让我们深入到在其上构建一个分散式应用程序的步骤中。

# 如何在 Polkadot 网络上构建 dApp？

基板提供了在 Polkadot 网络上构建 [dApp 的所有重要组件。](https://www.leewayhertz.com/polkadot-dapp-development/)

# 先决条件

*   您的计算机上本地安装的 Rust 应该配置为创建开发环境。
*   关于如何利用手工和软件编程的基本知识。

# 第一步

首先，使用基底建立一个区块链应用程序。基底上有已经格式化的模板，用于设置开发环境。

这些预格式化的模板有助于在基板上开发时添加更多自定义功能。

git 克隆[https://github . com/substrate-developer-hub/substrate-node-template](https://github.com/substrate-developer-hub/substrate-node-template)

然后运行以下命令，使用 Rust 集成夜间构建:

rustup 每夜更新 rustup 目标添加 was m32-未知-未知-每夜工具链

之后，将目录更改为。/sub rate-node-template 文件夹。然后在存储库中查找最新版本。

cd 基板-节点-模板

git 结帐最新

这个存储库保存 Rust 文件，可以根据项目的需要进行定制。

之后，运行下面的命令来编译并让节点模板在您的项目中运行。

> $ cargo build-release 2021–12–16 00:36:30 在开发模式下运行，RPC CORS 已被禁用。2021–12–16 00:36:30 基板节点…2021–12–16 00:36:33 位于#0 的最高已知块 2021–12–16 00:36:33 Prometheus exporter 开始于 127 . 0 . 0 . 1:9615 2021–12–16 00:36:33 监听 127.0.0.1:9944 上的新连接。2021–12–16 00:36:36 在父级 0 x4 bbcc 70 ccccc 322d 314 a5 df 12 a 814 c 28d 40 e 6879 b 7 b 930 df 5 a C5 a 50 Fe 4 be 4c 30 2021–12–16 00:36:36 在 1 (1 毫秒)为建议准备的块[hash:0x 18 f1 c 7 BF 91 a 1544 C9 A0 e 35 AC 08 c 8 f 036 B4parent _ hash:0x 4 BBC…4c 30；extrinsic s(1):[0x 6458…325 e]]2021–12–16 00:36:36 1 处的提案预密封块。哈希现 0 xf 10d 170d 82617 ff 5 df 6752 DC 911d 3483 badf 34 b 005 c 8 c 48 a 46 aeb 6b 708 c 915 b 2，前为 0x 18 f1 c 7 BF 91 a 1544 C9 A0 e 35 AC 08 c 8 f 036 B4 CB 2 f 8d 8297233 fffadb 94022 b 982 a 7。2021–12–16 00:36:36 导入的#1 (0xf10d…15b2)2021–12–16 00:36:38 空闲(0 对等)，最佳:# 1(0x F10 d…15 B2)，最终确定的#0 (0x4bbc…4c30)，0 0…2021–12–16 00:36:42 在 2。哈希现为 0x 409138 FDA 4 f 59 DC 093 DCE 60 fefbaca 31 c 354 ce 18 cef 1 bbea 6 f 69 a 5009 af 6 E0 f 4，之前为 0x 484 e 81 ea 15 f 04 a 640 a 595 CB 51d 41 EEC 05919 b4a 16839852 ba 4d 8 a 69440 e 1。…

然后，设置一个前端应用程序，以允许与网络终端上当前运行的分散应用程序进行交互。

**git 克隆**[https://github . com/substrate-developer-hub/substrate-front-end-template](https://github.com/substrate-developer-hub/substrate-front-end-template)

***现在，安装纱线:***

***纱线安装***

# 第二步

最后一步是使用洛可可测试和部署新开发的 [Polkadot dApp](https://www.leewayhertz.com/polkadot-dapp-development/) 。洛可可是一个波尔卡多副链测试网，它的功能基于一个权威证明的共识机制。在 testnet 上测试了 dApp 之后，现在就可以部署了。

# 包扎

[区块链平台](https://www.leewayhertz.com/top-blockchain-platforms/)单个都有鲜明的特点，但是如果这些区块链缺乏跨链通信，它们就没有用了。因此，互操作性是一个重要的特性，它正被大量集成到世界各地的大多数区块链中。凭借其多链兼容性和架构，Polkadot 解决了所有与互操作性和可伸缩性相关的问题。