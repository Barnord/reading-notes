# Objects
Variables and functions in an object are called properties and methods respectively. Names inside of objects are known as keys. Objects are signified by curly brackets. Seperate different values in an object with a comma, instead of the usual semicolon.

## Accessing an Object
You can access properties and methods of an object with dot notation, or using square brackets.
```
object.property
object.method()
object['property']
object['method']()
```
Square brackets are normally used when
* the property or method has special characters
* the name of the property is a number
* a variable is being used instead of a property name

JS knows objects declared as the same thing are different based on the variables inside them. The textbook used the example of hotel Quay and hotel Park. You can call variables inside those objects by using ```this.property``` instead of ```object.property```

## The DOM
The Document Object Model specifies how browsers should model an HTML page and how JS can access and change the contents of a web page while it's in the browser.

### Making a Model of the Page
When the browser loads a page, it creates a model of it in memory. The DOM specifices the way the model is structured using a DOM tree. The DOM is called an object model because the DOM Tree (the model) is made of objects. Each object is representative of a diffrerent part of the page loaded in the browser window.

### Accessing and Changing the HTML Page
The DOM also defines methods and properties to access and update each object in this model, changing the page appearance. People call the DOM an Application Programming Interface (API). APIs let programs and scripts talk to each other. The DOM states what your script can ask the browser about the current page, and how to tell the browser to update the users visuals.

### Using the Dom
This is a two step process, the steps are as follows.

#### 1.Access the Elements
Select an individual element.
* ```getElementById()``` Uses an elements id attribute
* ```querySelector()``` Uses a CSS selector and returns the first matching element

Select multiple elements.
* ```getElementsByClassName()``` Selects all elements that have a specific value for their class attribute.
* ```getElementsByTagName()``` Selects all elements that have the specified tag name.
* ```querySelectorAll()``` Uses a CSS selector to select all matching elements.

Traversing Between Element Nodes
* ```parentNode``` Selects the parent of the current node. (Returns one element)
* ```previousSibling/nextSibling``` Selects corresponding sibling from the DOM tree
* ```firstChild/lastChild``` Selects the corresponding child from the DOM tree.

#### Step 2: Work With The Elements
* Access/Update text nodes
  1. Select the element
  2. Use ```nodeValue``` to get text from the element
  * ```nodeValue``` Lets you acces or update a text node.
* Work with HTML content
  * ```innerHTML``` allows access to child elements and text content
  * ```textContent``` Only allows acces to text content
  * ```createElement(), creatTextNode(), appendChild()/removeChild()``` These methods allow you to create new nodes, add notes to a tree, and remove nodes from a tree, this is called DOM manipulation.
* Access or Update Attribute Values
  * ```className / id``` Lets you get or update the value of the class and id attributes.
  * ```hasAttribute(), getAttribute(), setAttribute(), removeAttribute()```
  Checks if an attribute exists, gets the value, updates the value, and removes an attribute, respectively.
  
  #### Accessing Elements
  Methods that only ever return one element will tell you the element, which can be stored in a variable. If a method is capable of returning multiple elements, it will always return a NodeList, which is an array of nodes.