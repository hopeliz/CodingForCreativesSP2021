# Bouncing Ball (Unity)

This activity looks at using colliders to get and update information when objects touch. It uses Unity 2020.2 and all code should allow you to copy and paste.

## Step 1: Create a Scene

Open Unity and create a scene by right-clicking in the Project window and selecting **Create > Scene**.

![](<../../.gitbook/assets/image (276).png>)

Give it a name and press ENTER or RETURN to confirm.

![](<../../.gitbook/assets/image (277).png>)

Double-click the scene and it will open.

By default, the scene is empty except for Main Camera and Directional Light objects.

![](<../../.gitbook/assets/image (278).png>)

## Step 2: Make a Box for the Ball to Bounce In

Here's a way I generally create these kinds of boxes that can serve as an interior space...

### Start with a cube

Right-click and select **3D Object > Cube**.

![](<../../.gitbook/assets/image (279).png>)

The cube will most likely appear away from the origin, so let's reset it. 

Select your cube to bring up its properties in the Inspector window. Right-click on the Transform component and select **Reset**.

![](<../../.gitbook/assets/image (280).png>)

Now, the cube will be at the origin (0, 0, 0).

![](<../../.gitbook/assets/image (281).png>)

![How it appears in the Game window](<../../.gitbook/assets/image (282).png>)

{% hint style="info" %}
If you can no longer see your cube in the Scene window, double-click on the cube object in the Hierarchy window to "focus" the Scene window on the object.
{% endhint %}

### Make your first wall

Using the scale tool on the top left of the screen, make your wall.

![Shortcut: Press R](<../../.gitbook/assets/image (260).png>)

![](<../../.gitbook/assets/image (283).png>)

![](<../../.gitbook/assets/image (284).png>)

![](<../../.gitbook/assets/image (285).png>)

### Duplicate your wall

Select the cube/wall in your Hierarchy window and do one of the following:

* Press CTRL+D
* Right-click and select Duplicate
* Press CTRL+C then CTRL+V 
* Right-click and select Copy, then right-click and select Paste

This will duplicate the object in the same location, adding (1) at the end of the name of the new object.

![](<../../.gitbook/assets/image (286).png>)

Select the first cube/wall and use the Move Tool on the top left of the screen to move the wall to the left.

![Shortcut: Press W](<../../.gitbook/assets/image (287).png>)

![](<../../.gitbook/assets/image (288).png>)

![](<../../.gitbook/assets/image (289).png>)

Once you have your left wall placed, use the X position coordinate for the other wall, but multiplied by -1. 

![Coordinates of the first cube/wall](<../../.gitbook/assets/image (290).png>)

![Coordinates of the second cube/wall](<../../.gitbook/assets/image (291).png>)

![](<../../.gitbook/assets/image (292).png>)

Rename your walls by clicking to select your object and click again to rename.

![](<../../.gitbook/assets/image (293).png>)

### Make the front and back walls

You might think you can just select both walls (hold SHIFT or CTRL and click), duplicate them, and use the Rotate Tool to rotate the walls.

However, this rotates each wall individually and doesn't save time.

![](<../../.gitbook/assets/image (294).png>)

INSTEAD, we will use an empty object to contain or hold these objects and rotate that.

BEFORE duplicating your walls, create an empty game object. Right-click in the Hierarchy window and select **Create Empty**.

![](<../../.gitbook/assets/image (295).png>)

Like all game objects in the scene, it comes with a Transform component.** If the empty game object is not at (0, 0, 0)**, reset it by right-clicking on the Transform component and selecting **Reset**.

Rename the game object to Left/Right Walls.

![](<../../.gitbook/assets/image (296).png>)

Select the Left Wall and Right Wall objects and click and drag them onto the Left/Right Walls object.

![](../../.gitbook/assets/BoucingBall\_01.gif)

This is called _Parenting_ objects. The containing object, shown at the top of the group and least indented, is the **parent **object and those inside and indented are **children** objects of the parent object. There can be multiple levels with children objects being a parent object of other objects.

When the parent object is changed (Position, Rotation, Scale, visibility, etc.), it changes the children objects _in relation to the parent_.

Now that we have an empty object with a center pivot, we can rotate the children objects on that pivot point by rotating the parent object.

Select and duplicate the Left/Right Walls "empty" object (the parent) and duplicate it.

This will duplicate the child objects as well.

![](<../../.gitbook/assets/image (297).png>)

Use the **Rotate Tool **to rotate the parent object.

![Shortcut: Press E](<../../.gitbook/assets/image (298).png>)

![](<../../.gitbook/assets/image (299).png>)

You probably won't be perfect rotating these walls into place, so I usually rotate it some, then use the Transform component to rotate it 90 degrees (or -90) by typing it in on the Y rotation coordinate.

![](<../../.gitbook/assets/image (300).png>)

Update the names of your new walls.

![](<../../.gitbook/assets/image (301).png>)

Right now, your walls probably have gaps.

![](<../../.gitbook/assets/image (302).png>)

Use the **Scale Tool** on the individual walls (best if two walls are selected at once) to close the gaps.

![](<../../.gitbook/assets/image (303).png>)

We can't see into the box in the Game window, so let's make the front wall invisible by turning off its Mesh Renerder component. This will make it appear invisible, but keep its collider so the ball can bounce off of it.

Select the front wall and uncheck the checkbox next to the Mesh Renderer component.

![](<../../.gitbook/assets/image (305).png>)

![](<../../.gitbook/assets/image (304).png>)

### Make the ceiling and floor

Duplicate the Left/Right Walls parent object and use the Rotate Tool to rotate it on the blue Z-axis.

![](<../../.gitbook/assets/image (306).png>)

To make it easier, type -90 (or 90) into the Z rotation coordinate in the Inspector window.

![](<../../.gitbook/assets/image (307).png>)

![](<../../.gitbook/assets/image (308).png>)

Update the name of the walls.

![](<../../.gitbook/assets/image (309).png>)

Use the Scale and Move tools on the individual walls (children objects) to fill the gaps.

![](<../../.gitbook/assets/image (310).png>)

### Polishing

Select Main Camera and use the Move Tool to move the camera down and forward to center the box in the game window.

![](<../../.gitbook/assets/image (311).png>)

The walls are currently a default white and appear as this god-awful yellow because of the directional light color. We'll turn that light off soon, so no need to change it.

However, let's give the walls a black material.

Create a black material by right-clicking in the Project Window and selecting **Create > Material**.

![](<../../.gitbook/assets/image (312).png>)

Give it a name.

![](<../../.gitbook/assets/image (313).png>)

Select the material to bring up its properties in the Inspector window.

Click the white color block next to Albedo to bring up a color picker wheel. Click on black (bottom left) and press ENTER or RETURN to confirm it.

![](<../../.gitbook/assets/image (314).png>)

Select all the individual walls (hold SHIFT and click) in the Hierarchy window.

![](<../../.gitbook/assets/image (315).png>)

Click and drag the Black material to the Inspector window to apply the material to all the selected objects.

![](<../../.gitbook/assets/image (316).png>)

![](<../../.gitbook/assets/image (317).png>)

## Step 3: Add a Ball

Click in an empty area of the Hierarchy window to deselect objects.

Right-click and select 3D Object > Sphere and name the new object, "Ball."

![](<../../.gitbook/assets/image (318).png>)

![](<../../.gitbook/assets/image (319).png>)

Reset the Transform of the ball.

![](<../../.gitbook/assets/image (320).png>)

![](<../../.gitbook/assets/image (281).png>)

OH NO! WE CAN'T SEE IT!

![](<../../.gitbook/assets/image (321).png>)

No worries! It's only because the ball is in a shadow.

Let's create a material that glows - or emits - a color.

Right-click in the Project window and select **Create > Material**.

![](<../../.gitbook/assets/image (312).png>)

Name it something like White Glow.

![](<../../.gitbook/assets/image (322).png>)

Select the material to see its properties in the Inspector window. The Albedo is already white.

Select the checkbox next to Emission.

![](<../../.gitbook/assets/image (323).png>)

Click on the HDR block next to the Color property to bring up a color picker for the glow color. Select white (top left) and press ENTER or RETURN to confirm.

![](<../../.gitbook/assets/image (324).png>)

Click and drag the White Glow material onto the Ball object in the Hierarchy window OR select the Ball object and click and drag the material into the Inspector window.

![](<../../.gitbook/assets/image (325).png>)

Although it appears to glow, it doesn't actually emit any light.

![Even close to a wall, no light is reflected.](<../../.gitbook/assets/image (326).png>)

Let's put a point light inside to make it appear to give off light.

In your Hierarchy window, right-click and select **Light > Point Light**.

![](<../../.gitbook/assets/image (327).png>)

Put your light at the same position as the ball. Select the Ball in the Hierarchy window. In the Inspector window, right-click the Transform component and select **Copy Component**.

![](<../../.gitbook/assets/image (328).png>)

Select the Point Light object in the Hierarchy window. In the Inspector window, right-click the Transform component and select **Paste Component Values**.

![](<../../.gitbook/assets/image (329).png>)

This puts the light where the ball is NOW, but we will be using gravity and randomness with the ball, so how do we get the light to stay with the ball?

PARENTING.

Click and drag the Point Light object onto the Ball object so that it becomes a child of the Ball object.

![](<../../.gitbook/assets/image (330).png>)

Now, wherever the ball goes, the light travels with it.

The ball now appears to emit light when near a wall.

![](<../../.gitbook/assets/image (331).png>)

Select the Directional Light in the Hierarchy window. Uncheck the checkbox to left of the name of the object in the Inspector window to turn off that unneeded object.

![](<../../.gitbook/assets/image (332).png>)

## Step 4: Make It Bounce

Select the Ball object in the Hierarchy or Scene window to bring up its properties and components. In the Inspector window, click the **Add Component** button.

![](<../../.gitbook/assets/image (333).png>)

Start typing Rigidbody and the options will appear.

![](<../../.gitbook/assets/image (334).png>)

Select Rigidbody to add the component.

![Default Rigidbody component](<../../.gitbook/assets/image (335).png>)

Play it!

![](../../.gitbook/assets/BoucingBall\_02.gif)

The default Rigidbody component gives it gravity and will stop it when it touches a collider of another object, but doesn't know how bouncy it should be. That is done with an added **Physic Material**. Let's make one!

In the Project window, right-click and select **Create > Physic Material**.

![](<../../.gitbook/assets/image (336).png>)

Name it something like Bouncy.

![](<../../.gitbook/assets/image (337).png>)

Select it to bring up its properties in the Inspector window.

Change the _Bounciness_ to 0.9 (meaning 90 percent) and the _Bounce Combine_ to Maximum. This will make it bouncy, but still lose momentum.

![](<../../.gitbook/assets/image (338).png>)

Select all the individual walls in the Hierarchy window.

![](<../../.gitbook/assets/image (339).png>)

In the Inspector window, in the Box Collider component, click and drag the Bouncy material into the _Material_ property or use the target icon to the right to select from a list.

![](<../../.gitbook/assets/image (340).png>)

Select the Ball object and change the Material of the Sphere Collider the same way.

![](<../../.gitbook/assets/image (341).png>)

Play it!

![](../../.gitbook/assets/BoucingBall\_03.gif)

## Step 5: Push the Ball Around

We want to push it in a random direction when the user presses the Space bar. We'll need to use a script.

In the Project window, right-click and select **Create > C# Script**.

![](<../../.gitbook/assets/image (342).png>)

Call it something like BallBehavior.

![](<../../.gitbook/assets/image (343).png>)

Double-click on the script to open it in Visual Studio.

We can store the object's Rigidbody component in a variable just before the `Start()` function.

```csharp
public Rigidbody ballRb;
```

This would replace the `object.GetComponent<Rigidbody>()` part of the code.

We want to be able to adjust the amount of force, so I'll make a multiplier value.

```csharp
public float forceMultiplier = 20;
```

We also need an integer variable to determine a direction.

```csharp
public int direction = 0;
// 0 - up, 1 - left, 2 - right, 3 - forward, 4 - back
```

In the `Update()` function, let's check for when the Spacebar is pressed.

We have three choices:

* `Input.GetKeyDown(KeyCode.Space)` - runs code ONLY on the first frame the key is pressed
* `Input.GetKey(KeyCode.Space)` - runs code on every frame the key is held down
* `Input.GetKeyUp(KeyCode.Space)` - runs code ONLY on the first frame the key is released

For deciding the random direction, we only want it to run once when the spacebar is pressed.

```csharp
if (Input.GetKeyDown(KeyCode.Space))
{
    // Get random number
}
```

But when we add force to the ball, the ball is already moving, so we need to add the force multiple times to actually push the ball. Having force being applied while the spacebar is pressed will give the user control.

```csharp
if (Input.GetKey(KeyCode.Space))
{
    // Add force while space is pressed
}
```

Let's get the random number.

We can use `Random.Range(float min, float max)` to get a random floating point number between two numbers. You'd think we'd use 0 as the min and 4 as the max, but that means 4 would also run if it randomly hits 4.0 only, making it rare. Instead, we want the max to be around 4.999 to give it a fair chance.

`Random.Range()` gives me a floating-point number, which cannot be stored in our `direction` variable because it's an integer. We need to cast or convert it to an integer. Unity has a math function called `FloorToInt()` that rounds a floating-point number down and converts it to an integer.

```csharp
if (Input.GetKeyDown(KeyCode.Space))
{
    // Get random number
    direction = Mathf.FloorToInt(Random.Range(0, 4.990F));
}
```

Now that we have a `direction` number, we can test it and use it to determine the direction to push the ball.

```csharp
if (Input.GetKey(KeyCode.Space))
{
    // Add force while space is pressed

    if (direction == 0)
    {
        ballRb.AddForce(Vector3.up * forceMultiplier);
    }

    if (direction == 1)
    {
        ballRb.AddForce(Vector3.left * forceMultiplier);
    }

    if (direction == 2)
    {
        ballRb.AddForce(Vector3.right * forceMultiplier);
    }

    if (direction == 3)
    {
        ballRb.AddForce(Vector3.forward * forceMultiplier);
    }

    if (direction == 4)
    {
        ballRb.AddForce(Vector3.back * forceMultiplier);
    }
}
```

**Full code so far:**

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class BallBehavior : MonoBehaviour
{
    public Rigidbody ballRb;
    public float forceMultiplier = 20;

    public int direction = 0;
    // 0 - up, 1 - left, 2 - right, 3 - forward, 4 - back

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
        {
            // Get random number
            direction = Mathf.FloorToInt(Random.Range(0, 4.990F));
        }

        if (Input.GetKey(KeyCode.Space))
        {
            // Add force while space is pressed

            if (direction == 0)
            {
                ballRb.AddForce(Vector3.up * forceMultiplier);
            }

            if (direction == 1)
            {
                ballRb.AddForce(Vector3.left * forceMultiplier);
            }

            if (direction == 2)
            {
                ballRb.AddForce(Vector3.right * forceMultiplier);
            }

            if (direction == 3)
            {
                ballRb.AddForce(Vector3.forward * forceMultiplier);
            }

            if (direction == 4)
            {
                ballRb.AddForce(Vector3.back * forceMultiplier);
            }
        }
    }
}

```

Save the code and go back to Unity.

Select the Ball object in the Hierarchy window. Add the BallBehavior script by clicking and dragging it into the Inspector window or use the Add Component button to search for it.

![](<../../.gitbook/assets/image (345).png>)

Click and drag the Ball object from the Hierarchy window or use the target symbol on the right of the property to select from a list.

![](<../../.gitbook/assets/image (344).png>)

Test it!

![Pressing and slightly holding Space to change directions.](../../.gitbook/assets/BoucingBall\_04.gif)

This is OK, but I want to give it a lift each time because there is a 4 in 5 chance it will not be pushed up enough for a bounce.

I'll add this in my `GetKey()` if statement:

```csharp
ballRb.AddForce(Vector3.up * 5);
```

## Step 6: Change the Color of the Walls Upon Impact

I want the walls to change color when the ball hits them.

We can store information in an integer to keep track of the color - 0 for the first material and 1 for the second, but I want to do this for ALL the walls. That could get messy trying to do it within our current script. Also, testing for the actual material of an object can produce odd issues when names don't match exactly.

BUT we can create a script that simply keeps track of the color number and have each wall keep track of it and report it to the ball. Then, the ball can tell the wall it's hitting to update the number!

Make a new script. In the Project window, right-click and select **Create > C# Script**.

![](<../../.gitbook/assets/image (342).png>)

I'll call this script WallData.

![](<../../.gitbook/assets/image (346).png>)

Double-click to open the script in Visual Studio.

All we need is a public variable right before the `Start()` function, but inside the class to hold the number representing the material number. Initialize it to zero (first color).

```csharp
public int colorNumber = 0;
```

`Start()` and `Update()` can be removed.

**Full code:**

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class WallData : MonoBehaviour
{
    public int colorNumber = 0;
}

```

Save it and return to Unity.

Select the individual walls in the Hierarchy window.

![](<../../.gitbook/assets/image (339).png>)

Click and drag the WallData script or use the Add Component button to search for the script to add it tall all the selected objects.

![](<../../.gitbook/assets/image (347).png>)

Open the BallBehavior script.

In the public global variables just before the `Start()` function, add two Material variables to store the materials.

```csharp
public Material mat1;
public Material mat2;
```

**At the very end, BUT before the final ending curly bracket `}`**, add the built-in function that runs only on the first frame that the collider of the ball touches the collider of another object:

```csharp
public void OnCollisionEnter(Collision collision)
{
    
}
```

In these curly brackets `{ }`,  we can check the color number of the wall we are hitting, then use it to determine what color/material to change it to.

The local or temporary variable, **`collision`**, stores information about the object the object the script is attached to is touching. We can get the game object, then all its components, including the Wall Data script component. Using that, we can access its public properties, variables, and functions.

Let's check to see if the `colorNumber` variable is zero:

```csharp
if (collision.gameObject.GetComponent<WallData>().colorNumber == 0)
{
    
}
```

If it is zero, change the color/material to the second material and update the `colorNumber` variable to 1.

```csharp
if (collision.gameObject.GetComponent<WallData>().colorNumber == 0)
{
    // Update wall to second material/color
    collision.gameObject.GetComponent<Renderer>().material = mat2;

    // Update the WallData.cs colorNumber variable
    collision.gameObject.GetComponent<WallData>().colorNumber = 1;
}
```

Otherwise, if the `colorNumber` variable is 1, change it back to the first material and `colorNumber` variable to zero.

```csharp
if (collision.gameObject.GetComponent<WallData>().colorNumber == 0)
{
    // Update wall to second material/color
    collision.gameObject.GetComponent<Renderer>().material = mat2;

    // Update the WallData.cs colorNumber variable
    collision.gameObject.GetComponent<WallData>().colorNumber = 1;
}
else
{
    // Update wall to second material/color
    collision.gameObject.GetComponent<Renderer>().material = mat1;

    // Update the WallData.cs colorNumber variable
    collision.gameObject.GetComponent<WallData>().colorNumber = 0;
}
```

**Full code so far:**

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class BallBehavior : MonoBehaviour
{
    public Rigidbody ballRb;
    public float forceMultiplier = 20;

    public int direction = 0;
    // 0 - up, 1 - left, 2 - right, 3 - forward, 4 - back

    public Material mat1;
    public Material mat2;

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
        {
            // Get random number
            direction = Mathf.FloorToInt(Random.Range(0, 4.990F));
        }

        if (Input.GetKey(KeyCode.Space))
        {
            // Add force while space is pressed

            ballRb.AddForce(Vector3.up * 5);

            if (direction == 0)
            {
                ballRb.AddForce(Vector3.up * forceMultiplier);
            }

            if (direction == 1)
            {
                ballRb.AddForce(Vector3.left * forceMultiplier);
            }

            if (direction == 2)
            {
                ballRb.AddForce(Vector3.right * forceMultiplier);
            }

            if (direction == 3)
            {
                ballRb.AddForce(Vector3.forward * forceMultiplier);
            }

            if (direction == 4)
            {
                ballRb.AddForce(Vector3.back * forceMultiplier);
            }
        }
    }

    public void OnCollisionEnter(Collision collision)
    {
        if (collision.gameObject.GetComponent<WallData>().colorNumber == 0)
        {
            // Update wall to second material/color
            collision.gameObject.GetComponent<Renderer>().material = mat2;

            // Update the WallData.cs colorNumber variable
            collision.gameObject.GetComponent<WallData>().colorNumber = 1;
        }
        else
        {
            // Update wall to second material/color
            collision.gameObject.GetComponent<Renderer>().material = mat1;

            // Update the WallData.cs colorNumber variable
            collision.gameObject.GetComponent<WallData>().colorNumber = 0;
        }
    }
}

```

Save the code and go back to Unity.

Select the Ball object in the Hierarchy window.

The Ball Behavior script component now has properties for _Mat 1_ and _Mat 2_.

![](<../../.gitbook/assets/image (348).png>)

Use the Black material for _Mat 1_ (click and drag it or click the target icon on the right to choose from a list).

For _Mat 2_, create another material with a color to change the wall to when the ball hits it. Click and drag or use the target icon to set it as _Mat 2_.

My _Ball Rb_ reset to None, so I had to click and drag the Ball object to set it again. (This doesn't always happen).

![](<../../.gitbook/assets/image (349).png>)

Test it!

![](../../.gitbook/assets/BoucingBall\_05.gif)

I'll add one more Material variable to appear only when the ball is actually touching the wall.

```csharp
public Material touchingMaterial;
```

At the very end, but BEFORE the final closing curly bracket `}`, we can use a built-in function to run EVERY frame the object the script is on is touching another object.

```csharp
public void OnCollisionStay(Collision collision)
{
    
}
```

When it's touching, we want to change the wall to the `touchingMaterial`.

```csharp
public void OnCollisionStay(Collision collision)
{
    collision.gameObject.GetComponent<Renderer>().material = touchingMaterial;
}
```

Save it and go back to Unity. A property for _Touching Material_ will appear.

![](<../../.gitbook/assets/image (350).png>)

Create a material and set it to _Touching Material_.

![](<../../.gitbook/assets/image (351).png>)

Test it!

![2x speed](../../.gitbook/assets/BoucingBall\_06.gif)

What's happening???

Well, the `OnCollisionStay()` works with sustained contact and a bounce might only register as one frame, so it's not enough. When it is enough, nothing is changing the color BACK to a color related to the `colorNumber`.

One way to fix this is to change `OnCollisionEnter()` to `OnCollisionExit()` - this way, the color change happens when the objects stop touching instead of when they start.

However, this still doesn't register a touch long enough for a Touching Material to appear for many of the bounces.

Fix this by adding an `OnCollisionEnter()` wth the code from the `OnCollisionStay()`.

## Here's the full code (BallBehavior.cs)

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class BallBehavior : MonoBehaviour
{
    public Rigidbody ballRb;
    public float forceMultiplier = 20;

    public int direction = 0;
    // 0 - up, 1 - left, 2 - right, 3 - forward, 4 - back

    public Material mat1;
    public Material mat2;
    public Material touchingMaterial;

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space))
        {
            // Get random number
            direction = Mathf.FloorToInt(Random.Range(0, 4.990F));
        }

        if (Input.GetKey(KeyCode.Space))
        {
            // Add force while space is pressed

            ballRb.AddForce(Vector3.up * 5);

            if (direction == 0)
            {
                ballRb.AddForce(Vector3.up * forceMultiplier);
            }

            if (direction == 1)
            {
                ballRb.AddForce(Vector3.left * forceMultiplier);
            }

            if (direction == 2)
            {
                ballRb.AddForce(Vector3.right * forceMultiplier);
            }

            if (direction == 3)
            {
                ballRb.AddForce(Vector3.forward * forceMultiplier);
            }

            if (direction == 4)
            {
                ballRb.AddForce(Vector3.back * forceMultiplier);
            }
        }
    }

    public void OnCollisionExit(Collision collision)
    {
        if (collision.gameObject.GetComponent<WallData>().colorNumber == 0)
        {
            // Update wall to second material/color
            collision.gameObject.GetComponent<Renderer>().material = mat2;

            // Update the WallData.cs colorNumber variable
            collision.gameObject.GetComponent<WallData>().colorNumber = 1;
        }
        else
        {
            // Update wall to second material/color
            collision.gameObject.GetComponent<Renderer>().material = mat1;

            // Update the WallData.cs colorNumber variable
            collision.gameObject.GetComponent<WallData>().colorNumber = 0;
        }
    }

    public void OnCollisionStay(Collision collision)
    {
        collision.gameObject.GetComponent<Renderer>().material = touchingMaterial;
    }

    public void OnCollisionEnter(Collision collision)
    {
        collision.gameObject.GetComponent<Renderer>().material = touchingMaterial;
    }
}

```

**Final result:**

![2x speed](../../.gitbook/assets/BoucingBall\_07.gif)

 
