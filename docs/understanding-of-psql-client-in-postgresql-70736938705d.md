# 对 PostgreSQL 中 psql 客户端的理解|面试问答

> 原文：<https://medium.com/nerd-for-tech/understanding-of-psql-client-in-postgresql-70736938705d?source=collection_archive---------1----------------------->

在这里，我们将看到 psql 客户端特性和元命令的详细信息

![](img/87547e9d97403cd6ace039535d879411.png)

什么是 psql 客户端？

1.  Psql 客户端是一个基于终端的 Postgresql 前端工具。
2.  我们可以交互地键入查询，或者从文件或命令行参数中输入，将它们发布到 PostgreSQL 中，并查看查询输出或结果。

3.它还提供了大量的元命令。

**连接集群:**

> psql -h 主机名-d 数据库名-U 用户名-p 端口号

这里

-h 表示主机名或端点

-d 表示数据库名

-U 是指用户名

-p 指端口号

**查看帮助选项:**

> Google=# \？
> 
> 或者
> 
> Google=# \h create table 还提供了每个特定于命令的选项。

它总是维护过去执行的查询的查询缓冲区，这意味着我们可以编辑或修改查询并再次运行它。为此，我们可以使用向上箭头

**元命令:**

这是 psql 的一个特性，也有助于执行数据库操作，而无需在数据库中使用单个查询

> \ c dbname 连接到指定的数据库
> 
> \l —列出所有数据库
> 
> \d —显示表格、视图和序列
> 
> \dt —仅显示表格
> 
> \dv —显示视图
> 
> \dm —显示实体化视图
> 
> \di —显示索引
> 
> \ dn 显示模式
> 
> \dT —显示数据类型
> 
> 等等。
> 
> \ SV[视图名称] —显示视图定义
> 
> \x —切换扩展显示。对于包含大量被访问列的表非常有用

**与操作系统交互:**

我们可以使用 psql 来连接 os 命令

**查看当前目录:**

> postgresql=# \！残疾人

**更改目录**:

> postgresql=# \cd 脚本

**运行脚本:**

> postgresql=# \i script.sql

**查看脚本计时:**

> postgresql = # \计时

**将输出写入文件:**

> postgresql=# \o 文件名

**至 psql 的出口:**

> postgresql=# \q

**总结:**

元命令不以分号结尾

元命令以\

用元命令添加+将提供大小和额外的细节