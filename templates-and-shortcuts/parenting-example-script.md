# Parenting Example Script

Download and inport this Unity Package to take a look at the scripts, scene, and see them work.

{% file src="../.gitbook/assets/parentingexample.zip" caption="ParentingExample.zip" %}

What's included:

* Parenting \(Scene\)
* MoveObject.cs \(Script\)
* ObjectDetails.cs \(Script\)
* SwitchParent.cs \(Script\)

### **Parenting \(Scene\)**

This scene has a cube on the left and a sphere on the right and a capsule in the center. The capsule is the object that changes its parent when you press a button. It's default parent is an empty game object called Empty Object.

There is a UI Canvas with two buttons: Switch Parent and Reset Parent.

![](../.gitbook/assets/image%20%28523%29.png)

![](../.gitbook/assets/image%20%28525%29.png)

### **MoveObject.cs \(Script\)**

This script is attached to both the cube and the sphere with the sphere having _Move Opposite_ checked.

![](../.gitbook/assets/image%20%28530%29.png)

![](../.gitbook/assets/image%20%28526%29.png)

The script has the object it is attached to move when the Up Arrow or W key is pressed or when the Down Arrow or S key is pressed.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class MoveObject : MonoBehaviour
{
    public bool moveOpposite = false;

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        // if the Up arrow or W key is pressed
        if (Input.GetKey(KeyCode.UpArrow) || Input.GetKey(KeyCode.W))
        {
            if (moveOpposite)
            {
                // Move down
                transform.Translate(Vector3.down * Time.deltaTime * 2);
            }
            else
            {
                // Move up
                transform.Translate(Vector3.up * Time.deltaTime * 2);
            }
        }

        // if the Down arrow or S key is pressed
        if (Input.GetKey(KeyCode.DownArrow) || Input.GetKey(KeyCode.S))
        {
            if (moveOpposite)
            {
                // Move up
                transform.Translate(Vector3.up * Time.deltaTime * 2);
            }
            else
            {
                // Move down
                transform.Translate(Vector3.down * Time.deltaTime * 2);
            }
        }

    }
}
```

### **ObjectDetails.cs \(Script\)**

This script is attached to the object that is changing parents \(the capsule\) to keep track of its original parent.

![](../.gitbook/assets/image%20%28529%29.png)

It sets its _Original Parent_ parameter upon playing the scene.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectDetails : MonoBehaviour
{
    public Transform originalParent;

    // Start is called before the first frame update
    void Start()
    {
        // Immediate look for and set the original parent of the object this script is on
        originalParent = transform.parent;
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```

### **SwitchParent.cs \(Script\)**

SwitchParent has functions for both buttons to run, so I attached it to the Canvas. I set the _Affected Object_ to the Capsule, _Parent Option 1_ to the Cube, and _Parent Option 2_ to the Sphere within Unity.

![](../.gitbook/assets/image%20%28524%29.png)

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class SwitchParent : MonoBehaviour
{
    public Transform affectedObject;
    public Transform parentOption1;
    public Transform parentOption2;

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        
    }

    public void ChangeParent()
    {
        // if the parent is the first option
        if (affectedObject.parent == parentOption1)
        {
            // Switch to second option
            affectedObject.parent = parentOption2;
        }
        else
        // if the parent is the second option or none of the options
        {
            // Switch to first option
            affectedObject.parent = parentOption1;
        }
    }

    public void ResetParent()
    {
        // Get the ObjectDetails of the object and the original parent and set the parent to the original
        affectedObject.parent = affectedObject.GetComponent<ObjectDetails>().originalParent;
    }
}

```

Note: `Start()` and `Update()` aren't needed here, but I left them in, in case it makes it easier for you to understand where the two custom functions would appear.

`ChangeParent()` checks to see if the affected object is parented to the first option. If it is, it switches to the second option. If it isn't, it switches it to the first.

`ResetParent()` looks at the ObjectDetails script attached to the affected object to determine and set the parent to the original parent.

To call these functions, I have the button objects reference the SwitchParent script and call the specific function:

![](../.gitbook/assets/image%20%28527%29.png)

![](../.gitbook/assets/image%20%28528%29.png)

### Test it!

When playing, the capsule should move with the parent object as well as appear as a child object in the Hierarchy window. When it's parented by its original parent, it will not move.

