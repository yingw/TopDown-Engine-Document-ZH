Multiplayer
===========

This page goes over how local multiplayer works in the TopDown Engine, and how you can setup your multiplayer scenes.

-   [Introduction](https://topdown-engine-docs.moremountains.com/multiplayer.html#introduction)[](https://topdown-engine-docs.moremountains.com/multiplayer.html#introduction)
-   [Example scene](https://topdown-engine-docs.moremountains.com/multiplayer.html#example-scene)[](https://topdown-engine-docs.moremountains.com/multiplayer.html#example-scene)
-   [Level Manager](https://topdown-engine-docs.moremountains.com/multiplayer.html#level-manager)[](https://topdown-engine-docs.moremountains.com/multiplayer.html#level-manager)
-   [Characters](https://topdown-engine-docs.moremountains.com/multiplayer.html#characters)[](https://topdown-engine-docs.moremountains.com/multiplayer.html#characters)

Introduction[](https://topdown-engine-docs.moremountains.com/multiplayer.html#introduction)
-------------------------------------------------------------------------------------------

The TopDown Engine comes ready for **local multiplayer support**, a potentially infinite number of players, and a 4-players example, complete with victory conditions and camera modes. Note that it could certainly be used for network based multiplayer as well, but that'd require some additional implementation of course.

Example scene[](https://topdown-engine-docs.moremountains.com/multiplayer.html#example-scene)
---------------------------------------------------------------------------------------------

![Jekyll](https://topdown-engine-docs.moremountains.com/images/multiplayer-1.png)

The Grasslands demo scene in its split screen setup

In the Demos folder you'll find a **Grasslands** folder, that contains a 4 players demo scene. In it, players compete to collect the most coins in 1 minute, or be the last player standing. They can move around, dash, and hit stuff - and each other.

Additionnally, the demo comes with 2 camera modes : **split screen** and **group shot**. You can switch between both modes by selecting the LevelManager object in the hierarchy, and from its inspector you can make your choice from the Camera Mode dropdown.

Level Manager[](https://topdown-engine-docs.moremountains.com/multiplayer.html#level-manager)
---------------------------------------------------------------------------------------------

The main difference between a regular scene and a multiplayer scene is the LevelManager. While usually using the default LevelManager class is fine, here you'll likely want to implement your own, as each multiplayer game usually has its own rules. To do so, it's recommended that you extend the **MultiplayerLevelManager** class (or simply use it directly if it fits your needs).

You'll find an example of such extension in the Grasslands demo. Its GrasslandsMultiplayerLevelManager extends the MultiplayerLevelManager class, to add support for score and countdown management.

The base MultiplayerLevelManager class will be responsible for spawning more than 1 character and for camera mode selection.

Characters[](https://topdown-engine-docs.moremountains.com/multiplayer.html#characters)
---------------------------------------------------------------------------------------

You'll want to set what characters you want to use in the **MultiplayerLevelManager**. There isn't anything special to do on each character. You can set their PlayerIDs to Player1, Player2, etc, but the system can also take care of this. You'll just want to make sure you have **one InputManager per player** in your scene. In the Grasslands demo you'll find them all on the GrasslandsUICamera object.