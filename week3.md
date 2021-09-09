### Notes from Week 3 lecture

Topics 
1. Conditional Expressions 
2. Logical Operators 
3. Basic Control Statements
4. Arrays

# Conditional Expressions 

Conditional Expressions evaluate to `true` or `false` and can be used to help direct the flow of your program.

## Relational Operators

One way to implement conditional expressions is by using relational operators 

|Operator|Name|Description|
| -- |-- |-- |
| == | Equal to | True if both operands are equal |
| != | Not equal to | True if the operands are not equal |
| > | Greater Than | True if left operand greater than right |
| < | Less Than | Tur if left operand less than right |
| >= | Greater than or equal to | True if left operand greater than OR equal to right |
| <= | Less than or equal to | True if left operand less than OR equal to right |

```js 
const x = 5, y = 7 

console.log('Equality == ')
console.log(x == y) // false, because  x (5) is not equal to y (7)
console.log(x + 2 == y) // true, because x + 2 = 7, and 7 is equal to 7

console.log('\nNot Equal != ')
console.log( x != y ) // true, becasue 5 is NOT equal to 7
console.log( x + 2 != y ) // false, because 7 is equal to 7, so the assertion that they are not equal is false

console.log('\nGreater Than >')
console.log(x > y) // 5 > 7? false
console.log(x + 10 > y) // 15 > 7 ? true 
console.log(x + 2 > y) // 7 > 7 is false

console.log('\nGreater Than or Equal to >=')
console.log(x >= y) 
console.log(x + 10 >= y)
console.log(x + 2 >= y) // now that we're looking at >=, this is true 7 >= 7 is true

console.log('\nLess Than < ')
console.log(x < y)

console.log('\nLess Than <= ')
console.log(x <= y)

```

### `isNaN()`

Another relational expression you can use it the `isNan()` method.  This tests whether the value of a string passed into the method __can be converted to a number__.  If the value cannot be converted to a number, the expression is `true`.  If the value CAN be converted a number, the expression returns `false`.

```js 
let str = 'blue'
console.log( isNaN(str) ) // true, because blue cannot be converted to a number

str = 'two'
console.log( isNaN(str) )  // true, because the string 'two' cannot be converted to number

str = '1234'
console.log( isNaN(str) )  // false, even though 1234 is a string when put in quotes, it CAN be converted to a number.
```

# Logical Operators 

Conditional expressions can be made compound, meaning we combine more than one expression.

The logical operator here that joined those together is `AND`.  For an `AND` condition to be true, BOTH of the conditions must be true.  If either one is false, the entire thing is false.

Another logical operator we can use is `OR`.  For an `OR` condition to be true, only ONE of the side need to tbe true.

#### Truth table for AND

|Left|Logical Operator|Right|Result|
|---|---|---|---|
|true|And|true|true|
|true|And|false|false|
|false|And|true|false|
|false|And|false|false|

#### Truth table for OR 

|Left|Logical Operator|Right|Result|
|---|---|---|---|
|true|Or|true|true|
|true|Or|false|tru|
|false|Or|true|true|
|false|Or|false|false|


AND is only true, when both sides are true

Or is only false if BOTH sides are false.

If the left side of an AND is false, we don't even need to look at the right side.

Similarly, if the left side of an OR is TRUE, we dont even need to look at the right side.

In JS, And is written as `&&` and OR is written as `||`. 

```js
const x = 5, y = 7
console.log(x < 10 && y > 2) // true because both sides are true
console.log(x < 3 && y > 2) // becomes false because 5 is not less than 3
console.log(x < 3 || y > 2) // but switching to OR makes it true again because we only need ONE side to be true here

```

### NOT `!` operator

You can reverse the value of a boolen with `!`

```js 
const x = 5, y = 7
console.log( x < y ) 
console.log( !(x < y) )
console.log( isNaN('1234') )
console.log( !isNaN('1234') )

```

*** 

# Basic Control Statements 

### If statements 

```js 
// syntax 
if (condition) {
  // do something
}
```

```js
let finalGrade = 79

if (finalGrade >= 60) {
  console.log("passing") // this code executes if our condition is true, i.e., grade is 60 or above
} else {
  console.log('not passsing') // this code executes if our condition is false
}
```

If statemes can have an else, but it is not required.  

```js 
let finalGrade = 79

if (finalGrade >= 90) {
  console.log('I got an A')
} else if (finalGrade >= 80) { // NOTE it isn't necessary to add an && finalGrade < 90 because if it was greater than 90, it would already be handled
  console.log('I got a B')
} else if (finalGrade >= 70) {
  console.log('I got a C')
} else if (finalGrade >= 60) {
  console.log('I got a D')
} else {
  console.log('I failed')
}

```

When you are evaulating a boolean, you dont have to write out the comparison

```js
let age = 20
let isVotingAge = age >= 18

if (isVotingAge == true) { // this is the same as saying if true == true)
  alert("You can register")
} 


// we could just write 

if (isVotingAge) {
  alert("You can register")
}
```

### ❗ WARNING : ASSIGNMENT VS EQUALITY 

```js 
// remember that = is assignment, == is equality
let x = 10

if (x = 3) {
  console.log("x is 3")
} else {
  console.log('x is not 3')
  
// in the above, we set x equal to 3, we did NOT test equality!

let x = 10

if (x == 3) { // note the change from = to == here
  console.log("x is 3")
} else {
  console.log('x is not 3')
```

## While and Do-While loops

While and do-while loops are two ways to repeat code (loop) based on a conditional expression.

The syntax of a while loop is this:

```js 
while (some condition) {
  // do stuff 
}
```

```js 
// let's print all the numbers from 0 to 10 
let i = 0 
// I could just console.log(0), console.log(1) ... console.log(10). but what If I wanted to go to 1000?  10,000?  See where this becomes hard?
// lets use a loop instead 

while (i <= 10) {
  console.log(i++)
  
  /*
  alternatively, 
  console.log(i)
  i += 1
  */
}
```

It is extremely important to consider your conditions when creating a while or do-while loop. 

This would cause an infinite loop and crash your browser!

```js
let i = 0

while (i >= 0) {  // i will ALWAYS be greater than or equal to 0
  console.log(i++)
}
```

We enter the loop at 0, and each time the loop iterates, we add 1.  So number becomes 1, then 2, then 3, and so on.  When will number EVER be < 0?  When will our loop end?  NEVER!  This is an __INFINITE LOOP__.

A while loop is tested at the BEGINNING of execution.  It is possible that your while loop may never be executed at all.

```js 
let i = 0

while (i > 10) {
  console.log(i++)
}
```

In this case, i is 0, 0 > 10 is false, so the loop will never be entered.

A `do-while` loop, however, works very similar to a while loop except the condition is tested at the END of the loop to determine wheter to start another iteration. A do while look is ALWAYS executed at least ONCE.

The syntax looks like this:

```js
do {
 // stuff
} while (conditions)
```

```js 
let number = null

do {
  number = parseInt(prompt("Enter a number between 1 and 10"))
} while (isNaN(number) || number < 1 || number > 10)

alert(`You entered ${number}`)

```

While and do-while loops are commonly used when you don't know in advance how many times a loop will be executed.  In the example above, we have no way to predict how many times a user will enter an invalid number, so we use a do while loop to execute the loop as many times as is necessary to obtain a valid input.


## For loops

For loops are typically used when you DO know a specific number of iterations you need in your loop.



Syntax:

```js
for (counter initialization; condition; increment expression) {
  // do stuff
}
```

Example:

```js 
for (let i = 0; i <= 10; i++) {
  console.log(i)
}
```

```js 
const investment = 10000
const annualRate = 7.0
const years = 10

let futureValue = investment 

for (let i = 1; i <= years; i++) {

  futureValue += futureValue * annualRate / 100
}

alert(futureValue.toFixed(0))
```


***
 
# Arrays

An array is an object that contains one or more items called elements.

The _length_ of the array indicated the number of elements it contains.



### TWO WAYS TO CREATE 

```js
const firstArray = new Array(10)
const secondArray = []
```

Array members are separated by commas, and can be primitive data types or objects.  

```js 
const presidents = ['Washington', 'Adams', 'Jefferson', 'Madison', 'Monroe']
```

It is not necessary for the elements to be of the same type
```js 
const mixed = ['Some text', 35, 0.12, true]
```

We can see the length using the `.length` property.

```js
console.log(presidents.length) // 5
console.log(firstArray.length) // 10
console.log(mixed.length) // 4
```

Note that if we print the first array, even though it has a length of 10, it does not have any elements
```js 
console.log(presidents) // we sell all of the elements
console.log(firstArray) // we see empty x 10
```

## Array Indexes

To access, or set, array members, we use what's called an INDEX - this is simply the position the item is in.  

There is one catch though: array indexes start at 0.  So the first item is 0, the second item is 1

The final index will be `arr.length - 1`

To use an index, you use square brackes after the identifier and put the index inside those brackets.

```js 
// Third president, Thomas Jefferson
presidents[2]
```

## Adding Elements to an array

```js 
const arr = []

console.log(arr)
console.log(arr.length)

arr[0] = 'NHL'
arr[1] = 'NFL'
arr[2] = 'MLB'

console.log(arr)
console.log(arr.length)
```

What happens if we add something out of order?
```js
arr[10] = 'NBA'
console.log(arr)
console.log(arr.length)
```


## Adding an Element to the end of an Array

Option 1: We know the last element of an array is always `length - 1` so arr[arr.length] is always going to be the next available index

```js
const arr = []
console.log(arr, arr.length)
arr[arr.length] = 'First Element'
arr[arr.length] = 'Second Element'
arr[arr.length] = 'Third Element'
console.log(arr, arr.length)
```

Another option, not yet covered in the book, is array.push()

```js
const arr = []
console.log(arr, arr.length)
arr.push('First Element')
arr.push('Second Element')
arr.push('Third Element')
console.log(arr, arr.length)
```


## Using For Loops with Arrays 

For loops are commonly used with arrays to iterate through an array and perform some action on each member.

let's stay we wanted to populate an array of integers

```js 
const arr = [1, 2, 3, 4....

// but what if we wanted to go to 100?

we could use a for loop to do that 
const arr = []
for (let i = 0; i < 100; i++ ){ 
  arr[i] = i + 1
}

console.log(arr)
```

> #### A NOTE HERE ABOUT CONSTANTS.  Notice in this example that I declared arr as a `const` and yet I am adding elements to it? What gives?  Elements of a const obj, like an array, __CAN__ change, you simple cannot perform a total reassignment 

```js
const arr = [1, 2, 3]
// this is ok
arr[0] = 17

// this is not 
arr = [17, 2, 3]
```

So we used a loop to populate our array.  We could also use a loop to display elements from our array

```js 
const arr = [120, 15, 1, 36, 64, 314, 148, 81, 35, 10, 25, 73]

// I want to know the sum of all of these numbers 

let sum = 0
for (let i = 0; i < arr.length; i++) {
  sum += arr[i]
}

console.log('sum is ', sum)
```

We could embed some conditionals in here as well 

```js 
const arr = [120, 15, 1, 36, 64, 314, 148, 81, 35, 10, 25, 73]

// I want to know the sum of all of these numbers 

const overLimit = []
const notOverLimit = []

const limit = 81

let sum = 0

for (let i = 0; i < arr.length; i++) {
  sum += arr[i]
  if (arr[i] > limit) {
    overLimit[overLimit.length] = arr[i]
  } else {
    notOverLimit[notOverLimit.length] = arr[i]
  }
}

console.log('sum is ', sum)

console.log('Over Limit: ', overLimit)
console.log('Not Over Limit: ', notOverLimit)

```

## Special 'For' Loops : For-in For-of

You can use special for loops called For-in and For-of to iterate array in an even simpler syntax.  The difference in for-in and for-of is whether you want to work in INDEXES or VALUES.

```js 
const subjects = ['Math', 'History', 'Art']

for (const i in subjects) {
  console.log(`Subject ${i} is ${subjects[i]}`)
}

// OR 

for (const subject of subjects) {
  console.log(subject)
}
```

While it isn't necessary, meaningful variable names can help us keep track of what a variable is.  In the for-in loop, I used 'i' to iterate the loop, because i (or whatever variable you use) will hold the index.  It will have values like 0 and 1.  To access the actual elements we'll still need to use `subjects[i]`

In the for-of loop, I used the singular version (subject) or the plural name of the array (subjects) because we're iteration the values.  As we loop through a for-of, the variable we choose holds "Math" or "History"-- __not__ an index like 0 or 1.
