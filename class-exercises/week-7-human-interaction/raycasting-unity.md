# Raycasting \(Unity\)

This activity uses Unity 2020.2 and all code should allow you to copy and paste.

## Raycasting

Raycasting is a powerful way \(just like collisions\) to get and update information about an object in Unity.

This activity is a VERY simple example, but this method of having Raycasting from the camera is used in first-person video games and experiences. Rays can be cast from objects as well \(aiming weapons/tools, having code run when an NPC \(non-player character\) is looking at an object, etc.\)

## Starter Scripts

To save time, please download these scripts to help with the movement of the camera.

{% file src="../../.gitbook/assets/firstpersoncameracontrols.zip" caption="firstPersonCameraControls.zip" %}

Inside this file:

**PlayerMovement.cs** - Uses WASD controls to move in directions relative to the object it is attached to. Can be used with other player objects as well.

**RotateCamera.cs** - A script I found years ago and have since modified that uses your mouse to look around. It might not be the most efficient, but it's good for testing other scripts. I also added a code for making the cursor hidden since the rotation will not match and this throws off the user. This, however, doesn't seem to work within Unity for Unity 2020.2 and newer.

## Step 1: Create and Set Up a New Scene

Open a previous Unity project file or create a new one.

{% hint style="info" %}
The layout in these examples uses a custom layout so both the Scene and Game windows can be viewed at the same time as well as having the Console visible. You can move the tabs and windows around by clicking and dragging the tabs.
{% endhint %}

### Create a New Scene

Create a new scene in your Project window/tab by going to the default **Scenes** folder, then right-click and choose Create &gt; Scene.

![](../../.gitbook/assets/image%20%28327%29.png)

Name your scene. I named this one "Looking at Things."

![](../../.gitbook/assets/image%20%28251%29.png)

Double-click on the new scene. This will open the scene in the Hierarchy, Scene, and Game windows.

The name of the scene will be at the top of the Hierarchy window. A scene will have a Main Camera and Directional Light by default. 

![](../../.gitbook/assets/image%20%28351%29.png)

### Add the Starter Codes

Once you have downloaded and unpacked/extracted the files from the zip files, click and drag them into your Assets folder or a Scripts subfolder in the **Project** window. This will make copies in your Unity project.

![](../../.gitbook/assets/image%20%28278%29.png)

## Step 2: Add Starter Scripts to Your Camera

You can:

**Option 1:** Click and drag the scripts onto the Main Camera object in the Hierarchy window

**Option 2:** Select the Main Camera in the Hierarchy window, bringing up the information in the Inspector window. Click and drag the scripts into the Inspector window

**Option 3:** Select the Main Camera in the Hierarchy window, bringing up the information in the Inspector window. Click the **Add Component** button and search for the scripts to add them.

![](../../.gitbook/assets/image%20%28344%29.png)

When added correctly, the scripts will appear as components:

![](../../.gitbook/assets/image%20%28339%29.png)

You can test the scene by pressing play, but it won't look like much without anything in the scene to show relative distance.

## Step 3: Add Objects

Objects here are just examples to test our Raycasting. When developing projects, simple things are used to test code before using the script in more detailed environments.

I will use a sphere and a cube, but you can use any other primitive 3D shape.

To add a 3D primitive shape object, right-click in the Hierarchy window and select 3D Object and one of the first five shapes.

![](../../.gitbook/assets/image%20%28269%29.png)

Reset the location of your objects by selecting them and right-clicking on the Transform component in the Inspector window and select **Reset**.

![](../../.gitbook/assets/image%20%28277%29.png)

Resetting the transform will put the objects at \(0, 0, 0\).

Rename your objects by right-clicking and selecting Rename.

![](../../.gitbook/assets/image%20%28268%29.png)

Move your objects with the **Move Tool**. Press W for a shortcut or click on the Move Tool button on the top left:

![](../../.gitbook/assets/image%20%28305%29.png)

You will want to move them closer to the camera and along the same horizon.

![](../../.gitbook/assets/image%20%28257%29.png)

{% hint style="info" %}
Your Scene window might be looking at your scene from a different angle than your Game window. The quickest way to get it to be the same direction, click on the red X end of the gizmo on the top right of your screen to make the cone get bigger on the right \(as pictured\).
{% endhint %}

You can test the scene now and it is best when viewed with **Maximize On Play** is on. Press ESC to bring the mouse back to stop playing.

![](../../.gitbook/assets/raycasting-01.gif)

## Step 4: Add a User Interface

One form of a user interface appears as a dot in the center of the screen that changes when the ray hits something, often with an added prompt \(what will happen when the player presses a button\).

We can do this with UI \(User Interface\) objects.

Start with a **Canvas** by right-clicking and selecting UI &gt; Canvas.

![](../../.gitbook/assets/image%20%28323%29.png)

This will also load an EventSystem.

![](../../.gitbook/assets/image%20%28324%29.png)

By default, the Render Mode is in Screen Space - Overlay so what is on this canvas appears as an overlay of the entire screen. However, in the Scene window, this canvas looks HUGE.

![](../../.gitbook/assets/raycasting-02.gif)

The good news is that the elements can be positioned with the move tool, making it easy to move them.

Add a **Panel** object. \(Create &gt; Panel\)

![](../../.gitbook/assets/image%20%28253%29.png)

This should create it as a child object of the Canvas object:

![](../../.gitbook/assets/image%20%28326%29.png)

The Source Image of the Panel is background by default and appears as a gray overlay.

Select the Panel object. In the Inspector window, you'll see that the Source Image of the Panel is background by default and appears as a gray overlay.

![](../../.gitbook/assets/image%20%28296%29.png)

This changes the image to a circle. However, it appears as an ellipse because it's trying to match the screen's aspect ratio.

![](../../.gitbook/assets/image%20%28284%29.png)

In the Inspector window, select **Preserve Aspect** under _Image Type_ so that it is checked.

![](../../.gitbook/assets/image%20%28289%29.png)

This will make the circle keep its shape in differently sized screens.

![](../../.gitbook/assets/image%20%28258%29%20%281%29.png)

Use the Scale Tool to make the circle SUPER tiny - almost dot-like.

![](../../.gitbook/assets/image%20%28320%29.png)

![](../../.gitbook/assets/image%20%28299%29.png)

Size of my dot in the Scene window \(color change to gray so you can see the size\):

![](../../.gitbook/assets/image%20%28256%29.png)

Select the Panel in the Hierarchy window and duplicate \(right-click &gt; Duplicate or CTRL+D\) the object.

Select the new Panel \(1\) and use the Scale Tool to make the dot slightly, but noticeably larger.

![Color changed to gray to be visible.](../../.gitbook/assets/image%20%28306%29.png)

Rename your Panel object to Default Dot and Panel \(1\) to Interact Dot.

![](../../.gitbook/assets/image%20%28244%29.png)

Add a Text UI object \(Right-click &gt; UI &gt; Text\).

![](../../.gitbook/assets/image%20%28310%29.png)

Rename it to Prompt Text.

![](../../.gitbook/assets/image%20%28313%29.png)

The default text says, "New Text" and will place a text object in the center of the screen. It will appear off to the left because it is left-aligned.

In the Inspector window in the **Text** component:

* Change the **alignment** under _Paragraph_ to Center-Center
* Change "New Text" to "Interact"
* Change the color to something more noticeable than Dark Gray.

![](../../.gitbook/assets/image%20%28342%29.png)

Use the Move Tool to move the text down off of the dots.

![](../../.gitbook/assets/image%20%28247%29.png)

![The text is just under the dots.](../../.gitbook/assets/image%20%28350%29.png)

## Step 5: Creating a Raycasting Script

Now, we'll write a script that sends an invisible "ray" or line from one position, in a direction and get information about whatever it hits.

Create a new C\# script by right-clicking in the Project window and selecting Create &gt; C\# Script.

![](../../.gitbook/assets/image%20%28325%29.png)

Name it something like RaycastingTest.

![](../../.gitbook/assets/image%20%28338%29.png)

Double-click the file to open it in Visual Studio.

We will be accessing and updating UI elements, so we need to include the library for `UI`. Add this to the top of the script immediately after using `UnityEngine;` and before the code for the class.

```csharp
using UnityEngine.UI;
```

We want the UI to change if our ray hits something so create variables for:

* default dot \(GameObject\)
* interact dot \(GameObject\)
* prompt text object \(GameObject\)
* prompt text message \(Text\)

```csharp
public GameObject defaultDot;
public GameObject interactDot;
public GameObject promptTextObject;
public Text promptText;
```

In the `Update()` function, create a variable for the object that is hit's information. 

We want to put it in an if statement to have things happen ONLY when the ray hits something.

```csharp
if (Physics.Raycast(transform.position, transform.TransformDirection(Vector3.forward), out RaycastHit hit, 5))
{

}
```

About this line of code:

* Raycasting is part of the Physics class that controls all the physics calculations and functions
* `Physics.Raycast()` can take different numbers of arguments to help determine the position, direction, distance, layer, etc. Details appear once you start typing the beginning parenthesis in Visual Studio.
* `out` is a way of putting information into a variable - we'll call it `hit`.
* The Transform component will have a built-in function that can determine a direction from the object the transform component is on

The function used here is `Physics.Raycast(Ray ray, out RaycastHit hitInfo, float maxDistance)`

The Ray includes the beginning position and direction of the ray.

{% hint style="info" %}
You'll notice I didn't have `== true` in the if statement test. It is not needed since it is testing for true or false and having `== true` is like asking if `true == true`.
{% endhint %}

Have the dots switch to the larger dot when true and smaller dot when false. Also, have the prompt only when the ray is hitting something. We can use `GameObject.SetActive()` to toggle the availability of a game object.

```csharp
void Update()
{

    if (Physics.Raycast(transform.position, transform.TransformDirection(Vector3.forward), out RaycastHit hit, 5))
    {
        defaultDot.SetActive(false);    // Turns off Default Dot
        interactDot.SetActive(true);    // Turns on Interact Dot
        promptTextObject.SetActive(true);   // Turns on the prompt text object
    }
    else
    {
        defaultDot.SetActive(true);    // Turns on Default Dot
        interactDot.SetActive(false);    // Turns off Interact Dot
        promptTextObject.SetActive(false);   // Turns off the prompt text object
    }
}
```

Save your script and return to Unity.

Add your RaycastingTest script to your **Main Camera** object. \(click and drag or use the **Add Component** button\)

![](../../.gitbook/assets/image%20%28281%29.png)

The new component will appear like this when Main Camera is selected:

![](../../.gitbook/assets/image%20%28331%29.png)

Update these fields using the click and drag method \(from Hierarchy to the fields in Inspector\) or click on the target/bull's eye icon for each. **Prompt Text** will be the object for both Prompt Text Object and Prompt Text.

![](../../.gitbook/assets/image%20%28287%29.png)

Now, test it and see if the dot changes and the text appears when close enough to an object and looking at it.

![](../../.gitbook/assets/raycasting-03.gif)

## Step 6: Affecting Individual Objects

Let's make each object act independently. There will be times when you will need to change things the ray is hitting instead of all objects. You might not have the information to store and control until after the program is running. The ray will get the information it is interacting with/hitting.

I want to make the object I'm looking at get bigger when when I click the left mouse button and smaller with the right.

### Adding Interaction

Let's use if statements to check for button presses.

I'll use `Input.GetKeyDown(KeyCode key)` to run code the frame the key is first pressed. To run the code again, I'll need to release the key and press it again. I don't know the key code of the letters, so I access it by going through the KeyCode library.

We can access the object we are hitting by getting the object stored in the variable `hit` and accessing its Transform component.

```csharp
if (Input.GetKeyDown(KeyCode.B))
{
    // Make hit object larger by 125 percent
    hit.transform.localScale *= 1.25F;
}

if (Input.GetKeyDown(KeyCode.N))
{
    // Make hit object smaller by 75 percent
    hit.transform.localScale *= 0.75F;
}
```

Full code so far:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class RaycastingTest : MonoBehaviour
{
    public GameObject defaultDot;
    public GameObject interactDot;
    public GameObject promptTextObject;
    public Text promptText;

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        if (Physics.Raycast(transform.position, transform.TransformDirection(Vector3.forward), out RaycastHit hit, 5))
        {
            defaultDot.SetActive(false);    // Turns off Default Dot
            interactDot.SetActive(true);    // Turns on Interact Dot
            promptTextObject.SetActive(true);   // Turns on the prompt text object
        }
        else
        {
            defaultDot.SetActive(true);    // Turns on Default Dot
            interactDot.SetActive(false);    // Turns off Interact Dot
            promptTextObject.SetActive(false);   // Turns off the prompt text object
        }

        if (Input.GetKeyDown(KeyCode.B))
        {
            // Make hit object larger by 125 percent
            hit.transform.localScale *= 1.25F;
        }

        if (Input.GetKeyDown(KeyCode.N))
        {
            // Make hit object smaller by 75 percent
            hit.transform.localScale *= 0.75F;
        }

    }
}

```

Save your script and test it in Unity!

![](../../.gitbook/assets/raycasting-04.gif)

## Step 7: Updating the UI Text

Go back to the script in Visual Studio.

We should have something more descriptive than "Interact," so let's change it in the raycasting if statement.

Update the prompt text to say, "Change the size of " and the name of the object. You can get it through the transform:

```csharp
promptText.text = "Change size of " + hit.transform.name;  // Updates the text to match the name of the object
```

Save your script and test it!

![](../../.gitbook/assets/raycasting-05.gif)

Just think of what you could do with tags \(grouping items\) and running code on specific instances of objects!

## Full Code

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class RaycastingTest : MonoBehaviour
{
    public GameObject defaultDot;
    public GameObject interactDot;
    public GameObject promptTextObject;
    public Text promptText;

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        if (Physics.Raycast(transform.position, transform.TransformDirection(Vector3.forward), out RaycastHit hit, 5))
        {
            defaultDot.SetActive(false);    // Turns off Default Dot
            interactDot.SetActive(true);    // Turns on Interact Dot
            promptTextObject.SetActive(true);   // Turns on the prompt text object
            promptText.text = "Change size of " + hit.transform.name;  // Updates the text to match the name of the object
        }
        else
        {
            defaultDot.SetActive(true);    // Turns on Default Dot
            interactDot.SetActive(false);    // Turns off Interact Dot
            promptTextObject.SetActive(false);   // Turns off the prompt text object
        }

        if (Input.GetKeyDown(KeyCode.B))
        {
            // Make hit object larger by 125 percent
            hit.transform.localScale *= 1.25F;
        }

        if (Input.GetKeyDown(KeyCode.N))
        {
            // Make hit object smaller by 75 percent
            hit.transform.localScale *= 0.75F;
        }

    }
}

```

Save your script and test it!

