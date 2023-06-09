# Chocolatey:在 Windows 中安装应用程序的最佳方式

> 原文：<https://medium.com/nerd-for-tech/chocolatey-the-best-way-to-install-applications-in-windows-3a26e4704ace?source=collection_archive---------1----------------------->

![](img/fc73f5b06ff3683acfb3e686aab00b56.png)

# 介绍

Linux 用户普遍称赞的众多因素之一是在他们的系统中安装应用程序的便利性。Linux 系统带有软件仓库，从那里可以下载和安装所有需要的应用程序。把软件仓库想象成你的安卓设备上的 Play Store，或者你的苹果设备上的 App Store 你只需要打开商店，搜索一个应用，然后点击“安装”。在 Linux 系统中，您可以使用包管理器来访问它们的软件存储库。

Linux 世界中有几个包管理器，比如 Ubuntu 中的`apt`、Fedora 中的`dnf`和 Arch 中的`pacman`——仅举几个例子。你可以使用基于这些包管理器构建的图形应用商店(如 Play Store 或 App Store)来安装应用程序；但是大多数有经验的 Linux 用户更喜欢在终端中编写命令来安装应用程序——这也非常容易。例如，如果你想在 Ubuntu 中安装 Mozilla Firefox，你只需输入`sudo apt install firefox`，然后输入你的密码，点击“回车”——就完成了！就这么简单！(`sudo`用于授予您安装的管理员权限，例如当 Windows 询问您*“您希望此应用程序对您的设备进行更改吗？”*)。如果您不确定这个包的名称或者它是否在存储库中，您可以简单地使用`apt search firefox`进行搜索。如果你想一次更新所有安装的应用程序，只需输入`sudo apt update`然后输入`sudo apt upgrade`！软件库的一大优点是它们的安全性，因为所有的包都由开发人员检查和验证，因此你可以确定安装应用程序不会引起任何问题。

多年来，在 Microsoft Windows 中安装应用程序的默认方式是使用 web 浏览器搜索应用程序，下载安装程序文件，然后运行安装程序。这种情况近年来有所改变，微软推出了一个应用商店(微软商店)，你可以在那里搜索应用程序，然后点击“安装”。虽然商店中的应用程序数量有所增加，但与 Windows 可用的应用程序数量相比，仍然微不足道。最近微软推出了一款基于命令的软件包管理器，名为[‘Windows Package Manager’(或‘winget’)](https://devblogs.microsoft.com/commandline/windows-package-manager-1-0/)，你可以在终端输入命令来搜索和安装软件包。存储库中的包的数量在增长，但是仍然很小。当然，并不是所有的 Linux 应用程序都可以在它们的库中找到，在某些情况下，您需要搜索并下载一个安装程序，但是通常 Linux 中的软件库是巨大的，几乎所有的应用程序都可以找到。

这就是巧克力糖来拯救我们的地方。这是一个非常简单的 Windows 包管理器，在他们的库中有一个巨大的应用程序库。Chocolatey 本身很容易安装，安装应用程序和更新已安装的应用程序是[“超级容易，勉强一个不方便”](https://www.urbandictionary.com/define.php?term=Super%20Easy%2C%20Barely%20an%20Inconvenience)！但在我们继续之前，需要有一个大的免责声明！

## 免责声明:

Chocolatey repository 包括开源软件，如 VLC(源代码可以免费检查、使用或修改)，免费软件，如 Adobe Reader(代码是专有的，不免费提供，但可以免费使用)和共享软件，如 Spotify(代码是专有的，可以免费使用，但在有限的时间内，或需要付费才能解锁所有功能)。Chocolatey 的存储库中没有付费应用程序，如 Adobe Creative Cloud apps 或 Microsoft Office，您需要先付费才能使用。

# 使用巧克力的好处

1.  在线搜索应用程序，进入下载页面，下载安装程序，然后双击运行安装程序，这是一件很麻烦的事情。从终端搜索并编写一个小命令来安装应用程序要容易得多。
2.  Chocolatey 为您提供了用一个命令安装多个应用程序的选项。在传统的 Windows 方法中，您必须搜索、下载安装程序，并为每个要安装的应用程序逐一运行它们。
3.  在 Windows 中，您必须确保您是从官方来源或可信网站下载安装程序文件。在过去，人们通过下载错误来源的安装程序在系统中感染病毒或恶意软件的例子不胜枚举。与 Linux 中的软件仓库一样，Chocolatey 通过检查所有应用程序的完整性并确保它们没有病毒来规避这个问题。
4.  更新 Windows 中的应用程序是另一个令人头疼的问题。如果应用程序有内置的更新程序，它会通知您进行更新。在某些情况下，应用程序没有更新程序，你必须手动在他们的网站上检查更新并安装它。无论如何，你必须一个接一个地更新所有的应用程序。使用 chocolatey，您只需一个命令就可以更新所有已安装的应用程序。

# 巧克力的安装

首先，打开一个 PowerShell 窗口。单击开始按钮，键入“powershell”。在搜索结果中，您应该会看到“Windows PowerShell”。右键单击它，并选择“以管理员身份运行”。在 PowerShell 窗口中，复制并粘贴以下命令，然后按 enter 键:

```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('[https://community.chocolatey.org/install.ps1'](https://community.chocolatey.org/install.ps1')))
```

该命令将在您的系统上安装 Chocolatey。在运行安装命令之前，Chocolatey 网站上的[帮助页面](https://chocolatey.org/install)要求在第一步检查`ExecutionPolicy`是否被限制；但是不需要额外的步骤，因为安装步骤会考虑所有要求。

# 使用 Chocolatey 安装应用程序

一旦安装了 Chocolatey，您将需要以管理员身份运行 Powershell 窗口或命令提示符来安装应用程序—任何一种方式都可以。

要搜索一个应用程序，比如 Mozilla Firefox，您只需在终端中键入以下命令

```
choco search firefox
```

在许多情况下，你会得到许多选项，或者同一应用程序的许多版本。使用以下命令，选择要安装的软件包，并使用软件包的确切名称进行安装

```
choco install firefoxesr
```

在这种情况下，我查看了选项列表，并安装了 Firefox ESR(扩展版)。

如果你愿意，你也可以在 [Chocolatey 网站](https://community.chocolatey.org/packages)使用他们的搜索功能搜索应用程序，而不是在终端中。好处是，你可以从网站上复制确切的命令来安装你想要的应用程序，并将其粘贴在终端上。

![](img/27b2ca28b51c12e28aa90500b9cffee9.png)

在 Chocolatey 网站上搜索应用程序

要一次安装多个应用程序，您只需在 install 命令中键入所有带空格的应用程序的名称。

```
choco install inkscape gimp krita audacity mpv ffmpeg youtube-dl
```

这种方法的一个缺点是，您必须多次按回车键才能获得安装所有应用程序的许可，但这很容易补救。在安装任何应用程序之前，在终端运行以下命令—

```
choco feature enable -n allowGlobalConfirmation
```

这将设置终端在安装单个或多个应用程序时不请求许可。

## 放弃

第一次安装软件包时要小心。可能有一些软件包尚未验证，或已在病毒测试中被标记，或已过期。您可以在 chocolatey 网站上查看这些详细信息，或者在终端中运行以下命令:

```
choco info firefox
```

![](img/24bf5c74f515cfbefdc7dd75099c91b1.png)

多次验证测试失败的应用程序

例如，如果您在 Chocolatey 中搜索 PasswordFox 包，您可以看到它没有通过验证测试和病毒扫描。在这种情况下安装软件包时要小心。

# 更新已安装的应用程序

应用程序更新可以一个接一个地完成，也可以一次完成多个，或者一次全部完成。例如，如果您只想更新 Mozilla Firefox，则运行以下命令:

```
choco upgrade firefox
```

要更新多个应用程序，请在名称的`choco upgrade`后键入空格。如果您想一次性更新所有应用程序，只需运行:

```
choco upgrade all
```

要更新 Chocolatey 本身，运行`choco upgrade chocolatey`。

# 卸载应用程序

要卸载应用程序，你可以运行`choco uninstall`来卸载一个或几个软件包。

# 收场白

Chocolatey 是在 Windows 中处理应用程序的一种极好的方式。它是一个快速和无麻烦的软件包管理器，在我看来是最好的选择。从我发现巧克力的那天起，我就一直在使用它，从来没有出现过任何问题。

当然，也有替代产品，比如 Ninite，它可以让你一次下载并安装多个应用程序，甚至是最近的 Windows 包管理器——但就库中可用的应用程序数量而言，Chocolatey 远远超过了它们。

在这篇文章中，我只提到了 chocolatey 中的一些选项和参数。一定要去 Chocolatey 网站阅读所有可用的选项，他们有很棒的文档。

如果你在读完这篇文章后尝试了 Chocolatey，并且发现它很有用，请在评论中告诉我。再见。