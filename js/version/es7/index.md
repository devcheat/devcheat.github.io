**ECMAScript 2016 / `ES7`**
===

- [What's new in ECMAScript 2016 / ES7](#whats-new-in-ecmascript-2016--es7)
- [Exponentiation Operator](#exponentiation-operator)
  - [Introduction to the JavaScript exponentiation operator](#introduction-to-the-javascript-exponentiation-operator)
  - [Summary](#summary)
- [Array includes()](#array-includes)
  - [Introduction to the JavaScript Array `includes()` method](#introduction-to-the-javascript-array-includes-method)
  - [The includes() accepts two arguments:](#the-includes-accepts-two-arguments)
  - [Example](#example)

----
# What's new in ECMAScript 2016 / ES7

> **ES7 ES2016 relesaed on June 2016**
>  **ECMAScript 7** is also known as **ES7** and **ECMAScript 2016**.

The following are the most important features of ES6.

# Exponentiation Operator   
> The exponentiation operator (**) that allows you to calculate a base to the exponent power, which is similar to Math.pow() method.
> 
## Introduction to the JavaScript exponentiation operator


To raise a number to the power of an exponent, you often use the static method `Math.power()` with the following syntax:

```js
Math.pow(base, exponent)
```


For example:
```js
let result = Math.pow(2,2);
console.log(result); // 4

result = Math.pow(2,3);
console.log(result); // 8
```


**ECMAScript 2016 ES7** provided an alternative way to get a base to the exponent power by using the exponentiation operator ( `**`) with the following syntax:

```
x**n
```

The operator `**` raises the `x` to the power of an exponent `n`.

Note that some languages use the caret symbol `^` for exponentiation. However, JavaScript already uses that symbol for the bitwise logical XOR operator.

The following example illustrates how to use the exponentiation operator (`**`):

```js
let result = 2 ** 2;
console.log(result); // 4

result = 2 ** 3;
console.log(result); // 8
```


Both `Math.pow()` and operator `**` accept values of the `number` type. However, the operator `**` also accepts the numbers of the `[bigint](https://www.javascripttutorial.net/es-next/javascript-bigint/)` type. For example:

```js
let result = 2n ** 3n;
console.log(result); // 8n
```

In addition, you can use the exponentiation operator  ( `**`) in the infix notation. For example:

```js
let x = 2;
x **= 4;
console.log(x); // 16
```

JavaScript doe not allow you to put a unary operator immediately before the base number. If you attempt to do so, you'll get a `SyntaxError`.

The following causes a syntax error:

```js
let result = -2**3;
```

**Error:**

```
Uncaught SyntaxError: Unary operator used immediately before exponentiation expression. Parenthesis must be used to disambiguate operator precedence
```



To fix this, you use parentheses like this:

```js
let result = (-2)**3;
console.log(result); // -8
```

## Summary


-   The exponentiation operator `**` raises a number to the power of an exponent.
-   The exponentiation operator `**` accepts values of the type `number` or `bigint`.

---

# Array includes()  
> Array includes() method that checks if an element is in an array.

## Introduction to the JavaScript Array `includes()` method
When working with an array, you often want to check if the array contains an element. To do this, you use the `indexOf()` method as follows:
```js
let numbers = [1,2,3];
if(numbers.indexOf(2) !== -1){
   // process here
}
```
The `indexOf()` method returns the index of the first occurrence of the element in the array. If the array doesn’t include the element, the indexOf() returns -1.

As you can see, the `indexOf()` method doesn’t really clearly state what it means. In addition, the indexOf() uses strict equality operator (`===`) for comparison, therefore, it doesn’t work with NaN as shown in the following example:
```js
[NaN].indexOf(NaN); // -1
```
In this example, the array contains one element of NaN. However, the indexOf(NaN) returns `-1`.

To work around this, developers came up with a helper function, for example, Lodash provides the `_.incudes()` method that checks if a value is in the array.

**ECMAScript 2016** standardized this functionality by providing the `Array.prototype.includes()` method.

The `includes()` method returns true if an array contains a given element; Otherwise, it returns false.

The following illustrates the syntax of the includes() method:
```
array.includes(element,fromIndex);
```
## The includes() accepts two arguments:

- The first argument is the element that can be searched.
- The fromIndex is the position in the array to which the search starts.
See the following example:
```js
[1,2,3].includes(2); // true
[1,2,3].includes(4); // false
[1,2,3].includes(1,1); // false
```
Unlike the indexOf() method, the includes() method works perfectly fine with the NaN:
```js
[NaN].includes(NaN); // true
```
Note that the includes() doesn’t distinguish between +0 and -0 as shown in the following example:
```js
[-0].includes(+0); // true
```

## Example
The following example demonstrates how to use the includes() method to check if an object is in an array.
```js
let bmw = {name: 'BMW' }, 
    toyota = { name: 'Toyota'},
    ford = {name: 'Ford'}

let cars = [ford, toyota];

console.log(cars.includes(ford)); // true
console.log(cars.includes(bmw)); // false
```

**In this example:**

1. First, we initialized the cars array with two objects: ford and toyota.
2. Then, we used the `includes()` method to check if the cars array contains the  ford object, in this case, it returns true.
3. Finally, the  bmw object is not in the  cars array, therefore, the `includes()` method returns true as expected.

---
