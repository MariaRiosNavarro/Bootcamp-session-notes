 ###  JS topics that are important in React (without claiming to be complete):
 
 
* all data types, basics of syntax

* Conditions, if-statements, ternary operator

* Loops

* event handling

* Array methods

* async/await

* functions & callback functions

* fetch

* modern syntax

* Testing


### ALL DATA TYPES, basic of syntax

Connect a JavaScript file with <script>
Log to the console
Select elements with querySelector
Add, remove and toggle CSS classes on click with addEventListener
 
 
````
 <script src="./index.js" defer></script>
````

````
const mainElement = document.querySelector('[data-js="main"]');
 
````
 
 - Better as:
 
 
````
// tag as identifier
const mainElement = document.querySelector("main");
// class as identifier -> .
const mainElement = document.querySelector(".main");
// id as identifier -> #
const mainElement = document.querySelector("#main");
````
 
 
 
###   ``` addEventListener ```
 
 
```` 
const button = document.querySelector('[data-js="button"]');
button.addEventListener("click", () => {
  console.log("Yeah");
});
```` 
 
 
###   ``` .classList ```
 
 
Add/remove & toggle classes: .classList.
 
 
````
 const main = document.querySelector('[data-js="main"]');
const button = document.querySelector('[data-js="button"]');

button.addEventListener("click", () => {
  main.classList.add("page--primary");
});
````
 
 
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
     
     
     
### Control Flow: ```if / else```
     
     
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
 
 
### Function Calls
 
When functions are defined you can call them by writing their name, followed by parentheses ("round brackets"). If the functions consume parameters you can pass them as arguments in the brackets.
 
 
greet();
printLetter("Jordan");
printSum(3, 4, 5);
 
 
### Scope
 
The scope defines where variables are visible and where they can be referenced. :
 

***global scope***: A variable is in the global scope when it is declared outside of any function, in a JavaScript file. Global variables are visible and can be accessed from anywhere in that JavaScript file after declaration.
 
***function scope***: Variables defined inside a function are not accessible from outside.
 
 
### ***return***
 
Return Statements:  a function can also return a value back to the place where it was called. This is done via a return statement.Its value is returned by the function and can be stored when the function is called:

 
 ````
function add3Numbers(first, second, third) {
  const sum = first + second + third;
  return sum;
}

const firstSum = add3Numbers(1, 2, 3);
// the return value is stored in "firstSum", namely 6
 
 ````
 
A function can return only one expression value, but can have multiple return statements, in combination with if else statements.

### Early Return Statements
 
As soon as a return statement is reached in a function call, the function execution is ended. The following console.log() is therefore never reached:
 

  ````
 function testFunction() {
 
  return "a returned string";

  console.log("I am never logged in the console.");

}
  ````

 
 This behavior can be used to our advantage as early return statements. Sometimes we want to execute certain parts of our code only if a condition applies. We can check this with an if else statement. When multiple conditions are in place, the code becomes harder to read and to understand. An alternative approach is to terminate the function with early return statements:
 
 
 
 ````
 //Version A -BAD:
 
 function setBackgroundColor(color) {
  if (typeof color === "String") {
    if (color.startsWith("#")) {
      if (color.length >= 7) {
        document.body.style.backgroundColor = color;
      }
    }
  }
}
 
 //Version B-early return- Better
 
 function setBackgroundColor(color) {
	// first condition
	if(typeof color !== 'String') {
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

//Hint: A return statement can be left empty, the returned value is then undefined.                     
                     
```` 
 
                     
 ### ARROW FUNCTIONS
                     
   The function is saved like a variable with the keyword const. The parameters are written normally in round brackets followed by an fat arrow =>. Then the function body is written in curly brackets.
                    
  ````
const addNumbers = (first, second) => {
  return first + second;
};
   ````
                
 
 ### Implicit Return Statements
The advantage of arrow functions are possible shorter notations when certain criteria apply:
 
 
1. - Omit the round brackets around the parameters: This is possible, if there is only one input:
 
 ````
const addOne = number => {
  return number + 1;
};
 ````
 
2. - Implicit return statements: If the function consists only of a return statement, the curly brackets and the return keyword can be omitted:
 
```` 
const addNumbers = (first, second) => {
  return first + second;
};
```` 
 
can be rewritten as:
 
```` 
const addNumbers = (first, second) => first + second;
````
 
 We will use with:
 
 ````
 button.addEventListener('click',() => {
	...
})
 ```` 
 
 <hr>
 <div align="center">(end first JS Week)</div>
 <hr>
 

# JS Inputs and Strings
	
## Strings

There are three ways to create strings using _string literals_:

1. `'string'`: single quotes
2. `"string"`: double quotes
3. `` `string` ``: back ticks or **template literals**.

 Strings can be chained together by using the `+` operator (yes, the same as the maths operator).
This is called **string concatination**:
	
## Template Literals

The third method to write strings has the useful property that you can insert variables into the
string by wrapping placeholders with a dollar sign and curly brackets `${}` . This is also called
**string interpolation**.
	
	
This way you don't have to concat multiple strings if you want to use a variable in your string:

```js
const stringConcatination = "Hello " + name + ", good to see you!";

const withTemplateString = `Hello ${name}, good to see you!`;
```
	
With template literals you can also write **multi-line strings**:
	
	
## String Properties and Methods

Strings in JavaScript have some build-in **properties** and functionalities called **methods**.
	
	

> 💡 Methods are functions, thus they need to be invoked by placing `()` brackets after the name of
> the method.

| Property / Method                   | Effect                                                                   |
| ----------------------------------- | ------------------------------------------------------------------------ |
| `.length`                           | returns the number of characters in a string.                            |
| `.toUpperCase()`                    | returns a all uppercase version of the string.                           |
| `.toLowerCase()`                    | returns a all lowercase version of the string.                           |
| `.trim()`                           | returns a string with all whitespace removed from the beginning and end. |
| `.replaceAll(oldString, newString)` | replaces all occurrences of `oldString` with the `newString`.            |
| `.startsWith(subString)`            | returns `true` if the string starts with subString.                      |
| `.endsWith(subString)`              | returns `true` if the string ends with subString.                        |
| `.includes(subString)`              | returns `true` if the string contains the subString.                     |

> 💡 Go to the
> [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#instance_properties)
> for even more string methods.
	
	
## Input Fields

Every input field in HTML holds a **value** in form of a string. You can access the value by using
`.value` on the input Element:

```html
<form>
  <input data-js="textInput" type="text" value="test 123" />
  <input data-js="numberInput" type="number" value="42" />
</form>
```

```js
const textInput = document.querySelector('[data-js="textInput"]');
const numberInput = document.querySelector('[data-js="numberInput"]');

textInput.value; // evaluates to 'test 123'
numberInput.value; // evaluates to '42' (still a string!)
```

You can also change the value of the input by assigning a new value to this input property:

```js
textInput.value = "changed value!";
```

This change is immediately visible on the website.

For example, you can enforce all uppercase letters in a form by combining this functionality with an
`input` event listener on the input element:

```js
// transform on every change the input value to uppercase letters
textInput.addEventListener("input", () => {
  const oldValue = textInput.value;
  const newValue = oldValue.toUpperCase();
  textInput.value = newValue;
});
```
	
[MDN Docs: String Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#instance_properties)


# JS Forms
	
### Understanding the Default Behavior of Form Submit
	
if we want to do something with the submitted data in our frontend code. You
can prevent this behavior with a method called `.preventDefault()`.
	
```js
const form = document.querySelector('[data-js="form"]');

form.addEventListener("submit", (event) => {
  event.preventDefault();
});
```

By calling `event.preventDefault()` the browser will not perform a GET request that would cause the
page to reload on submit.
	
---
		

### The `event` Object and `event.target`

The `event` object is created whenever an event is triggered. You can accept it as the first
parameter in the callback function and thus access it inside the function body (e.g. via
`event.preventDefault()`).

For now, the most important method of the `event` object is `.preventDefault()`.

`event.target` is a reference to the element to which the event originated from - in this case - the
form.

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();

  console.log(event.target);
});
// Output:
// <form data-js="form">
//		<fieldset>...</fieldset>
//		...
//		<button type="submit">Submit</button>
//	</form>
```

### Accessing Interactive Fields: `event.target.elements` and the `name` Attribute

While `event.target` represents the entire form, `event.target.elements` is a collection of all form
elements (form fields, field sets and buttons).

You get access to a specific form field via its `name` attribute and dot notation:

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();

  const formElements = event.target.elements;

  console.log(formElements.firstName);
  console.log(formElements.firstName.value);
});
```

Note that

- `event.target.elements` is stored in the variable `formElements` for better readability,
- `firstName` is the string value of the corresponding `name` attribute, as in
  `<input name="firstName"/>`, and
- `firstName.value` returns the user input for the field with `name="firstName"`.

---
	
### Using Input Values

You can access all input values of the form by using `FormData()`. This constructor uses
`event.target` and can be transformed into a usable object afterwards:

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();

  const formData = new FormData(event.target);
  const data = Object.fromEntries(formData);

  console.log(data);
});
```

This is very useful to easily access the input data of an entire form.

> 💡 Despite the fact that using `FormData` is much less verbose, `event.target.elements` is very
> useful if you want to access single form field. (Spoiler alert: In case you want to focus a
> specific field after resetting the form, for example.)
	
	
### Exception: Reading Values from Checkboxes

Checkboxes have two states: checked ("true") and not checked ("false"). In contrast to other input
types, the `value` attribute does not reflect this change, but is only used as an identifier for the
checkbox.

You can access the checkbox's state via the `.checked` property instead.

Imagine the following checkbox

```html
<input type="checkbox" name="colorBlue" value="blue" />
```

and its corresponding JavaScript:

```js
console.log(formElements.colorBlue.checked); // output: true or false
console.log(formElements.colorBlue.value); // output (always): blue
```

---

## Resources

- [Event interface](https://developer.mozilla.org/en-US/docs/Web/API/Event#properties)
	
	
---
	
# JS Forms 2
	
### HTML Form Validation

Before submitting a form, it is important to ensure all required form fields are filled out, in the
correct format. This is called **client-side form validation**.

HTML provides several form field attributes to enable validation features build into the browser.

| Attribute                 | Description                                                                                                                                        |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `required`                | if present, a form field needs to be filled in before the form can be submitted                                                                    |
| `minlength` / `maxlength` | minimum and maximum length of textual data (strings)                                                                                               |
| `min` / `max`             | minimum and maximum values of numerical input types                                                                                                |
| `type`                    | each input type has its own prefigured validation (like `email`)                                                                                   |
| `pattern`                 | [a regular expression pattern](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) the entered data needs to follow |
	
	
> ❗️ If the `required` attribute is omitted, the field is valid if it is empty or has a content
> between 3 and 30 characters, but invalid if 1 or 2 characters are entered.

`type="email"` will check if the input is a valid email address.
	
	
---

### The `input` Event

Occasionally, you may want to do something if the value of a single field changes even before the
form is submitted.

The `input` event is fired every time when the value of a form field has been changed. For example,
a `<textarea />` will fire this event with every keystroke.

```js
const messageField = document.querySelector('[data-js="message"]');

messageField.addEventListener("input", (event) => {
  console.log(event.target.value);
});
```

> ❗️ Don't confuse the `input` event with the `change` event, which is only fired after a field's
> content has been committed by the user by pressing enter or moving the focus to the next field.

---
	
### Focus Input Fields

You can focus an input field with the `.focus()` method. This can be used to improve the user
experience after submitting a form.

```js
const messageField = document.querySelector('[data-js="message"]');

form.addEventListener("submit", (event) => {
  event.preventDefault();
  // [...] handle form data
  messageField.focus();
});
```

Instead of querying the input element using `querySelector`, it can also be obtained via the
`event.target.elements` collection:

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();
  // [...] handle form data
  event.target.elements.message.focus();
});
```

This will focus a form field with the attribute `name="message"`.

---	
	
### Resetting Forms

You can reset all form fields to their default value with the `.reset()` method.

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();
  // [...] handle form data
  event.target.reset();
});
```

This often comes in handy in combination with `.focus()`. Think of a chat: After the message was
send, the input field is cleared and re-focussed, so users can write the next message.

---

## Resources

- [MDN web docs: Client-side form validation](https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation)
- [MDN web docs: input event](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/input_event)
	
		
	
# JS createElement
	
	
## The DOM

The **Document Object Model** is a representation of the HTML document. Each HTML Tag is modelled as
a **node** in a tree structure, which shows how HTML elements are nested.
	
	
## `document.createElement`
	

```js
const article = document.createElement("article");
const button = document.createElement("button");
```
	
After generating an element, you need to place the element into the DOM. For this, you can use the
`.append` method. It places the element as the **last child** into the respective element.

```js
document.body.append(article); // placing the created article at the end of the body
article.append(button); // placing the created button into the article
```
	
## Element Properties and Methods

As well as with queried HTML elements (via `querySelector`), we can add classes, event listeners and
more to the created HTML elements.

```js
article.classList.add("card");

button.addEventListener("click", () => {
  console.log("It works!");
});
```

The text of an element can be changed by reassigning the `.textContent` property:

```js
button.textContent = "Click me!";
```

### Common Element Properties and Methods

| Property          | Effect                                                             |
| ----------------- | ------------------------------------------------------------------ |
| `classList`       | add, toggle or remove classes from element                         |
| `textContent`     | get or set text inside element                                     |
| `style`           | define inline style, e.g. `element.style.backgroundColor = "red" ` |
| `hidden`          | boolean whether element is hidden or not                           |
| `focus()`         | focusses the element on the website                                |
| `hasAttribute()`  | returns true if the element has the given attribute                |
| `querySelector()` | returns the first child that matches the given CSS selector        |

> 💡 You can assign HTML attributes by using the element properties. Go to the
> [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/API/Element#properties) for a
> comprehensive list of element properties.
	
	
### Resetting Element Content

`.innerHTML` can also be used to **reset** the content of an element, e.g. a container
By setting the innerHTML to an empty string, the content is deleted:
	

```js
const cardContainer = document.querySelector('[data-js="cardContainer"]');
cardContainer.innerHTML = "";
```
The `innerHTML` property can be used to create the entire html layout of an element by passing the
html code as a string. By using **template literals** the content of the html can be dynamically
created.

```js
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

	
# JS Loops
	
- `while` loop: are used when a task needs to be executed until a specific criteria is met.
- `for` loop: are commonly used when a given task needs to be executed x times or for each element
  in an object / array.
	
## `while`

The while loop is the most fundamental type of loop. It repeats a code block as long as the stated
criteria is `true`.

```js
let string = "a";

while (string.length <= 8) {
  console.log(string);
  string = string + string;
}

// 'a'
// 'aa'
// 'aaaa'
// 'aaaaaaaa'
```

In this example, the while loop repeats itself 4 times, until the string becomes too long and the
loop criteria changes to `false`.

---

## `for`

`for` loops are intended for repeating a task a certain number of times. They consist of three
internal parts:

- an internal counter which is increased / decreased every iteration.
- a criteria which checks the value of the counter. As long as the criteria is `true`, the loop is
  executed.
- a rule how the counter is increased / decreased (in most cases it is increased by 1)

```js
for (let counter = 0; counter < 4; counter++) {
  console.log(counter);
}
// 0
// 1
// 2
// 3
```

The body of the for loop contains the code which is executed on each iteration. For the example
above it is a `console.log` which logs the value of the counter on each iteration until the value of
`counter` reached 4 and the loop is terminated.

---

## `for...in`

The `for...in` is a shorthand notation to loop through all keys of an OBJECT:

```js
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
```

The loop has an iterator variable, in this case `key` which is assigned the respective key value in
each iteration (first 'name', then 'age' and finally 'email').

---

## `for...of`

Similar to `for...in` the `for...of` loop is a shorthand notation, but for looping through all items
of an ARRAY.

```js
const fruits = ["apple", "banana", "melon"];

for (const fruit of fruits) {
  console.log(fruit);
}

// 'apple'
// 'banana'
// 'melon'
```

This time the iterator variable `fruit` is assigned the respective array item in each iteration.

---

## Resources

- [MDN article about loops and iterations](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration)


