成就
==

本页介绍了如何使用 TopDown Engine 中包含的成就系统并根据您的游戏对其进行自定义。

-   [介绍](https://topdown-engine-docs.moremountains.com/achievements.html#introduction)[](https://topdown-engine-docs.moremountains.com/achievements.html#introduction)
-   [重置成就](https://topdown-engine-docs.moremountains.com/achievements.html#resetting-achievements)[](https://topdown-engine-docs.moremountains.com/achievements.html#resetting-achievements)
-   [成就列表](https://topdown-engine-docs.moremountains.com/achievements.html#the-achievement-list)[](https://topdown-engine-docs.moremountains.com/achievements.html#the-achievement-list)
-   [解锁成就](https://topdown-engine-docs.moremountains.com/achievements.html#unlocking-achievements)[](https://topdown-engine-docs.moremountains.com/achievements.html#unlocking-achievements)
-   [MMA成就规则](https://topdown-engine-docs.moremountains.com/achievements.html#mmachievementrules)[](https://topdown-engine-docs.moremountains.com/achievements.html#mmachievementrules)
-   [成果展示](https://topdown-engine-docs.moremountains.com/achievements.html#achievements-display)[](https://topdown-engine-docs.moremountains.com/achievements.html#achievements-display)
-   [与 Steam、iOS 等接口](https://topdown-engine-docs.moremountains.com/achievements.html#interfacing-with-steam-ios-etc)[](https://topdown-engine-docs.moremountains.com/achievements.html#interfacing-with-steam-ios-etc)

介绍[](https://topdown-engine-docs.moremountains.com/achievements.html#introduction)
----------------------------------------------------------------------------------

自上而下引擎包括一个简单易用但功能强大的成就系统。它将允许您定义、触发和保存成就。此外，它**非常模块化** 且易于扩展，例如，如果您想将其插入特定平台的社交 API。

重置成就[](https://topdown-engine-docs.moremountains.com/achievements.html#resetting-achievements)
----------------------------------------------------------------------------------------------

关于成就系统，您需要了解的第一件事是**如何重置它**（无论如何，这是关于它的最常被问到的问题）。这可以在成就列表检查器的底部完成，也可以通过顶部菜单完成，方法是单击"更多山脉">"重置所有成就"。：

![杰基尔](https://topdown-engine-docs.moremountains.com/images/achievements-1.png)

More Mountains 顶级菜单。

成就列表[](https://topdown-engine-docs.moremountains.com/achievements.html#the-achievement-list)
--------------------------------------------------------------------------------------------

关于成就的第二件重要的事情是**如何定义它们**。这是通过可编写脚本的对象 AchievementsList 完成的。您可以创建自己的资产，但资产中已有一个可以修改。您可以在 Common/Resources/Achievements 下找到它。您只需选择它并通过其检查器修改其内容即可。请注意，该列表必须位于 Resources 文件夹中，否则 Unity 将无法加载它。

![杰基尔](https://topdown-engine-docs.moremountains.com/images/achievements-2.png)

成就清单。

如上图所示，成就由 ID（用于通过脚本解锁）、类型、标题、描述、相关图像和声音以及潜在进度构成。有两种类型的成就：简单的（完成游戏，找到宝藏，诸如此类的独特东西）和基于进度的成就（收集 50 个硬币，死亡 20 次等）。在基于进度的情况下，您需要指定解锁成就所需的目标进度。所有成就只能解锁一次，除非您当然重置它们。

解锁成就[](https://topdown-engine-docs.moremountains.com/achievements.html#unlocking-achievements)
----------------------------------------------------------------------------------------------

将成就添加到列表后，就该切换到代码以使其可解锁了。这可以在任何课程中完成，当然，您将在何处完成这取决于您的游戏和成就。引擎中有一些示例，因此您可以更好地了解它是如何完成的。请注意，此成就系统使用**Events**，如果您想更好地了解它是如何工作的，您可能需要[阅读此页面](https://topdown-engine-docs.moremountains.com/events.html)。

所以解锁成就非常简单，一行代码即可完成。你把那行代码放在哪里取决于你想做什么。我建议扩展 AchievementRules 类，以便您将它们集中在同一个地方，并让该类侦听事件并对其采取行动（如果您想了解有关如何操作的更多信息，请查看该类的代码）。但是，如果您愿意，您也可以在代码中的任何位置执行此操作。

以下是您如何解锁名为"踏脚石"的简单成就（当然，您需要将其替换为您的成就 ID）：

```
MMAchievementManager.UnlockAchievement("SteppingStone");

```

以下是为基于进度的成就添加进度的方法：

```
MMAchievementManager.AddProgress ("JumpAround", 1);

```

当然，您可以将"1"替换为您选择的任何值，以加快进度。

MMA成就规则[](https://topdown-engine-docs.moremountains.com/achievements.html#mmachievementrules)
---------------------------------------------------------------------------------------------

如前所述，现在的成就是由 AchievementRules 类触发的。这是一个 MonoBehaviour，因此您需要将它添加到您希望从中解锁成就的每个场景中的空 GameObject。不过成就是全局的，所以如果你在 A 级解锁一个，你将无法在 B 级再次解锁。如果你不想使用 AchievementRules 类，请确保将这些行添加到游戏开始时的经理：

```
// we load the list of achievements, stored in a ScriptableObject in our Resources folder.
MMAchievementManager.LoadAchievementList ();
// we load our saved file, to update that list with the saved values.
MMAchievementManager.LoadSavedAchievements ();

```

成果展示[](https://topdown-engine-docs.moremountains.com/achievements.html#achievements-display)
--------------------------------------------------------------------------------------------

![杰基尔](https://topdown-engine-docs.moremountains.com/images/achievements-3.png)

解锁成就会在屏幕的角落显示一个小弹出窗口。

该资产包括一个成就展示器。要使用它，您需要为它们准备一个容器。我发现垂直布局组效果很好，但您可以使用任何您想要的东西。该容器需要添加一个 MMAchievementDisplayer 组件。从它的检查器中，您将能够指定解锁成就时要实例化的预制件、它应该在屏幕上保留多长时间以及过渡应该有多快。您当然可以修改或创建一个新的预制件，以完全按照您想要的方式显示成就。它需要添加一个 MMAchievementDisplay 组件，以便您可以绑定 GUI 元素。

与 Steam、iOS 等接口[](https://topdown-engine-docs.moremountains.com/achievements.html#interfacing-with-steam-ios-etc)
-----------------------------------------------------------------------------------------------------------------

为避免创建对外部代码的**依赖**，此资产不包含适用于 Steam、Google Play、iOS 或其他平台的现成接口。但是这个成就系统是在考虑到这种演变的情况下构建的，因此您可以轻松扩展它并调用所需的方法，因为它们都或多或少地共享成就的结构。最好的方法是创建一个新类来侦听 MMAchievementUnlockedEvents（当然，每次解锁成就时都会触发这些事件）并将该成就传递给目标社交平台的 API。