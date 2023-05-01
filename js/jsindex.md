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

<hr>
Assignment Operators:
```+=```increase the value: ```count +=8``` count is increased by 6
```-=```decreases the value
```*=```multiplies the value
```/=```divide the variable on the left with the value on the right
```++```increase by 1
```--```decrement by 1

[Type Coercion](https://developer.mozilla.org/en-US/docs/Glossary/Type_coercion)

Number Systems: decimal (0-9), binary (0 1), hexadecimal (0-9, a-f)


### JS Conditions and Booleans:
### JS functions
### JS functions 2
### JS Inouts & Strings:
### JS Objects & Arrays:
### JS Create Element:
### JS Forms 2:
### JS ...
