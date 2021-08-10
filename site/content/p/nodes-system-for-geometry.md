---
slug: nodes-system-for-geometry
date: 2021-08-10 21:02:57
tags: ['vrdesign']
title: Nodes System for Geometry
---

A Nodes-like system for all actions (geometry-wise) is probably what I'll go with. It makes sense for the use-cases I'm planning to support. Incidentally, Blender [1] is moving in that direction too with Geometry Nodes, and Maya [2][3] already works that way.

It has its advantages:
1. Simple to reason about conceptually.
2. Very flexible and powerful.
3. Good for scripting.
4. Good for non-scripting (i.e. easy to build new functionality without writing code).

But it has its disadvantages too:
1. Leads to a spaghetti (complex and messy) graph quickly, if implemented in a "pure" way (for e.g. every extrude becomes a new node, like in Maya).
2. Performance hit with larger graphs (in the worst case, even for minor edits).
3. The mitigation for problem #1 is to delete the history every now-and-then, but that puts the onus on the user, whereas it probably shouldn't be their concern in the first place.
4. An empty Nodes "canvas" is probably intimidating to a beginner, compared to a dialog box with editable options and buttons to click.


While it costs more from a development perspective, it makes sense to build and maintain three different "interfaces", like every other software does:
1. Dialog boxes for people who don't want to deal with nodes
2. Nodes graph editor for people who do
3. Script runner (for running scripts)

But other than basic caching of results, I don't (at present) have a simple way to manage the exploding graph problem. It seems like an inevitable outcome of using "Nodes for everything" in a very pure manner.

One solution is to make edits destructive if they're done by directly manipulating the mesh by hand (in the 3D editor), but non-destructive if done using Nodes. This is similar to how Blender's mesh edits are destructive in the editor, but a modifier (or a Geometry Node) is non-destructive.

This would probably mitigate the performance and exploding graph complexity problem, while aligning with the user's intent (hand-modifications to the mesh in the 3D editor aren't generally expected to be non-destructive, beyond the usual undo/redo).

References:
[1] Geometry Nodes in Blender - https://developer.blender.org/T74967
[2] Maya DAG - https://help.autodesk.com/view/MAYAUL/2017/ENU/?guid=__files_DAG_Hierarchy_Overview_of_the_DAG_Hierarchy_htm
[3] Maya DAG - https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2022/ENU/Maya-Basics/files/GUID-5029CF89-D420-4236-A7CF-884610828B70-htm.html