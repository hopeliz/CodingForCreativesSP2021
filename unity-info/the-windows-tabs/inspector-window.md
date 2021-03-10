---
description: All the details of your assets and items
---

# Inspector Window

One of the most important windows, the Inspector shows all the components and attributes of a selected game object or Asset.

## Default View

The information in the Inspector window changes depending on what game objects and assets you have selected.

Example of a default sphere **game object** when selected in the Hierarchy window:

![](../../.gitbook/assets/image%20%2847%29.png)

Example of a default empty game object when selected in the Hierarchy window:

![](../../.gitbook/assets/image%20%2814%29.png)

Example of a Main Camera **game object** when selected in the Hierarchy window:

![](../../.gitbook/assets/image%20%2819%29.png)

Example of a directional light **game object** when selected in the Hierarchy window:

![](../../.gitbook/assets/image%20%2829%29.png)

Example of a material **asset** when selected in the Project window:

![](../../.gitbook/assets/image%20%2873%29.png)

## Game Object Header Information

![](../../.gitbook/assets/image%20%287%29.png)

The header generally shows the following elements for selected game objects:

**Icon, Label, or Gizmo** - represents the type of game object. Click on this icon to change it.

**Active \(checkbox\)** - objects can be turned on and off  
Notes:

* Shortcut:   ALT + SHIFT + A  
* Scripts trying to access inactive objects will give you an error.

**Game object name** - Can be updated within the Inspector window

**Static \(checkbox\)** - Whether the object is Static and the type of static. Click on "Static" to see more options.

**Tag** **\(Dropdown\)** - Tags can be added or selected from a list to help with organization and access through a script.

**Layer \(Dropdown\)** - Layers can help a script determine how elements interact with certain objects.

## Asset Header Information

![](../../.gitbook/assets/image%20%2838%29.png)

![](../../.gitbook/assets/image%20%2859%29.png)

The header generally shows the following elements for selected assets:

**Icon / Preview** representing the type of asset

**Name** - This can be changed in the Project window or within the Assets folder

**Connection to other assets** - Some assets use other assets \(materials use shaders\) and will have a reference to it.

**Commands \(Buttons\)** - Open folders, prefabs, and scripts.

## Transform Component

You'll notice that every game object in your scene has a _Transform_ component that stores coordinates for the object's position, rotation, and scale.

## Components

Components are really just pieces of script that you can add, update, and remove from game objects. Many have default built-in components so you do not have to write them yourself. They are even accessible by other scripts!

Components will not be covered in depth here, so please use the Unity documentation for specific details.

Let's look at some common elements of a component as it appears in the Inspector window:

![](../../.gitbook/assets/image%20%282%29.png)

Components can pile up in the Inspector window, so there are dropdown toggle triangles on the left. You can use these to collapse the entire component or sections of attributes.

Many components allow you to turn them off and on by using the checkbox to the left of the component name.

**Note:** Scripts will give an error if they are trying to access a component that has been turned off.

## Add Component Button

![](../../.gitbook/assets/image%20%2845%29.png)

At the bottom of the list of components, there's an "Add Component" button. This provides a list of current built-in and user-created components to add. You can also create a new script through this menu and it will automatically appear on that game object after naming it.

## Extras for Assets

Many assets have previews within the Inspector window at the bottom.

![](../../.gitbook/assets/image%20%2861%29.png)

The preview allows you to preview materials, videos, audio, and animation.

The blue "label" icon on the right allows you to label your assets with one or more labels.

For information on Asset Bundles, please see the [Unity documentation](https://docs.unity3d.com/ScriptReference/AssetBundle.html).

## Still lost?

Use the icons seen on the top right of components and parameters for Unity documentation, presets, and settings:

![](../../.gitbook/assets/image%20%2821%29.png)

