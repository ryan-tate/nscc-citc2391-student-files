# SYNTAX RULES

### JS is __CASE SENSITIVE__

```js
const nashState = 'NASHVILLE STATE'
console.log(nashState)
console.log(nashstate) // <-- WE'RE GOING TO THROW AN EXCEPTION HERE DUE TO CASE DIFFERENCE
console.log(NASHSTATE)
console.log(nashState)
```
💡 REMEMBER! An error like this _will halt further execution of your code!_

### SEMICOLONS

Use them, or don't.  Your choice.  But being consistent is good practice.

```js 
const x = 10 
// exactly the same as 
const x = 10; 
```

### WHITESPACE IS IGNORED

```js 
// THIS

if(true){console.log('this is true')}else{consle.log('this is false')}

// IS EXACTLY THE SAME AS THIS 

if ( true ) {
  console.log ( 'this is true' )
} else {
  console.log ( 'this is false' )
}

// OR EVEN THIS (BUT WHY DO THIS???)

if ( true ) {




  console.log ( 'this is true' )
  
  
  
} else {

  console.log ( 'this is false' )
  
  
  
  
}
```

### STRICT MODE

Use it!  Simply include `'use strict'` or `"use strict"` at the top of your js file.  

# IDENTIFIERS

#### Avoid reserved words

`if` `else` `for` `boolean` `int` `string` etc -- see p.63 in your book for full list

### Make your names meaningful

Consider 

```js 
const func1 = (a, b) => {
    const t = a * b
    const g = a + s 
    return { t, g }
}
```

Compared to 

```js
const calculateSalesTax = (subtotal, taxRate) => {
  const taxes = subtotal * taxRate 
  const grandTotal = subtotal + taxes
  return { taxes, grandTotal }
}
```

The programming logic is identical, but one is more easily understood.  Choose __clear__ and __meaningful__ names for your identifiers!

### Naming conventions

```js 
// camel case: first word is all lower case, subsequent words, capitalize first letter.  This is the normal JS convention
let nashvilleState
let hourlyPayRate

// snake case: all lower case, join words with underscore. This is also acceptable
let nashville_state
let hourly_pay_rate
```

#### Rules for names 
- only contain LETTERS, NUMBERS, UNDERSCORE, OR DOLLAR SIGN
- cannot START with a number 
- ARE case sensitive
- CAN be any length 
- CANNOT be the same as any reserved words 

# COMMENTS

Two kinds of comments, block comments and single-line comments.  

Block comments are enclosed by `/* */` and can span multiple lines.

```js 
/*
  This is a multi line, block
  comment that spans mutiple
  lines.  All of it is 
  commented out and will not effect
  the execution of any code
*/
console.log('test')

// This is a single line comment. It can be as long as I want it to be but it must be contained on this line. If I press enter, I'll no longer be in a comment
console.log('this is not a comment at all')
```

Comments are useful for documentation but are also useful for debugging; they allow you a quick way to take out a line or lines of code that may be causing issues!

> WHEN WRITING COMMENTS, IT IS IMPORTANT TO STRIKE A BALANCE.  You can under-comment code, but you can also __OVER__ comment.  Writing better code can reduce the need for frequent comments!

***

# Primitive Data Types

JS has 7 primitive data types:

1. number
2. string
3. boolean
4. symbol
5. null
6. undefined
7. bigint

Chapter 2 primarily talks about the first three: number, string, and boolean.

These are concepts you are likely familiar with from other programming classes but 'numbers' in JS encompass both INTEGERS and DECIMALS.  It can be values like 1, 2, -1, -2, 1.5, -1.5 to `console.log(Number.MAX_SAFE_INTEGER)`

Strings are characters sets.  They are enclosed in EITHER single or double quotes, but you must use the same type to open and close the string. 

Booleans have only two possible values: true or false.  You write true or false, as a boolean, with no quotes. If you put quotes around the words true or false, it becomes a string. Booleans can represent anything with only two states:  true/false, on/off, yes/no, etc.

### `Declaring and initializing variables and constants`

To declare a __VARIABLE__ in javascript, you use the __`let`__ keyword
To declare a __CONSTANT__ in javascript, you use the __`const`__ keyword

```js 

// Let's declare some varibles.
let name = 'Abraham Lincoln'
let birthYear = 1809
let isLiving = false


// you can also use a comma to separate multiple variable declarations 
let coinValue = 0.01, billValue = 5, coinType = 'penny'
```

Constants function exactly like variables, with one exception: their value cannot change one the variable is initialized.

```js 
// Constant Examples
const name = 'Abraham Lincoln' 
const birthYear = 1809
```

`const` vs `let` example 

```js 
let balance = 3450
console.log('Current balance: ', balance)
balance = 3000 // NOTE that we didn't DECLARE a new variable, we're simply reassigning a new value to the existing one
console.log('Current balance: ', balance)

// NOW TRY CONST
let balance = 3450
console.log('First balance: ', balance)
balance = 3000 // <-- WE'LL GET AN ERROR HERE -- we can't reassign a new value to a const
console.log('New balance: ', balance)
```

1. Variables and const both store values. Variable can change as the program executes, but a constant cannot.
2. Use `let` for variables, `const` for constants. Use <kbd>=</kbd> to _initialize_ a value
3. The data type of a variable is determined by the value that is assigned to it. This is *loose typing*, unlike languages with *strong typing* where you must declare the type of a variable upfront and the type cannot change. The type will change automatically to match the value stored.

```js 
  // Consider these examples
  const myNum = 1
  console.log(typeof myNum) // this will print "number"
  
  const myString = 'Test'
  console.log(typeof myString) // this will print "string"
  
  // Now consider 
  let myVariable = 'Pekka Rinne' 
  console.log(typeof myVariable) // string

  myVariable = 35
  console.log(typeof myVariable) // number

  myVariable = true 
  console.log(typeof myVariable) // boolean
  ```
  
  We declared ONE variable `myVariable` and assigned three different values to that variable, and the `type` of the variable changed each time!
  
  4. A variable can be declared but not initialized.  A constant MUST be initialized.

  ```js 
  let x
  x = 10 // this is ok

  const x // this is not ok and will result in an error
  x = 10 
  ```
  
  ***
  
  # Expressions 
  
  |Operator|Name|Description|
|---|---|---|
|<kbd>+</kbd>|Addition|Adds to operands|
|<kbd>-</kbd>|Subtraction|Subtracts the right operand from the left operand|
|<kbd>*</kbd>|Multiplication|Multiplies two operands|
|<kbd>/</kbd>|Division|Divides the right operand into the left. The result is always a decimal|
|<kbd>%</kbd>|Modulus|Divides the right operand into the left and returns the remainder|
|`++`|Increment|Adds 1 to the operand|
|`--`|Decrement|Subtracts 1 from the operand|

```js 
// Examples
console.log('7 + 3 = ', 7+3)
console.log('10 - 2 = ', 10-2)
console.log('10 * 5 =', 10*5)
console.log('10 / 3 =', 10/3)
console.log('10 % 3 =', 10 % 3)

// increment example
let x = 10
x++
console.log('after x++, x is ', x)

// note all of these are the same!
// x = x + 1 
// x += 1
// x++

x = 10 
x--
console.log('after x--, x is ', x)
```

### Order of Operations

```js 
// order of operations, just like math 
console.log(3 + 4 * 5) // will be 23 bc 5*4=20, 20+3=23
console.log( (3 + 4) * 5 ) // will be 35 because 3+4 = 7, 7 * 5 = 35
console.log(13 % 4 + 9) // mod is done first, 13 % 4 = 1, 1 + 9 = 10
console.log(13 % (4+9)) // 0, 4+9 = 13, 13%13 = 0
```

A Special note on order of operations with `++` 

```js 
let x = 10 
console.log(x++) // think you'll get 11?? No! You'll get 10.  Order of ops says this will console.log and THEN increment
console.log(x) // so NOW we'll get 11 bc it was incremented in the previous statement AFTER the console log occurred

x = 10 
console.log(++x) // doing ++ first means you'll see 11 print in the console
console.log(x) // and this will still be 11
```

## Assignments using Expressions


```js 
const subtotal = 200
const taxPercent = 0.05
const taxAmount = subtotal * taxPercent // <-- the expression evaluates and 10 is stored in taxAmount
const total = subtotal + taxAmount // the expression evaluates and 210 is stored in total
```


```js
const width = 4.25 
const length = 8.5 
const perimeter = (2 * width) + (2 * length) // (8.5 + 17) = 25.5
```

Sometimes we need to perform an mathematical operation on a variable and store the result back to the _same_ variable.  Consider 

```js 
let accountBalance = 500
accountBalance = accountBalance + 50 // this is one way 
accountBalance += 50 // this is shorter and accomplishes the same things

accountBalance -= 100 // subtract 100 from accountBalance and store the result back to accountBalance

// less common, but still valid
accountBalance *= .8
```

Increment examples 
```js 
let counter = 1
// all three of these do the same thing
counter = counter + 1 
counter += 1 
counter++
```

***

# String concatenation 

We can concatenate or join two strings together using the `+` operator.

```js
const firstName = 'Neil'
cosnt lastName = 'Armstrong'

// let's try concatenating these strings

console.log( firstName + lastName ) // this will work, but will run the names together like NeilArmstrong

// let's try adding a literal string containing a space between them
console.log( firstName + ' ' + lastName ) // this will give use Neil Armstrong

// that looks more natural!   We can also try 
console.log( lastName + ', ' + firstName ) // Now we get: Armstrong, Neil
```

We can also store the results of string concatenation 

```js
const fullName = firstName + ' ' + lastName 
console.log(fullName) 
```

We can also use the `+=` operator to concatenate a string and store the result in the original variable.

```js 
let name = 'Neil'

name += ' Armstrong'

console.log(name)
```

We can also use __template literals__ by using the <kbd>`</kbd> backtick key -- this is below <kbd>Esc</kbd> and is NOT a single quote!

```js 
const type = 'Tony'                
const winner = 'Lin-Manuel Miranda'
const award = 'Best Musical' 


// note how I have to remember to place spaces before and after, and remember to NOT put a space between winner and the period.  That concats
// take you out of the context more and, in my option, requires more effort to get it right.
const concat = 'And the ' + type + ' for ' + award + ' goes to ' + winner + '. Please come up to accept your award!'

// this does the same thing and where I want to include js, I can simply use ${ } and put the code inside
const message = `And the ${type} for ${award} goes to ${winner}. Please come up and accept your award!`


// it works with other variables, too.
// lets go back to our tax example:
const subtotal = 500
const taxRate = 0.05
console.log(`The taxes due on ${subtotal} will be ${subtotal * taxRate}`)
```

# Special Characters 

You can use escape sequences to insert special characters into your strings. 

- `\n` new line
- `\'` puts  single quote 
- `\"` puts a double quote 
- `\\` puts a backslash in a string


If I want to put this value in a string `Since I'm using single quotes here, I must escape`

One option is to escape the apostrophe.  Alternatively, in this case I could simply switch to double quotes around the string and escaping would not be necessary.

```js 
const a = 'Since I\'m using single quotes here, I must escape.'
```

Alternatively, we could just switch to double quotes
```js 
const a = "Since I'm using single quotes here, I must escape."
```

Another escape example:

```js
// we escape here because the literal string value has both single and double quotes
const a = "Armstrong said \"That's one small step...\" when he walked on the moon"
```

***

# Objects 

An __object__ is a collection of __methods__ and __properties__.  

A __METHOD__ performs a function or does an action 

A __PROPERTY__ is a data item.  


A person can be an object.  It has properties like a name, a birth date, and a height.  It has methods like eat, speak, walk. 

A car could be an object with properties like make, model, color.  Methods like accelerate, brake, startIgnition.

```js 
window.alert('This is an alert')
```

- WINDOW => the object 
- DOT => says we're accessing a method or property of that object
- ALERT => is the method (we know it's a method by the parentheses)
- THIS IS A TEST => the parameter value we're passing into the method

Prompt is similar to alert, except prompt actually takes an input back.  So we can store a result from a prompt.
```js
const name = window.prompt('Name a make of car')

console.log(`The user entered ${name}`)
```

💡 If the user clicks `Cancel` the value will be `null`


The `window` object is a special case because it's considered the global object for JS applications. As such, for this object __ONLY__ you may omit the object so 

```js 
window.alert('something')
// becomes 
alert('soemthing')
// or 
prompt('something')
```

### Prompting for Numerical Input

```js 
const userNumber = prompt("Enter a number", 21)
let newNumber = userNumber + 1

console.log(newNumber)
```

This gives 211, not 21.  Why? The value of `newNumber` is "21" as a string - so the + operator peforms string concatenation, NOT mathematical addition.

Solution: use `parseInt()` or `parseFloat()` to convert a string a number 

```js 
const userNumber = prompt("Enter a number", 21)
let newNumber = parseInt(userNumber) + 1

console.log(newNumber)
```

OR we could parse around the prompt

```js 
const userNumber = parseInt(prompt("Enter a number", 21))
let newNumber = userNumber + 1

console.log(newNumber)
```


> IMPORTANT NOTE ON PARSING INTEGERS FROM DECIMAL NUMBERS!  `parseInt()` will __TRUNCATE__ a decimal value, not round.  So `parseInt(10.9)` yields `10` not `11`

Parsing a number on a non-number value returns `NaN` or "Not a Number"

### toFixed()

The `toFixed()` method available on numbers. This does two things: 
1.rounds to the specified number of decimal places 
2. returns a STRING REPRESENTATION of that number.  

```js
const pi = 3.14159
console.log(pi.toFixed(2)) // shows 3.14

console.log(typeof pi.toFixed(2)) // <-- "STRING" -- NOTE THAT THIS IS NO LONGER A NUMBER!!!!
```

This also works to ADD decimal places if your original number had fewer.

```js
const i = 150
console.log(i.toFixed(10)) // 150.0000000000
```
