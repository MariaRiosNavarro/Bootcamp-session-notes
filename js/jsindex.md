#Javascript 

##Index

- [JS Basics:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-basics/js-basics.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-basics/challenges-js-basics.md)

- [JS Variables & Numbers:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-variables-and-numbers/challenges-js-variables-and-numbers.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-variables-and-numbers/challenges-js-variables-and-numbers.md)

- [JS Conditions and Booleans:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-conditions-and-booleans/js-conditions-and-booleans.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-conditions-and-booleans/challenges-js-conditions-and-booleans.md).

- [JS functions:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-functions/js-functions.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-functions/challenges-js-functions.md).

- [JS functions 2:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-functions-2/js-functions-2.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-functions-2/challenges-js-functions-2.md).

- [JS Inouts & Strings:]()[Challenges]().

- [JS Objects & Arrays:]()[Challenges]().

- [JS Create Element:]()[Challenges]().

- [JS Forms 2:]()[Challenges]().



<hr>

### JS Basics

We conect JS with the ```<script>``` Tag
```<script src="./index.js" defer ></script>```
defer tells the browser to delay the loading of the script until all HTML elements are loaded.

In JavaScript we can print text to the console of the web browser.Helps to debugging:
```console.log("Hola Mundo")```
To add interactivity we need to select the necessary HTML.

```
<body>
  <main class="main" id="main" data-js="main">...</main>
</body>
```
There are multiple ways to select the above main section within our JavaScript. A good practice is to use a data-* attribute, like the data-js in the following example:

```
const mainElement = document.querySelector('[data-js="main"]');
```

Other css selectors work as well, but the data-* attribute selectors should be preferred: 

document.querySelector("main"). --->TAG
document.querySelector(".main") --->CLASS
document.querySelector("#main") ---> ID

INTERACTION with ```.addEventListener()``` is used to react to events.

```
<button type="button" data-js="button">Log into console</button>
```
```
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {});
```
There different events you can listen to, for example: "mouseover","keydown"
[List of events](https://developer.mozilla.org/en-US/docs/Web/Events#event_listing)

ADD, Remove and Toggle with ```.classList```

E.g:

```
<main data-js="main">
  <button type="button" data-js="button">Add a class</button>
</main>

```

```
const main = document.querySelector('[data-js="main"]');
const button = document.querySelector('[data-js="button"]');

button.addEventListener("click", () => {
  main.classList.add("page--primary");
});

```

<hr>

### JS Variables & Numbers

Variables are a reference or alias for data stored in memory. You can access this data by using this variable.Three different keywords to declare a variable:

const - declares a constant, the value CAN´T BE CHANGED. DEFAULT way to declare variables.
let - declares a variable, the value CAN BE CHANGED. Only used when reassigning a new value is necessary.
var - outdated, not used anymore.
Normally the keyword const is used to declare a variable. The keyword let is only used when you need to reassign a value, for example when you want to increase a counter. ```=``` mean the value of the item on the right of the equal sign is saved in the item on the left of it.

```
let number = 13;
number = number + 2;
```

PRIMITIVE DATA TYPES: 
```string``` - "Hello", "123", e.g
```number``` - 123, 3, -5, -1,2
```boolean```- ```true```or ```false```
```null``` - represent "nothing"
```undefined```- state od "not "existing"
```BigInt``` -integers larger (uncommon)
```Symbol``` -unique elements (uncommon)

Variable Naming: Expressive variable names are very important for the readability of the code. Use ```camelCase```, better all the words, specific longer better than shorter and not legible.

Math & Operators: 

```+``` adds

```-``` subtracts

```*```multiplies

```/```divides

```**```potentiates- ```3**2 ->9```

```%``` modulos  ```15 % 2 -> 1``` You can also use this operator to determine if a number is even or odd ```6 % 2; // → 0```


Operator Precedence: In maths, some operators have a higher precedence than others. This means that they are performed before operators with a lower precedence. For example, multiplication comes before addition. But  Prettier will remove any unnecessary parentheses from your expression automatically. [operator precedence](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)


Assignment Operators:

```+=``` increase the value: ```count +=8``` count is increased by 6.

```-=``` decreases the value.

```*=``` multiplies the value.

```/=``` divide the variable on the left with the value on the right.

```++``` increase by 1.

```--``` decrement by 1.


[Type Coercion](https://developer.mozilla.org/en-US/docs/Glossary/Type_coercion)

Number Systems: decimal (0-9), binary (0 1), hexadecimal (0-9, a-f)


<hr>

### JS Conditions and Booleans:

Boolean Values are only ```true``` and ```false```
Truthy values are values that evaluate to true when converted to a boolean, and falsy values are values that evaluate to false when converted to a boolean. 

Truthy values:
- Non-empty strings, including whitespace (" ")
- Non-zero numbers
- Objects and arrays
- Functions
- Boolean value ```true```


Falsy values:
- Empty strings ("")
- Zero (0) and negative zero (-0)
- NaN (Not-a-Number)
- null
- undefined
- Boolean value ```false```

Comparison Operators:

```A === B ```	strict equal: is true if both values are equal (including their type). 

```A !== B```	strict not equal: is true if both values are not equal (including their type).

```A > B```strictly greater than: is true if A is greater than B.

```A < B```	strictly less than: is true if A is less than B.

```A >= B	```greater than or equal: is true if A is greater than or equal B.

```A <= B	```less than or equal: is true if A is less than or equal B.

IMPORTANT:

```= (const x = 0) ```is the assignment operator and has nothing to do with comparison.
```== ```and ```!= ```are non-strict equality operators. You should avoid them 99% of the time.
Non-strict equality tries to use type coercion to convert both values to the same type: "3" == 3 is true, which is seldomly what you want.
```===``` and ```!==``` are strict equality operators. This is what you need almost always.
Strict equality checks if type and value are the same: "3" === 3 is false.

Logical Operators: combine up to two booleans into a new boolean.

```!A```	not: flips a true value to false and vice versa.

```A || B```	or: is true if either A or B is true.

```A && B```	and: is true if both A and B is true.

 You can combine logical operators with brackets to define which operator should be evaluated first, e.g: ```(A || B) && (C || D)```
 
 CONTROL FLOW: ```ìf ( ) { }/ else { }```
 
 With an if statement we can control whether a part of our code is executed or not, based on a condition, The else block is executed only if the condition is false. The condition expression between the () brackets can be composed of logical or comparison operators as well. You can distinguish between more cases by chaining ```else if``` statements.
 
 ```
 if (hour < 12) {
  console.log("Good Morning.");
} else if (hour < 18) {
  console.log("Good afternoon.");
} else if (hour === 24) {
  console.log("Good night.");
} else {
  console.log("Good evening.");
}
```
 
 
 
 
 If the condition is not a boolean, it is converted into one by type coercion. This can be used to check whether a value is not 0 or an empty string
 
```
 const name = "Alex";
if (name) {
  console.log("Hi " + name + "!"); // only executed if name is not an empty string
}
```
 
TERNARY OPERATOR ```?  :```

condition ? expressionIfTrue : expressionIfFalse;

The operator can only distinguish between two expressions like values, math / logical operations or function calls, not between statements like variable declarations, if / else statements or multi-line code blocks.

[Ternary Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)

<hr>

### JS functions

<hr>
### JS functions 2


<hr>
### JS Inouts & Strings:

<hr>
### JS Objects & Arrays:


<hr>
### JS Create Element:

<hr>
### JS Forms 2:

<hr>
### JS ...
