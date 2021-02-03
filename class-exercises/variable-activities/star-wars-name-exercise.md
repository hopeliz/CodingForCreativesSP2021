# Star Wars Name Exercise

The steps below walk you through a Processing activity that uses **variables** and **printing to the console**. All code should allow you to copy and paste.

## The Goal

To find out your "Star Wars Name."

According to the graphic that has been shared all over Facebook, that's:

First Name:

1. Take the first three letters of your last name.
2. Add the first two letters of your first name.

Last Name:

1. Take the first two letters of your ~~mother's last name~~. parent's first name
2. Add the first three letters of the ~~city~~ state in which you were born.

{% hint style="danger" %}
I changed the last two since the info \(if you used real info\) can be used for identity theft.
{% endhint %}

## Step 1: Create the Variables for the Four Steps

These will be strings.

```java
String lastName;
String firstName;
String parentName;
String state;

void setup() {
}

void draw() {
}
```

## Step 2: Assign the Variables

Normally, these would be assigned after prompting the user and storing their response. To pretend that happened, let's assign the variables in the `setup()` function.

```java
String lastName;
String firstName;
String parentName;
String state;

void setup() {
    lastName = "Moore";
    firstName = "Hope";
    parentName = "Michael";
    state = "Ohio";
}

void draw() {
}
```

## Step 3: Use .substring\(\) to Get a Portion of a String Variable

To get parts of the strings \(i.e. "first 3 letters" etc.\).

### **Using a function on an existing variable**

The two ways you will see a variable work in or with a function are: 

First way:   
  
The variable is used within the parentheses as information being used  
  
Example: 

```java
String greeting = "Hello!";

void setup() {
    print(greeting);
}
```

Prints:

> Hello!

Second Way:

The name of the variable followed by a period and the function name. 

We will look further into this idea as we progress through the course. It's like starting with an object \(whatever the variable stands for\) and adding something to it OR digging deeper to get the object's properties.

Example using the built-in `length()` function that gets the number of characters in a string: 

```java
String mysteryWord;

void setup() {
    mysteryWord = "Booger";
    
    print("The mystery word has " + mysteryWord.length() + " letters.");
}
```

Prints:

> The mystery word has 6 letters.

### **Getting a Substring of a String**

We need to get the substrings of the variables we have. 

Let's use the built-in `.substring()` function:

`.substring(index of first letter)` __starts the string with the index/location of the first letter.

`.substring(index of first letter, index of limit letter)` starts the string with the index/location of the first letter and ends on the letter before the limit letter.

We'll use the second one since we need the beginning of each string. Remember to add a space between the second and third variables to show a separation between the first and last name.

```java
String lastName;
String firstName;
String parentName;
String state;

void setup() {
  lastName = "Moore";
  firstName = "Hope";
  parentName = "Michael";
  state = "Ohio";
  
  println(lastName.substring(0, 3) + firstName.substring(0, 2) + " " + parentName.substring(0, 2) + state.substring(0, 2));
}

void draw() {
}
```

Prints:

> MooHo MiOh

## Step 4: Polish It a Little

You'll notice the names have capital letters in the middle of each. We can make those lowercase by using the `.toLowerCase()` function. Just attach it to the end of the `substring()` function code to add the effect.

```java
String lastName;
String firstName;
String parentName;
String state;

void setup() {
  lastName = "Moore";
  firstName = "Hope";
  parentName = "Michael";
  state = "Ohio";
  
  println(lastName.substring(0, 3) + firstName.substring(0, 2).toLowerCase() + " " + parentName.substring(0, 2) + state.substring(0, 2).toLowerCase());
}

void draw() {
}
```

Prints:

> Mooho Mioh

## Python Version

{% hint style="info" %}
Thanks to Nick Montana for providing an example in the discord last semester. This has been modified to be similar to the exercise above.
{% endhint %}

**In this example:**

1. variables are defined at the top and given initial values.
2. The substrings are put into their own variables.
3. Variables are created for each name of the Star Wars name.

```python
last = "Moore"
first = "Hope"
pfirst = "Michael"
plast = "Ohio"

# Substrings
swfirst1 = last[:3]
swfirst2 = first[:2]
parent = pfirst[:3]
state = plast[:3]

# Create the names
starwars_first = swfirst1 + swfirst2.lower()
starwars_last = parent + state.lower()

print(starwars_first + " + starwars_last)
```

**What to look at:**

In python, substrings are controlled with square brackets `[ ]` and within them, the beginning letter and the end letter don't need a number to represent them. The "to", as in "from this letter **to** this letter" is symbolized by a colon \( `:` \)

The function to make the string lowercase is `.lower()`

