 ###  JS topics that are important in React (without claiming to be complete):
 
 
* all data types, basics of syntax


* async/await


* functions & callback functions


* fetch


* modern syntax


* event handling


* Conditions, if-statements, ternary operator


* Loops


* Array methods


* Testing


### ALL DATA TYPES, basic of syntax

Connect a JavaScript file with <script>
Log to the console
Select elements with querySelector
Add, remove and toggle CSS classes on click with addEventListener
 
```
<script src="./index.js" defer></script>
```
 
 
``` 
const mainElement = document.querySelector('[data-js="main"]');
```
 
 better as:
 
````
// tag as identifier
const mainElement = document.querySelector("main");
// class as identifier -> .
const mainElement = document.querySelector(".main");
// id as identifier -> #
const mainElement = document.querySelector("#main");
````
 
### ```addEventListener````
 
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {
  console.log("Yeah");
});
 
 
### ```.classList````
 
Add/remove & toggle classes: .classList.
 
````
 const main = document.querySelector('[data-js="main"]');
const button = document.querySelector('[data-js="button"]');

button.addEventListener("click", () => {
  main.classList.add("page--primary");
});
 
`````
 
 
<hr>
 

 ### Variable Declarations
 
 const, let and var
 
 Variable Naming: camelCase
 
type	represents
 
```string```	a sequence of characters: "abcd"
```number```	a number: 1234
```boolean```	a binary statement, can be true or false
```null```	represents "nothing", is typically set by developers
```undefined```	represents the state of "not existing". Anything not specified or not found in JavaScript defaults to the value undefined
```BigInt	uncommon```, used for integers larger than 9007199254740991
```Symbol	uncommon```, used for creating unique elements
 
 
Operators:
 
operator	effect
+	adds two numbers together.
-	subtracts two numbers
*	multiplies two numbers
/	divides two numbers
**	potentiates two numbers: 2 ** 4 → 16
%	The remainder or modulus. Gives you what remains after a whole number division: 8 % 3 → 2.
 
Assignment Operators

operator	effect
+=	Increases the value of the variable on the left about the value on the right: count += 6 → count is increased by 6
-=	Decreases the value of the variable on the left about the value on the right
*=	Multiplies the variable on the left with the value on the right
/=	Divides the variable on the left with the value on the right
++	Increments the value of a variable by one: count++ → count is increased by one
--	Decrements the value of a variable by one: count-- → count is decreased by one
 
Type Coersion
When you use an operator with a variable with an unfitting type, JavaScript will automatically convert (coerse) this variable into a fitting type
 
decimal system: the standard numbers, has 10 symbols "0" to "9".
binary system: only has 2 symbols "0" and "1". If you want to write a bigger number than 1, you add another digit: 2 → "10" in binary.
hexadecimal system: has 16 symbols "0" to "9" and "a" to "f". If you want to write a number bigger than 15 you add another digit: 12 → "c" in hexadecimal.
 
<hr>
 
### Truthy and Falsy Values

 
```truthy``` values:

non zero numbers: 1, 2, -3, etc.
non empty strings: "hello"
true
 
 
```falsy``` values:

0 / -0
null
false
undefined
empty string: ""
 
### Comparision Operators

Operator	Effect
A === B	strict equal: is true if both values are equal (including their type).
A !== B	strict not equal: is true if both values are not equal (including their type).
A > B	strictly greater than: is true if A is greater than B.
A < B	strictly less than: is true if A is less than B.
A >= B	greater than or equal: is true if A is greater than or equal B.
A <= B	less than or equal: is true if A is less than or equal B.
     
### Logical Operator

Operator	Effect
!A	not: flips a true value to false and vice versa.
A || B	or: is true if either A or B is true.
A && B	and: is true if both A and B is true.

     
### Control Flow: if / else
With an if statement we can control whether a part of our code is executed or not, based on a condition.The condition expression between the () brackets can be composed of logical or comparison operators as well. You can distinguish between more cases by chaining else if statements:
     
````
if (hour < 12) {
  console.log("Good Morning.");
} else if (hour < 18) {
  console.log("Good afternoon.");
} else if (hour === 24) {
  console.log("Good night.");
} else {
  console.log("Good evening.");
}
`````

### ternary operator
                   
````
condition ? expressionIfTrue : expressionIfFalse;
                     
const greetingText = time < 12 ? "Good morning." : "Good afternoon.";
 
moveElement(xPos > 300 ? 300 : xPos); // the element can't be moved further than 300.
 
````

if(undefined) → falsy, won't execute
if(null) → falsy, won't execute
if("") → falsy, won't execute, but might still be a useful variable
(e.g. when user clears an input field)
if(0) → falsy, won't execute, but might still be a useful variable
(e.g. when user wants to set the volume to 0)
if(" ") → truthy, will execute
if(-1) → truthy, will execute
 
---
 
### FUNCTIONS
 
You can define a function using a function declaration which consists of:

the function keyword
the function name
the function body (JavaScript statements / JavaScript code)
 
```
function greet() {
  console.log("Hi Friends!");
  console.log("Nice to be here.");
}
 
function printLetter(name) {
  console.log("Hi " + name + ", hope you are fine. Love, Johnny");
}

function printSum(first, second, third) {
  const sum = first + second + third;
  console.log("The sum of your numbers is: " + sum);
}
 
````
 
 
Function Calls
When functions are defined you can call them by writing their name, followed by parentheses ("round brackets"). If the functions consume parameters you can pass them as arguments in the brackets.
 
greet();
printLetter("Jordan");
printSum(3, 4, 5);
 
Scope
The scope defines where variables are visible and where they can be referenced. :

global scope: A variable is in the global scope when it is declared outside of any function, in a JavaScript file. Global variables are visible and can be accessed from anywhere in that JavaScript file after declaration.
function scope: Variables defined inside a function are not accessible from outside.
 
 
### return
 
Return Statements:  a function can also return a value back to the place where it was called. This is done via a return statement.Its value is returned by the function and can be stored when the function is called:

function add3Numbers(first, second, third) {
  const sum = first + second + third;
  return sum;
}

const firstSum = add3Numbers(1, 2, 3);
// the return value is stored in "firstSum", namely 6
 
A function can return only one expression value, but can have multiple return statements, in combination with if else statements.

### Early Return Statements
 
As soon as a return statement is reached in a function call, the function execution is ended. The following console.log() is therefore never reached:
 
function testFunction() {
 
  return "a returned string";

  console.log("I am never logged in the console.");

}
 

 

 
