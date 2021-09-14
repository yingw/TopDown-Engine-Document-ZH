Introduction to the TopDown Engine
==================================

Welcome to the TopDown Engine Documentation. Here you'll find everything you need to know to create your own top-down game!

-   [What is the TopDown Engine?](https://topdown-engine-docs.moremountains.com/index.html#what-is-the-topdown-engine)[](https://topdown-engine-docs.moremountains.com/index.html#what-is-the-topdown-engine)
-   [I get errors after installing the package / The camera doesn't move!](https://topdown-engine-docs.moremountains.com/index.html#i-get-errors-after-installing-the-package--the-camera-doesnt-move)[](https://topdown-engine-docs.moremountains.com/index.html#i-get-errors-after-installing-the-package--the-camera-doesnt-move)
-   [What's the best way to update from an old version of the engine?](https://topdown-engine-docs.moremountains.com/index.html#whats-the-best-way-to-update-from-an-old-version-of-the-engine)[](https://topdown-engine-docs.moremountains.com/index.html#whats-the-best-way-to-update-from-an-old-version-of-the-engine)
-   [Can I use URP with the TopDown Engine?](https://topdown-engine-docs.moremountains.com/index.html#can-i-use-urp-with-the-topdown-engine)[](https://topdown-engine-docs.moremountains.com/index.html#can-i-use-urp-with-the-topdown-engine)
-   [Where do I start ?](https://topdown-engine-docs.moremountains.com/index.html#where-do-i-start-)[](https://topdown-engine-docs.moremountains.com/index.html#where-do-i-start-)

What is the TopDown Engine?[](https://topdown-engine-docs.moremountains.com/index.html#what-is-the-topdown-engine)
------------------------------------------------------------------------------------------------------------------

The TopDown Engine is a top-down framework, by the creator of the Corgi Engine, available on the [Unity Asset Store](https://assetstore.unity.com/packages/templates/systems/topdown-engine-89636?aid=1011lKhG).

It's a very fast, tight, mobile-friendly, robust and extendable engine built with **quality** and **game feel** at its core to start creating your own 2D or 3D game with a top-down perspective right now with Unity.

It's been designed to act as a foundation for **all sorts of top down games**, from dungeon crawlers like Binding of Isaac, to adventure games like old Zelda games, through beat em all like Final Fight or gun heavy games like Hotline Miami, and really **any game where the camera is positioned above the action**.

It's a fast, **production ready**, versatile, lightweight, and easy to extend solution that will help you give a serious boost to your project.

![Jekyll](https://topdown-engine-docs.moremountains.com/images/intro-1.png)

The TopDown Engine's start screen

I get errors after installing the package / The camera doesn't move![](https://topdown-engine-docs.moremountains.com/index.html#i-get-errors-after-installing-the-package--the-camera-doesnt-move)
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Are your errors related to a Unity package? Have you tried updating it to the latest version? If that doesn't solve your problem, make sure you read the install instructions included in the IMPORTANT-HOW-TO-INSTALL.txt file included within the asset. You can also check [the dedicated part of the documentation](https://topdown-engine-docs.moremountains.com/install.html).

What's the best way to update from an old version of the engine?[](https://topdown-engine-docs.moremountains.com/index.html#whats-the-best-way-to-update-from-an-old-version-of-the-engine)
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Whatever you do, make sure you have a commit / backup to rollback to** if a problem happens. Then, **remove the old TopDownEngine folder**, and import the new one. If you don't, due to the way the Asset Store importer works, some scripts may be duplicated, not removed, etc. Depending on what version you're updating from, and what version you're updating to, you may have some light refactoring to do. Make sure you check the [release notes](http://topdown-engine.moremountains.com/topdown-engine-releases) to see what changed and what may have an impact on your own code.

Can I use URP with the TopDown Engine?[](https://topdown-engine-docs.moremountains.com/index.html#can-i-use-urp-with-the-topdown-engine)
----------------------------------------------------------------------------------------------------------------------------------------

Yes, the engine doesn't do any rendering, **it'll work with any render pipeline**. The demos are made using the **Standard Render Pipeline**, as it's still the only stable one, and the most common denominator, but you can use any RP you prefer. You'll find a few steps to get you started in the [install documentation](https://topdown-engine-docs.moremountains.com/install.html#importing-the-asset-in-a-urp-project). It's recommended to have at least basic knowledge of render pipelines before picking URP or HDRP, considering the many quirks of these two render pipelines.

Where do I start ?[](https://topdown-engine-docs.moremountains.com/index.html#where-do-i-start-)
------------------------------------------------------------------------------------------------

First of all, **you don't have to read all that documentation**. The engine is built with Unity good practices in mind, and is packed with help boxes. So if this is not your first Unity project, you'll probably be ok on your own. And you can always go back here if something's not clear.

That said, you can use the **menu on the left** to get to specific places. This documentation is functional. If you have questions about the code itself, you'll rather want to have a look at [the API documentation](http://topdown-engine-docs.moremountains.com/API/). It's also recommended to look at the code's comments directly, usually they cover pretty much any question you might have.

If you want a list of features, or are wondering if this or that is included in the engine, you can have a look [at this page](http://topdown-engine.moremountains.com/). It also includes a changelog, and other useful stuff.

There are also [video tutorials on Youtube](https://www.youtube.com/playlist?list=PLl3caEhMYxQGFQ8LA5doTSkWhP2Mx84Gx).

And if all that doesn't help, you can always use the **support email link** [on the Asset's page](https://topdown-engine.moremountains.com/topdown-engine-contact).