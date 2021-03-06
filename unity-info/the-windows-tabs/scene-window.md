---
description: A way to see all of your scene
---

# Scene Window

This window shows your scene overall.

**Note:** The viewpoint could look different on your computer.

## Up Close

The default Scene window will have what they call a Skybox \(the environment that looks like a horizon, sky, and sun\) and Gizmos \(symbols representing non-physical objects\) for the Main Camera and the Directional Light.

![](../../.gitbook/assets/image%20%2846%29.png)

## Movement and Viewpoint

### Changing the Viewpoint

To rotate the view around the center of the scene, hold ALT and click and drag your mouse holding down the left-click button.

To rotate the scene view camera, click and drag your mouse holding down the right-click button.

To move the whole view, hold the scroll wheel on your mouse and drag the view.

To zoom in and out, scroll the scroll wheel or hold ALT and click and drag your mouse holding down the right-click button.

### Using the Scene Gizmo

The thing in the top right of the tab is called the Scene Gizmo. It gives you a reference about which direction is x, y, or z.

The default view is the perspective view that provides a sense of depth. If you want an isometric or orthographic view to help with lining up objects, etc., click on the area below the gizmo \("Persp" in the example\) to toggle between the views. Perspective views will have the arrow/depth symbol and isometric views will have three straight lines.

Want a view directly from one of the directions? Click on the desired handle to go to the isometric view from that vector.

![](../../.gitbook/assets/image%20%2823%29.png)

![](../../.gitbook/assets/image%20%2850%29.png)

The lock symbol keeps the view from rotating. It will still allow you to move the whole view.

## Options

The dropdown at the top left of the window provides more options for how to view things within the scene. The default Shading Mode is "Shaded." This tutorial will not go in-depth about these options. Please see the links for Unity's documentation.

![](../../.gitbook/assets/image%20%2833%29.png)

### Toggle Options

![](../../.gitbook/assets/image%20%2811%29.png)

**2D** - Toggles between 2D and 3D

**Scene Lighting** - when on, the lights added to the scene are active

**Audio** - toggle audio on and off

**Effects** - Toggle multiple effects in the scene

![](../../.gitbook/assets/image%20%2860%29.png)

**Hidden Objects** - When objects are hidden in the [Hierarchy ](hierarchy-window.md)window, the count shows here. Clicking this symbol in the Scene Tab toggles the visibility of the hidden objects. They will remain listed as hidden within the Hierarchy Tab.

**Grid Options** - Adjust how and if the grid is visible in the Scene Tab

![](../../.gitbook/assets/image%20%2827%29.png)

### Options on the Top Right Side of the Tab

![](../../.gitbook/assets/image%20%2880%29.png)

**Tool Display** - Toggles the visibility of tools within the Scene Tab

**Scene View Camera Settings** - Where you can adjust how the Scene View Camera appears and behaves

![](../../.gitbook/assets/image%20%2816%29.png)

Please see the links to access the Unity documentation for more in-depth info about these settings.

**Gizmo Options** - Where you can toggle gizmos for items on and off

![](../../.gitbook/assets/image%20%284%29.png)

The slider at the top adjusts the size of the visible gizmos. 

Please see the links to access the Unity documentation for more in-depth info about these options.

## Search

When typing in a search term, the matching items will be listed in the Hierarchy window and the Scene window will appear to get whiter. Click the X to clear the search quickly.

![](../../.gitbook/assets/image%20%2826%29.png)

## More Tools Outside of the Tab

These tools are available at the top left of the window in all layouts and are primarily used in the Scene window.

![](../../.gitbook/assets/image%20%2849%29.png)

**Hand Tool** - Move around the scene without accidentally moving a selected object

**Move Tool** - Move selected objects on an x \(red\), y \(green\), and z \(blue\) axes

**Rotate Tool** - Rotate selected objects on an x \(red\), y \(green\), and z \(blue\) axes

**Scale Tool** - Scale selected objects on an x \(red\), y \(green\), and z \(blue\) axes

**Rect Tool** - Usually for 2D game objects, move, rotate, and scale selected objects on x and y axes

**Transform Tool** - Move, rotate, and scales selected objects on an x \(red\), y \(green\), and z \(blue\) axes \(equivalent to having the Move, Rotate, and Scale tools on at the same time\)

**Custom Tools** - Access custom tools, if available

**Center/Pivot Toggle** - For parenting objects, this allows you to choose between rotating on an axis that goes through the parenting object or the center of all the objects together

**Global/Local Toggle** - Choose whether to change the values locally \(in relation to a parent object\) or globally \(in relation to the scene\)

