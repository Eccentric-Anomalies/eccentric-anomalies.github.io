---
title: "New in 0.1.4: Realistic Landing Gear Physics"
date: 2024-07-04T17:35:00
categories:
  - blog
tags:
  - tungsten moon
---
The Tungsten Moon Demo, [version 0.1.4](https://github.com/Eccentric-Anomalies/Tungsten-Moon-Demo-Releases/releases/tag/0.1.4), has been released. 

From the Github releases page:

One major and several minor improvements:

Major: The landing gear model incorporates all four feet as independent damped springs, using Godot collision volumes to detect contact with any terrain surface. It should (knock wood) no longer be possible to get stuck in the ground. The landing feet no longer disappear into the landing surface during landings!

Minor:

* Four feet on the ground is a new requirement for a "safe" landing, which means it should not be possible to auto-save the landing in a situation where one foot is off the pad and the ship is tipping over.
* Position saves are rounded to prevent floating point errors from progressively building up over multiple saves. No respawn drift.
* The input configuration panel has its own "power" button to enable/disable it. This prevents accidental activation of the buttons in VR mode, and should reduce the processing load of looking at all the collision surfaces in the panel in every frame.
* The spacecraft "body" has a collision surface that will cause a "crash" if the body touches the terrain (such as when it tips over).
* The spacecraft can now tip over. The landing foot physics and center of mass make it possible to roll the craft over. Fortunately, the center of mass is low enough to prevent tipping during most landings. There is some wonkiness with collision detection on the ground, so ship that is tipping over on the ground may see one of its feet sink below the ground. The ship will "crash" in this situation.
* The landing gear spring constants have been designed to allow a landing at up to 3 m/s vertical descent rate, with a maximum gear deflection of 1 meter, at 0.9 g's of peak acceleration. Similar horizontal velocities are theoretically possible, too, but more difficult to achieve in practice. The landing difficulty is similar to what it was before.

A VERY short demo of the new functionality:

<iframe width="560" height="315" src="https://www.youtube.com/embed/-g4qKziMxRc?si=JTBYSHQIGrC-VuRJ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>