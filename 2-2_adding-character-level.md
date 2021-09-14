Adding your character to your scene
===================================

This page explains how to add your character to a scene in the TopDown Engine.

-   [Introduction](https://topdown-engine-docs.moremountains.com/adding-character-level.html#introduction)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#introduction)
-   [The Level Manager](https://topdown-engine-docs.moremountains.com/adding-character-level.html#the-level-manager)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#the-level-manager)
-   [Having your character already present in your scene](https://topdown-engine-docs.moremountains.com/adding-character-level.html#having-your-character-already-present-in-your-scene)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#having-your-character-already-present-in-your-scene)
-   [Other characters (AIs, NPCs)](https://topdown-engine-docs.moremountains.com/adding-character-level.html#other-characters-ais-npcs)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#other-characters-ais-npcs)
-   [Multiplayer](https://topdown-engine-docs.moremountains.com/adding-character-level.html#multiplayer)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#multiplayer)
-   [Accessing the player character via script](https://topdown-engine-docs.moremountains.com/adding-character-level.html#accessing-the-player-character-via-script)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#accessing-the-player-character-via-script)

Introduction[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#introduction)
------------------------------------------------------------------------------------------------------

Once you've [created your character](https://topdown-engine-docs.moremountains.com/how-to-create-character.html), you'll probably want to play with it. There are multiple ways to do it, and this page explains the different ways you can add characters, whether they're playable or not, to your scene.

The Level Manager[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#the-level-manager)
----------------------------------------------------------------------------------------------------------------

The **LevelManager** class is a very central class in the TopDown Engine. It's responsible for spawning the player(s), handling checkpoints as well as points of entry in a scene. It basically defines the rules of your level as a whole. It will also be used as the main way for classes throughout the engine to [communicate with the player](https://topdown-engine-docs.moremountains.com/adding-character-level.html#accessing-the-player-character-via-script).

It's recommended to have the LevelManager in charge of **spawning** your character. This means it won't be present in the scene until your press Play, and will be **instantiated** at runtime. To let your LevelManager know what character it should instantiate, select the LevelManager object in your scene's hierarchy, unfold the PlayerPrefabs array, and just drag and drop a Character prefab from your project view into the Element0 field.

![Jekyll](https://topdown-engine-docs.moremountains.com/images/adding-to-scene-1.png)

Binding your character to the LevelManager.

You can learn more about the LevelManager [in the dedicated part of the documentation](https://topdown-engine-docs.moremountains.com/managers.html#level-manager).

Having your character already present in your scene[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#having-your-character-already-present-in-your-scene)
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

While the method above is the recommended one, you can also have your character already present in your scene and still have the LevelManager reference it. For this to work, you'll need to have a Character object in your scene, and drag it into the LevelManager's SceneCharacters array.

![Jekyll](https://topdown-engine-docs.moremountains.com/images/adding-to-scene-2.png)

Binding a character from your scene to the LevelManager.

Other characters (AIs, NPCs)[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#other-characters-ais-npcs)
-----------------------------------------------------------------------------------------------------------------------------------

For other characters, that are not meant to be controlled by the player, it's much easier, you just have to drag their prefab somewhere in the scene.

Multiplayer[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#multiplayer)
----------------------------------------------------------------------------------------------------

In multiplayer, you'll have to let your MultiplayerLevelManager know what characters to instantiate. This is done just like for a single character :

![Jekyll](https://topdown-engine-docs.moremountains.com/images/adding-to-scene-3.png)

Binding character to the LevelManager in a multiplayer context.

Accessing the player character via script[](https://topdown-engine-docs.moremountains.com/adding-character-level.html#accessing-the-player-character-via-script)
----------------------------------------------------------------------------------------------------------------------------------------------------------------

The best way to access the player(s) via script is via the **LevelManager** class, as it keeps a reference to it at all times (or to them if you have more than one playable character in your level). From any class, you can access the player array via :

```
LevelManager.Instance.Players

```

Players is an array, so if you only have one playable character, you can access it via :

```
LevelManager.Instance.Players[0]

```

And it's an array of Characters, so from there it's very easy to interact with your player :

```csharp
// this will freeze your main character
LevelManager.Instance.Players[0].Freeze();

// sets the main character's max Health to 50
LevelManager.Instance.Players[0].gameObject.MMGetComponentNoAlloc<Health>().MaximumHealth = 50;

// forces the character to dash
LevelManager.Instance.Players[0].gameObject.MMGetComponentNoAlloc<CharacterDash>().StartDash();

```