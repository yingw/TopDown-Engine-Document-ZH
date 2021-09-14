如何安装 TopDown 引擎
==========

本页介绍了如何下载和安装 TopDown 引擎。

-   [介绍](https://topdown-engine-docs.moremountains.com/install.html#introduction)[](https://topdown-engine-docs.moremountains.com/install.html#introduction)
-   [导入资源（Unity 2019.2.9f1 或更高版本）](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-unity-201929f1-or-higher)[](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-unity-201929f1-or-higher)
-   [在 URP 项目中导入资产](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-in-a-urp-project)[](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-in-a-urp-project)
-   [引擎尚不支持的 Unity 版本](https://topdown-engine-docs.moremountains.com/install.html#unity-versions-not-yet-supported-by-the-engine)[](https://topdown-engine-docs.moremountains.com/install.html#unity-versions-not-yet-supported-by-the-engine)

介绍[](https://topdown-engine-docs.moremountains.com/install.html#introduction)
-----------------------------------------------------------------------------

无论您使用什么版本的 Unity，请记住始终在**空项目中**导入资产，以便正确导入引擎的项目设置。如果您决定不在空白项目中导入，请至少确保先**删除旧的 TopDown Engine 文件夹**以避免冲突。

此资产依赖于一些 Unity 包来运行。在导入时，这很可能会导致错误，这是正常的，并且很容易修复。这一切都在这个页面上进行了解释。

导入资源（Unity 2019.2.9f1 或更高版本）[](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-unity-201929f1-or-higher)
---------------------------------------------------------------------------------------------------------------------------------------

要导入资产，请按照下列步骤操作：

1.  从 Unity Hub创建一个**新项目**，选择最新的 Unity**稳定**版本作为你的 Unity 版本，2D 或 3D 作为模板
2.  转到 Asset Store 窗口并**导入**项目（它必须在一个空项目中，而不是现有项目中）
3.  您将收到警告，导入 TopDown Engine 将覆盖您当前的项目设置（这是正常的），单击导入。
4.  这将需要一些时间。
5.  完成后，您将收到提示"This Unity Package has Package Manager **dependencies** "。这也正常，点击"安装/升级"。
6.  之后，您将获得引擎内容的列表，不要触摸任何内容，然后单击右下角的**导入**。
7.  导入也需要一段时间。导入完成后，您就可以使用引擎了。玩得开心！

在 URP 项目中导入资产[](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-in-a-urp-project)
----------------------------------------------------------------------------------------------------------------

引擎不做任何渲染，**它可以与任何渲染管道一起工作**。

演示是使用**标准渲染管线制作的**，因为它仍然是唯一稳定的，也是最常见的分母，但您可以使用任何您喜欢的 RP。如果您决定在您的项目中使用 URP 或 HDRP，最好的方法是在手头使用 SRP 的另一个项目来测试引擎的演示，同时您在 URP/HDRP 中实现您自己的游戏。

以下是在 URP 项目上安装 TDE 的步骤。考虑到这两种渲染管线的许多怪癖，建议在选择 URP 或 HDRP 之前至少**具有渲染管线的基本知识**。

1.  在 Unity 2019.4.28f1（或更高版本）中创建一个新项目，使用 URP 模板
2.  导入自顶向下引擎
3.  打开上校演示场景（或任何其他场景）
4.  打开你的项目设置，在Graphics中，在它的顶部，设置一个Scriptable render pipeline asset（URP默认模板通常有几个，选择HighQuality一个）
5.  在场景中，选择 UICamera，在它的 Camera 组件上，将 RenderType 设置为 Overlay
6.  选择嵌套在 UICamera 下的 Canvas，将其 SortingLayer 设置为 Above
7.  选择 MainCamera，在它的 Camera 组件底部，将 UICamera 添加到它的 Stack
8.  如果您想将所有（或大部分）材质转换为 URP，只需转到 Edit > Render Pipeline > Universal Render Pipeline > Upgrade Project Materials to URP Materials，按播放，演示将播放。请注意，您还必须移植后期处理效果，因为 Unity 在 URP/HDRP 上使用不同的系统（卷）。

引擎尚不支持的 Unity 版本[](https://topdown-engine-docs.moremountains.com/install.html#unity-versions-not-yet-supported-by-the-engine)
-----------------------------------------------------------------------------------------------------------------------------

自顶向下引擎的更新通常支持Unity的最新**稳定**版本，但有时它们会滞后一点。如果您在新发布的 Unity 版本中导入资产，则可能需要通过包管理器更新某些包。