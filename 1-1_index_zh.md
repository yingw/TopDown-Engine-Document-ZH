TopDown 引擎简介
========

欢迎使用自顶向下引擎文档。在这里，您将找到创建自己的自上而下游戏所需的一切！

- [什么是自顶向下引擎？](https://topdown-engine-docs.moremountains.com/index.html#what-is-the-topdown-engine)[](https://topdown-engine-docs.moremountains.com/index.html#what-is-the-topdown-engine)
- [安装包后出现错误/相机不动！](https://topdown-engine-docs.moremountains.com/index.html#i-get-errors-after-installing-the-package--the-camera-doesnt-move)[](https://topdown-engine-docs.moremountains.com/index.html#i-get-errors-after-installing-the-package--the-camera-doesnt-move)
- [从旧版本引擎更新的最佳方法是什么？](https://topdown-engine-docs.moremountains.com/index.html#whats-the-best-way-to-update-from-an-old-version-of-the-engine)[](https://topdown-engine-docs.moremountains.com/index.html#whats-the-best-way-to-update-from-an-old-version-of-the-engine)
- [我可以将 URP 与 TopDown 引擎一起使用吗？](https://topdown-engine-docs.moremountains.com/index.html#can-i-use-urp-with-the-topdown-engine)[](https://topdown-engine-docs.moremountains.com/index.html#can-i-use-urp-with-the-topdown-engine)
- [我从哪里开始 ？](https://topdown-engine-docs.moremountains.com/index.html#where-do-i-start-)[](https://topdown-engine-docs.moremountains.com/index.html#where-do-i-start-)

什么是自顶向下引擎？[](https://topdown-engine-docs.moremountains.com/index.html#what-is-the-topdown-engine)
-------------------------------------------------------------------------------------------------

TopDown Engine 是一个自顶向下的框架，由 Corgi Engine 的创建者提供，可在[Unity Asset Store 上找到](https://assetstore.unity.com/packages/templates/systems/topdown-engine-89636?aid=1011lKhG)。

这是一个非常快速、紧凑、移动友好、强大且可扩展的引擎，以**质量**和**游戏感觉**为核心构建，现在可以使用 Unity 开始创建具有自上而下视角的 2D 或 3D 游戏。

它被设计为**各种自上而下的游戏的基础**，从像以撒的结合这样的地牢爬行游戏到像旧的塞尔达游戏这样的冒险游戏，再到像 Final Fight 或像 Hotline Miami 这样的枪重游戏，以及**任何其他类型的**游戏。**相机位于动作上方的游戏**。

这是一个快速、**生产就绪**、多功能、轻量级且易于扩展的解决方案，将帮助您大力推进您的项目。

![杰基尔](https://topdown-engine-docs.moremountains.com/images/intro-1.png)

自顶向下引擎的启动屏幕

安装包后出现错误/相机不动！[](https://topdown-engine-docs.moremountains.com/index.html#i-get-errors-after-installing-the-package--the-camera-doesnt-move)
--------------------------------------------------------------------------------------------------------------------------------------------

您的错误是否与 Unity 软件包有关？您是否尝试将其更新到最新版本？如果这不能解决您的问题，请确保您阅读了包含在资产中的 IMPORTANT-HOW-TO-INSTALL.txt 文件中的安装说明。您还可以查看[文档的专用部分](https://topdown-engine-docs.moremountains.com/install.html)。

从旧版本引擎更新的最佳方法是什么？[](https://topdown-engine-docs.moremountains.com/index.html#whats-the-best-way-to-update-from-an-old-version-of-the-engine)
--------------------------------------------------------------------------------------------------------------------------------------------

**无论您做什么，请确保您有一个提交/备份，以便**在发生问题时**回滚**。然后，**删除旧的 TopDownEngine 文件夹**，并导入新**文件夹**。如果不这样做，由于 Asset Store 导入器的工作方式，某些脚本可能会被复制，不会被删除等。根据您更新的版本以及更新到的版本，您可能有一些轻量级重构。确保您查看[发行说明](http://topdown-engine.moremountains.com/topdown-engine-releases)以了解更改的内容以及可能对您自己的代码产生影响的内容。

我可以将 URP 与 TopDown 引擎一起使用吗？[](https://topdown-engine-docs.moremountains.com/index.html#can-i-use-urp-with-the-topdown-engine)
-----------------------------------------------------------------------------------------------------------------------------

是的，引擎不做任何渲染，**它可以与任何渲染管道一起工作**。演示是使用**标准渲染管线制作的**，因为它仍然是唯一稳定的，也是最常见的分母，但您可以使用任何您喜欢的 RP。您将在[安装文档中](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-in-a-urp-project)找到一些帮助您入门的步骤。考虑到这两种渲染管线的许多怪癖，建议在选择 URP 或 HDRP 之前至少具有渲染管线的基本知识。

我从哪里开始 ？[](https://topdown-engine-docs.moremountains.com/index.html#where-do-i-start-)
--------------------------------------------------------------------------------------

首先，**您不必阅读所有文档**。该引擎在构建时考虑到了 Unity 的良好实践，并带有帮助框。因此，如果这不是您的第一个 Unity 项目，那么您自己可能会没事的。如果有什么不清楚的地方，你可以随时回到这里。

也就是说，您可以使用**左侧**的**菜单**前往特定地点。本文档是功能性的。如果您对代码本身有疑问，您宁愿查看[API 文档](http://topdown-engine-docs.moremountains.com/API/)。还建议直接查看代码的注释，通常它们几乎涵盖了您可能遇到的任何问题。

如果您需要功能列表，或者想知道引擎中是否包含这个或那个，您可以查看[此页面](http://topdown-engine.moremountains.com/)。它还包括一个变更日志和其他有用的东西。

[Youtube上](https://www.youtube.com/playlist?list=PLl3caEhMYxQGFQ8LA5doTSkWhP2Mx84Gx)也有[视频教程](https://www.youtube.com/playlist?list=PLl3caEhMYxQGFQ8LA5doTSkWhP2Mx84Gx)。

如果所有这些都没有帮助，您可以随时使用[资产页面上的](https://topdown-engine.moremountains.com/topdown-engine-contact)**支持电子邮件链接** 。[](https://topdown-engine.moremountains.com/topdown-engine-contact)
