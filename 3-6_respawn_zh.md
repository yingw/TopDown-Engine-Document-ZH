重生
==

本页介绍了游戏周期和重生机制。

-   [重生是如何工作的？](https://topdown-engine-docs.moremountains.com/respawn.html#how-does-respawn-work)[](https://topdown-engine-docs.moremountains.com/respawn.html#how-does-respawn-work)
-   [检查点](https://topdown-engine-docs.moremountains.com/respawn.html#checkpoints)[](https://topdown-engine-docs.moremountains.com/respawn.html#checkpoints)

重生是如何工作的？[](https://topdown-engine-docs.moremountains.com/respawn.html#how-does-respawn-work)
---------------------------------------------------------------------------------------------

在大多数自上而下的游戏中，您的角色可能会受到伤害，如果其生命值降为零，则最终会死亡。在自上而下引擎中，这也是**默认行为**。当你的角色受到伤害时，一个相对复杂的事件链就会开始：

-   你的角色受到 X 点伤害，这由你角色的健康部分处理
-   它失去 X 生命值
-   如果它的生命值低于零，Health 组件调用它的 Kill() 方法并告诉 LevelManager 玩家已经死亡
-   LevelManager 重置关卡，触发玩家和场景中潜在的其他对象的重生

Respawn 是通过检查玩家最后到达的检查点，重新定位玩家，并重新生成所有注册到该检查点的对象来完成的。检查点在其检查器中分配了一个 CheckPointOrder 值。该顺序将定义到达它们的顺序。您还可以对它们进行 ForceAssignation，这意味着进入 ForceAssignation 检查点的角色会认为该检查点是它最后经过的检查点。

如果你想让你的敌人或物体重生，只需在它们上面放置一个**Autorespawn**组件。

检查点[](https://topdown-engine-docs.moremountains.com/respawn.html#checkpoints)
-----------------------------------------------------------------------------

![杰基尔](https://topdown-engine-docs.moremountains.com/images/checkpoints-1.png)

游戏运行时，场景视图中的检查点由绿线链接。

在 TopDown Engine 中创建和放置检查点**非常简单**。您所要做的就是创建一个空的游戏对象，并向其中添加一个**Checkpoint 组件**。它还需要一个碰撞器组件，2D 或 3D 取决于您使用的角色类型。它的形状无关紧要，它可以是 BoxCollider、CircleCollider、SphereCollider 等......确保将其 IsTrigger 设置为 true。

然后你所要做的就是改变对撞机的大小。该大小将决定触发检查点的区域，使其足够大，以便您的角色不会错过它。您还可以从 Checkpoint 组件的检查器设置面向方向。这就是您的玩家角色在重生时将面对的方向。

然后，您可以在场景中定位检查点，并添加更多检查点。您可以做的最后一件事是在检查点的检查器中设置 CheckPointOrder。检查点应按升序编号。当您按下播放键时，您会看到所有检查点都由一条绿线按照必须越过的顺序连接起来。