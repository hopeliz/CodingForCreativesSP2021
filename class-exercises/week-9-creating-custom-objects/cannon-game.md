# Cannon Game (Unity)

This activity looks at creating and using prefabs. It uses Unity 2020.2 and all code should allow you to copy and paste.

## Step 1: Create a Scene

Open Unity and create a scene by right-clicking in the Project window and selecting **Create > Scene**.

![](<../../.gitbook/assets/image (276).png>)

Give it a name - I named mine "Cannon Game" - and press ENTER or RETURN to confirm.

![](<../../.gitbook/assets/image (357).png>)

Double-click the scene and it will open.

By default, the scene is empty except for Main Camera and Directional Light objects.

![](<../../.gitbook/assets/image (358).png>)

## Step 2: Create a Cannon

We'll start with a ground plane, which is simply a plane named "ground."

Right-click in the Hierarchy window and select **3D Object > Plane**.

![](<../../.gitbook/assets/image (359).png>)

Name the plane object _Ground_:

![](<../../.gitbook/assets/image (360).png>)

Select the Ground object. In the Inspector window, right-click on the Transform component and select **Reset** to place the plane at the origin.

![](<../../.gitbook/assets/image (361).png>)

![](<../../.gitbook/assets/image (362).png>)

In the Hierarchy window, click a blank area to deselect any objects.

Right-click and select **3D Object > Sphere**. This will be our cannon base.

![](<../../.gitbook/assets/image (363).png>)

Rename the sphere to Cannon.

![](<../../.gitbook/assets/image (364).png>)

Just like the plane, select the sphere object and put it at the scene origin by right-clicking on the Transform component in the Inspector window and selecting **Reset**.

![](<../../.gitbook/assets/image (365).png>)

![](<../../.gitbook/assets/image (366).png>)

You should now have something that looks a little like this:

![The view in the Scene window might not match this image.](<../../.gitbook/assets/image (367).png>)

Let's add a cylinder to be our cannon tube. Right-click in the Hierarchy window and select **3D Object > Cylinder**.

![](<../../.gitbook/assets/image (368).png>)

Rename the cylinder to Cannon Tube.

![](<../../.gitbook/assets/image (369).png>)

Reset the Cannon Tube to the origin just like the last two objects.

![](<../../.gitbook/assets/image (370).png>)

![](<../../.gitbook/assets/image (371).png>)

Use the **Scale Tool** on the top left to make the cylinder smaller and longer. 

![](<../../.gitbook/assets/image (372).png>)

Click on the center white cube that appears when the Scale Tool is on and drag to the left to make it smaller on all axes. 

![](<../../.gitbook/assets/image (373).png>)

Then, click on the green vector and drag upward to make it longer along the Y-axis.

![](<../../.gitbook/assets/image (374).png>)

Use the **Rotate Tool** or type in the rotation X coordinate in the Inspector window to 90.

![](<../../.gitbook/assets/image (375).png>)

![](<../../.gitbook/assets/image (376).png>)

![Your position and scale might be different.](<../../.gitbook/assets/image (377).png>)

Use the **Move Tool** to move the Cannon Tube into place. You might need to use the **Scale Tool** to make it a good size.

![](<../../.gitbook/assets/image (378).png>)

![](<../../.gitbook/assets/image (379).png>)

Now, we want the Cannon Tube to rotate with the Cannon object. The best way to do this is to make the Cannon Tube a child object of the Cannon. 

In the Hierarchy window, click and drag the Cannon Tube object onto the Cannon object. The Cannon Tube object should now be indented and the Cannon object will have a triangle on the left allowing for opening and collapsing the list of children under it.

![](<../../.gitbook/assets/image (380).png>)

Now, if you rotate the Cannon object, the Cannon Tube follows.

{% hint style="warning" %}
Make sure you have it set to **Pivot** at the top and NOT Center. See image below.
{% endhint %}

![](<../../.gitbook/assets/image (381).png>)

![](../../.gitbook/assets/Week9-2\_01.gif)

Use the Move Tool to move the Cannon back toward the camera. Select the Main Camera in the Hierarchy window and use the Move and Rotate tools to have a better view of the game.

![](<../../.gitbook/assets/image (382).png>)

![](<../../.gitbook/assets/image (383).png>)

## Step 3: Create a Cannon Ball

Create a sphere.

![](<../../.gitbook/assets/image (384).png>)

Rename it Cannon Ball.

![](<../../.gitbook/assets/image (385).png>)

Instead of resetting, we can have the Cannon Ball move to where the center of the Cannon Tube is. Since child objects have the Transform values in relation to their parent object, we need to first add the Cannon Ball to the Cannon object as a child. In the Hierarchy window, click and drag the Cannon Ball object on top of the Cannon object. It should appear indented.

![](<../../.gitbook/assets/image (386).png>)

Select the Cannon Tube object to bring up its components in the Inspector window.

Right-click on the word "Position" in the Transform component and select **Copy**.

![](<../../.gitbook/assets/image (387).png>)

Then, select the Cannon Ball object in the Hierarchy window to bring up its components in the Inspector window.

Right-click on the word "Position" in the Transform component and select **Paste**.

![](<../../.gitbook/assets/image (388).png>)

Use the Scale Tool to scale down the Cannon Ball to be smaller than the tube. Click and drag left on the white center cube that appears when the Scale Tool is turned on.

![](<../../.gitbook/assets/image (389).png>)

## Step 4: Make the Cannon Ball Move

All we want the cannon balls to do is move forward until they hit something. Let's make a script!

Create a C# script. In the Project window, right-click and select **Create > C# Script**.

![](<../../.gitbook/assets/image (390).png>)

Name it CannonBallBehavior.

![](<../../.gitbook/assets/image (391).png>)

Double-click the script to open it in Visual Studio.

We will be adding this script to the cannon ball, so any reference to the transform, tag, etc. will be for whatever object the script is attached to.

For movement, it's good to have a `speed` modifier variable to make it easy to update later within Unity.

Put this variable before `Start()`, but inside the class. I'm initializing it to 5, but you can change it in Unity later.

```csharp
public float speed = 5;
```

Inside the `Update()` function, we want the cannon ball to go forward on every frame. Here, we use `Translate()` instead of updating the `position` because `Translate()` uses the direction from the object while `position` uses the overall direction of the scene.

```csharp
// The cannon ball will continuously move forward
transform.Translate(Vector3.forward * Time.deltaTime * speed);
```

Full Code so far for CannonBallBehavior.cs:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class CannonBallBehavior : MonoBehaviour
{
    public float speed = 5;

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        // The cannon ball will continuously move forward
        transform.Translate(Vector3.forward * Time.deltaTime * speed);
    }
}

```

Save the script and go back to Unity.

Add the script to the Cannon Ball object - here are the ways to do that:

* Click and drag it to the Cannon Ball object in the Hierarchy window
* Select the Cannon Ball object and click and drag the script to the Inspector window OR
* Select the Cannon Ball object and use the **Add Component** button to search for and select the script

It will appear like this in your Inspector window:

![](<../../.gitbook/assets/image (392).png>)

Test it! Your cannon ball should fly out forward.

## Step 5: Create a Cannon Ball Prefab

As you can see, this Cannon Ball object has been resized and has a script. You could even add a material and other scripts. However, you don't want to go through that mess every time, so we create a **prefab** or custom object.

To do this, simply click and drag your object from the Hierarchy window to the Project window.

 It will appear as a reusable asset in the Project window.

![](<../../.gitbook/assets/image (393).png>)

The object in the Hierarchy window will now appear blue with an arrow on the right.

![](<../../.gitbook/assets/image (394).png>)

Clicking on the arrow will open up the Prefab object. This is where you can make changes that change all the _instances_ of the prefab in your scene.

![](<../../.gitbook/assets/image (395).png>)

To go back, click on the left arrow to the left of the name of the Prefab in the Hierarchy window.

![](<../../.gitbook/assets/image (396).png>)

**REMOVE** the Cannon Ball object from the Hierarchy window. We will be creating them while the scene is running. We also don't want it as a child object of the cannon anymore.

## Step 6: Make the Cannon Rotate

We want the Cannon object to rotate when pressing the left and right arrow keys. Let's make a script!

Create a C# script. In the Project window, right-click and select **Create > C# Script**.

![](<../../.gitbook/assets/image (390).png>)

Name it CannonBehavior.

![](<../../.gitbook/assets/image (397).png>)

Double-click the script to open it in Visual Studio.

Rotating objects should have a speed modifier variable as well, so declare a `rotateSpeed` variable inside the class, but before the `Start()` function. I'm initializing it to 20, but it can be changed later in Unity.

```csharp
public float rotateSpeed = 50;
```

In `Update()`, we want to put our code to get the key pressed and to rotate the Cannon when it's the correct key. `Input.GeyKey()` will run the code for each frame the key is pressed.

```csharp
// Rotate left when the Left Arrow key is held down
if (Input.GetKey(KeyCode.LeftArrow))
{
    transform.Rotate(Vector3.down * Time.deltaTime * rotateSpeed);
}

// Rotate right when the Right Arrow key is held down
if (Input.GetKey(KeyCode.RightArrow))
{
    transform.Rotate(Vector3.up * Time.deltaTime * rotateSpeed);
}
```

Save the script and return to Unity.

Add the script to the Cannon object (click and drag the script onto the object or use the Add Component button). It should look like this in the Inspector window:

![](<../../.gitbook/assets/image (398).png>)

Test it!

## Step 7: Make the Cannon Fire

Now, we want to have the cannon fire when we press the space bar. We can create objects while the scene is running with the `Instantiate()` function.

Go back or open the CannonBehavior script.

We need to have a variable hold the game object to create - the prefab. Put this variable near the other one near the top.

```csharp
public GameObject cannonBallPrefab;
```

In the `Update()` function, put the code to check for the space bar and run the instantiate code:

```csharp
// Create a cannon ball on the first frame the space bar is pressed
if (Input.GetKeyDown(KeyCode.Space))
{
    Instantiate(cannonBallPrefab);
}
```

Save the script and return to Unity.

Select the Cannon object. The script component should now appear like this:

![](<../../.gitbook/assets/image (399).png>)

Click and drag the Cannon Ball prefab from the Project window OR use the target icon to the right of the parameter and select from a list.

![](<../../.gitbook/assets/image (400).png>)

Once that's assigned, test it!

You'll notice the cannon balls will only appear from the origin of the scene and travel only forward in relation to the scene.

There's another form of `Instantiate()` we can use that will make the prefab appear where we want it and at the rotation we want it.

Go back to your CannonBehavior script.

We want the position of the Cannon Tube object, so we should store the object in a variable near the other variables.

```csharp
public GameObject cannonTube;
```

Now, we can update the `Instantiate()` to include the position of the Cannon Tube and whatever rotation is of the prefab.

```csharp
Instantiate(cannonBallPrefab, cannonTube.transform.position, transform.rotation);
```

Full Code for CannonBehavior.cs:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class CannonBehavior : MonoBehaviour
{
    public float rotateSpeed = 50;
    public GameObject cannonBallPrefab;
    public GameObject cannonTube;

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        // Rotate left when the Left Arrow key is held down
        if (Input.GetKey(KeyCode.LeftArrow))
        {
            transform.Rotate(Vector3.down * Time.deltaTime * rotateSpeed);
        }

        // Rotate right when the Right Arrow key is held down
        if (Input.GetKey(KeyCode.RightArrow))
        {
            transform.Rotate(Vector3.up * Time.deltaTime * rotateSpeed);
        }

        // Create a cannon ball on the first frame the space bar is pressed
        if (Input.GetKeyDown(KeyCode.Space))
        {
            Instantiate(cannonBallPrefab, cannonTube.transform.position, transform.rotation);
        }
    }
}
```

Save the script and return to Unity.

Select the Cannon object. The script component should now look like this:

![](<../../.gitbook/assets/image (401).png>)

Click and drag the Cannon Tube object from the Hierarchy window to the Cannon Tube parameter or click on the target icon to choose from a list.

![](<../../.gitbook/assets/image (402).png>)

Test it!

![](../../.gitbook/assets/Week9-2\_02.gif)

## Step 8: Have the Cannon Ball Disappear Upon Impact

We want the cannon balls to delete themselves when they hit something.

Open your CannonBallBehavior script.

After the closing curly bracket `}` of `Update()`, but before the final curly bracket `}`, put these two functions to detect when the cannon ball hits something. The `OnColliderStay()` is a backup for cannon balls that go too fast to be detected at the surface. `Destroy()` is a built-in function that deletes whatever is in the parentheses `()` from the scene or object.

```csharp
public void OnCollisionEnter(Collision collision)
{
    Destroy(gameObject);
}

public void OnCollisionStay(Collision collision)
{
    Destroy(gameObject);
}
```

Full code for CannonBallBehavior.cs:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class CannonBallBehavior : MonoBehaviour
{
    public float speed = 5;

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        // The cannon ball will continuously move forward
        transform.Translate(Vector3.forward * Time.deltaTime * speed);
    }

    public void OnCollisionEnter(Collision collision)
    {
        Destroy(gameObject);
    }

    public void OnCollisionStay(Collision collision)
    {
        Destroy(gameObject);
    }
}

```

Save the scene and return to Unity.

Double-click on the Cannon Ball prefab in the Project window to make it appear in the Hierarchy and Scene windows.

![](<../../.gitbook/assets/image (403).png>)

Select the Cannon Ball object to bring up its components.

Use the **Add Component** button to search for and add a **Rigidbody** component.

![](<../../.gitbook/assets/image (404).png>)

![](<../../.gitbook/assets/image (405).png>)

Remove the check for "Use Gravity" to turn off the gravity.

![](<../../.gitbook/assets/image (406).png>)

Click the left arrow to the left of the Cannon Ball prefab name in the Hierarchy window to return to the scene.

Add a cube for testing.

![](<../../.gitbook/assets/image (407).png>)

Use the Move Tool to move the cube to further away in front of the cannon.

![](<../../.gitbook/assets/image (408).png>)

Test it!

NOTHING HAPPENS???

It's because all 3D Objects are added with colliders so the cannon ball deletes itself when it is created in the cannon tube.

So select the Cannon Tube object in the Hierarchy window and remove the Capsule Collider component form the Inspector window - right-click and select **Remove Component**.

![](<../../.gitbook/assets/image (409).png>)

Select the Cannon object in the Hierarchy window and check Is Trigger so that the collider changes to a trigger and doesn't register collisions the same.

![](<../../.gitbook/assets/image (410).png>)

Now, test it!

{% hint style="warning" %}
If your ball is disappearing before it hits your cube, you might need to use the Move Tool to move the cannon tube up off the ground plane.
{% endhint %}

![](../../.gitbook/assets/Week9-2\_03.gif)

## Step 9: Create an Enemy

Delete the cube because we'll replace it with enemies.

Use 3D objects in the Hierarchy window to create an enemy shape. Have the main enemy object be the parent object and click and drag the other objects (nose/limbs/etc.) onto it to make them children objects.

Here is my enemy:

![](<../../.gitbook/assets/image (411).png>)

{% hint style="info" %}
When you create your enemy, it will be facing forward and away from your cannon.
{% endhint %}

## Step 10: Make the Enemy Attack

We can have the enemy move toward the cannon and die (disappear) when it gets hit enough times. Let's make a script!

Create a C# script. In the Project window, right-click and select **Create > C# Script**.

![](<../../.gitbook/assets/image (390).png>)

Name it EnemyBehavior.

![](<../../.gitbook/assets/image (412).png>)

Double-click the script to open it in Visual Studio.

We need to store what the cannon is so it knows where to face and move toward. The enemy will be moving, so we should also store its speed. Place the variables inside the class, but before the `Start()` function.

```csharp
public GameObject cannon;
public float speed = 2;
```

In the `Update()` function, the enemy should look at the cannon. transform.LookAt() is a built-in function.

```csharp
transform.LookAt(cannon.transform);
```

Now, the enemy just needs to move forward, just like the cannon ball does.

```csharp
transform.Translate(Vector3.forward * Time.deltaTime * speed);
```

Full code so far for EnemyBehavior:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyBehavior : MonoBehaviour
{
    public GameObject cannon;
    public float speed = 2;

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        transform.LookAt(cannon.transform);

        transform.Translate(Vector3.forward * Time.deltaTime * speed);
    }
}
```

Save the script and return to Unity.

Add the EnemyBehavior script to the Enemy object with the click-and-drag method or using the **Add Component** button.

When you select the Enemy game object, the script should appear like this in the Inspector window:

![](<../../.gitbook/assets/image (413).png>)

Click and drag the Cannon object from the Hierarchy window to the Cannon parameter or use the target icon to choose from a list.

![](<../../.gitbook/assets/image (414).png>)

Test it! Try using the move tool to test different locations for the enemy as well.

{% hint style="info" %}
`LookAt()` will also look vertically, so this works best with the enemy at zero on the Y axis. There's a version of LookAt() that takes a world position that can also use a Vector3 so you can set the Y value it looks at to be the same as your enemy.
{% endhint %}

## Step 11: Attack Back!

Double-click on your Cannon Ball prefab to open it in your Hierarchy and Scene windows.

![](<../../.gitbook/assets/image (403).png>)

Select the Cannon Ball object in the Hierarchy window to bring up its components in the Inspector window.

Click on the Tag drop down menu near the top of the Inspector window and select **Add Tag...**

![](<../../.gitbook/assets/image (415).png>)

Click the plus sign + to add a tag. I'm naming it "Cannon Ball." Click **Save** to save the tag.

![](<../../.gitbook/assets/image (416).png>)

![](<../../.gitbook/assets/image (417).png>)

Click on the Cannon Ball object in the Hierarchy window to bring up the components again.

Now, when you click the drop down menu for Tags, you can select Cannon Ball.

![](<../../.gitbook/assets/image (418).png>)

![](<../../.gitbook/assets/image (419).png>)

This way, we can test for a tag since each instance of the Cannon Ball will be named differently.

Open up the EnemyBehavior script.

Let's give our enemy a number of hit points stored in a variable near our other variables. This should be an integer.

```csharp
public int hitPoints = 2;
```

Now, whenever something hits it, we can see if it's a cannon ball, then take off a hit point if it is.

Put this after the last curly bracket `}` of `Update()` and before the final curly bracket `}`:

```csharp
public void OnCollisionEnter(Collision collision)
{
    if (collision.transform.tag == "Cannon Ball")
    {
        hitPoints -= 1;
    }
}
```

The temp variable `collision` holds information about the object hitting it. We can get and compare its tag.

To make sure it actually registers the hit, even at faster speeds, repeat this code in an `OnCollisionStay()` function.

```csharp
public void OnCollisionStay(Collision collision)
{
    if (collision.transform.tag == "Cannon Ball")
    {
        hitPoints -= 1;
    }
}
```

In `Update()`, we can check to see if the enemy is at zero hit points and have it delete itself.

```csharp
if (hitPoints == 0)
{
    Destroy(gameObject);
}
```

Full code so far for EnemyBehavior.cs:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyBehavior : MonoBehaviour
{
    public GameObject cannon;
    public float speed = 2;
    public int hitPoints = 2;

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        transform.LookAt(cannon.transform);

        transform.Translate(Vector3.forward * Time.deltaTime * speed);

        if (hitPoints == 0)
        {
            Destroy(gameObject);
        }
    }

    public void OnCollisionEnter(Collision collision)
    {
        if (collision.transform.tag == "Cannon Ball")
        {
            hitPoints -= 1;
        }
    }

    public void OnCollisionStay(Collision collision)
    {
        if (collision.transform.tag == "Cannon Ball")
        {
            hitPoints -= 1;
        }
    }
}
```

Save your script, return to or open your scene, and test it in Unity!

![](../../.gitbook/assets/Week9-2\_05.gif)

## Step 12: Keep Score

To keep score, we need a script on an object that is not going to disappear. I usually create an empty object called Game Controller or Game Master.

![](<../../.gitbook/assets/image (420).png>)

![](<../../.gitbook/assets/image (421).png>)

Click and drag it to the top of the Hierarchy window to find it easily.

![](<../../.gitbook/assets/image (422).png>)

Click and drag the Enemy object into the Project window to create an Enemy prefab.

![](<../../.gitbook/assets/image (424).png>)

![](<../../.gitbook/assets/image (425).png>)

Create a C# script. In the Project window, right-click and select **Create > C# Script**.

![](<../../.gitbook/assets/image (390).png>)

Name it GameMaster.

![](<../../.gitbook/assets/image (423).png>)

Double-click the script to open it in Visual Studio.

We need to keep track of the score and to hold the enemy prefab in a variable so we can instantiate them.

We also need something that counts down between spawning the enemies. Putting this as a public variable means you can change the rate as the game progresses.

Put these variables inside the class and before the Start() function.

```csharp
public int score = 0;
public GameObject enemyPrefab;
public float timeBetweenSpawn = 2;
public float countdownToSpawn;
```

In the Start() function, set the countdown.

```csharp
countdownToSpawn = timeBetweenSpawn;
```

In Update(), we want the countdown to count down.

```csharp
countdownToSpawn -= 1 * Time.deltaTime;
```

We also want to reset it when it reaches zero. Since time might jump past zero, we look for zero or less.

```csharp
if (countdownToSpawn <= 0)
{
    countdownToSpawn = timeBetweenSpawn;
}
```

But when it hits zero, we want to spawn a new enemy prefab at a random spot on the X-axis. I'll move my current enemy around to get the minimum and maximum X-axis values.

```csharp
if (countdownToSpawn <= 0)
{
    Instantiate(enemyPrefab, new Vector3(Random.Range(-4.31F, 4.26F), enemyPrefab.transform.position.y, enemyPrefab.transform.position.z), enemyPrefab.transform.rotation); 
    countdownToSpawn = timeBetweenSpawn;
}
```

Full code so far for GameMaster.cs:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class GameMaster : MonoBehaviour
{
    public int score = 0;
    public GameObject enemyPrefab;
    public float timeBetweenSpawn = 2;
    public float countdownToSpawn;

    // Start is called before the first frame update
    void Start()
    {
        countdownToSpawn = timeBetweenSpawn;
    }

    // Update is called once per frame
    void Update()
    {
        countdownToSpawn -= 1 * Time.deltaTime;

        if (countdownToSpawn <= 0)
        {
            Instantiate(enemyPrefab, new Vector3(Random.Range(-4.31F, 4.26F), enemyPrefab.transform.position.y, enemyPrefab.transform.position.z), enemyPrefab.transform.rotation); 
            countdownToSpawn = timeBetweenSpawn;
        }
    }
}

```

Save your script and return to Unity.

Add your GameMaster script to the Game Master object via the click and drag method or the **Add Component** button.

![](<../../.gitbook/assets/image (426).png>)

Click and drag the Enemy prefab from the Project folder or use the target icon to select from the list.

![](<../../.gitbook/assets/image (427).png>)

Delete the Enemy object currently in the scene and test it.

OH NO! They spawn but don't attack!

Take a look at the Enemy prefab by selecting it in the Project window. In the Inspector window, you'll notice the Enemy Behavior script component no longer references the Cannon. That's because the cannon only exists in that scene and the enemy prefab can be used in multiple scenes.

![](<../../.gitbook/assets/image (428).png>)

You can't click and drag it either! And we will make a variable soon to reference the Game Master, so how are we to do that if we can't click and drag it??

Well, check it out...

Open your EnemyBehavior script.

In your variable area, add a variable to hold a GameMaster type - this will reference the GameMaster.cs script directly.

```csharp
public GameMaster gameMaster;
```

In `Start()`, we can use a built-in function to find the game object in our scene with a particular component - in this case, the GameMaster script.

```csharp
gameMaster = FindObjectOfType<GameMaster>();
```

Once we have that, we can access other things, like the cannon. We will need to hold the info we need in the GameMaster script.

Save EnemyBehavior.cs for now and open GameMaster.cs.

Add a variable for the cannon with the other variables.

```csharp
public GameObject cannon;
```

Save GameMaster.cs and go back to EnemyBehavior.cs.

In `Start()`, add code that will use the `gameMaster` variable to access its `cannon` variable:

```csharp
cannon = gameMaster.cannon;
```

We can also update the score in Game Master when the enemy reaches zero hitPoints but it will have to be BEFORE it deletes itself.

```csharp
if (hitPoints == 0)
{
    gameMaster.score += 1;
    Destroy(gameObject);
}
```

Full Code for EnemyBehavior.cs:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyBehavior : MonoBehaviour
{
    public GameMaster gameMaster;
    public GameObject cannon;
    public float speed = 2;
    public int hitPoints = 2;

    // Start is called before the first frame update
    void Start()
    {
        gameMaster = FindObjectOfType<GameMaster>();
        cannon = gameMaster.cannon;
    }

    // Update is called once per frame
    void Update()
    {
        transform.LookAt(cannon.transform);

        transform.Translate(Vector3.forward * Time.deltaTime * speed);

        if (hitPoints == 0)
        {
            gameMaster.score += 1;
            Destroy(gameObject);
        }
    }

    public void OnCollisionEnter(Collision collision)
    {
        if (collision.transform.tag == "Cannon Ball")
        {
            hitPoints -= 1;
        }
    }

    public void OnCollisionStay(Collision collision)
    {
        if (collision.transform.tag == "Cannon Ball")
        {
            hitPoints -= 1;
        }
    }
}
```

Full code for GameMaster.cs:

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class GameMaster : MonoBehaviour
{
    public int score = 0;
    public GameObject enemyPrefab;
    public float timeBetweenSpawn = 2;
    public float countdownToSpawn;
    public GameObject cannon;

    // Start is called before the first frame update
    void Start()
    {
        countdownToSpawn = timeBetweenSpawn;
    }

    // Update is called once per frame
    void Update()
    {
        countdownToSpawn -= 1 * Time.deltaTime;

        if (countdownToSpawn <= 0)
        {
            Instantiate(enemyPrefab, new Vector3(Random.Range(-4.31F, 4.26F), enemyPrefab.transform.position.y, enemyPrefab.transform.position.z), enemyPrefab.transform.rotation); 
            countdownToSpawn = timeBetweenSpawn;
        }
    }
}
```

Save your scripts and return to Unity.

Select the Game Master object in the Hierarchy window to pull up its components.

![](<../../.gitbook/assets/image (429).png>)

Click and drag the cannon object or use the target icon to choose from a list.

![](<../../.gitbook/assets/image (430).png>)

Test it! You can watch the score in the Inspector window.

![](../../.gitbook/assets/Week9-2\_06.gif)

## Your turn!

See if you can create a Game Over state, User Interface, color changes, sound, etc.
