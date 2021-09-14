Minimal Scene Requirements
==========================

This page covers all the gameobjects you need in your scene for the engine to work.

-   [Introduction](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements.html#introduction)[](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements.html#introduction)
-   [Minimal Scene](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements.html#minimal-scene)[](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements.html#minimal-scene)

Introduction[](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements.html#introduction)
----------------------------------------------------------------------------------------------------------

In the TopDown Engine, like in most Unity projects, a level is made of a Scene. You can add lots of stuff to your scene (walls, enemies, etc.), it can be huge, or very small, **it's really up to you**. But whatever you do, there are a few elements required for the engine to work. The engine includes two examples of "minimal" scenes, a 3D one, and a 2D one. These scenes show the "standard conditions" minimal elements. Technically, you could even remove more stuff, but they act as good **starting points**.

Minimal Scene[](https://topdown-engine-docs.moremountains.com/minimal-scene-requirements.html#minimal-scene)
------------------------------------------------------------------------------------------------------------

![Jekyll](https://topdown-engine-docs.moremountains.com/images/minimal-requirements.png)

The contents of the minimal scene

You'll find an example of a starting 2D scene in the Minimal2D folder, and an example of a 3D one in the Minimal3D folder. Both are pretty similar, the only difference lying in the type of cameras they use (one is perspective, the other is orthographic). Here's what they contain :

-   **GameManager** : the GameManager is responsible for handling the game loop. It's mandatory in every scene if you want to use most "game mechanics" classes in the engine.
-   **SoundManager** : as the name implies, it's a central point for playing sounds. It's not mandatory, but you'll probably want to have it around.
-   **Other managers** : The **LevelManager** is in charge of spawning your character, and handling level specific stuff. You'll have to specify what character this level uses, as well as an initial spawn point in its inspector. The **InitialSpawnPoint** is just a transform, to tell the LevelManager where to spawn the first character. The **TimeManager** will handle all time manipulations for you. That goes for advanced stuff like slowing down time, but also for simple stuff like a pause. Finally, **AchievementRules** are optional, and describe what achievements can be unlocked in this level.
-   **Camera** : Usually you'll want to have a camera in your level. Both Minimal scenes come with advanced camera setups, complete with Cinemachine virtual camera, and a UICamera to support your UI elements. Of course, you could remove all that and use a simple Camera. Note that the UICamera also contains the **InputManager**. Without an InputManager, your characters **won't move**. So if you decide to get rid of that UICamera, make sure you have an InputManager somewhere in your scene.
-   **Level** : Basic ground/walls. Optional, and should be replaced with yours.