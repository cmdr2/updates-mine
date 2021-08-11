---
slug: nodes-system-for-geometry
date: 2021-08-10 21:02:57
tags: ['vrdesign']
title: Nodes System for Geometry
---

A Nodes-like system for all actions (geometry-wise) is probably what I'll go with. It makes sense for the use-cases I'm planning to support. Incidentally, Blender is moving in that direction too with Geometry Nodes, and Maya already works that way.

It has its advantages:
1. Simple to reason about conceptually.
2. Very flexible and powerful.
3. Good for scripting.
4. Good for non-scripting (i.e. easy to build new functionality without writing code).

But it has its disadvantages too:
1. Leads to a spaghetti (complex and messy) graph quickly, if implemented in a "pure" way (for e.g. every extrude becomes a new node).
2. Performance hit with larger graphs (in the worst case, even for minor edits).
3. The mitigation for problem #1 is to delete the history every now-and-then, but that puts the onus on the user, whereas it probably shouldn't be their concern in the first place.
4. An empty Nodes "canvas" is probably intimidating to a beginner, compared to a dialog box with editable options and buttons to click.


While it costs more from a development perspective, it makes sense to build and maintain three different "interfaces", like every other software does:
1. Dialog boxes for people who don't want to deal with nodes
2. Nodes graph editor for people who do
3. Script runner (for running scripts)

But other than basic caching of results, I don't (at present) have a simple way to manage the exploding graph problem. It seems like an inevitable outcome of using "Nodes for everything" in a very pure manner.

One solution is to make edits destructive if they're done by directly manipulating the mesh (i.e. by hand in the 3D editor), but non-destructive if done using Nodes. This would probably mitigate the performance and exploding graph complexity problem, while aligning with the user's intent (hand-modifications to the mesh in the 3D editor aren't generally expected to be non-destructive, beyond the usual undo/redo).

The other solution is to compress all user edits (made by hand) into a single UserEdit node. So then the graph can be something like `SphereGenerator -> UserEdit -> Bevel -> UserEdit -> Extrude -> Output`. That drastically reduces the number of nodes created automatically, but I don't think it really solves the problem. If I delete a single UserEdit in between, I suspect it won't always result in consistent behavior (if future Nodes depended on the user's action). Plus it'll still lead to an Extrude explosion for common modelling tasks, and the user can't delete an Extrude in the middle (since future Extrudes may rely on the verts created by it). So I don't think it really solves the problem, and can lead to inconsistent and annoying results for the user.

And like I mentioned earlier, the first solution seems to align with (my opinion) of what makes sense for the user. Editing by hand is destructive, and Nodes are non-destructive. I'll probably go with that.