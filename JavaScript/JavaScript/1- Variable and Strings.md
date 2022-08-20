# Variable and Strings
Before understanding this topic, keep in mind that JavaScript has two modes. 
1. Sloopy Mode 
	It is by defalut mode and is less strict in terms of checking errors
2. Strict Mode
	It is attained using ```  'use strict' ``` and more errors are thrown. It prevents the pitfuls(unexpected behaviour) of language

1. Variables
We can declare variables in three ways in JavaScript
- Var
- Let
- Const

***Var*** is basically used to declare a global scoped or function scoped variable.
*Example* 
```
var x = 1;
if (x === 1) {
  var x = 2;

  console.log(x);
  // expected output: 2
}

console.log(x);
// expected output: 2
```
The output in this case will be 
```
2
2
```
*Reason* : Because, ***Var*** will affect the global scope and will change the value of x to 2. 

***Let*** is basically used to declare a local scope variable 
*Example* : 
```
let x = 1;

if (x === 1) {
  let x = 2;

  console.log(x);
  // expected output: 2
}

console.log(x);
// expected output: 1

```
The output in this case will be
```
2 
1
```
*Reason* 
Two x will be created. One with value of x = 1 and other with value of x = 2 and there will be no affect to global scope variable x which is 1.

***Const*** 
*Constants are block-scoped*, much like variables declared using the let keyword. The value of a constant can't be changed through reassignment (i.e. by using the assignment operator), and it can't be redeclared (i.e. through a variable declaration). However, *if a constant is an object or array its properties or items can be updated or removed.*

```
const number = 42;

try {
  number = 99;
} catch (err) {
  console.log(err);
  // expected output: TypeError: invalid assignment to const `number'
  // Note - error messages will vary depending on browser
}

console.log(number);
// expected output: 42
```

## String Methods
1. startsWith()

### ***Interview Questions***

1. ***Hoisting***
Hosting is the way the JS developers describe the strange ability of JS to access variable before it is initialized  

```
console.log(age);
var age = 26;
```
*Explanation* 
This will not throw an error, but it will log out undefined


2. ***Global Variable Overriding***
If one variable is not declared by *let/const/var*, 
If it is present in global object, it will override it else will create new property in global object

```
console = 'hi'
console.log("hi");
```
`
*Explanation*

This will give the following Error

`!TypeError: console.log is not a function`

because console = 'hi' will override the property which is in global object because **it is not declared with var/let/const**

3. What is global object is referred in browser and server, mention a common name too which works everywhere?

	- Browse -> window  
	- Server -> global  
	- Common Name -> globalThis

4. Falsy Values 
	  - null
	  - undefined
	  - any type of string
		  - Single Quote
		  - Double Quote
		  - String Literals
	  - false
	  - 0
	  - NaN
5. Null vs Undefined
	When JavaScript tells us that variable is empty, it will be termed as Undefinced
	When one JS developer tells other that this variable is empty, it will be termed as null


