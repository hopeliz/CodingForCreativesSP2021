# Popular SOPs

Surface operators \(SOPs\) are colored blue and manipulate 3D objects.

![](../.gitbook/assets/td-op-create-dialog-full-sop.png)

## Extra for 3D

For 3D scenes, you'll need the following:

* Light COMP
* Camera COMP
* Geometry COMP \(see below how to do this with pre-existing 3D objects\)
* Render Top

Adding each will set them up without adding more connections.

### Make a Geometry COMP from your SOP

![](../.gitbook/assets/tdgeocomp.gif)

How it should look when everything is added:

![](../.gitbook/assets/geometry.png)

## Basics

### Null SOP

Provides a snapshot of sorts of a point within your network. Commonly used to help look at the effects of major changes later and remove them easily when necessary.

![](../.gitbook/assets/null-sop.png)

### Noise SOP

For when you want some randomness.

![](../.gitbook/assets/tdnoisesop.gif)

### Switch SOP

Takes in multiple surface operators \(SOPS\) and creates an array. A single element of the array can be accessed by the Switch SOP's Index parameter.

![](../.gitbook/assets/switch-sop.png)

### Select SOP

Provides a visual "copy" that references another surface operator. This is great for large projects where you are referencing SOPs in other areas far from the one you need it for.

Click and drag the original SOP into the Select SOP or type in the original SOP's name in the Select SOP's parameter.

![](../.gitbook/assets/select-sop.png)

## Shapes / Primitives / Transforms

### Box SOP, Sphere SOP, Torus SOP, Text SOP

Creates 3D shapes or text.

![](../.gitbook/assets/shape-sop.png)

### Transform SOP

Manipulates position, rotation, scale, etc.

![](../.gitbook/assets/transform-sop.png)

