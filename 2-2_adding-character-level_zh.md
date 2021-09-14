将您的角色添加到场景中
===========

本页介绍了如何将您的角色添加到 TopDown 引擎中的场景中。

-   [介绍](https://topdown-engine-docs.moremountains.com/adding-character-level.html#introduction)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#introduction)
-   [水平经理](https://topdown-engine-docs.moremountains.com/adding-character-level.html#the-level-manager)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#the-level-manager)
-   [让你的角色已经出现在你的场景中](https://topdown-engine-docs.moremountains.com/adding-character-level.html#having-your-character-already-present-in-your-scene)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#having-your-character-already-present-in-your-scene)
-   [其他角色（AI、NPC）](https://topdown-engine-docs.moremountains.com/adding-character-level.html#other-characters-ais-npcs)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#other-characters-ais-npcs)
-   [多人游戏](https://topdown-engine-docs.moremountains.com/adding-character-level.html#multiplayer)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#multiplayer)
-   [通过脚本访问玩家角色](https://topdown-engine-docs.moremountains.com/adding-character-level.html#accessing-the-player-character-via-script)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#accessing-the-player-character-via-script)

介绍[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#introduction)
--------------------------------------------------------------------------------------------

一旦你[创建了你的角色](https://topdown-engine-docs.moremountains.com/how-to-create-character.html)，你可能会想要玩它。有多种方法可以做到这一点，本页解释了可以将角色添加到场景中的不同方法，无论它们是否可玩。

水平经理[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#the-level-manager)
---------------------------------------------------------------------------------------------------

该**LevelManager**类是自上而下的发动机一个非常核心的类。它负责生成玩家、处理检查点以及场景中的入口点。它基本上定义了整个关卡的规则。它还将用作整个引擎中的类[与玩家](https://topdown-engine-docs.moremountains.com/adding-character-level.html#accessing-the-player-character-via-script)进行[通信](https://topdown-engine-docs.moremountains.com/adding-character-level.html#accessing-the-player-character-via-script)的主要方式。

我们推荐在充电LevelManager**产卵**你的性格。这意味着在您按下 Play 之前它不会出现在场景中，并将在运行时**实例化**。要让您的 LevelManager 知道它应该实例化哪个角色，请在您的场景层次结构中选择 LevelManager 对象，展开 PlayerPrefabs 数组，然后将一个 Character 预制件从您的项目视图中拖放到 Element0 字段中。

![杰基尔](https://topdown-engine-docs.moremountains.com/images/adding-to-scene-1.png)

将您的角色绑定到 LevelManager。

您可以[在文档的专用部分](https://topdown-engine-docs.moremountains.com/managers.html#level-manager)了解有关 LevelManager 的更多信息。

让你的角色已经出现在你的场景中[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#having-your-character-already-present-in-your-scene)
------------------------------------------------------------------------------------------------------------------------------------------------

虽然上面的方法是推荐的方法，但您也可以让您的角色已经出现在您的场景中，并且仍然让 LevelManager 引用它。为此，您需要在场景中有一个 Character 对象，并将其拖到 LevelManager 的 SceneCharacters 数组中。

![杰基尔](https://topdown-engine-docs.moremountains.com/images/adding-to-scene-2.png)

将场景中的角色绑定到 LevelManager。

其他角色（AI、NPC）[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#other-characters-ais-npcs)
-------------------------------------------------------------------------------------------------------------------

对于其他不打算由玩家控制的角色，这要容易得多，您只需将他们的预制件拖到场景中的某个位置即可。

多人游戏[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#multiplayer)
---------------------------------------------------------------------------------------------

在多人游戏中，您必须让 MultiplayerLevelManager 知道要实例化哪些角色。这就像单个字符一样完成：

![杰基尔](https://topdown-engine-docs.moremountains.com/images/adding-to-scene-3.png)

在多人游戏环境中将角色绑定到 LevelManager。

通过脚本访问玩家角色[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#accessing-the-player-character-via-script)
---------------------------------------------------------------------------------------------------------------------------------

通过脚本访问玩家的最佳方式是通过**LevelManager**类，因为它始终保持对它的引用（或者如果您的关卡中有多个可玩角色，则对它们的引用）。从任何类，您都可以通过以下方式访问播放器数组：

```
LevelManager.Instance.Players

```

Players 是一个数组，所以如果你只有一个可玩角色，你可以通过以下方式访问它：

```
LevelManager.Instance.Players[0]

```

它是一个角色数组，所以从那里可以很容易地与你的玩家互动：

```
// this will freeze your main character
LevelManager.Instance.Players[0].Freeze();

// sets the main character's max Health to 50
LevelManager.Instance.Players[0].gameObject.MMGetComponentNoAlloc<Health>().MaximumHealth = 50;

// forces the character to dash
LevelManager.Instance.Players[0].gameObject.MMGetComponentNoAlloc<CharacterDash>().StartDash();

```