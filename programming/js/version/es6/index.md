# ECMAScript 2015 / `ES6`
---
- [**What's new in ECMAScript 2015 / ES6**](#whats-new-in-ecmascript-2015--es6)
- [`let` keyword](#let-keyword)
  - [Differences Between `var` and `let`](#differences-between-var-and-let)
    - [Variable scopes](#variable-scopes)
    - [Creating global properties](#creating-global-properties)
    - [Redeclaration](#redeclaration)
    - [The Temporal dead zone](#the-temporal-dead-zone)
      - [The var variables](#the-var-variables)
      - [The let variables](#the-let-variables)
- [`const` keyword](#const-keyword)
- [Arrow Function](#arrow-function)
  - [With multiple parameters](#with-multiple-parameters)
  - [With a single parameter](#with-a-single-parameter)
  - [With no parameter](#with-no-parameter)
  - [Line break between parameter definition and arrow](#line-break-between-parameter-definition-and-arrow)
  - [Summary](#summary)
- [The `for`/`Of` Loop](#the-forof-loop)
  - [Looping over an Array](#looping-over-an-array)
  - [Looping over a String](#looping-over-a-string)
- [JavaScript `class`](#javascript-class)
  - [Using a `class`](#using-a-class)
  - [The `constructor()` Method](#the-constructor-method)
  - [Class Methods](#class-methods)
  - [Class Inheritance](#class-inheritance)
  - [Getters and Setters](#getters-and-setters)
  - [Hoisting](#hoisting)
  - [JavaScript Static Methods](#javascript-static-methods)
- [JavaScript Promises](#javascript-promises)
  - [Promise Syntax](#promise-syntax)
- [The Symbol Type](#the-symbol-type)
- [Default `funtion` Parameter](#default-funtion-parameter)
- [Rest `function` Parameter](#rest-function-parameter)
- [Spread Operator](#spread-operator)
  - [Using spread operator and `apply()` method](#using-spread-operator-and-apply-method)
  - [Using spread with Array’s push() method](#using-spread-with-arrays-push-method)
  - [Using array manipulation](#using-array-manipulation)
    - [Constructing array literal](#constructing-array-literal)
    - [Concatenating arrays](#concatenating-arrays)
    - [Copying an array](#copying-an-array)
  - [Summary](#summary-1)
- [Array.find()](#arrayfind)
- [Array.findIndex()](#arrayfindindex)
- [Object property initializer shorthand](#object-property-initializer-shorthand)
- [Computed property name](#computed-property-name)
- [Concise method syntax](#concise-method-syntax)
- [New Math Methods](#new-math-methods)
  - [The `Math.trunc()` Method](#the-mathtrunc-method)
  - [The `Math.sign()` Method](#the-mathsign-method)
  - [The `Math.cbrt()` Method](#the-mathcbrt-method)
  - [The `Math.log2()` Method](#the-mathlog2-method)
  - [The `Math.log10()` Method](#the-mathlog10-method)
- [New Number Properties](#new-number-properties)
- [New Number Methods](#new-number-methods)
  - [The `Number.isInteger()` Method](#the-numberisinteger-method)
  - [The `Number.isSafeInteger()` Method](#the-numberissafeinteger-method)
- [New Global Methods](#new-global-methods)
  - [The `isFinite()` Method](#the-isfinite-method)
  - [The `isNaN()` Method](#the-isnan-method)
- [Octal literals](#octal-literals)
- [Binary literals](#binary-literals)
---
# **What's new in ECMAScript 2015 / ES6**
> ECMAScript 6 was the second major revision to JavaScript.

> ECMAScript 6 is also known as ES6 and ECMAScript 2015.

The following are the most important features of ES6.


# `let` keyword
 The ```let``` keyword allows you to declare a variable with block scope.

**Example**
```js
var x = 10;
// Here x is 10
{
  let x = 2;
  // Here x is 2
}
// Here x is 10
```
## Differences Between `var` and `let`

### Variable scopes
The var variables belong to the global scope when you define them outside a function.
```js
for (var i = 0; i < 5; i++) {
	console.log("Inside the loop:", i);
}

console.log("Outside the loop:", i);

/*
Output:
Inside the loop: 0 
Inside the loop: 1 
Inside the loop: 2 
Inside the loop: 3 
Inside the loop: 4 
Outside the loop: 5
*/
```

The following example uses the `let` keyword instead of the var keyword:
```js
for (let i = 0; i < 5; i++) {
	console.log("Inside the loop:", i);
}

console.log("Outside the loop:", i);
/*
OUTPUT:
Inside the loop: 0
Inside the loop: 1
Inside the loop: 2
Inside the loop: 3
Inside the loop: 4
Uncaught ReferenceError: i is not defined
*/
```
Since this example uses the let keyword, the variable i is blocked scope. It means that the variable i only exists and can be accessible inside the for loop block.

### Creating global properties
The global var variables are added to the global object as properties. 
```js
var counter = 0;
console.log(window.counter); //  0
```
However, the let variables are not added to the global object:
```js
let counter = 0;
console.log(window.counter); // undefined
```
### Redeclaration
The var keyword allows you to redeclare a variable without any issue:
```js
var counter = 10;
var counter;
console.log(counter); // 10
```
However, if you redeclare a variable with the let keyword, you will get an error:
```js
let counter = 10;
let counter; // error
```

### The Temporal dead zone
The let variables have temporal dead zones while the var variables don’t. To understand the temporal dead zone, let’s examine the life cycles of both var and let variables, which have two steps: creation and execution.

#### The var variables
1. In the creation phase, the JavaScript engine assigns storage spaces to var variables and immediately initializes them to undefined.
2. In the execution phase, the JavaScript engine assigns the var variables the values specified by the assignments if there are ones. Otherwise, the var variables remain undefined.

#### The let variables
1. In the creation phase, the JavaScript engine assigns storage spaces to the let variables but does not initialize the variables. Referencing uninitialized variables will cause a ReferenceError.
2. The let variables have the same execution phase as the var variables.

The temporal dead zone starts from the block until the `let` variable declaration is processed. In other words, it is the location where you cannot access the `let` variables before they are defined.

---

# `const` keyword
 The const keyword allows you to declare a constant (a JavaScript variable with a constant value).

Constants are similar to let variables, except that the value cannot be changed.

**Example**
```js
var x = 10;
// Here x is 10
{
  const x = 2;
  // Here x is 2
}
// Here x is 10
```

---

# Arrow Function
 With arrow functions, you don't have to type the function keyword, the return keyword, and the curly brackets.

**Example**
```js
// ES5
var x = function(x, y) {
   return x * y;
}

// ES6
const x = (x, y) => x * y;
```
- Arrow functions do not have their own this. They are not well suited for defining object methods.

- Arrow functions are not hoisted. They must be defined before they are used.

- Using const is safer than using var, because a function expression is always a constant value.

- You can only omit the return keyword and the curly brackets if the function is a single statement. Because of this, it might be a good habit to always keep them:

**Example**
```js
var v = (x,y) => {
    var c = x+y;
    return ("hello:" + c);
};

const x = (x, y) => { return x * y };

```

## With multiple parameters
To sort an array of numbers in the descending order, you use the sort() method of the array object as follows:
```js
//ES5
let numbers = [4,2,6];
numbers.sort(function(a,b){ 
    return b - a; 
});
console.log(numbers); // [6,4,2]
```
The code is more concise with the arrow function syntax:
```js
//ES6
let numbers = [4,2,6];
numbers.sort((a,b) => b - a);
console.log(numbers); // [6,4,2]
```

## With a single parameter
If an arrow function takes a single parameter, you use the following syntax:
```
(p1) => { statements }
```
Note that you can omit the parentheses as follows:
```
p => { statements }
```
The following example uses an arrow function as an argument of the map() method that transforms an array of strings into an array of the string’s lengths.
```js
//ES6
let names = ['John', 'Mac', 'Peter'];
let lengths = names.map(name => name.length);

console.log(lengths);
```

## With no parameter
If the arrow function has no parameter, you need to use parentheses, like this:
```js
let logDoc = () => console.log(window.document);
logDoc();
```

## Line break between parameter definition and arrow
```js
let multiply = (x,y) => 
x * y;
```

## Summary


-   Use the `(...args) => expression;` to define an arrow function.
-   Use the `(...args) => { statements }` to define an arrow function that has multiple statements.
-   An arrow function doesn't have its binding to `this` or `super`.
-   An arrow function doesn't have `arguments` object, `new.target` keyword, and `prototype` property.

---

# The `for`/`Of` Loop
> The JavaScript for/of statement loops through the values of an iterable objects.

for/of lets you loop over data structures that are iterable such as Arrays, Strings, Maps, NodeLists, and more.

The for/of loop has the following syntax:

Synatx
```js
for (variable of iterable) {
  // code block to be executed
}
```
- variable - For every iteration the value of the next property is assigned to the variable. Variable can be declared with const, let, or var.

- iterable - An object that has iterable properties.

## Looping over an Array
**Example**
```js
var cars = ["BMW", "Volvo", "Mini"];
var x;

for (x of cars) {
  document.write(x + "<br >");
}
```

## Looping over a String
**Example**
```js
var txt = "JavaScript";
var x;

for (x of txt) {
  document.write(x + "<br >");
}
```

---
# JavaScript `class`
 JavaScript Classes are templates for JavaScript Objects.

Use the keyword ```class``` to create a class.

- Always add a method named constructor():

**Syntax**
```js
class ClassName {
  constructor() { ... }
}
```

**Example**
```js
class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
}
```
*Note*
- The example above creates a class named "Car".
- The class has two initial properties: "name" and "year".
- A JavaScript class is not an object.
- It is a template for JavaScript objects.

## Using a `class`
> When you have a class, you can use the class to create objects:

**Example**
```js
let myCar1 = new Car("Ford", 2014);
let myCar2 = new Car("Audi", 2019);
```

The constructor method is called automatically when a new object is created.

## The `constructor()` Method
The constructor method is a special method:

- It has to have the exact name "constructor"
- It is executed automatically when a new object is created
- It is used to initialize object properties
- If you do not define a constructor method, JavaScript will add an empty constructor method.

## Class Methods
Class methods are created with the same syntax as object methods.

- Use the keyword ```class``` to create a class.
- Always add a `constructor()` method.

Then add any number of methods.

**Syntax**
```
class ClassName {
  constructor() { ... }
  method_1() { ... }
  method_2() { ... }
  method_3() { ... }
}
```
Create a Class method named "age", that returns the Car age:

**Example**
```js
class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
  age() {
    let date = new Date();
    return date.getFullYear() - this.year;
  }
}

//usage
let myCar = new Car("Ford", 2014);
document.getElementById("demo").innerHTML =
"My car is " + myCar.age() + " years old.";
```
You can send parameters to Class methods:

**Example**
```js
class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
  age(x) {
    return x - this.year;
  }
}

let date = new Date();
let year = date.getFullYear();

let myCar = new Car("Ford", 2014);
document.getElementById("demo").innerHTML=
"My car is " + myCar.age(year) + " years old.";
```

## Class Inheritance
To create a class inheritance, use the extends keyword.

A class created with a class inheritance inherits all the methods from another class:

**Example**
Create a class named `Model` which will inherit the methods from the `Car` class:
```js
class Car {
  constructor(brand) {
    this.carname = brand;
  }
  present() {
    return 'I have a ' + this.carname;
  }
}

class Model extends Car {
  constructor(brand, mod) {
    super(brand);
    this.model = mod;
  }
  show() {
    return this.present() + ', it is a ' + this.model;
  }
}

let myCar = new Model("Ford", "Mustang");
document.getElementById("demo").innerHTML = myCar.show();
```
The ```super()``` method refers to the parent class.

By calling the ```super()``` method in the constructor method, we call the parent's constructor method and gets access to the parent's properties and methods.

> Inheritance is useful for code reusability: reuse properties and methods of an existing class when you create a new class.

## Getters and Setters
Classes also allows you to use getters and setters.

It can be smart to use getters and setters for your properties, especially if you want to do something special with the value before returning them, or before you set them.

To add getters and setters in the class, use the get and set keywords.

**Example**
Create a getter and a setter for the "carname" property:
```js
class Car {
  constructor(brand) {
    this.carname = brand;
  }
  get cnam() {
    return this.carname;
  }
  set cnam(x) {
    this.carname = x;
  }
}

let myCar = new Car("Ford");

document.getElementById("demo").innerHTML = myCar.cnam;
```
> **Note:** even if the getter is a method, you do not use parentheses when you want to get the property value.

The name of the getter/setter method cannot be the same as the name of the property, in this case carname.

Many programmers use an underscore character _ before the property name to separate the getter/setter from the actual property:

**Example**
You can use the underscore character to separate the getter/setter from the actual property:
```js
class Car {
  constructor(brand) {
    this._carname = brand;
  }
  get carname() {
    return this._carname;
  }
  set carname(x) {
    this._carname = x;
  }
}

let myCar = new Car("Ford");

document.getElementById("demo").innerHTML = myCar.carname;
```
To use a setter, use the same syntax as when you set a property value, without parentheses:

**Example**
Use a setter to change the carname to "Volvo":
```js
class Car {
  constructor(brand) {
    this._carname = brand;
  }
  get carname() {
    return this._carname;
  }
  set carname(x) {
    this._carname = x;
  }
}

let myCar = new Car("Ford");
myCar.carname = "Volvo";
document.getElementById("demo").innerHTML = myCar.carname;
```
## Hoisting
Unlike functions, and other JavaScript declarations, `class` declarations are not hoisted.

That means that you must declare a class before you can use it:

**Example**
```js
//You cannot use the class yet.
//myCar = new Car("Ford")
//This would raise an error.

class Car {
  constructor(brand) {
    this.carname = brand;
  }
}

//Now you can use the class:
let myCar = new Car("Ford")
```
> Note: For other declarations, like functions, you will NOT get an error when you try to use it before it is declared, because the default behavior of JavaScript declarations are hoisting (moving the declaration to the top).

## JavaScript Static Methods
Static class methods are defined on the class itself.

You cannot call a static method on an object, only on an object class.

**Example**
```js
class Car {
  constructor(name) {
    this.name = name;
  }
  static hello() {
    return "Hello!!";
  }
}

let myCar = new Car("Ford");

// You can calll 'hello()' on the Car Class:
document.getElementById("demo").innerHTML = Car.hello();

// But NOT on a Car Object:
// document.getElementById("demo").innerHTML = myCar.hello();
// this will raise an error.
```
If you want to use the myCar object inside the static method, you can send it as a parameter:

**Example**
```js
class Car {
  constructor(name) {
    this.name = name;
  }
  static hello(x) {
    return "Hello " + x.name;
  }
}
let myCar = new Car("Ford");
document.getElementById("demo").innerHTML = Car.hello(myCar);
```

# JavaScript Promises
 A Promise is a JavaScript object that links "Producing Code" and "Consuming Code".

 "Producing Code" can take some time and "Consuming Code" must wait for the result.

## Promise Syntax
```js
let myPromise = new Promise(function(myResolve, myReject) {
// "Producing Code" (May take some time)

  myResolve(); // when successful
  myReject();  // when error
});

// "Consuming Code" (Must wait for a fulfilled Promise).
myPromise.then(
  function(value) { /* code if successful */ },
  function(error) { /* code if some error */ }
);
```
**Example Using a Promise**
```js
let myPromise = new Promise(function(myResolve, myReject) {
  setTimeout(function() { myResolve("I love You !!"); }, 3000);
});

myPromise.then(function(value) {
  document.getElementById("demo").innerHTML = value;
});
```

# The Symbol Type
 A JavaScript Symbol is a primitive datatype just like Number, String, or Boolean.

 It represents a unique "hidden" identifier that no other code can accidentally access.

For instance, if different coders want to add a person.id property to a person object belonging to a third-party code, they could mix each others values.

- Using `Symbol()` to create a unique identifiers, solves this problem:

**Example**
```js
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};

let id = Symbol('id');
person[id] = 140353;
// Now Person[id] = 140352
// but person.id is still undefined
```
**Note**
- Symbols are always unique.
- If you create two symbols with the same description they will have different values.

```js
Symbol("id") == Symbol("id") // false
```

# Default `funtion` Parameter
ES6 allows function parameters to have default values.

**Example**
```js
function myFunction(x, y = 10) {
  // y is 10 if not passed or undefined
  return x + y;
}
myFunction(5); // will return 15
```
# Rest `function` Parameter
The rest parameter (...) allows a function to treat an indefinite number of arguments as an array:

**Example**
```js
function sum(...args) {
  let sum = 0;
  for (let arg of args) sum += arg;
  return sum;
}

let x = sum(4, 9, 16, 25, 29, 100, 66, 77);
```
---
# Spread Operator
ES6 provides a new operator called spread operator that consists of three dots (...). The spread operator allows you to spread out elements of an iterable object such as an array, map, or set. For example:
```js
const odd = [1,3,5];
const combined = [2,4,6, ...odd];
console.log(combined);

/*
OUTPUT:
[ 2, 4, 6, 1, 3, 5 ]

*/
```
In this example, the three dots ( ...) located in front of the odd array is the spread operator. The spread operator (...) unpacks the elements of the odd array.

> Note that **ES6** also has the three dots ( ...) which is a rest parameter that collects all remaining arguments of a function into an array.

Here are the main differences:

- The spread operator (...) unpacks the elements of an iterable object.
- The rest parameter (...) packs the elements into an array.

The rest parameters must be the last arguments of a function. However, the spread operator can be anywhere:

```js
const odd = [1,3,5];
const combined = [...odd, 2,4,6];
console.log(combined);

//or
const odd = [1,3,5];
const combined = [2,...odd, 4,6];
console.log(combined);

```

## Using spread operator and `apply()` method

```js
function compare(a, b) {
    return a - b;
}

let result = compare(...[1, 2]);
console.log(result); // -1

```

## Using spread with Array’s push() method
Sometimes, a function may accept an indefinite number of arguments. Filling arguments from an array is not convenient.
```js
let rivers = ['Nile', 'Ganges', 'Yangte'];
let moreRivers = ['Danube', 'Amazon'];

rivers.push(...moreRivers);

```
## Using array manipulation
### Constructing array literal
The spread operator allows you to insert another array into the initialized array when you construct an array using the literal form. See the following example:
```js
let initialChars = ['A', 'B'];
let chars = [...initialChars, 'C', 'D'];
console.log(chars); // ["A", "B", "C", "D"]
```

### Concatenating arrays
Also, you can use the spread operator to concatenate two or more arrays:
```js
let numbers = [1, 2];
let moreNumbers = [3, 4];
let allNumbers = [...numbers, ...moreNumbers];
console.log(allNumbers); // [1, 2, 3, 4]
```

### Copying an array
In addition, you can copy an array instance by using the spread operator:
```js
let scores = [80, 70, 90];
let copiedScores = [...scores];
console.log(copiedScores); // [80, 70, 90]
```

> **Note** that the spread operator only copies the array itself to the new one, not the elements. This means that the copy is shallow, not deep.

## Summary
- The spread operator is denoted by three dots (…).
- The spread operator unpacks elements of iterable objects such as arrays, sets, and maps into a list.
- The rest paramter is also denoted by three dots (…). However, it packs the remaining arguments of a function into an array.
- The spread operator can be used to clone an iterable object or merge iterable objects into one.

---
# Array.find()
The find() method returns the value of the first array element that passes a test function.

This example finds (returns the value of ) the first element that is larger than 18:

**Example**
```js
var numbers = [4, 9, 16, 25, 29];
var first = numbers.find(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```
Note that the function takes 3 arguments:
```
The item value
The item index
The array itself
```
# Array.findIndex()
The findIndex() method returns the index of the first array element that passes a test function.

This example finds the index of the first element that is larger than 18:

**Example**
```js
var numbers = [4, 9, 16, 25, 29];
var first = numbers.findIndex(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```
Note that the function takes 3 arguments:
```
The item value
The item index
The array itself
```
# Object property initializer shorthand
Prior to ES6, an object literal is a collection of name-value pairs. For example:
```js
//ES5
function createMachine(name, status) {
    return {
        name: name,
        status: status
    };
}
```
The createMachine() function takes two arguments name and status and returns a new object literal with two properties: name and status.

The name and status properties take the values of the name and status parameters. This syntax looks redundant because name and status mentioned twice in both the name and value of properties.

**ES6** allows you to eliminate the duplication when a property of an object is the same as the local variable name by including the name without a colon and value.

For example, you can rewrite the createMachine() function in ES6 as follows:
```js
function createMachine(name, status) {
    return {
        name,
        status
    };
}
```
Similarly, you can construct an object literal from local variables as shown in the following example:
```js
let name = 'Computer',
    status = 'On';

let machine = {
   name,
   status
};
```
---
# Computed property name
Prior to ES6, you could use the square brackets(`[]`)  to enable the computed property names for the properties on objects.

The square brackets allow you to use the string literals and variables as the property names.

Example:
```js
let name = 'machine name';
let machine = {
    [name]: 'server',
    'machine hours': 10000
};

console.log(machine[name]); // server
console.log(machine['machine hours']); // 10000
```
The name variable was initialized to a value of 'machine name'. Since both properties of the machine object contains a space, you can only reference them using the square brackets.

In **ES6**, the computed property name is a part of the object literal syntax, and it uses the square bracket notation.

__When a property name is placed inside the square brackets, the JavaScript engine evaluates it as a string.__ It means that you can use an expression as a property name. For example:
```js
let prefix = 'machine';
let machine = {
    [prefix + ' name']: 'server',
    [prefix + ' hours']: 10000
};

console.log(machine['machine name']); // server
console.log(machine['machine hours']); // 10000
```
The machine object’s properties evaluate to 'machine name' and 'machine hours', therefore you can reference them as the properties of the machine object.

---

# Concise method syntax
Prior to __ES6__, when defining a method for an object literal, you need to specify the name and full function definition as shown in the following example:
```js
let server = {
	name: "Server",
	restart: function () {
		console.log("The" + this.name + " is restarting...");
	}
};
```
__ES6__ makes the syntax for making a method of the object literal more succinct by removing the colon `:` and the function keyword.

The following example rewrites the server object above using the ES6 syntax.
```js
let server = {
    name: 'Server',
    restart() {
        console.log("The" + this.name + " is restarting...");
    }
};
```
This shorthand syntax is also known as the concise method syntax. It’s valid to have spaces in the property name. For example:
```js
let server = {
    name: 'Server',
    restart() {
        console.log("The " + this.name + " is restarting...");
    },
    'starting up'() {
        console.log("The " +  this.name + " is starting up!");
    }
};

server['starting up']();
```
In this example, the method 'starting up' has spaces in its name. To call the method, you use the following syntax:
```
object_name['property name']();
```

---



# New Math Methods
ES6 added the following methods to the Math object:

```js
Math.trunc()
Math.sign()
Math.cbrt()
Math.log2()
Math.log10()
```
## The `Math.trunc()` Method
`Math.trunc(x)` returns the integer part of x:

**Example**
```js
Math.trunc(4.9);    // returns 4
Math.trunc(4.7);    // returns 4
Math.trunc(4.4);    // returns 4
Math.trunc(4.2);    // returns 4
Math.trunc(-4.2);    // returns 4
```
## The `Math.sign()` Method

`Math.sign(x)` returns if x is negative, null or positive:

**Example**
```js
Math.sign(-4);    //returns -1
Math.sign(0);    //returns 0
Math.sign(4);    //returns 1
```

## The `Math.cbrt()` Method
Math.cbrt(x) returns the cube root of x:

**Example**
```js
Math.cbrt(8);    // returns 2
Math.cbrt(64);    // returns 4
Math.cbrt(125);    // returns 5
```
## The `Math.log2()` Method
Math.log2(x) returns the base 2 logarithm of x:

**Example**
```js
Math.log2(2);    // returns 1
```
## The `Math.log10()` Method
Math.log10(x) returns the base 10 logarithm of x:

**Example**
```js
Math.log10(10);    // returns 1
```
# New Number Properties
ES6 added the following properties to the Number object:
```js
EPSILON
MIN_SAFE_INTEGER
MAX_SAFE_INTEGER
```


**Example**
```js
var x = Number.EPSILON;
```
**Example**
```js
var x = Number.MIN_SAFE_INTEGER;
```
**Example**
```js
var x = Number.MAX_SAFE_INTEGER;
```
# New Number Methods
ES6 added 2 new methods to the Number object:
```js
Number.isInteger()
Number.isSafeInteger()

```


## The `Number.isInteger()` Method
The `Number.isInteger()` method returns true if the argument is an integer.

**Example**
```js
Number.isInteger(10);        // returns true
Number.isInteger(10.5);      // returns false
```

## The `Number.isSafeInteger()` Method
A safe integer is an integer that can be exactly represented as a double precision number.

The `Number.isSafeInteger()` method returns true if the argument is a safe integer.

**Example**
```js
Number.isSafeInteger(10);    // returns true
Number.isSafeInteger(12345678901234567890);  // returns false
```
Safe integers are all integers from -(253 - 1) to +(253 - 1).
This is safe: 9007199254740991. This is not safe: 9007199254740992.

# New Global Methods
ES6 added 2 new global number methods:
```js
isFinite()
isNaN()
```
## The `isFinite()` Method
 The global ```isFinite()``` method returns false if the argument is Infinity or NaN.

Otherwise it returns true:

**Example**
```js
isFinite(10/0);       // returns false
isFinite(10/1);       // returns true
```
## The `isNaN()` Method
The global isNaN() method returns true if the argument is NaN. Otherwise it returns false:

**Example**
```js
isNaN("Hello");       // returns true
```
---

# Octal literals
> **Octal literals** start with `0o` followed by a sequence of numbers between `0` and `7`

To represent an octal literal in ES5, you use the zero prefix (0) followed by a sequence of octal digits (from 0 to 7). For example:
```js
let a = 051;
console.log(a); // 41
```
If the octal literal contains a number that is out of range, JavaScript ignores the leading 0 and treats the octal literal as a decimal, as shown in the following example:
```js
let b = 058; // invalid octal
console.log(b); // 58
```
In this example, since 8 is an invalid digit for representing the octal number, JavaScript ignores the 0 and treats the whole number as a decimal with a value of 58.

Note you can use the octal literals in non-strict mode. If you use them in strict mode, JavaScript will throw an error.
```js
"use strict"
let b = 058; // invalid octal 
console.log(b);
```
Here is the error message:
```js
SyntaxError: Decimals with leading zeros are not allowed in strict mode.
```
ES6 allows you to specify the octal literal by using the prefix 0o followed by a sequence of octal digits from 0 through 7. Here is an example:
```js
let c = 0o51;
console.log(c); // 41 
```
If you use an invalid number in the octal literal, JavaScript will throw a SyntaxError as shown in the following example:
```js
let d = 0o58;
console.log(d); // SyntaxError
```

---

# Binary literals
> **Binary literals** start with 0b followed by a sequence of number `0` and `1`

In ES5, JavaScript didn’t provide any literal form for binary numbers. 

To parse a binary string, you use the parseInt() function as follows:
```js
let e = parseInt('111',2);
console.log(e); // 7
```
ES6 added support for binary literals by using the 0b prefix followed by a sequence of binary numbers (0 and 1). Here is an example:
```js
let f = 0b111;
console.log(f); // 7
```


***
