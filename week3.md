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
