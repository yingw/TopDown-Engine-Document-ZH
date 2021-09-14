How to install the TopDown Engine
=================================

This page explains how to download and install the TopDown Engine.

-   [Introduction](https://topdown-engine-docs.moremountains.com/install.html#introduction)[](https://topdown-engine-docs.moremountains.com/install.html#introduction)
-   [Importing the asset (Unity 2019.2.9f1 or higher)](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-unity-201929f1-or-higher)[](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-unity-201929f1-or-higher)
-   [Importing the asset in a URP project](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-in-a-urp-project)[](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-in-a-urp-project)
-   [Unity versions not yet supported by the engine](https://topdown-engine-docs.moremountains.com/install.html#unity-versions-not-yet-supported-by-the-engine)[](https://topdown-engine-docs.moremountains.com/install.html#unity-versions-not-yet-supported-by-the-engine)

Introduction[](https://topdown-engine-docs.moremountains.com/install.html#introduction)
---------------------------------------------------------------------------------------

Whatever version of Unity you're using, remember to always import the asset in an **empty project**, so that the engine's project settings get properly imported. If you decide not to import in a blank project, at least make sure to **remove the old TopDown Engine folder** first to avoid conflicts.

This asset relies on a few Unity packages to function. On import this will very likely cause errors, that's normal, and easily fixed. It's all explained on this page.

Importing the asset (Unity 2019.2.9f1 or higher)[](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-unity-201929f1-or-higher)
-----------------------------------------------------------------------------------------------------------------------------------------------------------

To import the asset, follow these steps :

1.  Create a **new project** from Unity Hub, pick the latest **stable** version of Unity as your Unity version, and 2D or 3D as the Template
2.  Go to the Asset Store window and **import** the project (it has to be in an empty project, not an existing one)
3.  You will be warned that importing the TopDown Engine will overwrite your current project settings (that's normal), click on Import.
4.  This will take a bit of time.
5.  Once this is complete, you'll get a prompt saying "This Unity Package has Package Manager **dependencies**". This is also normal, click on "Install/Upgrade".
6.  After that you'll get a list of the contents of the engine, don't touch anything, and click on **Import** in the bottom right corner.
7.  Import will also take a while. Once import is complete, you're ready to use the engine. Have fun!

Importing the asset in a URP project[](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-in-a-urp-project)
---------------------------------------------------------------------------------------------------------------------------------------

The engine doesn't do any rendering, **it'll work with any render pipeline**.

The demos are made using the **Standard Render Pipeline**, as it's still the only stable one, and the most common denominator, but you can use any RP you prefer. If you decide to use URP or HDRP in your project, the best approach would be to keep another project at hand, using SRP, to test the engine's demos in, while you implement your own game in URP/HDRP.

Below are steps to install TDE on a URP project. It's recommended to have at least **basic knowledge of render pipelines** before picking URP or HDRP, considering the many quirks of these two render pipelines.

1.  Create a new project in Unity 2019.4.28f1 (or higher), using the URP template
2.  Import the TopDown Engine
3.  Open the Colonel demo scene (or any other)
4.  Open your project settings, in Graphics, at the top of it, set a Scriptable render pipeline asset (the URP default template usually comes with a few, pick the HighQuality one)
5.  In the scene, select the UICamera, on its Camera component, set RenderType to Overlay
6.  Select the Canvas nested under UICamera, set its SortingLayer to Above
7.  Select the MainCamera, at the bottom of its Camera component, add the UICamera to its Stack
8.  If you want to convert all (or most) materials to URP, simply go to Edit > Render Pipeline > Universal Render Pipeline > Upgrade Project Materials to URP Materials, press play, the demo will play. Note that you'd also have to port post processing effects, as Unity went with a different system (volumes) on URP/HDRP.

Unity versions not yet supported by the engine[](https://topdown-engine-docs.moremountains.com/install.html#unity-versions-not-yet-supported-by-the-engine)
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Updates for the TopDown Engine usually support the latest **stable** version of Unity, but sometimes they lag behind a bit. If you're importing the asset in a freshly released Unity version, you may have to update some packages via the Package Manager.