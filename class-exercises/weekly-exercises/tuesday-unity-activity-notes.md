# Tuesday Unity Activity Notes

The activity we did was to get you practicing a little more with the **Translate**, **Rotate**, and **Scale** properties in Unity - all controlled by the **Transform** component \(a built-in script\) in the **Inspector** tab.

The Inspector tab gives you a visual representation of a text script. The three coordinates - X, Y, and Z are all **floating point** numbers \(precision numbers that have a decimal point\). Since it is a "float," as you move or click and drag over the letter to watch the numbers change, they change in a more precise range. On Friday, we will see the difference when we create integers \(whole numbers\) instead.

For a more in-depth look at using Translate, Rotate, and Scale, go here:

[https://hopemoore.gitbook.io/unity-basics/translate-rotate-and-scale/intro-to-transforms](https://hopemoore.gitbook.io/unity-basics/translate-rotate-and-scale/intro-to-transforms)

## Move / Translate 

**Unity Shortcut:** W key

**Move Button:**

![Located at the top left - Move button is selected here.](../../.gitbook/assets/image%20%28108%29.png)

Your object will appear to have **arrows**:

![](https://lh4.googleusercontent.com/MYoRyu8PfHN1OJNePj8Tdmc3ldxgpCHQVXzY1HXqXPdQVgkp53Z61oAKCWI1D00bJuT5mCkBjcUjj35v7nESJifh7oP3qyVObv_Cjz9gQWhgsca10yKMFWJGaprdkKsB4JzX1ykiSEM)

## Rotate

**Unity Shortcut:** E key

**Rotate Button:**

![Located at the top left - Rotate button is selected here.](../../.gitbook/assets/image%20%28103%29.png)

Your object will appear to have **circles** or **curves**:

![](https://lh6.googleusercontent.com/sDADyYNrL60x9P31LCmTfpqh7MK1yDrujuSjGXXl01E6cG1bo6RdFoKAi8KR7Q528uA7v1pHHURwbQMKk4qBDdDnrT3LH0RhcdCXXaNJvZIdooZig8NkRsv27t1gq6dXUGfw5Wskc-U)

## Scale

**Unity Shortcut:** R key

**Scale Button:**

![Located at the top left - Scale button is selected here.](../../.gitbook/assets/image%20%28106%29.png)

 Your object will appear to have **blocks** at the end of lines:

![](https://lh4.googleusercontent.com/97hlsLObtgBi7Tmk3NERJFOhgtg4Nd0-RFOPfLlb_m8NEXN7W3Br-nOVEH6h_ufgEVBEbP_SVxc4Sv2uKMJfrVD7vbONdYyz9C_bWMWFP1ZCND7xmuqzU_D7W5ErdheEgo8W7gnmv0M)

## Rigidbody Component

By default, objects will not move when the game is played. The objects can also overlap. 

Adding a **Rigidbody** component will give the object simulated gravity and will use the object's **Collider** component to know where the edges of the objects are. This makes overlapping items with this component explode! It also allows objects to fall and affect those around them.

Add a built-in component through the **Inspector** window:

![Inspector window for an example cube.](../../.gitbook/assets/image%20%2890%29.png)

Click the **Add Component** button.

![](../../.gitbook/assets/image%20%28111%29.png)

Use the dropdown menu items to navigate to Physics &gt; Rigidbody OR use the search and start typing the name of the component to find it:

![](../../.gitbook/assets/image%20%2894%29.png)

Click on the component to add it and it will appear in the Inspector window:

![The component appears at the bottom of the list of attached components.](../../.gitbook/assets/image%20%28117%29.png)

## Creating a Material

Materials are separate, REUSABLE "objects" \(called **Assets**\) in Unity that you create and then add to other game objects in your scene. 

### **Step 1: Create a Material**

Your **Project** window is a visual representation of your project folder. It shows you your files in your **Assets** folder.

Right-click in your Project window and select Create &gt; Material

![](../../.gitbook/assets/image%20%2899%29.png)

This will create a new material, which you can name.

![](../../.gitbook/assets/image%20%28105%29.png)

This name can include spaces.

I named this "Blue Materia." \(Yes, that was an accident and I didn't feel like changing it for this page.\)

![](../../.gitbook/assets/image%20%2895%29.png)

### **Step 2: Modify a Material**

Once selected, the properties of the material will appear in the **Inspector** window:

![](../../.gitbook/assets/image%20%28102%29.png)

Here, you can change different aspects of the material. We'll just change the color here by clicking on the white square next to "Albedo."

![](../../.gitbook/assets/image%20%2893%29.png)

Click first on the **Hue** \(color\) in the circle, then on the square to choose your **Saturation** \(intensity\) and **Value** \(brightness\) of that color.

![Example of a type of blue.](../../.gitbook/assets/image%20%28113%29.png)

Hit the ENTER key or close the color wheel popup. This will update the material.

![](../../.gitbook/assets/image%20%2896%29.png)

### Step 3: Adding a Material to an Object

Unity's best feature is its click-and-drag capability. To add your material to an object in your scene, click and drag your material from your **Project** window to the object in your **Scene** window OR **Hierarchy** window.

![](../../.gitbook/assets/addingmaterials.gif)

When it has been added, not only will you be able to see it update in the Scene window, but you can also see the Material component update at the bottom of the **Inspector** window.

![](../../.gitbook/assets/image%20%2887%29.png)

{% hint style="danger" %}
Remember: When you update the properties of an asset in the **Project** window, it updates it for ALL objects the asset is added to.
{% endhint %}

