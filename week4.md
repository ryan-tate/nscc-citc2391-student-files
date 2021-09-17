### OBJECTS, FUNCTIONS, AND EVENTS


# Objects

JavaScript has a "window" object, with methods like alert and prompt.  We've used those methods in some of our applications to date.  We also learned that the window object is a special case, a 'default' object that we can use without expressly calling `window.` to get to its methods.

We have also used the document object, using the `write()` method to add content to our DOM.

A object is a collection of _methods_ (to do actions) and _properties_ which contain data.

----

Objects aren't only something that exists in the browser or natively in JavaScript.  You can actually create your own objects.  

Example of a custom object

```js
const car = {
    // properties: these contain data about our object
    make: 'Ford',
    model: 'Mustang',
    isRunning: false,
    gear: 'N',
    
    // methods: actions our object can perform 
    startEngine: function() {
        this.isRunning = true
    },
    killEngine: function() {
        this.isRunning = false
    },
    shiftUp: function () {
        if (this.gear == 'N') {
            this.gear = 1
        } else if (this.gear >= 1 && this.gear <= 5) {
            this.gear++
        } 

        console.log(`Now in gear ${this.gear}`)
    }
}

// examples of using our car object 

console.log(car.isRunning)
car.startEngine()
console.log(car.isRunning)
car.killEngine()
console.log(car.isRunning)

// let's try shifting

for (let i = 0; i < 10; i++) {
  car.shiftUp()
}

```

-------------

## Using the Window Object


Like `prompt()` and `alert()`, window has a `confirm()` method.

```js 
'use strict'

const response = confirm('Are you sure?')

console.log(response) // will be true (OK) or false (Cancel)
```

This gives a popup message similar to an alert, but shows the user two options: OK or Cancel.  If the user clicks OK, the confirm method returns true.  If they click cancel, it returns false.

There are many uses for this type of confirmation. You likely see them all the time in applications you use.  Are you sure you want to delete.  You're about to close without saving.... things like that. 

## Using the Document Object 

The _document_ object is the highest object in the DOM structure.  It represents the HTML elements on a page.

Unlike the `window` object, document is not the default object, so you __do__ need to code the `document.` to access it's methods and properties.


### Query Selector

`document.querySelector` is one of the most important links between your HTML markup and the JavaScript you will write to interact with it.  

Query Selector Example

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Intro to JS</title>
        <style>
          .blue {
            color: blue
          }
          .hasError {
                color: red;
                text-decoration: underline;
                text-decoration-style:dotted
            }
        </style>
    </head>
    <body>
        <h1>This is a demo</h1>

        <p id="first_paragraph" class="top2">
            This is a paragraph of text
        </p>

        <p id="second_paragraph" class="top2">
            This is another paragraph
        </p>

        <p>
            This is my last paragraph
        </p>

    </body>
</html>
```

Remember that JavaScript selectors work exactly like CSS selectors.  We can select a type (h1, div, p, etc), or a class (using a dot and the class name) or an id (using a hash and the id).

Select the heading using the h1 type. 

```js
const heading = document.querySelector('h1')

console.log(heading) // note that we print the h1 to the console.
```

Change the text property of the heading.

```js
heading.innerText = 'New Heading Value'
```

Let's add our 'blue' class.  Remember our H1 didn't have a class at all. We're going to add a class to it, and that will apply styles associated with that blue.

```js
heading.className = 'blue'
```

Try using a selector that has more than one element in the DOM

```js
const paragraphs = document.querySelector('p')
console.log(paragraphs)
```

Note that you'll only get the first occurrence of that element using `querySelector()` no matter how many items are on the page.

To get all, use `querySelectorAll()`.  That is going to return an __array__ of elements. 

Modify to `querySelectorAll()`

```js
const paragraphs = document.querySelectorAll('p')
console.log(paragraphs)
```

This gives a 'nodeList', essentially an array or list of the nodes.

Use a for loop to append text to all `p` 

```
for (const p of paragraphs) {
  p.innerText += '. This has been updated'
}
```

Each time this loop iterates, the constant 'p' is the individual 'p' tag. 

----

## Using Textbox and Number objects 

```HTML
<body>
        <h1>This is a demo</h1>

        <p id="first_paragraph" class="top2">
            This is a paragraph of text
        </p>

        <p id="second_paragraph" class="top2">
            This is another paragraph
        </p>

        <p>
            This is my last paragraph
        </p>

        <label>A Textbox</label>
        <input type="text" id="my_text" value="Initial Value">
    

    </body>

    <script>
        // one way to get this  
        const element = document.querySelector('#my_text')
        const userInput = element.value 

        // or we could do this all as one action by 'chaining' querySelector and value 
        const val = document.querySelector('#my_text').value

        // what if our input was a number 

        let input = document.querySelector('#my_text')
        input = input.value 
        input = parseInt(input)

        // OR 

        const a = parseInt(document.querySelector('#my_text').value)
    </script>
```

Using the assignment operator `=` and the `.value` prop we can change the textbox's value:

```js 
element.value = 'New value set by js'
```

We can also set a disabled property 

```js 
element.disabled = true
```

There are serveral methods we can use with our textbox.  

Demo 

1. `.focus()` -- Now we we reload, our text box already had focus, the cursor is there and we can start typing
2. `.select()` -- gives focus and highlights existing value for easy replace
3. `.remove()` -- takes the element off the page 

We're going to work more with textboxes later in the assignment as we look at events.

---

## Dates

Unlike strings or numbers, there is not a primitive data type of dates. To use a date, you have to _construct_ or _instantiate_ an instance of the date class like this .

```js 
const today = new Date() // similar to the syntax we used for new Array(10)
```

Some date methods:

```js
console.log( today.toDateString() )
console.log( today.getFullYear() )
console.log( today.getDate() )
console.log( today.getMonth() )
```

Create a specific date:

```js 
const expirationDate = new Date('10/17/2019')
console.log( expirationDate.toDateString() )
```

## Strings 

Length prop:

```js 
let str = "This is my string"
console.log(str.length) // gets the length of the string.  length is a property of teh String object, used here on a primitive string
```

### Methods

We can change the case of a string using `toUpperCase()` or `toLowerCase()`.   These can be really useful for comparisons.  

Substring methods help us extract partial strings.  JS has two substring methods and each works a little different.

`substr(start, length)` returns a substring that starts at the specified index (starting at 0) and contains the specified number of characters.  If I put `.substr(4, 10)`, we're going to get 10 characters, starting at position 4.  

```js 
const str = "Never gonna give you up, never gonna let you down"
console.log(str.substr(6, 10)
```
That means str.substr(6,10), the result will have 10 characters, starting at index 6.

`substring(start, stop)` however, takes in a start index and ending INDEX - both counting from 0.  So the result will have only 4 characters: those from positions 6, 7, 8, 9.  Note it does not include the character at the stop position.  

We can also use `indexOf()` to find a specific character or string's position in a string.

```js 
const str = "Never gonna give you up, never gonna let you down"
const indexOfComma = str.indexOf(",")

// we can combine this with substr to extract everything before that
const sub = str.substr(0, indexOfComma)

```
# Functions

A function is a block of code that we call (or invoke) or perform a task or set of actions.

A function has a __name__, it may take in one or more _parameters_ and it can optionally _return_ a value.

## Function Declarations

Begin with the keyword `function`, then the name.  Then in parens, we list any parameters the function takes.  Enclose the code block in braces.

```js
function sayHello() {
    console.log('Hello World')
}

// to call the funciton, use the name and pass parameters if needed 
sayHello() // this takes no params
```

```js 
function saySomething(message) {
    console.log(message)
}

// call the function, this time passing in a param 

saySomething("hello")

// or 

const mmyMessage = "Hello!!!"
saySomething(myMessage)
```

```js 
function calculateSquare(number) { 
    console.log(number * number)
}

calculateSquare(2)
calculateSquare(10)
calculateSquare(17)
```

Let's change our square function to RETURN a value instead of printing it.  

```js 
function calculateSquare(number) {
    return(number * number)
}

const value = calculateSquare(2)
// or use it directly 

console.log(calculateSquare(2))
```

Example from wk 2 hw

```js 
"use strict";

const length = parseInt(prompt("Enter the length"));

const width = parseInt(prompt("Enter the width"));

const area = parseInt(length * width);

const periemter = parseInt(2 * (length + width));

// display results
document.write(`<p><label>Length: </label>${length}</p>`)
document.write(`<p><label>Width: </label>${width}</p>`)
document.write(`<p><label>Area: </label>${area}</p>`)
document.write(`<p><label>Perimeter: </label>${periemter}</p>`)
```

That output is tedious and repetitive.  We can replace with a function.

 

```js
// our writeValue() function will take two parameters: label and value.  The label will be the string we're printing as the label.  The value is the value we're printing for that label
function writeValue (label, value) {
    document.write(`<p><label>${label}: </label> ${value}</p>`)
}

// now 
writevalue('Length', length)
writeValue('Width', width)
writeValue('Area', area)
writeValue('Perimeter', perimeter)
```

### `$()` function

Typically you want meaningful function names.  You will use a verb-noun combo a lot.  saySomething.  doSomething. calculateValue. Things like that.

The $ function is all about simplifying query selectors.

We already discussed that you can use document.querySelector() and pass in a selector to get that element 

```js 
const element = document.querySelector("#myId")
```

or to get a value from a text box, we can use

```js 
const element = document.querySelector("#myId").value
```

The $ function lets us trim that down to a much shorter call.

```js
function $ (selector) {
    return document.querySelect(selector)
}
```

Now we can change `document.querySelector("#myId")` to just `$("#myId")` or `document.querySelector("#myId").value` to `$("#myId").value`

### Things to note with Function and Function Declarations

1. Functions are hoisted.  This means they are logically pulled to the top of the code.  You can call a function above the definition for that function.

```js 
sayHello()
console.log('I haven't coded my function yet')

function sayHello() {
    console.log('hello')
}
```

2. A return statment will exit your function, even if there is more code.

```js 
sayHello()

function sayHello() {
    console.log('This is my first statement')
    
    console.log('This is my second statement')
}

```

Now add a return in there

```js
function sayHello() {
    console.log('This is my first statement')
    return   
    console.log('This is my second statement')
}
```

And note that the second statment will NOT be executed.

## Function Expressions

Function expressions use the assignment operator `=` to assign a function to a variable or constant name 

```js
const sayHello = function() {
    console.log('hello world!')
}
```

```js 
const $ = function(selector) {
    return document.querySelector(selector)
}
```

So the only real difference in the _syntax_ is `const name = function` vs `function name`

One key difference in usage is that unlike function declarations, function expressions are __NOT__ hoisted.  

This works :

```js 
sayHello()

function sayHello() { 
    console.log('Hello World')
}
```

But this does __NOT__:

```js 
sayHello()

const sayHello = function() { 
    console.log('Hello World')
}
```

> My recommendation - don't do this, at least for now.

## Arrow functions 

Arrow functions are a shorter, more concise way to write function expressions.

```js 
const sayHello = () => {
    console.log('hello world')
}
```

We still use const (or let), followed by the name that will store the function, then an assignment operator.  We list the parameters in parens, and then we use an arrow `=>` followed by the curly braces.

There are a couple of special cases in array functions to be aware of.

First, if an arrow function contains only a single statement, you can omit the `{}`

```js 
const sayHello = () => {
    console.log('hello world')
}

// becomes

const sayHello = () => console.log('hello world')
```

Another shortcut is that if there is ONLY ONE parameter -- not zero, not more than one -- EXACTLY one param, you can omit the parens around it.

```js 
//lets remember our calculate square function 
function calculateSquare (number) {
    return number * number
}
```

Turned into an arrow function this becomes 

```js
const calculateSquare = number => number * number
```

Our `number` param does not require parens because its the only parameter.  (Could also be written as `(number)`.  Our return statement is omitted as are the curly braces.  Here you can start to see where arrow functions can save you some time!

Our query selector `$` function can also be rewritten to an arrow function

```js
const $ = () => document.querySelector(selector)
```

Arrow functions are a more precise way to code function expressions.

*** 

# Scope

When we talk about scope in programming, we're referring to the visibility of your code.  In other words, scope refers to where in your program you can use the variables, constants and functions you have defined.  

Variables and constants defined outside of functions are considered to have global scope.  That means they can be used by a function without passing them to function as a parameter.

```js
const taxRate = 0.07

const taxAmount = calculateTaxes(100)

console.log(taxAmount)

function calculateTaxes (subtotal) {
    return subtotal * taxRate
}
```

In this example, taxRate is a global variable, declared outside any function. As such, I can use it in my calculation inside my function without explicitly passing it in as a parameter.

Reconfigure this function instead of returning the taxAmount, we'll set a global variable inside the function and access the value from the global scope.

```js
const taxRate = 0.07
let taxAmount = 0 

calculateTaxes(100)

console.log(taxAmount)

function calculateTaxes(subtotal) {
    taxAmount = subtotal * taxRate
}
```

Let's look at an example of a local scope

```js 
for (let i = 0; i < 10; i++) {
    console.log(i)
}

// note that i prints a value through each loop iteration.  

console.log(i) // <---- ERROR, because i only exists in the scope of the loop, it is LOCAL to the loop.  It does not exist here.


```

Another local scope

``` js 
let x = 0

if (x < 10) {
    x = 100
    let y = 75
} 

console.log(x) // x still exists, it was declared globally and used inside the scope of the if
console.log(y) // y on the other hand was declared locally.  it is not defined outside that scope.
```

### Local scope overrides the global scope

```js
let x = 100, y = 100 // global

console.log(y)

if (x == 100) {
    let y = 75 // local y
    console.log('y inside the if statement: ', y) // block (local) y
}

console.log('y outside the if statement: ', y) // global y
```

We had a global `y` with a value of 100.  Inside the local scope of our if, we declared a different y - a y with local scope.  when we access y inside that scope, the LOCAL y will take precedent.  When we print y inside the if, we see 75.  But notice when we get back OUT, y is back to 100.  Because the global y never changed.

If we go below `let y = 75` and add a line that says `y = 50` we'll now see 50 printed inside and 100 still printed outside.  Our assignment, just like the log, goes against our LOCAL y. 


### Proper use of scope

Whenever possible you want to use LOCAL scope for variables.  

Consider two versions of a function:

```js 
const taxRate = 0.07
let tax = 0 

const calculateTax = subtotal => {
    tax = subtotal * taxRate
    tax = tax.toFixed(2)
}

calculateTax(100)

alert(tax)
```


```js 

const calculateTax = (subtotal, taxRate) => {
    const tax = subtotal * taxRate
    return tax.toFixed(2)
}

const tax = calculateTax(100, 0.07)
alert(tax)
```

These may not seem very different viewed here, be consider if there are 75 lines of code between `let tax = 0` and the `calculateTax` function in the first example.  What if there are multiple functions that can all affect the global variable `tax`.  Using local variables make our code much cleaner and less error prone.

# Events

JS commonly need to respond to actions like a user clicking on a button.  These actions are called _events_.

The functions that handle events are called _event handlers_.

A few common events:

|Object|Event|Occurs|
|-- |-- |-- |
|window|load|the whole page has been loaded into the bdroawer including external style sheets and images|
|document|DOMContentLoaded|The HTML doc has been loaded and the DOM is ready|
|button|click| |
|control or link|focus|The control receives focus|
| |blur|The control loses focus|
|control|change|The user changes the value in the control|
||select|The user selects text in a text box or text area|
|element|click||
||dblclick||
||mouseover|moves the mouse over an element|
||mousein|moves the mouse into the element|
||mouseout|moves the mouse out of the element|

## Attaching an Event Handler to an Event 

An event handler is a __function__ that is executed when an event occurs.  As the name implies, it __handes__ the event.


To attach an event handler, you the `addEventListener()` method.  This takes two parameters.  The first is a string with the name of the event to listen for.The second is a function that handles the event.

```html
<button id="alertBtn">Click Me</button>
<button id="removeBtn">Remove Alert</button>
```

```js 
const $ = selector => document.querySelector(selector)

const showAlert = () => alert("you clicked the button")

$('#alertBtn').addEventListener('click', showAlert)

```

Note that you don't code the `()` parens after the name of the constant that stores the function.  That's because we're attaching the event handler, NOT calling the function.  The function will be called by the event handler when the event fires, but we aren't calling it HERE; we are just attaching it.

## Removing an Event Handler 

Although used less frequently than attaching event handlers, there are times when you may need to remove an event handler.  The syntax is exactly the same, but with `removeEventListener` instead of `addEventListener`

```js 
const $ = selector => document.querySelector(selector)

const showAlert = () => alert("you clicked the button")
const unbindAlert = () => $('#alertBtn').removeEventListener('click', showAlert)

$('#alertBtn').addEventListener('click', showAlert)
$('#removeBtn').addEventListener('click', unbindAlert)

```

## Anonymous Functions with Event Handlers

In the previous examples, we declared functions to use as event handlers.

This is useful when you may need to call the function you attached to the event in OTHER circumstances.  It is also necessary if you need to remove the event handler.  You cannot remove an event handler bound to an anonymous function.

If you do not need to reuse the code outside of the event handler, and you do not need to remove it the listener, you can use an _anonymous function_ instead.

```js 
const $ = selector => document.querySelector(selector)

$('#alertBtn').addEventListener('click', () => alert("You clicked me!"))
```

```js 
const $ = selector => document.querySelector(selector)

$('#alertBtn').addEventListener('click', () => {
    const value = prompt("Enter a value")
    alert(`You entered ${value}`)
})
```

# Event Object

When an event occurs, the browser will automatically pass an Event object to the function that's handling the event.  This object provides properties and methods that you can use to work with that event.

The __currentTarget__ property contains an object that represents the HTML element that the event handler is attached to.  So for a button click, it will be the button.

```js
const $ = selector => document.querySelector(selector)

$('#alertBtn').addEventListener('click', (event) => {
    console.log(event.currentTarget)
    // also try event.currentTarget.innerText
    // also try event.currentTarget.id
    // also try event.currentTarget.type
})
```

```html
<a href='http://www.nscc.edu'>NSCC</a>
```

```js
const $ = selector => document.querySelector(selector)

$("a").addEventListener('click', (event) => {
    event.preventDefault()
    alert(`You clicked a link for ${event.currentTarget.innerText}`)
})
```

*****

# Applications

Let's put this all together and look at how these components work together in an application

```HTML AND CSS 
    <body>
        <main>
            <h1>The Miles Per Gallon Calculator</h1>

            <div>
                <label for="miles">Miles Driven: </label>
                <input type="text" id="miles">
            </div>

            <div>
                <label for="gallons">Gallons of Fuel Used: </label>
                <input type="text" id="gallons">
            </div>

            <div>
                <label for="mpg">Miles Per Gallon: </label>
                <input type="text" id="mpg" disabled>
            </div>

            <div>
                <label>&nbsp;</label>
                <input type="button" id="calculate" value="Calculate MPG">
            </div>


        </main>
        <script src='mpg.js'></script>
    </body>
```

```js 
'use strict'

const $ = selector => document.querySelector(selector)

const getErrorMsg = lbl => `${lbl} must be a valid number greater than zero`

const focusAndSelect = selector => {
    const element = $(selector)
    element.focus()
    element.select()
}

const processEntries = () => {
    const miles = parseFloat($("#miles").value)
    const gallons = parseFloat($("#gallons").value)

    if (isNaN(miles) || miles <= 0) {
        alert(getErrorMsg('Miles Drive'))
        focusAndSelect("#miles")
    } else if (isNaN(gallons) || gallons <= 0) {
        alert(getErrorMsg('Gallons of fuel used'))
        focusAndSelect('#gallons')
    } else {
        $("#mpg").value = (miles / gallons).toFixed(2)
    }
}

document.addEventListener('DOMContentLoaded', () => {
    $("#calculate").addEventListener('click', processEntries)
    $("#miles").focus()
})
```


Notice that other than the 'use strict' declaration and the document event listener, everything is placed within functions.  Nothing has global scope!!

****

## Email List Application

```html

    <body>
        <main>
            <h1>Please join our email list</h1>
            <form id='email_form' name='email_form' action='join.html' method="get">
                <div>
                    <label for="email_1">Email Address:</label>
                    <input type="text" id="email_1" name="email_1">
                </div>

                <div>
                    <label for="email_2">Re-enter Email Address:</label>
                    <input type="text" id="email_2" name="email_2">
                </div>

                <div>
                    <label for="first_name">First Name:</label>
                    <input type="text" id="first_name" name="first_name">
                </div>

                <div>
                    <label>&nbsp;</label>
                    <input type="submit" id="join_list" value="Join our List">
                    <input type="button" id="clear_form" value="Clear Form">
                </div>
            </form>
        </main>
        <script src='email.js'></script>
    </body>
</html>
```

```js
'use strict'

const $ = selector => document.querySelector(selector)

document.addEventListener('DOMContentLoaded', () => {

    $("#join_list").addEventListener('click', evt => {
        // get values user entered in text boxes
        const email1 = $("#email_1").value
        const email2 = $("#email_2").value
        const firstName = $("#first_name").value

        // create an error message and set to an empty string
        let errorMessage = ''

        // validate user entries, add to error if invalid
        if (email1 == '') {
            errorMessage += "First email is required.\n"
        }

        // note we are NOT else else if -- we want ALL of these conditions to evalute, regardless if the previous one was true

        if (email2 == '') {
            errorMessage += "Second email is required.\n"
        }

        if (email1 != email2) {
            errorMessage += "Both emails must match.\n"
        }

        if (firstName == "") {
            errorMessage += "First name is requried.\n"
        }

        if (errorMessage != "") {
            alert(errorMessage)
            evt.preventDefault()
        }
    })

    // clear the form 
    $("#clear_form").addEventListener('click', () => {
        $("#email_1").value = ""
        $("#email_2").value = ""
        $("#first_name").value = ""

        $("#email_1").focus
    })

    $("#email_1").focus()

})

```
