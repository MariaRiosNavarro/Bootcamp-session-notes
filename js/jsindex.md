
# Javascript



## Index



- [JS Basics:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-basics/js-basics.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-basics/challenges-js-basics.md)

- [JS Variables & Numbers:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-variables-and-numbers/challenges-js-variables-and-numbers.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-variables-and-numbers/challenges-js-variables-and-numbers.md)

- [JS Conditions and Booleans:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-conditions-and-booleans/js-conditions-and-booleans.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-conditions-and-booleans/challenges-js-conditions-and-booleans.md).

- [JS functions:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-functions/js-functions.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-functions/challenges-js-functions.md).

- [JS functions 2:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-functions-2/js-functions-2.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-functions-2/challenges-js-functions-2.md).

- [JS Inputs & Strings:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-inputs-and-strings/js-inputs-and-strings.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-inputs-and-strings/challenges-js-inputs-and-strings.md).

- [JS Objects & Arrays:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-objects-and-arrays/js-objects-and-arrays.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-objects-and-arrays/challenges-js-objects-and-arrays.md).

- [JS Forms:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-forms/js-forms.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-forms/challenges-js-forms.md).


- [JS Create Element:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-createelement/js-createelement.md)[Challenges]().

- [JS Forms 2:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-forms-2/js-forms-2.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-forms-2/challenges-js-forms-2.md).

- [JS Loops :](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-loops/js-loops.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-loops/challenges-js-loops.md).

- [JS Callback Functions :](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-callback-functions/js-callback-functions.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-callback-functions/challenges-js-callback-functions.md).

- [JS Array Methods:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-array-methods/js-array-methods.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-array-methods/challenges-js-array-methods.md).

- [npm and Linting Basics:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/npm-and-linting-basics/npm-and-linting-basics.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/npm-and-linting-basics/challenges-npm-and-linting-basics.md).

- [JS Structure :](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-structure/js-structure.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-structure/challenges-js-structure.md).

- [JS Arrays Methods 2:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-array-methods-2/js-array-methods-2.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-array-methods-2/challenges-js-array-methods-2.md).

- [JS Async Functions:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-async-functions/js-async-functions.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-async-functions/challenges-js-async-functions.md).

- [JS Fetch](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-fetch/js-fetch.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-fetch/challenges-js-fetch.md).

- [JS Modern Syntax](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-modern-syntax/js-modern-syntax.md)[Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-modern-syntax/challenges-js-modern-syntax.md).



<hr>

### 1.-JS Basics ###

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

### 2.-JS Variables & Numbers

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

### 3.-JS Conditions and Booleans:

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

```=``` (```const x = 0```) is the assignment operator and has nothing to do with comparison.

```== ```and ```!= ```are non-strict equality operators. You should avoid them 99% of the time.

Non-strict equality tries to use type coercion to convert both values to the same type: "3" == 3 is true, which is seldomly what you want.

```===``` and ```!==``` are strict equality operators. This is what you need almost always.

Strict equality checks if type and value are the same: "3" === 3 is false.



LOGICAL OPERATORS: combine up to two booleans into a new boolean.

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

### 4.-JS functions

Functions are a fundamental concept in JavaScript. They contain a set of statements - in other words: They contain JavaScript code. Functions have to be defined. When a function is defined it can be called an arbitrary number of times.
To declare we need.

- the ```function``` keyword
- the function name
- the function body (JavaScript statements / JavaScript code)

```
function greet() {
  console.log("Hi Friends!");
  console.log("Nice to be here.");
}
```


Parameters: Functions can accept parameters. Parameters can be used like predefined variables inside the function body. When declaring a function we are free to choose a name for the parameters

```
function printSum(first, second, third) {
  const sum = first + second + third;
  console.log("The sum of your numbers is: " + sum);
}
```

Function Calls: When functions are defined you can call them by writing their name, followed by parentheses ("round brackets"). If the functions consume parameters you can pass them as arguments in the brackets. With the e.g of above: ```printSum( 1, 2, 3);```


 
Scope:

The scope defines where variables are visible and where they can be referenced. In JavaScript there are different kinds of scope, for example:

- global scope : A variable is in the global scope when it is declared outside of any function, in a JavaScript file. Global variables are visible and can be accessed from anywhere in that JavaScript file after declaration.
- function scope : Variables defined inside a function are not accessible from outside. But all variables outside of the function can be accessed from inside the function body.

```
const globalVariable = "some Text";

function myFunction() {
  const localVariable = true;

  console.log(globalVariable);
  console.log(localVariable);
}

myFunction();
// logs:
// some Text
// true

console.log(localVariable); // Error! Variable not available outside of function

```



<hr>

### 5.-JS functions 2: 

```return``` statement, early return, fat arrow notation:
A function can also return a value back to the place where it was called. This is done via a ```return``` statement.

```
function add3Numbers(first, second, third) {
  const sum = first + second + third;
  return sum;
}
```
A function can return only one expression value, but can have multiple return statements, in combination with if else statements for example:

```
function checkInputLength(inputString) {
  if (inputString.length > 3) {
    return true;
  } else {
    return false;
  }
}
```

[Statements vs Expressions](https://www.joshwcomeau.com/javascript/statements-vs-expressions/)

EARLY RETURN STATEMENTS: As soon as a return statement is reached in a function call, the function execution is ended. The following console.log() is therefore never reached:

```
function testFunction() {
  return "a returned string";

  console.log("I am never logged in the console.");
}
```

This behavior can be used to our advantage as early return statements. Sometimes we want to execute certain parts of our code only if a condition applies. 

```
function setBackgroundColor(color) {
  if (typeof color === "String") {
    if (color.startsWith("#")) {
      if (color.length >= 7) {
        document.body.style.backgroundColor = color;
      }
    }
  }

```
```
function setBackgroundColor(color) {
	// first condition
	if(typeOf color !== 'String') {
		return;
	}

	// second condition
	if(!color.startsWith('#')) {
		return;
	}

	// third condition
	if(color.length < 7) {
		return;
	}

	// only if all 3 conditions are passed the final line of code is executed.
	body.style.backgroundColor = color;
}
```
This way of writing the code is more readable

A return statement can be left empty, the returned value is then undefined

ARROW FUNCTION EXPRESSIONS: The function is saved like a variable with the keyword const. The parameters are written normally in round brackets followed by an fat arrow =>. Then the function body is written in curly brackets.
```
const addNumbers = (first, second) => {
  return first + second;
};

```
IMPLICIT RETURN STATEMENTS

The advantage of arrow functions are possible shorter notations when certain criteria apply:
- Omit the round brackets around the parameters: This is possible, if there is only one input:

```
const addOne = (number) => {
  return number + 1;
};
```

- Implicit return statements: If the function consists only of a return statement, the curly brackets and the return keyword can be omitted:

```
const addNumbers = (first, second) => {
  return first + second;
};

```

can rewritten to: ```const addNumbers = (first, second) => first + second```



The syntax of the addEventListener method. We encountered these arrow functions there already!

<hr>


###  6.-JS Inputs & Strings:


There are three ways to create strings using string literals-

```
'string': single quotes
```

```
"string": double quotes
```

```
`string`: back ticks or template literals.
```


- Strings can be chained together by using the + operator (yes, the same as the maths operator). This is called string concatination

```
const name = "Alex";
const stringConcatination = "Hello " + name + ", good to see you!";
```

Template Literals

The third method to write strings has the useful property that you can insert variables into the string by wrapping placeholders with a dollar sign and curly brackets ${} . This is also called string interpolation

```
const stringConcatination = "Hello " + name + ", good to see you!";

const withTemplateString = `Hello ${name}, good to see you!`;
```
Any expression can be placed into these placeholders:
````
const greeting = `Hello ${
  name !== null ? name : "mysterious person"
}, good to see you!`;
````

With template literals you can also write multi-line strings:

String Properties and Methods: 

Strings in JavaScript have some build-in properties and functionalities called methods. You can call them with the dot notation followed by the name of the property / method

```.length```-returns the number of characters in a string.


```.toUpperCase()```-returns a all uppercase version of the string.


```.toLowerCase()```-returns a all lowercase version of the string.


```.trim()```-returns a string with all whitespace removed from the beginning and end


```.replaceAll(oldString, newString)```- replaces all occurrences of oldString with the newString.


```.startsWith(subString)```-returns true if the string starts with subString.


```.endsWith(subString)```-returns true if the string ends with subString.


```.includes(subString)```-returns true if the string contains the subString.



[More methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#instance_properties)


### Input Fields


Every input field in HTML holds a value in form of a string. You can access the value by using .value on the input Element:

```
<form>
  <input data-js="textInput" type="text" value="test 123" />
  <input data-js="numberInput" type="number" value="42" />
</form>
```
Here in JS:

```
const textInput = document.querySelector('[data-js="textInput"]');
const numberInput = document.querySelector('[data-js="numberInput"]');

textInput.value; // evaluates to 'test 123'
numberInput.value; // evaluates to '42' (still a string!)
```


You can also change the value of the input by assigning a new value to this input property. 
This change is immediately visible on the website.For example, you can enforce all uppercase letters in a form by combining this functionality with an input event listener on the input element:


```
// transform on every change the input value to uppercase letters
textInput.addEventListener("input", () => {
  const oldValue = textInput.value;
  const newValue = oldValue.toUpperCase();
  textInput.value = newValue;
});
```

Change a Input.value from string to number with ```Number.parseInt()``` :

```
const inputString = input.value;
const inputNumber = Number.parseInt(inputString);
````
or you can use: 

```
`$(inputString.parseInt())`

````


<hr>


###  7.-JS Objects & Arrays:

### Array - structured data type- Look like:

```
const array = ["string", 22, true];
const nestedArray = [23, false, [true, "hello"], "apple"]

````


We can acces to the values with index (begin at 0). You can access individual items using the bracket notation and the item's index. You can overwrite individual values in an array too. With the examples of above:
 
```
const secondItemOfArray = array[1];
const thirdItemOfNestedArray = nestedArray[2][0];
//add new value
const shoppingList = ["apple", "tomato"];
shoppingList[0] = "banana";
shoppingList; // ["banana","tomato"];

````

Array Methods:

```array.length```	returns the number of elements in the array

```array.push(element)```	adds element to the end of the array

```array.pop()```	removes the last element of an array

```array.unshift(element)```	adds element as the first element of the array

```array.shift()	```removes the first element of the array




### Object

````
const object = { 
	propierty1:"string",
	propierty2: 22,
	propierty3: true
	}

const nestedObject = {
    name: "Marge",
    age: 36,
    parents: {
      mothersName: "Jacqueline Bouvier",
      fathersName: "Clancy Bouvier",
    	}
    }

````




For the Objects we can acces with dot notation or with brackets notation:


````
const thirdPropiertyValueOfObject = object.propierty3;
const thirdPropiertyValueOfObjectVERSION = object["propierty3"];
// thirdPropiertyValueOfObject AND thirdPropiertyValueOfObjectVERSION are the same propierty
const firstPropiertyOfThirdPropiertyNestedObject= nestedObject.parents.mothersName

`````


You can change values of object properties by reassigning them using the dot or bracket notation, you can add new properties in the same way. You can delete properties using the delete keyword

delete object.propierty;


<hr>


### 8.-JS Forms:


With ``` .preventDefault().```  we prevent a GET request from being sent in the browser (it is predefined).

To prevent this behaviour:

- put the event object as argument of the arrow function of the event listener

- call event.preventDefault()


The browser will not make a GET request that causes the page to reload when it is submitted.


While event.target represents the entire form, event.target.elements is a collection of all form elements (form fields, field sets and buttons).

You can access a specific form field through its name attribute and dot notation:

``` 
form.addEventListener("submit", (event) => {
  event.preventDefault();

  const formElements = event.target.elements;

  console.log(formElements.firstName);
  console.log(formElements.firstName.value);
});
``` 

event.target.elements is stored in the variable formElements for better readability,
firstName is the string value of the corresponding name attribute, as in <input name="firstName"/>, and
firstName.value returns the user input for the field with name="firstName".

To receive an object from the entire form we use:

```

form.addEventListener("submit", (event) => {
  event.preventDefault();

  const formData = new FormData(event.target);
  const data = Object.fromEntries(formData);

  console.log(data);
});

````

Exception: Reading Values from Checkboxes

Checkboxes have two states: checked ("true") and not checked ("false"). In contrast to other input types, the value attribute does not reflect this change, but is only used as an identifier for the checkbox.

You can access the checkbox's state via the .checked property instead.

Imagine the following checkbox

```
<input type="checkbox" name="colorBlue" value="blue" />
```

and its corresponding JavaScript:

```
console.log(formElements.colorBlue.checked); // output: true or false
console.log(formElements.colorBlue.value); // output (always): blue
```

<hr>


### 9.-JS Create Element:

The DOM:
The Document Object Model is a representation of the HTML document. Each HTML Tag is modelled as a node in a tree structure, which shows how HTML elements are nested. A computer program such as your JavaScript file can access and manipulate the HTML website by changing the DOM via the document object.

You can generate an HTML element with JavaScript by using the document.createElement method. It expects the type of element as an argument.After generating an element, you need to place the element into the DOM. For this, you can use the .append method. It places the element as the last child into the respective element.

```

const article = document.createElement("article");
const button = document.createElement("button");

document.body.append(article); // placing the created article at the end of the body
article.append(button); // placing the created button into the article

```


```

<body>
  ...
  <article>
    <button></button>
  </article>
</body>

```


Element Properties and Methods

As well as with queried HTML elements (via querySelector), we can add classes, event listeners and more to the created HTML elements.The text of an element can be changed by reassigning the .textContent property

Common Element Properties and Methods:

```classList```-	add, toggle or remove classes from element
```textContent```-	get or set text inside element
```style```-	define inline style, e.g. element.style.backgroundColor = "red" 
```hidden```-	boolean whether element is hidden or not
```focus()```-focusses the element on the website
```hasAttribute()```-	returns true if the element has the given attribute
```querySelector()```-returns the first child that matches the given CSS selector


**.innerHTML**

The innerHTML property can be used to create the entire html layout of an element by passing the html code as a string. By using template literals the content of the html can be dynamically created.❗️ innerHTML can be unsafe when user input is passed into the template literal. Use it with caution. Read this article for more information about it.
The innerHTML property can be used to create the entire html layout of an element by passing the html code as a string. By using template literals the content of the html can be dynamically created.Resetting Element Content

```
const cityName = "Lissabon";

article.innerHTML = `
	<h2> ${cityName} </h2>
	<p class="card__content">
		${cityName} is a very beautiful city in Portugal. 
		Go there and enjoy the stay!
	</p>
	<button type='button' class="card__booking-button"> 
		Book Trip 
	</button>
`;
```

HTML:

```
<body>
  ...
  <article>
    <h2>Lissabon</h2>
    <p class="card__content">
      Lissabon is a very beautiful city in Portugal. Go there and enjoy the
      stay!
    </p>
    <button type="button" class="card__booking-button">Book Trip</button>
  </article>
</body>

```


.innerHTML can also be used to reset the content of an element, e.g. a container:

html before:

<ul data-js="cardContainer">
  <li class="card">...</li>
  <li class="card">...</li>
  <li class="card">...</li>
</ul>

after that:

```
const cardContainer = document.querySelector('[data-js="cardContainer"]');
cardContainer.innerHTML = "";

```

is our ul empty:

<ul data-js="cardContainer"></ul>

!!!


<hr>

### 10.-JS Forms 2:

HTML FORM VALIDATION:
Before submitting a form, it is important to ensure all required form fields are filled out, in the correct format. This is called client-side form validation. HTML provides several form field attributes to enable validation features build into the browser: 

```required ```	if present, a form field needs to be filled in before the form can be submitted
```minlength / maxlength```	minimum and maximum length of textual data (strings)
```min / max```	minimum and maximum values of numerical input types
```type	```each input type has its own prefigured validation (like email)
```pattern```	a regular expression pattern the entered data needs to follow

EG:
```
<input
  id="input-name"
  type="text"
  name="name"
  minlength="3"
  maxlength="30"
  required
/>

```

 If the required attribute is omitted, the field is valid if it is empty or has a content between 3 and 30 characters, but invalid if 1 or 2 characters are entered.
 
 ## The input Event
 
 Occasionally, you may want to do something if the value of a single field changes even before the form is submitted.

The input event is fired every time when the value of a form field has been changed. For example, a <textarea /> will fire this event with every keystroke. ( Don't confuse the input event with the change event, which is only fired after a field's content has been committed by the user by pressing enter or moving the focus to the next field.)

```
const messageField = document.querySelector('[data-js="message"]');

messageField.addEventListener("input", (event) => {
  console.log(event.target.value);
});

````

Focus Input Fields: You can focus an input field with the .focus() method. This can be used to improve the user experience after submitting a form.

const messageField = document.querySelector('[data-js="message"]');

```

form.addEventListener("submit", (event) => {
  event.preventDefault();
  // [...] handle form data
  messageField.focus();
});

```

Instead of querying the input element using querySelector, it can also be obtained via the event.target.elements collection:

```

form.addEventListener("submit", (event) => {
  event.preventDefault();
  // [...] handle form data
  event.target.elements.message.focus();
});

```

This will focus a form field with the attribute name="message".

Resetting Forms: You can reset all form fields to their default value with the .reset() method.

```

form.addEventListener("submit", (event) => {
  event.preventDefault();
  // [...] handle form data
  event.target.reset();
});

```

This often comes in handy in combination with .focus(). Think of a chat: After the message was send, the input field is cleared and re-focussed, so users can write the next message.



<hr>

### 11.-JS Loops ...


A loop executes a respective block of code over and over again until an end criteria is met. In JavaScript, two basic types of loops exist:

```while```  loop: are used when a task needs to be executed until a specific criteria is met.
```for``` loop: are commonly used when a given task needs to be executed x times or for each element in an object / array.
The while loop is the most fundamental type of loop. It repeats a code block as long as the stated criteria is true.

````
let string = "a";

while (string.length <= 8) {
  console.log(string);
  string = string + string;
}

// 'a'
// 'aa'
// 'aaaa'
// 'aaaaaaaa'

````

````for```` loops are intended for repeating a task a certain number of times. They consist of three internal parts:

an internal counter which is increased / decreased every iteration.
a criteria which checks the value of the counter. As long as the criteria is true, the loop is executed.
a rule how the counter is increased / decreased (in most cases it is increased by 1)

````
for (let counter = 0; counter < 4; counter++) {
  console.log(counter);
}
// 0
// 1
// 2
// 3
````

The ````for...in```` is a shorthand notation to loop through all keys of an object:

````
const user = {
  name: "Alex",
  age: 28,
  email: "alex@mail.com",
};

for (const key in user) {
  console.log(user[key]);
}

// 'Alex'
// 28
// 'alex@mail.com'

````

Similar to ````for...in```` the ````for...of```` loop is a shorthand notation, but for looping through all items of an array.

````

const fruits = ["apple", "banana", "melon"];

for (const fruit of fruits) {
  console.log(fruit);
}

// 'apple'
// 'banana'
// 'melon'

````



<hr>

### 12.-JS Callback Functions ...


###  Callback Functions
A callback function is a function that is passed as an argument into another function.

The outer function can execute this callback function at the correct moment or multiple times, for example:

when an event is triggered
when the fetched data arrived on your computer
for each element in an array.
Callback functions are used, whenever the program itself needs to figure out when or how many times the function needs to be executed. We already used callback functions in event listeners:

````
button.addEventListener("click", () => {
  console.log("Inside the callback function.");
});
````
Here the structure is as follows:

outer function: addEventListener()
first argument: 'click'
second argument: callback function
````
() => {
  console.log("Inside the callback function.");
};

````
This type of function is called anonymous function, since it is declared without giving it a name.

###  Named Callback Functions
Any function can be used as a callback function. It just needs to be passed to another function. You can declare a normal function and then use the name of the function to pass it into another function:
````
function sayHello() {
  console.log("Hey Dude!");
}

button.addEventListener("click", sayHello);
````

❗️ Note that we do not call the function here (we wrote sayHello instead of sayHello()). We only pass the function to the event listener. The function is only called when the event happens.

###  Higher Order Functions
A higher order function is a function that takes a callback function as an argument and calls the callback function inside their body, e.g. the addEventListener method.
````
// this function calls its callback function 3 times!
function myHigherOrderFunction(callback) {
  callback();
  callback();
  callback();
}
````
We will encounter these higher order functions in future sessions:

.````then````

.````forEach````

.````map````

.````filter````


💡 Don't worry, you don't have to write higher order functions yourself, you only apply them to solve certain problems.

### Parameters in Callback Functions
A callback function can accept parameters. The values for the parameters are provided by the function, that calls the callback function (the "higher order function").

In this example the callback function can accept a parameter to retrieve information about the occurred event:
````
button.addEventListener("click", (event) => {
  console.log("This button was clicked:", event.target);
});

````





<hr>

### 13.-JS Array Methods ...

Introduction to array methods
All array methods presented here have a lot in common and can be used in the same way.

You provide a callback function with one parameter
The array method iterates over an array
The provided callback function gets called for each element in the array
With each call to the function the current array element gets passed as first argument
This way you can write code and apply it to each element within an array


### .for each

````
const pets = ["bird", "cat", "dog", "ferret", "fish"];
pets.forEach((pet) => {
  const petElement = document.createElement("p");
  petElement.textContent = pet;
  document.body.append(petElement);
});

````

The array method forEach executes some logic for each element within an array.❗️ The callback function provided to forEach must not use a return statement. forEach > does not return a new array.
❗️ You should use forEach to use a side-effect, like document.createElement

### .map

```
const pets = ["bird", "cat", "dog", "ferret", "fish"];
const uppercasePets = pets.map((pet) => {
  return pet.toUpperCase();
});
console.log(uppercasePets); // ['BIRD', 'CAT', 'DOG', 'FERRET', 'FISH']

````

The array method map is used to apply a transformation to each ***element of an array.***

The transformed elements are stored in the newly created array returned by map. The elements in the original array are not being altered.

You can define the kind of transformation applied to each element in the callback function and return the transformed element.

The created and the original array have the same length. ❗️ The callback function provided to map must use a return statement to return a transformed element. map returns a new array.

❗️ You should not use map to trigger a side-effect, like document.createElement


### .filter

```
const pets = ["bird", "cat", "dog", "ferret", "fish"];
const petsWithF = pets.filter((pet) => {
  return pet.startsWith("f");
});
console.log(petsWithF); // ['ferret', 'fish']
```

The array method filter is used to create a new array with a subset of the elements of the original array.

The callback function returns a boolean value to define, if an element is being included in the resulting array or not. The original array is not being altered.

The created array is likely to have a shorter length than the original array. ❗️ The callback function provided to filter must use a return statement to return a boolean value.


### Chaining array methods
Often times you need to combine multiple array methods to achieve a desired result. Array methods like map and filter, that return a new array, can be chained. Instead of storing each array in a separated variable, the methods can be called directly after another. This reduces the amount of code and improves readable.

````
const pets = ["bird", "cat", "dog", "ferret", "fish"];
const uppercasePetsWithF = pets
  .filter((pet) => {
    return pet.startsWith("f");
  })
  .map((pet) => {
    return pet.toUpperCase();
  });
console.log(uppercasePetsWithF); // ['FERRET', 'FISH']

````

### document.querySelectorAll

With document.querySelectorAll you can select a list of elements from the DOM. This is in contrast to document.querySelector, which provides only the first occurrence of an element matching the selector.
````
const pets = document.querySelectorAll('[data-js="pet"]');
console.log(pets.length); // 5
The NodeList returned by document.querySelectorAll is an array-like object. You can use the forEach method to iterate over the DOM elements.

const pets = document.querySelectorAll('[data-js="pet"]');
pets.forEach((pet) => {
  pet.addEventListener("click", () => {
    // [...]
  });
});

````
❗️ A NodeList is not an array! Other array methods like map or filter can't be used. If you need to use array methods, you can convert the NodeList to an array using ***Array.from()***

<hr>

### 14.-JS npm and Linting Basics ...

npm
It's a package registry that works like an app store for your project.

package.json
Packages that are installed into your project are called dependencies. They are kept inside a package.json file in your project root. The package.json file also contains information about your project.

A package.json may look something like this:

```
{
  "name": "my-app",
  "version": "1.0.0",
  "description": "A description of my app",
  "scripts": {
    "test": "npm run …"
  },
  "author": "Alex Newfish",
  "license": "UNLICENSED",
  "dependencies": {
    "my-dependency": "^10.4.1",
    "my-other-dependency": "^2.0.0"
  },
  "devDependencies": {
    "my-dev-dependency": "^8.0.105",
    "my-other-dev-dependency": "^0.1.6"
  }
}
```

dependencies are packages that your application source code directly depends on, like libraries or frameworks.
devDependencies are packages that help you while developing your application, like linters or build tools.
Installing dependencies
dependencies and devDependencies inside the package.json can be installed by running npm install (or just npm i for short).

💡 Do not forget to run npm install after cloning a new repository that has a package.json file.

When installing, npm creates a node_modules folder and a package-lock.json file.

node_modules must always be in your .gitignore and must not be committed to your repository!
package-lock.json should be commited to your repository.


### Semantic Versioning

A semantic version is updated whenever a package changes and a new version is published.

It follows this schema: Major.Minor.Patch (e.g. 1.2.3)

Major → major version, changes when the public api of a package changes (breaking change)
Minor → minor version, changes when new features are added
Patch → patch version, changes when bugs are fixed
When defining dependencies in package.json npm uses version ranges to define which version of package should be installed. npm always installs the newest version of package that still matches the range description.

^ (e.g. "^10.4.1") → Newer minor updates and patches can be installed, but major updates cannot.
(Here version 10.5.6 would be installed but not 11.0.0)

~ (e.g. "~10.4.1") → Newer patches can be installed, minor and major updates cannot.
(Here version 10.4.8 would be installed but not 10.5.0)

> (e.g. ">10.4.1") → Any newer version will be installed.
(Here any version newer than 10.4.1 would be installed)

Version ranges described with ^ are by far the most commmon choice because they are usally safe and won't break your application.

### Linters

Linters are tools which analyze your code and show syntax errors, oversights like undeclared variables, bugs and stylistic errors. Some important linters are Prettier (Code formatter), HTMLHint (HTML), and ESLint (JavaScript).

To run these linters, we can define a script inside of the package.json as in the following example:
```
	"scripts": {
		"test": "npm run htmlhint && npm run prettier:check && npm run eslint",
		"fix": "npm run htmlhint && npm run prettier:write && npm run eslint",
		"htmlhint": "npx htmlhint \"**/*.html\"",
		"prettier:check": "npx prettier --check .",
		"prettier:write": "npx prettier --write .",
		"eslint": "npx eslint \"**/*.js\""
	}
```
### Prettier

Prettier makes sure that your code / the code of your team is formatted in the exact same way. There are two important ways to use it:

npx prettier --check . (checks for stylistic errors)
npx prettier --write . (fixes stylistic errors)
The command npx (x = execute) starts prettier; the dot . at the end tells prettier to go through all files. You can also choose to check only specific files or folders.

The flags --check and --write decide whether to only check for errors or immediately fixing them.

We can also use the scripts called "prettier:check" and "prettier:write" in the package.json above via npm run prettier:check or npm run prettier:write. It will do the exact same thing as npx prettier [...].

### HTMLHint

HTMLHint analyzes your HTML. You can use

npx htmlhint index.html (analyzes the index.html file) or the script
npm run htmlhint.
Note that, according to the above package.json, the script will run npx htmlhint \"**/*.html\" and thus analyze all files ending with .html.

### ESLint

ESLint analyzes your JavaScript and highlights errors. You can use

npx eslint index.js (analyzes the index.js file) or the script
npm run eslint.
Note that, according to the above package.json, the script will run npx eslint \"**/*.js\" and thus analyze all files ending with .js.


### Combining Scripts

We can write a script using several other scripts and thus running all linters at once. See the above mentioned scripts npm run test and npm run fix which will run htmlhint, prettier and eslint.

The && means that the script will run one after another. The next script only is executed if the one before found no issues.

### Setup Files for Linters

All linters come with a built-in ruleset, but we can configure these rules. We do this with files at the root of our project called .eslintrc.js, .htmlhintrc.json, or .prettierrc. You can recognize them by the "rc", but the file ending might differ.

We can also say which files the linter will ignore. This is done inside of .eslintignore or .prettierignore.

Error messages are your friends

💡 Error messages are your friends, that kindly point you towards errors. Learning to correctly read error messages is one of the most important skills you'll pick up as a developer.

If you come across an error message, take your time to fully understand what it is saying. Then navigate to the place in code where it found the issue. This way you know exactly what to fix and where.



<hr>

### 15.-JS Structure ...

### JavaScript Modules
JavaScript modules (sometimes also called "ECMAScript Modules" or "ESM") are a way to organize code into separate files. To use modules you have to let the browser know that you are using modules. This is done by adding the type="module" attribute to the <script> tag.

````<script type="module" src="./my-module.js"></script>````
	
	
💡 Modules allow you to use import and export statements but also change a few other things about how the browser treats your code that differ from standard scripts: They have their own scope and are not accessible from the global scope (unless exported). They also do not require the defer attribute as they are deferred by default. The scripts are executed in the more modern strict mode automatically.

💡 When reading about modules online you might stumble upon the file extension .mjs which is sometimes used for JavaScript modules. For modules both .js and .mjs work fine but we've decided to use the .js extension for consistency. There is a great section discussing .js vs .mjs on mdn.

### Exporting using export Statements
	
Using the export statement you can export a variable or function to make it available to other modules. You can use named exports to export multiple variables or functions or one default export per module to export the main functionality of the module.

### Named Exports
	
Usally named exports are created by using the keyword export dircectly before const, let or function.

```
export const name = "Alex";
export const age = 26;
export function sayHello() {
  console.log("Hello");
}
```
	
It is also possible to export functions or variables after they have been declared.
	

````
const name = "Alex";
const age = 26;
function sayHello() {
  console.log("Hello");
}

export { name, age, sayHello };
	
````
	
	
	
### default Exports
	
Default exports are created by using the keyword export default. You can only have one default export per module.

Before a function declaration the syntax is similar to named exports.

````
export default function sayHello() {
  console.log("Hello");
}
````	
For directly exporting variables as default you only declare the value of the thing you're exporting.
	
	
export default "Alex";
	
	
This is the same for arrow functions.	

````
export default () => {
  console.log("Hello");
};	
````
	
💡 Notice that there is no const name = or const sayHello = in the code above. Default exports are nameless and constant by default.

Just like with named exports you can export the default export after it has been declared.

````
const name = "Alex";

export default name;
````
	
	
💡 Notice that since default exports have no clear name the should semantically correspond to the name of the module. The above example should have a module name like name.js.
	
	
### Mixing Named and default Exports
	
	
You can mix named and default exports.
		
	
````
export const name = "Alex";
export default function sayHello() {
  console.log("Hello");
}
````
	
### Importing using import Statements
	
Code from other modules can be imported using the import statement. Import statements should always be placed at the top of the file. Everything that can be exported from a module can also be imported from another module.

### Importing Named Exports
	
If another module exports a named export you can import it as such.
	
	
````
import { name, age } from "./my-module.js";
	
````
	
	
Now name and age are available in the current module.

### Importing default Exports
	
If another module exports a default export you have to give it a name when importing it.
	
	
	
````

import myModule from "./my-module.js";
	
````
	
	
💡 Notice that the name you give it does not nessesarily have to match the name of the module or the original name of the thing that was exported. For example myModule could have the value of the sayHello function which is not clear from the name. Since you could import the same module in multiple files you can also give it a different name every time.

### Mixing Named and default Imports
	
You can mix named and default imports.
	
	
	
````
import myModule, { name, age } from "./my-module.js";
````
	
	
### Renaming Named Imports
	
	
You can rename named imports explicitly by using the as syntax.
	

````
import { name as firstName, age as yearsSinceBorn } from "./my-module.js";
````
	
	
The variables firstName and yearsSinceBorn are now available in the current module. This can be useful if the name of an import conflicts with a local variable name.

In contrast to default imports, you have to be explicit that you are renaming and what the original names were.

### Structuring JavaScript Code
	
Utility Functions and Constants
Utility functions are functions that are used in multiple places in your code. They are usually smaller functions that are used to perform a specific task. They should be be pure and not have any side effects.

Shared constants are constants that are used in multiple places in your code.

Functions and constants can be grouped into files that are named after the functionality they provide. For example math.js could contain functions like add, subtract, multiply and divide.

The file should have a named export for each function.

We recommend to create a utils folder in your project and put all utility functions in there.

### Vanilla JavaScript Components
	
Vanilla JavaScript means that you are not using a framework like React (from vanilla being the most basic variant of ice cream).

Even though there is no set standard for structuring vanilla JavaScript components, we recommend the following:

### Create a folder for each component
	
Make your component file and function names uppercase (PascalCase)
Each component has a named export for the component function (e.g. export function ButtonGroup())
Components can take arguments that are called props or properties a convention (e.g. export function ButtonGroup(props))
Components should not depend on the outside world and create their own DOM elements
Components should return a single DOM element
💡 These are just recommendations

Another common convention is to use kabap-case names for component files. This way they are named after the BEM block class name. For example you could use button-group/button-group.js and button-group/button-group.css for a component that has a .button-group class. This is the same organizational style you are used to when working with just CSS.

The name of the component function could also be createButtonGroup() or even createButtonGroupElement() to make it is clear that it is a function that creates a DOM element.

Whatever style you choose, make sure you are consistent per project.

Here is an example of a component that creates a button:

````
export function Button(props) {
  const button = document.createElement("button");
  button.classList.add("button");
  button.textContent = props.text;
  return button;
}
````
	
	
An advanced use case are components that call other components (composition):
	
	

````
import { Button } from "../Button/Button.js";

export function ButtonGroup(props) {
  const buttonGroup = document.createElement("div");
  buttonGroup.classList.add("button-group");
  for (const buttonProps of props.buttons) {
    const button = Button(buttonProps);
    buttonGroup.append(button);
  }
  return buttonGroup;
}
````
	
Here is how these components could be used in another file:
	
	
````
import { ButtonGroup } from "./ButtonGroup/ButtonGroup.js";
import { Button } from "./Button/Button.js";

const myButtonGroup = ButtonGroup({
  buttons: [{ text: "Button 1" }, { text: "Button 2" }, { text: "Button 3" }],
});
document.body.append(myButtonGroup);

const myButton = Button({ text: "Button" });
document.body.append(myButton);
````
	
	
	
		
		
	
	

<hr>


### 16.-JS Arrays Methods 2: ...


	ARRAY METHODS


-`Arrax.forEach` - run logic on the array
-`Array.map()` -transforms the array
-`Array.filter() - to create a new array with a subset of the elements from the original array
  				(you need a filter on the object, xj .startsWith etc)


- `Array.includes()` - V or F - checks if the array contains the specified value.
- `Array.find()` - to receive the first element of the array that satisfies the provided check function. Otherwise, returns undefined.
- Array.findIndex()` - to receive the index of the first element of the array satisfying the provided hash function. If no such element exists, -1 is returned.


- `Array.slice()` - It is important to note that some array methods, such as sort(), do not create a new array, but mutate the original. slice makes a copy.
- `Array.sort()` - to sort the elements of an array. You need to provide a callback function to indicate how the array is sorted.
                          - two things inside the callback function: lowercase both strings before comparing them (uppercase also works)
			   using if statements, be explicit about the return values that depend on the result of the comparison (nameA < 				nameB and nameA > nameB)


- `Array.some()` - T or F - Use some() to check if at least one element of the array passes the test provided.
- `Array.every()` - V or F - Use every() to check if all elements pass the test.
- `Array.reverse()` - To reverse an array, simply use array.reverse(). This can also be combined with sort():
- `Array.reduce()` -the end result is a single value. This is an array method for reducing a list of values to a single value.
	1- it 	executes the callback on each element of the array, 
	2- the return value of each calculation is passed to the next calculation (i.e. it becomes the new starting value for the next 	iteration through the array). Its main use case is to calculate the sum of an array of numbers.

- `String.startsWith()`.
- `String.endWith()`.
	
	
<hr>

### 17.-JS Async Functions ...
	
Asynchronous code is code that runs in the background. This is useful for tasks that can take a long time to complete, but don't need to block the main thread.

JavaScript is a single-threaded language, meaning that only one thing can happen at a time.

Blocking the main thread is bad because it prevents the user from interacting with the page because no other JavaScript code can be executed. Examples of asynchronous code include: network requests, file system access, animations and timers.
	
	
	### Promises
	
	
A Promise is an object that represents the eventual completion (or failure) of an asynchronous operation, and its resulting value. Most of the time it is returned by a function that performs an asynchronous operation.

The Promise object has the following properties and methods:
	
	
```state```	the state of the Promise object, can be "pending", "resolved" or "rejected"
```result```	the result of the asynchronous operation (you'll almost never need to access this directly)
```then()```	a method that takes a callback function that will be called when the asynchronous operation is complete
```catch()```	a method that takes a callback function that will be called when the asynchronous operation fails
```finally()```	a method that takes a callback function that will be called when the asynchronous operation is complete, regardless of whether it was successful or not
	
	
```	
functionThatReturnsAPromise().then((value) => {
  console.log(value);
});
	
```
	
💡 Promises are almost always created for you by other asynchronous APIs, only rarely do you create them yourself. If you create a Promise yourself (new Promise()), you either know exactly what you are doing, or you are probably doing something wrong.
	
### Asnyc Functions and the await Keyword
	
Asnyc functions are a syntactic sugar for Promises. Using the await keyword, you can write asynchronous code that looks synchronous. Any function can be prefixed with the async keyword:

```
async function myAsyncFunction() {
  // ...
}

const myAsyncArrowFunction = async () => {
  // ...
};
```
	
	
Inside an async function, you can use the await keyword to wait for a Promise to be resolved:
	
```
async function myAsyncFunction() {
  const value = await functionThatReturnsAPromise();
  console.log(value);
}
```
	
	
This is can be easier to read than the Promise syntax especially when you have multiple asynchronous operations that depend on each other.

	
```
async function myAsyncFunction() {
  const value1 = await functionThatReturnsAPromise1();
  const value2 = await functionThatReturnsAPromise2(value1);
  const value3 = await functionThatReturnsAPromise3(value2);
  console.log(value3);
}
```
	
	
	
Compared to:

	
```
// avoid doing this:
function myFunction() {
  functionThatReturnsAPromise1()
    .then((value1) => {
      return functionThatReturnsAPromise2(value1);
    })
    .then((value2) => {
      return functionThatReturnsAPromise3(value2);
    })
    .then((value3) => {
      console.log(value3);
    });
}
```
	
	
💡 async functions always return a Promise. If the function returns a value, the Promise will be resolved with that value. Even if you're not using the return keyword the function will return a Promise that resolves to undefined when it reaches the end of it's scope. If the function throws an error, the Promise will be rejected with that error.

### Handling Errors
	
When using Promises, you can use the catch() method to handle errors. Using async functions, you can use the try/catch syntax.

try/catch
	
```
async function myAsyncFunction() {
  try {
    const value = await functionThatReturnsAPromise();
    console.log(value);
  } catch (error) {
    console.error(error);
  }
}
	
```
	
	
The try block will be executed, and if an error is thrown, the catch block will be executed. The catch block has access to the error that was thrown.

If any error is thrown in the try block, the catch block will be executed immediately aborting the execution of any further code in the try block:

	
```
async function functionThatThrowsAnError() {
  throw new Error("ooops 🫣");
}

async function myAsyncFunction() {
  try {
    const value = await functionThatThrowsAnError();
    // The following code will never be executed because
    // `functionThatThrowsAnError()` throws an error.
    // The execution will jump to the `catch` block.
    console.log(value);
    const value2 = await functionThatReturnsAPromise2();
    console.log(value2);
  } catch (error) {
    console.error(error);
  }
}
```
	
	
finally
You can also use a finally block after any try block to run code after the try block is resolved, regardless of whether it was successful or not:

```
async function myAsyncFunction() {
  try {
    const value = await functionThatReturnsAPromise();
    console.log(value);
  } catch (error) {
    console.error(error);
  } finally {
    console.log("done");
  }
}
```
	
	
try/catch is not limited to async Functions
	
The try/catch/(finally) syntax is not limited to async functions, you can use it with any JavaScript code that might throw an error.

	
```
function functionThatThrowsAnError() {
  throw new Error("ooops 🫣");
}

function myFunction() {
  try {
    functionThatThrowsAnError();
    console.log("this will never be executed");
  } catch (error) {
    console.error(error);
  } finally {
    console.log("done");
  }
}
	
```
	
	
Parallel Promises
	
Promise.all()
If you have multiple asynchronous operations that you want to run in parallel, you can use Promise.all().

Promise.all() takes an array of Promises and returns a Promise that resolves to an array of the results of the Promises in the same order.

```
async function myAsyncFunction() {
  try {
    const values = await Promise.all([
      functionThatReturnsAPromise1(),
      functionThatReturnsAPromise2(),
      functionThatReturnsAPromise3(),
    ]);
    console.log(values); // [value1, value2, value3]
  } catch (error) {
    console.error(error);
  }
}
```
	
	
This will run all three asynchronous operations in parallel, and wait for all of them to complete before continuing. If any of the asynchronous operations fail, Promise.all() will fail as well.


Controlling when to Resolve or Reject Parallel Promises
	
There are advanced use cases where you might want to control when to resolve or reject a Promise. Promise.allSettled() (does not care if Promises are rejected or resolved) and Promise.any() (resolves once the first Promise is resolved) are two methods that allow you to do that.

Asynchronous Browser APIs
	
Here are some examples of asynchronous browser APIs that return a Promise:

fetch() — makes an HTTP request and returns a Promise that resolves to a Response object
element.animate().finished — animates an element and returns a Promise that resolves when the animation is complete
navigator.getBattery() — gets the current battery level and returns a Promise that resolves with the battery level

	
<hr>
### 18.-JS Fetch ...

<hr>

### 19.-JS Modern Syntax ...

<hr>





