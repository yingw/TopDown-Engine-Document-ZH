多人游戏
====

本页介绍了本地多人游戏在自上而下引擎中的工作原理，以及如何设置多人游戏场景。

-   [介绍](https://topdown-engine-docs.moremountains.com/multiplayer.html#introduction)[](https://topdown-engine-docs.moremountains.com/multiplayer.html#introduction)
-   [示例场景](https://topdown-engine-docs.moremountains.com/multiplayer.html#example-scene)[](https://topdown-engine-docs.moremountains.com/multiplayer.html#example-scene)
-   [级别经理](https://topdown-engine-docs.moremountains.com/multiplayer.html#level-manager)[](https://topdown-engine-docs.moremountains.com/multiplayer.html#level-manager)
-   [人物](https://topdown-engine-docs.moremountains.com/multiplayer.html#characters)[](https://topdown-engine-docs.moremountains.com/multiplayer.html#characters)

介绍[](https://topdown-engine-docs.moremountains.com/multiplayer.html#introduction)
---------------------------------------------------------------------------------

自上而下引擎已准备好支持**本地多人游戏**、潜在无限数量的玩家和一个 4 人游戏示例，包括胜利条件和相机模式。请注意，它当然也可以用于基于网络的多人游戏，但这当然需要一些额外的实现。

示例场景[](https://topdown-engine-docs.moremountains.com/multiplayer.html#example-scene)
------------------------------------------------------------------------------------

![杰基尔](https://topdown-engine-docs.moremountains.com/images/multiplayer-1.png)

分屏设置中的 Grasslands 演示场景

在 Demos 文件夹中，您会找到一个**Grasslands**文件夹，其中包含一个 4 人演示场景。在其中，玩家竞争在 1 分钟内收集最多的硬币，或者成为最后一个站立的玩家。他们可以四处走动、冲刺和击打东西 - 以及彼此。

此外，该演示还带有 2 种相机模式：**分屏**和**群拍**。您可以通过选择层次结构中的 LevelManager 对象在两种模式之间切换，并且从其检查器中，您可以从"相机模式"下拉列表中进行选择。

级别经理[](https://topdown-engine-docs.moremountains.com/multiplayer.html#level-manager)
------------------------------------------------------------------------------------

常规场景和多人场景之间的主要区别在于 LevelManager。虽然通常使用默认的 LevelManager 类很好，但在这里您可能需要实现自己的类，因为每个多人游戏通常都有自己的规则。为此，建议您扩展**MultiplayerLevelManager**类（或者如果它适合您的需要，则直接使用它）。

您将在 Grasslands 演示中找到此类扩展的示例。它的 GrasslandsMultiplayerLevelManager 扩展了 MultiplayerLevelManager 类，以添加对分数和倒计时管理的支持。

基本 MultiplayerLevelManager 类将负责生成 1 个以上的角色和相机模式选择。

人物[](https://topdown-engine-docs.moremountains.com/multiplayer.html#characters)
-------------------------------------------------------------------------------

您需要在**MultiplayerLevelManager 中**设置要使用的字符。每个角色都没有什么特别的事情要做。您可以将他们的 PlayerID 设置为 Player1、Player2 等，但系统也可以处理此问题。您只需要确保场景中的**每个玩家**都有**一个 InputManager**。在 Grasslands 演示中，您将在 GrasslandsUICamera 对象上找到它们。