---
date: 2018-01-11
title: Meshes
description: Learn what mesh properties are supported on 3D models imported to Decentraland.

categories:
  - 3d-modeling
type: Document
aliases:
  - /3d-modeling/meshes/
url: /creator/3d-modeling/meshes
---

3D models have a _mesh_ composed of triangular _faces_. These faces meet each other on _edges_ (the lines along which they touch) and _vertices_ (the points where their corners join).

## Scene limits

All 3D models in your scene must fit within the limits of its parcels. If they extend beyond these limits when running a preview, the meshes will be marked in red and bounding boxes will be highlighted in white.

For performance reasons, Decentraland checks the positions of the _bounding boxes_ around meshes (not the vertices in the meshes themselves) to verify that they are within the scene's limits.

If you have a model that has all of its vertices neatly inside the scene area, but that has large bounding boxes that are mostly empty and extend beyond the scene limits, the entire model will be marked as outside the scene limits.

To avoid this problem, you can clean up your 3D models to reset positions and rotations of meshes so that bounding boxes don't extend beyond the meshes they wrap.

## Smooth geometries

You can configure a mesh to be _smooth_. This tells the engine to render its shape as if there was an infinite number of intermediate faces rounding it off. This setting can greatly help you reduce the number of triangles needed to make a shape appear to be rounded.

The image below shows two identical models with the same materials. They differ in that the one on the right has most of its geometry set to _smooth_.

![](/images/media/meshes_smooth_vs_sharp.png)

Note how you can see distinct faces on all of the cylindrical shapes of the model on the left, but not on the model on the right.

This setting can be configured separately over individual _faces_, _edges_ and _vertices_ of a model. One same model could have some of its faces or edges set to _smooth_ and others to _sharp_

## Bounding boxes

Every mesh has a bounding box, that surrounds the limits of the shape. Keep in mind that the bounding boxes of all 3D models in a Decentraland scene must fit inside the scene limits, see [position entities]({{< ref "/content/creator/scenes/3d-essentials/entity-positioning.md#scene-boundaries" >}}) for more details.

![](/images/media/bounding-box.png)

To make a 3D model more usable inside decentraland, make sure that its bounding boxes don't extend beyond the model more than necessary.

For example, be cautious when rotating a sub-mesh near the border of your model. Since bounding boxes are cubes, even if the mesh is round, the corners of its bounding box might end up sticking out after rotating it 45°.

We recommend that you bake the rotation and scale of every mesh in the model, to make sure that there are no unwanted bounding boxes extending beyond the size they need to have.

## Best practices for geometries

- Be mindful of how many faces you add to your 3D models, as more faces make its rendering more demanding. See [scene limitations]({{< ref "/content/creator/scenes/optimizing/scene-limitations.md" >}}) for the limits imposed by a scene.
- Make sure there are no hidden faces that can't be seen but that add to the triangle count.
- For shapes that should have rounded sides, set them to be _smooth_ rather than adding additional faces.
- Make sure the _normals_ of all faces are facing outwards instead of inwards. If there are faces in your model that seem not to be there when you render it, this is most likely the cause.
- Bake the rotation and scale of your meshes, so that their bounding boxes don't extend out unnecessarily.
