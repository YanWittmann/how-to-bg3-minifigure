# Print preparation in Blender

## Installing NinjaRipper Import Plugin

In the installation directory of NinjaRipper ([see installation guide here](ripper.md#installing-ninjaripper), e.g. `C:\Program Files (x86)\Ninja Ripper 2.8\bin64\importers`), you can find a file `io_import_nr.zip` that you can import into blender as a plugin (Preferences > Add-ons > Install).

- How to import mesh files (NinjaRipper homepage): https://www.ninjaripper.com/faq#how-do-i-import-files
- Video showing installation process of the plugin: https://www.youtube.com/watch?v=gl9wlEz82ho

## Importing the model

A new option in the `Import` setting should appear: `Ninja Ripper 2 World Space`

![import-model-dropdown.png](img/blender-import/model-dropdown.png)

Navigate to the extracted mesh directory specified in [this chapter](ripper.md#extracting-the-game-models): `%APPDATA%\Ninja Ripper\<game-dir>\<frame-dir>`

There should be a few hundreds of `.nr` files.
Since importing them all at once may not only lead to very long loading times, I've had blender crash on me if I loaded too many.
We will therefore only select the first 100-200 files (click on the first, scroll down, hold shift, click on the last you want to select) and with each attempt of finding the character model select the next batch.

Import settings:

- Position: `Reprojection (Full)`
- FOV_Y: `30` (this is the FOV you configured in the camera mode)
- Width / Height: The size of the screen you had Baldur's Gate 3 running on when running the extraction (e.g. `2560`x`1440`px)
- Flip Geometry: Checked

Finally, click on `Import Ninja Ripper 2`.

![import-configuration.png](img/blender-import/configuration.png)

The import may take a while.

If your scene does not contain all your character meshes as seen on the following image, try the next batch of files.

![import-various-scene-objects.png](img/blender-import/various-scene-objects.png)

Because the photo mode camera in game becomes the origin of the scene in blender, your character should be slightly below the scene origin:

![import-model-below-plane.png](img/blender-import/model-below-plane.png)

Simply move the model upwards until the feet are flush with the X/Y plane (`g+z`) and use the `Origin to Geometry` action to properly move the origins which will make it easier to work with later.

Each mesh *may be* overlayed by several copies of itself (was not the case every time for me).
Remove the copies of the objects.
