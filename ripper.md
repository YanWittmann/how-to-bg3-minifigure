> [!IMPORTANT]
> The author of this guide is not affiliated with "NinjaRipper".

> [!CAUTION]
> Attention: the program "NinjaRipper" is intended only for research of the places of the levels of games located "behind" the camera and does not pursue the goal of piracy.

---

# Chapter 1: Obtaining the 3D Model

[Main Page](readme.md) &bullet; [Blender Import >](blender-import.md)

This section covers the setup of the extraction software, preparing the in-game scene, and executing the geometry capture.

## Installing NinjaRipper

This workflow relies on **NinjaRipper 2.x**.
This software is currently behind a paywall.

- Cost: [€4.50 (one-time Patreon subscription)](https://www.patreon.com/ninjaripper)
- Download: [NinjaRipper Website](https://www.ninjaripper.com)

You will keep access to versions of the software you were subscribed for without limitation if you unsubscribe.
After installation, launching the software will open a browser window to authenticate your license.

If you are in possession of a different software that is able to perform a similar task, you may use it instead.

## Configuration

Ensure your settings match the configuration below.
The defaults usually work.
The "Rip Duration" may need adjustment if large scenes fail to extract completely.

<img alt="The &#39;Output Settings&#39; section in the image shows a dropdown menu labeled &#39;Save Textures,&#39; which is set to &#39;DDS.&#39; This setting determines how textures are saved during the ripping process, with DDS being a common format used by many games and game engines." height="500" src="img/ripper/settings.png"/>

Then, configure the path to the game executable and directory.

<img alt="This image shows the executable path and working directory settings in the Ninja Ripper tool, which are used to configure the game&#39;s launch process." height="150" src="img/ripper/launch-screen.png"/>

## Launching the game

Ensure that Steam or any other launcher you installed the game with is not started on your computer.
Then, use the "Launch" button to start the game.

The game will tell you that you are not logged into your account, which is completely fine.

<img alt="A login button with a blue and gold color scheme is displayed, prompting users to log in to their account." height="150" src="img/ripper/game-not-logged-in.png"/>

Verify the hook was successful by looking for the NinjaRipper overlay in the top-left corner of the game window.

![The image shows a green text overlay with the message 'NR 2.8 D3D11 Press PrintScr/Insert Frame: 127503 (FPS: 30)'.](img/ripper/ninjaripper-overlay.png)

## Scene Setup

Load the save file you want to extract the character model from.

You will likely be located in one of the large overworld areas of the game.
However, having the game load so many models at once will not only make the ripping process take much longer later, it will also make finding the correct model files in the export later a lot harder.

So, navigate to any cellar, cave or other small subarea in which you are shown a short blackout loading screen.
Only take your character there that you want to get the model from, leave the rest of your party outside.
Place them on a flat surface with space around them to make it easier to find and work with later.

![A grid-based map of a cellar, likely used to plan and navigate through the space during character preparation for modeling.](img/ripper/cellar-map.png)

## Character Setup

Equip the armor, weapons, and accessories exactly as you want them to appear on the print. The geometry is extracted "What You See Is What You Get."

With your scene prepared, you must choose a pose for the character to have in the export.
Since we will be switching to photo mode later on anyway, you can also pick any of the poses and expressions from there.

A bit of inspiration:

- Melee attacks
- Casting a spell
- Sitting on a chair
- Doing one of the photo mode poses
- etc.

This is a good time to save your game, just in case any of the next steps crash the game or time it out.

<img alt="The image shows a character preparation menu in a video game, where the player can select and customize their character&#39;s abilities and equipment before entering combat." height="300" src="img/ripper/character-preparation.png"/>

## Extracting the game models

If you haven't already: Activate photo mode using `F9`.

Since the extraction of the models is relative to the camera screen space, we will have to prepare the camera in this special way to make our lives a lot easier later.
Enabling camera mode will allow us to control the camera exactly as we want.
Also, the models might be more detailed in photo mode, but I was unable to confirm this.
Since the game culls objects and model parts that are not visible, we need to position the camera in a way that the entire character is on the screen at once.

- Set FOV to 30
- Place camera right above your character
- Look straight downwards

You should also note down the size of the screen in pixels on which you perform this extraction on.
We will need it later.

This is what it should look like:

![The image shows a screenshot of the photo mode in BG3 showing  a top-down view of the character and the FOV being set to 30..](img/ripper/photo-mode-setup.png)

Then, press the key as indicated by the NinjaRipper overlay in the top left.
This might be different depending on your configuration of the software.
For me, it's `PrintScr`.
This will start the model extraction, which might take **a long time** depending on the scene size and compute power available.
For me, it's roughly two or three minutes.

You can view the models being extracted in real time if you observe `%APPDATA%\Ninja Ripper` (or press the button in the NinjaRipper UI).
Enter the directory named similar to `2025.12.10_17.46.28_bg3_dx11.exe_2888` and view the `frame_0` directory.
Each new extraction will create a new `frame_n` directory.

In this, you will have a directory full of numbered files like `mesh_148.nr` that contain the meshes of the models that were loaded in the game.

---

[Main Page](readme.md) &bullet; [Blender Import >](blender-import.md)
