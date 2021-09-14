回馈
==

本页介绍了如何使用自上而下引擎向游戏的各个方面添加反馈。

-   [介绍](https://topdown-engine-docs.moremountains.com/feedback.html#introduction)[](https://topdown-engine-docs.moremountains.com/feedback.html#introduction)
-   [MM反馈](https://topdown-engine-docs.moremountains.com/feedback.html#mmfeedback)[](https://topdown-engine-docs.moremountains.com/feedback.html#mmfeedback)
-   [屏幕抖动](https://topdown-engine-docs.moremountains.com/feedback.html#screen-shake)[](https://topdown-engine-docs.moremountains.com/feedback.html#screen-shake)
-   [屏幕闪光](https://topdown-engine-docs.moremountains.com/feedback.html#screen-flash)[](https://topdown-engine-docs.moremountains.com/feedback.html#screen-flash)
-   [时间管理](https://topdown-engine-docs.moremountains.com/feedback.html#time-management)[](https://topdown-engine-docs.moremountains.com/feedback.html#time-management)
-   [健康棒](https://topdown-engine-docs.moremountains.com/feedback.html#health-bars)[](https://topdown-engine-docs.moremountains.com/feedback.html#health-bars)
-   [伤害漂浮物](https://topdown-engine-docs.moremountains.com/feedback.html#damage-floaties)[](https://topdown-engine-docs.moremountains.com/feedback.html#damage-floaties)
-   [动画、爆炸、击退、粒子](https://topdown-engine-docs.moremountains.com/feedback.html#animations-explosions-knockback-particles)[](https://topdown-engine-docs.moremountains.com/feedback.html#animations-explosions-knockback-particles)
-   [触觉反馈](https://topdown-engine-docs.moremountains.com/feedback.html#haptic-feedback)[](https://topdown-engine-docs.moremountains.com/feedback.html#haptic-feedback)

介绍[](https://topdown-engine-docs.moremountains.com/feedback.html#introduction)
------------------------------------------------------------------------------

游戏中的反馈**非常重要**。无论是视觉反馈、触觉振动、声音还是其他任何东西，反馈都是在某件事发生时发生的事情的总和，通常是对玩家输入的反应。这将确保玩家始终了解其行为的后果。**TopDown 引擎在所有级别都考虑到了这一点**，并带有许多类和预制件，您可以使用它们来改善游戏的总体感觉。本页重点介绍了一些示例。

MM反馈[](https://topdown-engine-docs.moremountains.com/feedback.html#mmfeedback)
------------------------------------------------------------------------------

![杰基尔](https://topdown-engine-docs.moremountains.com/images/feedback-2.png)

检查器中的绑定反馈（上），以及它们如何存储在层次结构中（下）

该引擎带有**强大的 MMFeedback 系统**，可让您使用简单的**单线**播放"反馈"。您会在许多类中找​​到它的示例，请随时查看 Dash2D 组件以供参考。

许多课程都使用它：武器、健康、能力等等。要使用它，您需要做的就是创建一个新的空对象，向其添加一个 MMFeedbacks 组件，然后将其拖入武器或技能的插槽中。然后，在 MMFeedbacks 检查器中，您需要从反馈列表中添加您想要的反馈，并单独调整它们。完成后，您可以按播放来测试您的能力（或武器，或任何您触发反馈的东西）。您还可以在播放模式下使用测试按钮来测试您的反馈行为。

![杰基尔](https://topdown-engine-docs.moremountains.com/images/feedback-3.png)

具有一些反馈活动的 MMFeedbacks 示例

该**MMFeedbacks**类暴露了一堆的方法，特别是PlayFeedbacks（）。这个类将允许您一次触发许多反馈，只使用一行。要在你自己的类中利用 MMFeedbacks 系统，你所要做的就是在你的类或能力中声明一个公共的 MMFeedbacks（S 很重要），然后使用它的 PlayFeedbacks() 和 StopFeedbacks() 方法来触发它，任何你想的地点都可以。它会自动将上面的面板添加到您班级的检查员，您可以从中添加、删除和自定义反馈。

**要了解有关 MMFeedbacks 的更多信息**，您可以[在 Feel 的文档网站上](http://feel-docs.moremountains.com/getting-started.html)查看其文档。

屏幕抖动[](https://topdown-engine-docs.moremountains.com/feedback.html#screen-shake)
--------------------------------------------------------------------------------

可能是我个人最喜欢的，屏幕抖动会给你的游戏**带来**很大的**影响**，并有助于出售武器的力量或跳跃的力量。在引擎中，您将能够直接使用某些组件的屏幕抖动，例如武器，您可以在其中自动将屏幕抖动与武器的使用相关联，或者直接通过代码。为此，您所要做的就是调用 CameraController 的**Shake 方法**，将其传递给 ShakeParameters（持续时间、强度和频率）。您可以查看 CharacterDive 能力类，了解它是如何完成的。或者，您可以使用 MMTools 的**ScreenShakeEvents**并将 MMCameraShaker 组件添加到您的相机以抓取此事件并为您摇晃您的相机。

屏幕闪光[](https://topdown-engine-docs.moremountains.com/feedback.html#screen-flash)
--------------------------------------------------------------------------------

闪烁屏幕也是在游戏中推销动作的好方法。无论您是在射击时将其闪烁为白色或黄色，还是在被击中时将其闪烁为红色，它都会帮助玩家了解屏幕上发生的情况。该引擎带有**MMFlash**类，您可以在所有 UICameras 中找到该类的示例，它允许您在一行代码中使用 MMFlashEvent 闪烁屏幕，如下所示：

```
MMFlashEvent.Trigger(Color.white);

```

时间管理[](https://topdown-engine-docs.moremountains.com/feedback.html#time-management)
-----------------------------------------------------------------------------------

停止、加速或减慢时间的流动将使您能够突出游戏中的某些动作。也许您想在命中时添加**定格帧**，就像在街头霸王游戏中一样，或者您想在 Boss 死亡时平滑地放慢动作。多亏了**MMTimeManager**类，所有这些都可以在自顶向下引擎中**轻松**完成。您需要将其添加到场景中的一个空对象中，然后您就可以使用简单的单行事件来操纵时间。

例如，这是触发冻结帧的方式：

```
MMFreezeFrameEvent.Trigger(FreezeFramesOnHitDuration);

```

这就是您将时间减慢 3 秒的方法，将当前时间速度除以一半：

```
MMTimeScaleEvent.Trigger(MMTimeScaleMethods.For, 0.5f, 3f, true, 1f, false);

```

MMTimeManager 类带有**更多选项**，因此请随时查看其文档（或查看其代码）以获取更多详细信息。要知道的重要一点是它作为一个堆栈工作，所以你可以减慢时间，然后减慢它更多，然后暂停，取消暂停，冻结帧，只要你只修改时间，所有这些都会很好地协同工作使用它，而不是通过本机时间刻度 API。

健康棒[](https://topdown-engine-docs.moremountains.com/feedback.html#health-bars)
------------------------------------------------------------------------------

反馈可能非常明显，例如屏幕抖动，但也可能更**微妙**。拥有闪烁和动画的漂亮健康条是一种以非常清晰的方式传达角色健康变化的好方法。该引擎带有**MMHealthBar**组件，这是一种创建美观健康条的非常强大的方法。要使用它，只需将它放在带有 Health 组件的 Character 上。从其检查器中，您将能够定义其颜色、动画速度、延迟、凹凸动画等。您可以决定让引擎为您绘制它，或者您可以创建自己的视觉效果并使用它们。

伤害漂浮物[](https://topdown-engine-docs.moremountains.com/feedback.html#damage-floaties)
------------------------------------------------------------------------------------

在施加伤害时，您可能想显示造成了多少伤害。虽然 MMFeedbacks 已经提供了一个系统来执行此操作，但 TDE 包含一个专用反馈，您可以使用它来简化将损坏信息传递给浮动文本生成器的过程：**MMFeedbackTopDownEngineFloatingText**。此反馈可让您触发浮动文本的外观，这将反映对目标生命值组件造成的损坏。这需要在场景中正确设置 MMFloatingTextSpawner，否则什么都不会发生。为此，创建一个新的空对象，向其添加 MMFloatingTextSpawner。将（至少）一个 MMFloatingText 预制件拖入其 PooledSimpleMMFloatingText 插槽中。您会在 MMTools/Tools/MMFloatingText/Prefabs 文件夹中找到此类预制件，但您可以随意创建自己的。

动画、爆炸、击退、粒子[](https://topdown-engine-docs.moremountains.com/feedback.html#animations-explosions-knockback-particles)
--------------------------------------------------------------------------------------------------------------------

同样，反馈是引擎的支柱之一，因此几乎每个组件都会为您提供**让事情感觉更好的选项**。无论是设置动画、在事情发生时添加视觉或声音效果（死亡、命中......）、为武器添加击退、接触地面时的粒子效果，还是添加到你的射弹的传播，我建议你使用这些来推动你的游戏更上一层楼。

触觉反馈[](https://topdown-engine-docs.moremountains.com/feedback.html#haptic-feedback)
-----------------------------------------------------------------------------------

如果你想更进一步，你可能想看看[Nice Vibrations](https://assetstore.unity.com/packages/tools/integration/nice-vibrations-108559?aid=1011lKhG)。这是另一个**More Mountains**资产，它允许您仅使用一行代码在移动设备上触发**触觉反馈**（微小的、非常令人愉悦的振动）。当然，这适用于 Android 和 iOS。