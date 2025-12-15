# Print preparation in Blender

This is where the long, tedious part of the process starts.
We need to ensure the model is clean for 3D printing.

The central concept you must understand for this phase is manifold geometry.
For a 3D model to be printable, it must be manifold, meaning it forms a strictly enclosed volume.
In a mathematically correct manifold mesh, **every** edge connects exactly two faces, which allows for the clear calculation of the inside and the outside volume of the object.

Video game assets are designed to look good from specific camera angles and use various visual tricks to simulate depth and detail.
They consist of zero-thickness surfaces and frequently contain intersecting geometry that does not physically connect.
To a 3D printer slicing software, these assets are essentially unintelligible.

Beyond fixing the topology, we must also adapt the physical properties of the mesh for the real world.
Elements like hair strands, loose cloth, or thin armor plating often exist as two-dimensional planes or very thin objects in the game.
These need to be solidified and extruded to have physical thickness to exist as plastic.
Furthermore, microscopic details that look great on a monitor must often be simplified or exaggerated, as they may be smaller than the physical resolution of your printer nozzle.

The objects may look correct in Blender or in the Slicer object view.
However, if you attempt to slice the model directly after import, you will likely encounter missing layers, floating artifacts, or complete structural failure.

<table>
<tbody>
<tr>
<td><img alt="broken-model-slices-1.png" src="img/printing/broken-model-1.png"/></td>
<td><img alt="broken-model-slices-2.png" src="img/printing/broken-model-2.png"/></td>
</tr>
<tr>
<td>The mesh looks good when viewed in the model view.</td>
<td>Slicing it reveals missing layers everywhere.</td>
</tr>
<tr>
<td><img alt="broken-model-slices-3.png" src="img/printing/broken-model-3.png"/></td>
<td><img alt="broken-model-slices-4.jpg" src="img/printing/broken-model-4.jpg" height="450"/></td>
</tr>
<tr>
<td>Attempting to use several pieces of automated 3D-printing fixing software did not result in a usable mesh.</td>
<td>Small hidden broken meshes may reveal themselves only upon closer inspection, so find them before you print!</td>
</tr>
</tbody>
</table>

This chapter covers the manual process of converting these hollow surfaces into a single, printable solid.
While automated repair tools exist, they frequently destroy the specific details required for a character figure or fail to resolve the complex internal geometry of game rips.
We will manually close gaps, merge mesh islands, and enforce manifold geometry to ensure structural integrity.

## Before we start

Before we start:

- resize your object to be a little smaller to avoid object culling issues later
- right side > view (n) > clip start > something like 0.001m
- viewport overlays > face orientation
- join the most relevant objects into single objects (body, shield, weapon, cape) individually
- on the individual objects, select islands that should belong together and merge vertecies by distance.
  in my experience, you should be a bit careful with this, as you will end up merging islands that do not belong
  together.
  it will make your life easier and harder in some parts; maybe just try out manually selecting islands and then merging
  vertecies, idk.
- edit mode recalculate outside (do this every now and then on the individual models)

For each object:

- select individual object
- ctrl+i, h, numpad delete to focus on object
- enter edit mode

To select all islands that have non manifold geometry:

- "select" > "by trait" > "non manifold" (this is what we are after)
- ctrl+l, ctrl+i, h

If you have islands that you would not expect to connect:

- select one island, ctrl-click on the other --> shortest path between

To quickly fill an entire area either of the area type:

- large area surrounded by a clear edge boundary: alt-click on the edge and press f --> triangulate faces (ctrl+t)
- small irregular portions: click one (smart, order matters) or three (explicit) vertecies and press f
- bridge edge loops

If you work in a tight space, you can always hide one half of the model to view the inside of the other

Hair:

- solidify (choose value yourself)
- decimate (around .5)
- save before applying
- apply both
- it does not matter if you have non-manifold here, it's going to be dense enough anyways

And now time to prepare the model for 3D printing:

- all thin or small parts, make them thicker or larger, alt+s is good for most
- move the shoes in a way that the character stands firm on the ground, potentially make them larger to ensure good
  footing
    - tieflings already have a resting support lol (I didn't use it though)
- don't forget that proportional editing exists
- edit identical islands at the same time (ctrl+l on all) with individual origins
- and so on idk.

Smoothen out certain parts:

- you can select the object you want to have subdivided to be smoother and enter edit mode
- select > sharp edges > 25° (depends on the model)
- right side > Item > Edges Data > Mean Crease > 1.0
- object mode add subdivision modifier (1, 2, 3 levels idk)
- apply (maybe only later when you really need it)
