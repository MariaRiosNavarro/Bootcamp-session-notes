
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

- [JS Array Methods:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/js-array-methods/js-array-methods.md)[Challenges]().

- [npm and Linting Basics:](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/npm-and-linting-basics/npm-and-linting-basics.md)[Challenges]().

- [JS Structure :]()[Challenges]().

- [JS Arrays Methods 2:]()[Challenges]().

- [JS Async Functions:]()[Challenges]().

- [JS Fetch]()[Challenges]().

- [JS Modern Syntax]()[Challenges]().



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

<hr>

### 12.-JS Callback Functions ...

<hr>

### 13.-JS Array Methods ...

<hr>

### 14.-JS npm and Linting Basics ...

<hr>

### 15.-JS Structure ...

<hr>


### 16.-JS Arrays Methods 2: ...

<hr>

### 17.-JS Async Functions ...

<hr>
### 18.-JS Fetch ...

<hr>

### 19.-JS Modern Syntax ...

<hr>





