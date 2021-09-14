Contents of the Asset
=====================

This page describes the contents of the asset.

-   [Introduction](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#introduction)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#introduction)
-   [Common](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#common)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#common)
-   [Demos](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#demos)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#demos)
    -   [Koala2D](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#koala2d)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#koala2d)
    -   [Explodudes](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#explodudes)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#explodudes)
    -   [Grasslands](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#grasslands)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#grasslands)
    -   [LevelSelection](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#levelselection)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#levelselection)
    -   [Loft3D](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#loft3d)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#loft3d)
    -   [Minimal2D](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#minimal2d)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#minimal2d)
    -   [Minimal3D](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#minimal3d)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#minimal3d)
    -   [Startscreen](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#startscreen)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#startscreen)
-   [ThirdParty](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#thirdparty)[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#thirdparty)

Introduction[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#introduction)
-----------------------------------------------------------------------------------------------------

When you import the asset into your project, you'll get a TopDownEngine folder, containing three subfolders. I recommend leaving that folder as it is, and **not modifying its content**. Instead, create a dedicated folder for your game's assets, and if you need to modify code, just extend the TopDown Engine's class into one of yours. If you want to know more about that, look at the ["Inheritance" section](https://topdown-engine-docs.moremountains.com/creating-your-own-game.html#inheritance). Here's a rundown of the contents of these four folders, and of the general folder structure.

![Jekyll](https://topdown-engine-docs.moremountains.com/images/contents-1.png)

The contents of the asset

Common[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#common)
-----------------------------------------------------------------------------------------

As the name implies, Common contains all the scripts and visual assets necessary for the engine to work. You'll want to keep that folder in your game. The main structure is made of the following folders :

-   **Animations** : all the common animations (mostly GUI stuff).
-   **Fonts** : the fonts used in the various GUI screens are stored there.
-   **PhysicsMaterials** : a few physics materials used across most demos, but not specific to any.
-   **Prefabs** : all the prefabs used throughout the various demo levels.
-   **Resources** : the prefabs that are instantiated via code directly.
-   **Scripts** : the "core" of the engine, and where most of its value resides. We'll go over the details in a minute.
-   **Sprites** : all the sprites common to all demos. Again, mostly GUI stuff.

The Scripts folder is where all the engine's scripts are stored. Each demo may have one or more specific scripts, but otherwise it's somewhere in there. Note that the MMTools scripts are located in another of the root folders, for easier maintenance and better logic separation. Here are the main Scripts folders :

-   **Achievements** : Mostly achievements rules, the rest of the achievements scripts are in MMTools if you ever find yourself looking for them.
-   **Camera** : various camera related scripts
-   **Characters** : here you'll find all the scripts that make the characters move and act. From the controllers, character abilities, to AI scripts and weapons.
-   **Environment** : From falling blocks to teleporters, you'll find in this folder most of the scripts that handle the level's objects.
-   **GUI** : As the name implies, here you'll find everything GUI related : level selector, pause screens, etc.
-   **Items** : Coins or pickable weapons can be found in this folder.
-   **Managers** : All managers ("super" classes, often singletons, that handle global stuff) are in this.
-   **Spawn** : All spawn specific scripts go in there.

Demos[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#demos)
---------------------------------------------------------------------------------------

The Demos folder contains all the demos included in the engine. They're grouped by "universe", each universe may contain one or more scene. Usually each demo aims at showcasing **one or more particular aspects of the engine**, or how you can achieve different results with just a few tweaks and different art.

### Koala2D[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#koala2d)

-   **KoalaDungeon** : a "complete" demo of what the engine can do in 2D

### Explodudes[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#explodudes)

-   **Explodudes** : a 4-players 3D demo in the style of Bomberman. Drop bombs, move on a grid, break crates and your opponents. This scene comes complete with its own startscreen, pickable power ups, and all of class Bomberman's core mechanics.

### Grasslands[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#grasslands)

-   **Grasslands** : a 2D demo of a 4-players multiplayer game. You get to pick a camera mode (either split screen or grouped shot), and players compete to get the most coins in 1 minute, or be the last player standing.

### LevelSelection[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#levelselection)

-   **LevelSelection** : a carousel based level selection screen

### Loft3D[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#loft3d)

-   **Loft3D** : an Hotline Miami inspired 3D scene

### Minimal2D[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#minimal2d)

-   **Minimal2D** : the minimum requirements to start a 2D scene quickly
-   **Minimal2DRooms1** : an example of how you can link rooms together
-   **Minimal2DRooms2** : the second part of that example
-   **MinimalSandbox2D** : a scene showcasing most of the features you can put in a 2D scene
-   **Minimal2DGrid** : this scene demonstrates how you can implement grid based movement in 2D

### Minimal3D[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#minimal3d)

-   **MinimalAI3D** : examples of advanced AI behaviours
-   **MinimalPathfinding3D** : a scene showcasing how to use pathfinding in the engine
-   **MinimalSandbox3D** : a scene packed with features you can use in your own 3D scenes
-   **MinimalScene3D** : the minimum requirements to start a 3D scene quickly
-   **MinimalSword3D** : a demo scene showcasing a 3D combo-based sword wielding character, pitted against cone of vision guided AIs
-   **Minimal3DGrid** : this scene demonstrates how you can implement grid based movement in 3D

### Startscreen[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#startscreen)

-   **Startscreen** : an example of a startscreen, complete with an option popup and AI powered background

ThirdParty[](https://topdown-engine-docs.moremountains.com/contents-of-the-asset.html#thirdparty)
-------------------------------------------------------------------------------------------------

ThirdParty contains scripts and resources that are not directly specific to the TopDown Engine.

-   The **Inventory Engine** is another asset by More Mountains, usually sold separately, but included in the TopDown Engine as a gift. As its name implies, it'll help with creating and customizing inventories.
-   **MMInterface** is a library and resources by More Mountains, aimed at speeding up the process of creating UI screens in Unity.
-   The **MMTools** are helpers and small classes used throughout all More Mountains assets. Some of them may not be used in the TopDown Engine, but I'd advise **against removing them**. The unused ones won't make your build heavier, so it's just safer and simpler to keep them. This documentation doesn't cover them in details, but they're all commented, and explained in the API documentation if you're interested.
-   The **MMToolsForThirdParty** are More Mountains scripts aimed at piloting or enriching Unity APIs that are not yet built in, such as Cinemachine or the PostProcessing stack.
-   **NavmeshComponents** : from https://github.com/Unity-Technologies/NavMeshComponents, will be replaced by a package dependency, as soon as it's available
-   **Tilemap** : from https://github.com/Unity-Technologies/2d-extras/tree/master/Assets/Tilemap/Brushes, will be replaced by a package dependency, as soon as it's available