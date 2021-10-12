# Creating Custom Objects (Processing)

This activity looks at creating custom reusable objects in Processing. All code should allow you to copy and paste.

## Step 1: Making One Object

Let's start with a regular sketch. To for projects that use multiple tabs, it's best to save the sketch even if you are just practicing.

### Create the shape

Set up your canvas in `setup()`.

```java
void setup() {
  // Create a canvas that's 600 by 600
  size(600, 600); 
}
```

Let's create a simple button, but with a little complexity in its design. Something like this:

![](<../../.gitbook/assets/image (476).png>)

It's just layered squares.

We can do this in `draw()` so that it is drawn in each frame.

```java
void draw() {
  // Set background to black
  background(0);
  
  // Set the rectMode to CENTER so squares and recatangles are drawn from the center and have a center pivot point.
  rectMode(CENTER);
  
  // Set the fill color to white for now
  fill(255);
  square(300, 300, 100);
  
  // Set the fill for the next square to black
  fill(0);
  square(300, 300, 80);
  
  // Set the fill for the next square to white for now
  fill(255);
  square(300, 300, 60);
  
  // Set the fill for the next square to black
  fill(0);
  square(300, 300, 40);
  
  // Set the fill for the next square to white for now
  fill(255);
  square(300, 300, 20);
}
```

We have a LOT of repetition here - the color, the location of the squares - even the size is based on the size of the first square. Let's turn those things into reusable variables so we can update the whole thing easily.

At the very top, above setup() put the _global_ and _public_ variables:

```java
float xPosition = 300;
float yPosition = 300;
float size = 100;
color fillColor = color(255, 255, 255);
color stripeColor = color(0, 0, 0);
```

Then, replace the values in the code with the variables.

```java
void draw() {
  // Set background to black
  background(0);
  
  // Set the rectMode to CENTER so squares and recatangles are drawn from the center and have a center pivot point.
  rectMode(CENTER);
  
  // Set the fill color to white for now
  fill(fillColor);
  square(xPosition, yPosition, size);
  
  fill(stripeColor);
  square(xPosition, yPosition, size * 0.8);
  
  fill(fillColor);
  square(xPosition, yPosition, size * 0.6);
  
  fill(stripeColor);
  square(xPosition, yPosition, size * 0.4);
  
  fill(fillColor);
  square(xPosition, yPosition, size * 0.2);
}
```

Full code so far:

```java
float xPosition = 300;
float yPosition = 300;
float size = 100;
color fillColor = color(255, 255, 255);
color stripeColor = color(0, 0, 0);

void setup() {
  // Create a canvas that's 600 by 600
  size(600, 600); 
}

void draw() {
  // Set background to black
  background(0);
  
  // Set the rectMode to CENTER so squares and recatangles are drawn from the center and have a center pivot point.
  rectMode(CENTER);
  
  // Set the fill color to white for now
  fill(fillColor);
  square(xPosition, yPosition, size);
  
  fill(stripeColor);
  square(xPosition, yPosition, size * 0.8);
  
  fill(fillColor);
  square(xPosition, yPosition, size * 0.6);
  
  fill(stripeColor);
  square(xPosition, yPosition, size * 0.4);
  
  fill(fillColor);
  square(xPosition, yPosition, size * 0.2);
}
```

### Add some interaction

We can create a custom function that changes the fill color when the user hovers their cursor over the shape, when they select it, and a color to determine when the button is "on."

What we need to add variable-wise at the top of the sketch:

* whether the button is on or off (boolean)
* state of the button (integer)
* colors for each state (unselected/default, hover, selected, and "on")

```java
boolean buttonOn = false;
int state = 0;    // 0 = unselected, 1 = hover, 2 = selected
color unselectedColor = color(255, 0, 0); // Red
color hoverColor = color(255, 255, 0); // Yellow
color selectedColor = color(255, 255, 255); // White
color buttonOnColor = color(0, 255, 0); // Green
```

Now, for the custom function, we need to test to see if the cursor is within the boundaries of our shape. Since the object is drawn from the center, the boundaries are half the size from that point.

After the final curly bracket `}` of `draw()`, add the custom functions - one for checking the button boundaries and sets the state and one function that determines the color:

```java
void checkButtonState() {
  // Check if the mouse cursor is within the button
  if (mouseX >= xPosition - size/2 && mouseX <= xPosition + size/2 && mouseY >= yPosition - size/2 && mouseY <= yPosition + size/2) {
    // Change state to hover
    state = 1;
    
    // Check for a mouse BUTTON PRESS (true when held down)
    if (mousePressed) {
      // Change state to selected
      state = 2;
    }
  }
  // Otherwise, the state should be unselected
  else {
    state = 0;
  }
}

void determineColor() {
  
  // Determine the fill color based on the state
  if (state == 1) {
    fillColor = hoverColor;
  }
  
  else if (state == 2) {
    fillColor = selectedColor;
  }
  
  else {
    if (buttonOn) {
      fillColor = buttonOnColor;
    }
    else {
      fillColor = unselectedColor;
    }
  }
}
```

Add one last function, the built-in `mouseClicked()` function to switch the `buttonOn` variable, but ONLY when the button is not unselected.

```java
void mouseClicked() {
  // Only run when the state is higher than 0
  if (state > 0) {
    // Switch the buttonOn variable to its opposite
      buttonOn = !buttonOn;
  }
}
```

Now, call the `checkButtonState()` and `determineColor()` functions before the line referencing the `fillColor` variable.

```java
checkButtonState();
determineColor();
```

Full code so far:

```java
float xPosition = 300;
float yPosition = 300;
float size = 100;
color fillColor = color(255, 255, 255);
color stripeColor = color(0, 0, 0);
boolean buttonOn = false;
int state = 0;    // 0 = unselected, 1 = hover, 2 = selected
color unselectedColor = color(255, 0, 0); // Red
color hoverColor = color(255, 255, 0); // Yellow
color selectedColor = color(255, 255, 255); // White
color buttonOnColor = color(0, 255, 0); // Green


void setup() {
  // Create a canvas that's 600 by 600
  size(600, 600); 
}

void draw() {
  // Set background to black
  background(0);
  
  // Set the rectMode to CENTER so squares and recatangles are drawn from the center and have a center pivot point.
  rectMode(CENTER);
  
  // Call the checkButtonState() and determineColor() functions before getting the fillColor variable
  checkButtonState();
  determineColor();
  
  // Set the fill color to white for now
  fill(fillColor);
  square(xPosition, yPosition, size);
  
  fill(stripeColor);
  square(xPosition, yPosition, size * 0.8);
  
  fill(fillColor);
  square(xPosition, yPosition, size * 0.6);
  
  fill(stripeColor);
  square(xPosition, yPosition, size * 0.4);
  
  fill(fillColor);
  square(xPosition, yPosition, size * 0.2);
}

void checkButtonState() {
  // Check if the mouse cursor is within the button
  if (mouseX >= xPosition - size/2 && mouseX <= xPosition + size/2 && mouseY >= yPosition - size/2 && mouseY <= yPosition + size/2) {
    // Change state to hover
    state = 1;
    
    // Check for a mouse BUTTON PRESS (true when held down)
    if (mousePressed) {
      // Change state to selected
      state = 2;
    }
  }
  // Otherwise, the state should be unselected
  else {
    state = 0;
  }
}

void determineColor() {
  
  // Determine the fill color based on the state
  if (state == 1) {
    fillColor = hoverColor;
  }
  
  else if (state == 2) {
    fillColor = selectedColor;
  }
  
  else {
    if (buttonOn) {
      fillColor = buttonOnColor;
    }
    else {
      fillColor = unselectedColor;
    }
  }
}

void mouseClicked() {
  // Only run when the state is higher than 0
  if (state > 0) {
    // Switch the buttonOn variable to its opposite
      buttonOn = !buttonOn;
  }
}
```

Output so far:

![The circle click effects were added.](../../.gitbook/assets/Week9-1\_01.gif)

## Step 2: Move the Code to a Class

**Create a new tab**

Near the play button, click the tab with a down arrow and select **New Tab**. 

![](<../../.gitbook/assets/image (477).png>)

Give your object type a name.

![](<../../.gitbook/assets/image (478).png>)

This will create a tab with the name.

![](<../../.gitbook/assets/image (479).png>)

At the top, create a _class_ that is named for your new object type - use a capital letter to begin:

```java
class Button { }
```

In the first tab, copy the variables that relate to the object and paste them into the new tab. You can remove them from the first tab inside the curly brackets `{ }`.

```java
class Button {

float xPosition = 300;
float yPosition = 300;
float size = 100;
color fillColor = color(255, 255, 255);
color stripeColor = color(0, 0, 0);
boolean buttonOn = false;
int state = 0;    // 0 = unselected, 1 = hover, 2 = selected
color unselectedColor = color(255, 0, 0); // Red
color hoverColor = color(255, 255, 0); // Yellow
color selectedColor = color(255, 255, 255); // White
color buttonOnColor = color(0, 255, 0); // Green

}
```

This means these variables only exist in this object.

We will be setting these values in a different way, so remove any initial values you want to customize.

```java
class Button {
    float xPosition;
    float yPosition;
    float size;
    color fillColor;
    color stripeColor = color(0, 0, 0); // Default as black no matter what
    boolean buttonOn = false;
    int state = 0;    // 0 = unselected, 1 = hover, 2 = selected
    color unselectedColor;
    color hoverColor;
    color selectedColor;
    color buttonOnColor;
}
```

We now need a "constructor" function that will take information from another part of the script - even a user - to determine these variable values instead of having them written out like this.

Just after the variables, but inside/before the final curly bracket `}`, we use the name of the object followed by parentheses `( )` with _parameters_ in the parameters, separated by commas. Each parameter should have its variable type before its name and, since these are temporary variables, I usually put "temp" in the variable names.

```java
Button(float tempXPosition, float tempYPosition, float tempSize, color tempUnselectedColor, color tempHoverColor, color tempSelectedColor, color tempButtonOnColor) {
}
```

Inside the `Button()` curly brackets `{ }`, set each of the variables to the temp variables/parameters.

```java
Button(float tempXPosition, float tempYPosition, float tempSize, color tempUnselectedColor, color tempHoverColor, color tempSelectedColor, color tempButtonOnColor) {
    xPosition = tempXPosition;
    yPosition = tempYPosition;
    size = tempSize;
    unselectedColor = tempUnselectedColor;
    hoverColor = tempHoverColor;
    selectedColor = tempSelectedColor;
    buttonOnColor = tempButtonOnColor;
  }
```

Now, we need a custom function to display the object. Put this inside/before the final curly bracket of the class.

```java
void display() {
    
}
```

Copy the code in `draw()` in the first tab and paste it in the `display()` function. You can delete it from the first tab.

```java
void display() {
    rectMode(CENTER);
    
    checkButtonState();
    determineColor();
    
    fill(fillColor);
    square(xPosition, yPosition, size);
    
    fill(stripeColor);
    square(xPosition, yPosition, size * 0.8);
    
    fill(fillColor);
    square(xPosition, yPosition, size * 0.6);
    
    fill(stripeColor);
    square(xPosition, yPosition, size * 0.4);
    
    fill(fillColor);
    square(xPosition, yPosition, size * 0.2);
}
```

Copy the functions that follow `draw()` in the first tab and paste them before the final curly bracket (inside the class) in the second tab (the object tab). The `mouseClicked()` needs to stay on the main tab to work.

```java
  void checkButtonState() {
    // Check if the mouse cursor is within the button
    if (mouseX >= xPosition - size/2 && mouseX <= xPosition + size/2 && mouseY >= yPosition - size/2 && mouseY <= yPosition + size/2) {
      state = 1;    // Hover
    
      if (mousePressed) {
        state = 2;   // Selected
      }
    }
    else {
      state = 0;   // Unselected
    }
  }

  void determineColor() {
    // Determine the fill color based on the state
    if (state == 1) {
      fillColor = hoverColor;
    }
    else if (state == 2) {
      fillColor = selectedColor;
    }
    else {
      if (buttonOn) {
        fillColor = buttonOnColor;
      }
      else {
        fillColor = unselectedColor;
      }
    }
  }
}
```

Code so far:

{% hint style="info" %}
I have added /\* and \*/ around mouseClicked() to "comment out" the function for now
{% endhint %}

First tab

```java
void setup() {
  // Create a canvas that's 600 by 600
  size(600, 600); 
}

void draw() {
  // Set background to black
  background(0);
}

/*
void mouseClicked() {
  // Only run when the state is higher than 0 (not unselected)
  if (state > 0) {
    // Switch the buttonOn variable to its opposite
    buttonOn = !buttonOn;
  }
  
}
*/
```

Second tab

```java
class Button {
  float xPosition;
  float yPosition;
  float size;
  color fillColor;
  color stripeColor = color(0, 0, 0); // Default as black no matter what
  boolean buttonOn = false;
  int state = 0;    // 0 = unselected, 1 = hover, 2 = selected
  color unselectedColor;
  color hoverColor;
  color selectedColor;
  color buttonOnColor;

  Button(float tempXPosition, float tempYPosition, float tempSize, color tempUnselectedColor, color tempHoverColor, color tempSelectedColor, color tempButtonOnColor) {
    xPosition = tempXPosition;
    yPosition = tempYPosition;
    size = tempSize;
    unselectedColor = tempUnselectedColor;
    hoverColor = tempHoverColor;
    selectedColor = tempSelectedColor;
    buttonOnColor = tempButtonOnColor;
  }
  
  void display() {
    rectMode(CENTER);
    
    checkButtonState();
    determineColor();
    
    fill(fillColor);
    square(xPosition, yPosition, size);
    
    fill(stripeColor);
    square(xPosition, yPosition, size * 0.8);
    
    fill(fillColor);
    square(xPosition, yPosition, size * 0.6);
    
    fill(stripeColor);
    square(xPosition, yPosition, size * 0.4);
    
    fill(fillColor);
    square(xPosition, yPosition, size * 0.2);
  }

  void checkButtonState() {
    // Check if the mouse cursor is within the button
    if (mouseX >= xPosition - size/2 && mouseX <= xPosition + size/2 && mouseY >= yPosition - size/2 && mouseY <= yPosition + size/2) {
      state = 1;    // Hover
    
      if (mousePressed) {
        state = 2;   // Selected
      }
    }
    else {
      state = 0;   // Unselected
    }
  }

  void determineColor() {
    // Determine the fill color based on the state
    if (state == 1) {
      fillColor = hoverColor;
    }
    else if (state == 2) {
      fillColor = selectedColor;
    }
    else {
      if (buttonOn) {
        fillColor = buttonOnColor;
      }
      else {
        fillColor = unselectedColor;
      }
    }
  }
}
```

{% hint style="info" %}
I have removed the extra comments to make it less cluttered. Please reference the code near the beginning of this activity to understand what each step does.
{% endhint %}

## Step 3: Display the Objects in the Main Sketch

If you play it now, nothing but a black canvas will appear.

We should create some variables to hold our buttons at the top.

```java
Button redButton;
Button yellowButton;
Button greenButton;
Button blueButton;
```

We can assign/set these buttons in setup() putting _arguments_ in the parentheses that match the parameters in the constructor.

For each, I'll use an unselected color that is a darker version of the color, a hover and selected color that is a lighter tint, and the "on" color the full color.

```java
// Red button 
redButton = new Button(225, 225, 100, color(150, 0, 0), color(255, 100, 100), color(255, 200, 200), color(255, 0, 0)); 

// Yellow button 
yellowButton = new Button(375, 225, 100, color(150, 150, 0), color(255, 255, 100), color(255, 255, 200), color(255, 255, 0));

// Green button 
greenButton = new Button(225, 375, 100, color(0, 150, 0), color(100, 255, 100), color(200, 255, 200), color(0, 255, 0));

// Blue button 
blueButton = new Button(375, 375, 100, color(0, 0, 150), color(100, 100, 255), color(200, 200, 255), color(0, 0, 255));
```

Let's put code in the draw() function to display some button objects we made.

```java
redButton.display();
yellowButton.display();
greenButton.display();
blueButton.display();
```

Code so far:

```java
Button redButton;
Button yellowButton;
Button greenButton;
Button blueButton;

void setup() {
  // Create a canvas that's 600 by 600
  size(600, 600); 
  
  // Red button 
  redButton = new Button(225, 225, 100, color(150, 0, 0), color(255, 100, 100), color(255, 200, 200), color(255, 0, 0)); 
  
  // Yellow button 
  yellowButton = new Button(375, 225, 100, color(150, 150, 0), color(255, 255, 100), color(255, 255, 200), color(255, 255, 0));
  
  // Green button 
  greenButton = new Button(225, 375, 100, color(0, 150, 0), color(100, 255, 100), color(200, 255, 200), color(0, 255, 0));
  
  // Blue button 
  blueButton = new Button(375, 375, 100, color(0, 0, 150), color(100, 100, 255), color(200, 200, 255), color(0, 0, 255));
}

void draw() {
  // Set background to black
  background(0);
  
  redButton.display();
  yellowButton.display();
  greenButton.display();
  blueButton.display();
}

/*
void mouseClicked() {
  // Only run when the state is higher than 0 (not unselected)
  if (state > 0) {
    // Switch the buttonOn variable to its opposite
    buttonOn = !buttonOn;
  }
  
}
*/
```

Output so far (the buttons should have hover and select effects):

![](<../../.gitbook/assets/image (480).png>)

## Step 4: Get the Clicking Effect to Work

The mouseClicked() only works on the first tab, so we'll have to replace the code with references to our buttons.

Remember to take off the /\* and \*/ lines.

```java
void mouseClicked() {
  if (redButton.state > 0) {
    // Switch the buttonOn variable to its opposite
    redButton.buttonOn = !redButton.buttonOn;
  }
  
  if (yellowButton.state > 0) {
    // Switch the buttonOn variable to its opposite
    yellowButton.buttonOn = !yellowButton.buttonOn;
  }
  
  if (greenButton.state > 0) {
    // Switch the buttonOn variable to its opposite
    greenButton.buttonOn = !greenButton.buttonOn;
  }
  
  if (blueButton.state > 0) {
    // Switch the buttonOn variable to its opposite
    blueButton.buttonOn = !blueButton.buttonOn;
  }
}
```

Full code so far:

First tab:

```java
Button redButton;
Button yellowButton;
Button greenButton;
Button blueButton;

void setup() {
  // Create a canvas that's 600 by 600
  size(600, 600); 
  
  // Red button 
  redButton = new Button(225, 225, 100, color(150, 0, 0), color(255, 100, 100), color(255, 200, 200), color(255, 0, 0)); 
  
  // Yellow button 
  yellowButton = new Button(375, 225, 100, color(150, 150, 0), color(255, 255, 100), color(255, 255, 200), color(255, 255, 0));
  
  // Green button 
  greenButton = new Button(225, 375, 100, color(0, 150, 0), color(100, 255, 100), color(200, 255, 200), color(0, 255, 0));
  
  // Blue button 
  blueButton = new Button(375, 375, 100, color(0, 0, 150), color(100, 100, 255), color(200, 200, 255), color(0, 0, 255));
}

void draw() {
  // Set background to black
  background(0);
  
  redButton.display();
  yellowButton.display();
  greenButton.display();
  blueButton.display();
}

void mouseClicked() {
  if (redButton.state > 0) {
    // Switch the buttonOn variable to its opposite
    redButton.buttonOn = !redButton.buttonOn;
  }
  
  if (yellowButton.state > 0) {
    // Switch the buttonOn variable to its opposite
    yellowButton.buttonOn = !yellowButton.buttonOn;
  }
  
  if (greenButton.state > 0) {
    // Switch the buttonOn variable to its opposite
    greenButton.buttonOn = !greenButton.buttonOn;
  }
  
  if (blueButton.state > 0) {
    // Switch the buttonOn variable to its opposite
    blueButton.buttonOn = !blueButton.buttonOn;
  }
}
```

Second tab:

```java
class Button {
  float xPosition;
  float yPosition;
  float size;
  color fillColor;
  color stripeColor = color(0, 0, 0); // Default as black no matter what
  boolean buttonOn = false;
  int state = 0;    // 0 = unselected, 1 = hover, 2 = selected
  color unselectedColor;
  color hoverColor;
  color selectedColor;
  color buttonOnColor;

  Button(float tempXPosition, float tempYPosition, float tempSize, color tempUnselectedColor, color tempHoverColor, color tempSelectedColor, color tempButtonOnColor) {
    xPosition = tempXPosition;
    yPosition = tempYPosition;
    size = tempSize;
    unselectedColor = tempUnselectedColor;
    hoverColor = tempHoverColor;
    selectedColor = tempSelectedColor;
    buttonOnColor = tempButtonOnColor;
  }
  
  void display() {
    rectMode(CENTER);
    
    checkButtonState();
    determineColor();
    
    fill(fillColor);
    square(xPosition, yPosition, size);
    
    fill(stripeColor);
    square(xPosition, yPosition, size * 0.8);
    
    fill(fillColor);
    square(xPosition, yPosition, size * 0.6);
    
    fill(stripeColor);
    square(xPosition, yPosition, size * 0.4);
    
    fill(fillColor);
    square(xPosition, yPosition, size * 0.2);
  }

  void checkButtonState() {
    // Check if the mouse cursor is within the button
    if (mouseX >= xPosition - size/2 && mouseX <= xPosition + size/2 && mouseY >= yPosition - size/2 && mouseY <= yPosition + size/2) {
      state = 1;    // Hover
    
      if (mousePressed) {
        state = 2;   // Selected
      }
    }
    else {
      state = 0;   // Unselected
    }
  }

  void determineColor() {
    // Determine the fill color based on the state
    if (state == 1) {
      fillColor = hoverColor;
    }
    else if (state == 2) {
      fillColor = selectedColor;
    }
    else {
      if (buttonOn) {
        fillColor = buttonOnColor;
      }
      else {
        fillColor = unselectedColor;
      }
    }
  }
}
```

Output:

![The circle click effects were added to show actual clicking.](../../.gitbook/assets/Week9-1\_02.gif)
