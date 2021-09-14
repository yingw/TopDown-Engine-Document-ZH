Collisions
==========

This page explains how collisions work in the TopDown Engine.

-   [Introduction](https://topdown-engine-docs.moremountains.com/collisions.html#introduction)[](https://topdown-engine-docs.moremountains.com/collisions.html#introduction)
-   [Layers](https://topdown-engine-docs.moremountains.com/collisions.html#layers)[](https://topdown-engine-docs.moremountains.com/collisions.html#layers)
-   [Tags](https://topdown-engine-docs.moremountains.com/collisions.html#tags)[](https://topdown-engine-docs.moremountains.com/collisions.html#tags)

Introduction[](https://topdown-engine-docs.moremountains.com/collisions.html#introduction)
------------------------------------------------------------------------------------------

The engine's TopDownControllers, whether we're talking about the 2D or 3D versions, are built on Unity's foundations. The 2D one will pilot a RigidBody2D, while the 3D version pilots a CharacterController. So for collisions you'll need **colliders**, set on your characters and obstacles/ground/etc.

Layers[](https://topdown-engine-docs.moremountains.com/collisions.html#layers)
------------------------------------------------------------------------------

The engine relies on [layers](https://docs.unity3d.com/Manual/Layers.html) to identify certain objects, notably walls and agents. Layers are metadatas you can associate your gameobjects with, and you can then use these to casts rays on certain layers only, via Layer masks (a selection of layers). Note that layers and [sorting layers](https://unity3d.com/learn/tutorials/topics/2d-game-creation/sorting-layers) are completely different things. There are no restrictions or naming conventions regarding sorting layers in the TopDown Engine.

Here's a list of the main layers used by the engine. Note that the only mandatory ones are the platform related ones :

-   **Ground** : whether you're in 2D or 3D, this marks the colliders that will be considered as ground (and walkable) by your characters. When in 2D and working with tilemaps, it's important that your ground's CompositeCollider2D's GeometryType be set to Polygons. You can see an example of that in multiple demo scenes across the engine, the Koala2D one for example.
-   **Obstacles** : colliders that will stop your character from walking, from getting up if they're in a tunnel, and will stop your bullets as well.
-   **MovingPlatform** : for all your moving platforms.
-   **Enemies** : put all colliders belonging to enemies (that will hurt and get hurt by your character)
-   **Hole** : for 2D only, mark colliders with this tag and characters will consider them as holes they can fall down into
-   **FallingPlatform** : for all your falling platforms
-   **Projectile** : a layer to put all projectiles colliders on
-   **Player** : the layer to put the player's colliders on
-   **ObstaclesDoors** : a special layer to put certain safety areas around 3D doors, to convey that information to the pathfinding AI
-   **NoPathfinding** : a layer to put colliders you want the pathfinding AIs to avoid

These layers, like in any Unity project, rely on the physics collision matrix to determine which ones they can interact or collide with. You can edit the collision matrix via Edit > Project Settings > Physics (or Physics2D for 2D controllers). There you'll see a matrix of checkboxes, just make sure that the intersection of the two layers you want to interact is checked. For example, if you want your Player to be able to collide with other players, make sure the Player/Player checkbox is checked.

Tags[](https://topdown-engine-docs.moremountains.com/collisions.html#tags)
--------------------------------------------------------------------------

[Tags](https://docs.unity3d.com/Manual/Tags.html) are metadata you can add to your gameobjects to find them easier from other scripts. The engine doesn't rely on tags at all. Feel free to keep using them in your scripts though!