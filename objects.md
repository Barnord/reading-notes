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