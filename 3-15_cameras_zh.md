相机
==

本页介绍了如何在自顶向下引擎中使用相机。

-   [介绍](https://topdown-engine-docs.moremountains.com/cameras.html#introduction)[](https://topdown-engine-docs.moremountains.com/cameras.html#introduction)
-   [常规和 UI 相机](https://topdown-engine-docs.moremountains.com/cameras.html#regular-and-ui-cameras)[](https://topdown-engine-docs.moremountains.com/cameras.html#regular-and-ui-cameras)
-   [电影机](https://topdown-engine-docs.moremountains.com/cameras.html#cinemachine)[](https://topdown-engine-docs.moremountains.com/cameras.html#cinemachine)
-   [像素完美](https://topdown-engine-docs.moremountains.com/cameras.html#pixel-perfect)[](https://topdown-engine-docs.moremountains.com/cameras.html#pixel-perfect)
-   [后期处理](https://topdown-engine-docs.moremountains.com/cameras.html#postprocessing)[](https://topdown-engine-docs.moremountains.com/cameras.html#postprocessing)
-   [相机旋转](https://topdown-engine-docs.moremountains.com/cameras.html#camera-rotation)[](https://topdown-engine-docs.moremountains.com/cameras.html#camera-rotation)

介绍[](https://topdown-engine-docs.moremountains.com/cameras.html#introduction)
-----------------------------------------------------------------------------

与任何其他 Unity 项目一样，您的关卡中需要一个（或更多）摄像机才能看到动作。自上而下引擎包括一些特定于相机的脚本。请注意，**您可以将任何相机脚本与资产一起使用**，或者实现您自己的脚本，或者在提供的脚本之上构建。这里**没有强制要求**，您可以随心所欲。本页介绍了主要脚本以及如何使用它们。

常规和 UI 相机[](https://topdown-engine-docs.moremountains.com/cameras.html#regular-and-ui-cameras)
----------------------------------------------------------------------------------------------

![杰基尔](https://topdown-engine-docs.moremountains.com/images/camera-1.png)

自上而下引擎的两个摄像头和摄像头装备

默认情况下，在自上而下引擎的大多数演示场景中，您会注意到一个**摄像机装备**：一个包含普通摄像机（2D、3D、是否跟随玩家等）和一个 UI 摄像机的变换。UI 相机的剔除蒙版设置在 UI 上，这意味着它只会渲染 UI 标记的东西，并设置为**叠加**在主相机的渲染上。它包含一个或多个画布，您会在其中找到按钮、屏幕等。MainCamera 是一个普通的 Unity 摄像机，在大多数演示中，引擎使用 Unity 惊人的 Cinemachine 来驱动它。

电影机[](https://topdown-engine-docs.moremountains.com/cameras.html#cinemachine)
-----------------------------------------------------------------------------

该引擎依靠[Cinemachine](https://unity3d.com/learn/tutorials/topics/animation/using-cinemachine-getting-started)来处理摄像机的基本行为。这是一个漂亮而强大的工具，它应该可以满足您在相机移动和行为方面的所有需求。本文档不包括如何使用 Cinemachine，因为它[自己的文档](https://unity3d.com/learn/tutorials/topics/animation/using-cinemachine-getting-started)做得很好。

TopDownEngine 的唯一细节是这些组件，添加到虚拟相机：

-   使用 Cinemachine Confiner，在启动时自动设置为 LevelManager 的边界，因此您不必担心。
-   一个 MMCinemachineCameraShaker，用于捕捉相机抖动事件并以抖动模式移动虚拟相机。
-   一个 CinemachineCameraController，一个允许你打开或关闭跟随的最小类

像素完美[](https://topdown-engine-docs.moremountains.com/cameras.html#pixel-perfect)
--------------------------------------------------------------------------------

对于您希望相机的像素完美行为的 2D 场景，引擎依赖于 Unity 的原生 Pixel Perfect Camera 组件来提供清晰的视觉效果。[查看其文档](https://github.com/Unity-Technologies/2d-pixel-perfect/blob/master/Documentation/2D%20Pixel%20Perfect%20Camera.md)以获取有关如何使用它的更多详细信息。您还可以在 Koala Dungeon 演示场景中看到它的使用情况。

后期处理[](https://topdown-engine-docs.moremountains.com/cameras.html#postprocessing)
---------------------------------------------------------------------------------

自上而下引擎依靠 Unity 出色的后处理堆栈来实现后处理效果。不要犹豫，查看[其文档](https://github.com/Unity-Technologies/PostProcessing/wiki)以获取有关如何充分利用它的更多信息。

相机旋转[](https://topdown-engine-docs.moremountains.com/cameras.html#camera-rotation)
----------------------------------------------------------------------------------

虽然自上而下引擎专注于自上而下的动作游戏，这些游戏传统上采用非旋转相机，但该引擎具有专用功能 CharacterRotateCamera，可让您在垂直轴（2D 中的 z，3D 中的 y）上旋转相机你的性格。它还提供旋转输入以匹配相机方向、确定旋转空间和速度的选项，以及武器的专用瞄准选项。您将在 Loft3D 演示场景中找到它的示例（使用 L 和 M 旋转相机）。虽然可能，但引擎中并未内置更高级的相机运动（第三人称视角等），该引擎仅专注于自上而下的动作游戏。