# Guide: 3D Print a Custom Baldur's Gate 3 Character

This repository contains a guide for extracting custom character models (including equipment and pose) from Baldur's Gate 3, converting the geometry into manifold meshes, and preparing them for 3D printing.

Users should be advised that the transition from a game asset to a printable object involves significant manual labor during the repair phase.
My initial attempts required 10+ hours of cleanup; my second attempts reduced this to 3 and I'm sure I could do it even faster now.

<table>
<tbody>
    <tr>
        <td><img height="400" src="img/result/printed-ramie-1.png" alt="3D printed Tiefling character"></td>
        <td><img height="400" src="img/result/printed-t-1.png" alt="3D printed Bard character"></td>
    </tr>
</tbody>
</table>

#### Disclaimer

This guide is intended for personal use and educational purposes only.
All game assets remain the intellectual property of Larian Studios.
Do not redistribute extracted 3D files or sell prints derived from game assets.

This guide was created as personal research notes while I was figuring out how to print my characters.
Feel free to adapt and modify any steps you have more knowledge or other ideas in.
And please, open up an issue with your printed models if you end up using this guide, I'd love to see them!

## Prerequisites

Execution of this guide requires the following software and hardware.

- Windows PC
- Baldur's Gate 3 (Larian Studios)
- Ninja Ripper (covered in this tutorial, or bring your own equivalent tool)
- Blender 3.0 or higher
- 3D Printer
- Slicing Software (PrusaSlicer, Cura, Chitubox, Lychee, etc.)

## Guide Phases

Follow the documentation in the specific order listed below.

|                                                                                                                                       | Phase                                 | Description                                                                                     |
|---------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------|:------------------------------------------------------------------------------------------------|
| [<img alt="character-preparation.png" height="75" src="img/ripper/character-preparation.png"/>](ripper.md)                            | [Model Extraction](ripper.md)         | Inject an extraction tool into the running BG3 process to capture player character geometry.    |
| [<img alt="character-preparation.png" height="75" src="img/blender-import/model-inside-box.png"/>](blender-import.md)                 | [Blender Import](blender-import.md)   | Import the raw mesh data into Blender, cleaning the model, and organizing the mesh islands.     |
| [<img alt="character-preparation.png" height="75" src="img/blender-cleanup/thickening-armor-flames-before.png"/>](blender-cleanup.md) | [Blender Cleanup](blender-cleanup.md) | The core manual process of non-manifold repair, thickening surfaces, smoothening and remeshing. |
| [<img alt="character-preparation.png" height="75" src="img/printing/printing-stage-11.png"/>](printing.md)                            | [3D Printing](printing.md)            | Slicing the model and printing it on a 3D printer.                                              |

## Reference Directories

Use these paths to locate necessary files on your system.

- BG3 Save Files: `%localappdata%\Larian Studios\Baldur's Gate 3\PlayerProfiles\Public\Savegames\Story`
- Extracted Models: `%APPDATA%\Ninja Ripper`

---

[Begin Guide >](ripper.md)
