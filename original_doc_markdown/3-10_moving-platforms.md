Moving Platforms
================

This page explains how to create moving platforms in the TopDown Engine.

-   [Introduction](https://topdown-engine-docs.moremountains.com/moving-platforms.html#introduction)[](https://topdown-engine-docs.moremountains.com/moving-platforms.html#introduction)
-   [Creating a moving platform](https://topdown-engine-docs.moremountains.com/moving-platforms.html#creating-a-moving-platform)[](https://topdown-engine-docs.moremountains.com/moving-platforms.html#creating-a-moving-platform)
-   [Setting up moving Platforms](https://topdown-engine-docs.moremountains.com/moving-platforms.html#setting-up-moving-platforms)[](https://topdown-engine-docs.moremountains.com/moving-platforms.html#setting-up-moving-platforms)

Introduction[](https://topdown-engine-docs.moremountains.com/moving-platforms.html#introduction)
------------------------------------------------------------------------------------------------

Creating **moving platforms** in the TopDown Engine is very simple, yet there are a lot you can do with them, and a lot of ways to tweak them to your unique needs. For examples of moving platforms, you can check the bottom right room of the KoalaDungeon demo level. There's also one in the MinimalSandbox3D scene.

![Jekyll](https://topdown-engine-docs.moremountains.com/images/moving-platform-1.png)

An example of a Moving Platform in the KoalaDungeon demo level

Creating a moving platform[](https://topdown-engine-docs.moremountains.com/moving-platforms.html#creating-a-moving-platform)
----------------------------------------------------------------------------------------------------------------------------

To create a moving platform, simply follow these simple steps :

-   Start by dragging a sprite in your scene, or a 3D model
-   Select your newly created game object, and set its layer to "MovingPlatforms"
-   Add a non trigger BoxCollider2D or BoxCollider (depending on whether you're working with 2D or 3D characters) to it
-   Add a Rigidbody or RigidBody2D component to it, set it to kinematic
-   Add a MovingPlatform2D or MovingPlatform3D component to your object.
-   You're done! All that's left to do is tweaking the MovingPlatform's component's inspector.

Setting up moving Platforms[](https://topdown-engine-docs.moremountains.com/moving-platforms.html#setting-up-moving-platforms)
------------------------------------------------------------------------------------------------------------------------------

From the MovingPlatform's inspector, there are a few things you can tweak.

First of all there's the **Path** section. You can first decide on a **Cycle Option**. You can select Back and Forth (it'd go 1 > 2 > 3 > 2 > 1 > 2 etc), Loop (1 > 2 > 3 > 1 > 2...), and Only Once (1 > 2 > 3). Then there's the loop initial movement direction, which depending on your choice will start the movement either with the first (ascending) or last (descending) point in the path. And then of course there's the actual **Path Elements** where you'll need to specify an array's size. From there, you can either enter the points coordinates, or simply drag and position the little handles that appeared next to your platform to the position of your choice.

![Jekyll](https://topdown-engine-docs.moremountains.com/images/moving-platform-2.png)

Positioning a moving platform's path elements in the MinimalSandbox3D scene

Once you're happy with their placement, you can go back to the inspector, and set the **Movement Speed** and **Acceleration Type**. The MinDistanceToGoal field is best left to its default value but feel free to change it if necessary.