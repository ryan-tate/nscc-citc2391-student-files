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
