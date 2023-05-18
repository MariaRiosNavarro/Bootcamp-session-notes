
### 1 .- CALLBACK FUNCTIONS

### 2 .- OBJECTS, ARRAYS and ARRAYs METHODS

### 3 .- ASYNC FUNCTIONS

### 4 .- API and FETCH

### 5 .- JS STRUCTURE

### 6 .- MODERN SYNTAX

### 7 .- UNIT TESTING

### 8 .- NPM and LINTING BASICS


---

### 1 .- CALLBACK FUNCTIONS


## Callback Functions

A callback function is a function that is passed **as an argument** into another function.

The outer function can execute this callback function at the correct moment or multiple times, for
example:

- when an event is triggered
- when the fetched data arrived on your computer
- for each element in an array.

Callback functions are used, whenever the program itself needs to figure out **when** or **how many
times** the function needs to be executed. We already used callback functions in **event
listeners**:

```js
button.addEventListener("click", () => {
  console.log("Inside the callback function.");
});
```

Here the structure is as follows:

- outer function: `addEventListener()`
- first argument: `'click'`
- second argument: callback function
  ```js
  () => {
    console.log("Inside the callback function.");
  };
  ```

This type of function is called **anonymous function**, since it is declared without giving it a
name.

## Named Callback Functions

Any function can be used as a callback function. It just needs to be passed to another function. You
can declare a normal function and then use the **name of the function** to pass it into another
function:

```js
function sayHello() {
  console.log("Hey Dude!");
}

button.addEventListener("click", sayHello);
```

> ❗️ Note that we do not call the function here (we wrote `sayHello` instead of `sayHello()`). We
> ***only pass the function to the event listener***. The function is ***only called when the event happens***.

## Higher Order Functions

A higher order function is a function that takes a **callback function as an argument** and **calls
the callback function** inside their body, e.g. the `addEventListener` method.

```js
// this function calls its callback function 3 times!
function myHigherOrderFunction(callback) {
  callback();
  callback();
  callback();
}
```

We will encounter these higher order functions in future sessions:

- `.then`
- `.forEach`
- `.map`
- `.filter`


## Parameters in Callback Functions

A callback function can accept parameters. The values for the parameters are provided by the
function, that calls the callback function (the "higher order function").

In this example the callback function can accept a parameter to retrieve information about the
occurred event:

```js
button.addEventListener("click", (event) => {
  console.log("This button was clicked:", event.target);
});
```

---

## Resources

- [MDN Callback Functions](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function)





### 2 .- OBJECTS, ARRAYS and ARRAYs METHODS

# JS Objects and Arrays


## Arrays

Arrays are a structured data type which can store multiple values in one variable.

You can declare an array using `[]` square brackets (array literals):

```js
const shoppingList = ["apple", "tomato"];
```

Each item in the array has an index, which starts at 0. You can access individual items using the
bracket notation and the item's index:

```js
shoppingList[0]; // "apple"
shoppingList[1]; // "tomato"
```

Arrays can hold any type of value, even another array. This is called a nested array. The values of
nested arrays can be accessed by choosing the index of the nested array first and then stating the
index of the element inside the nested array.

```js
const nestedArray = ["a", 1, ["a", "new", "sentence"], false];
nestedArray[2][1]; // "new"
```

You can overwrite individual values in an array:

```js
const shoppingList = ["apple", "tomato"];
shoppingList[0] = "banana";
shoppingList; // ["banana","tomato"];
```

### Common Array Attributes and Methods

| Attribute / Method       | Effect                                           |
| ------------------------ | ------------------------------------------------ |
| `array.length`           | returns the number of elements in the array      |
| `array.push(element)`    | adds `element` to the end of the array           |
| `array.pop()`            | removes the last element of an array             |
| `array.unshift(element)` | adds `element` as the first element of the array |
| `array.shift()`          | removes the first element of the array           |

> 💡 There are much more array methods and attributes which we will discover in later sessions. Go
> to the
> [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#instance_methods)
> for more information.

---

## Objects

Objects are a structured data type, which couple their values not to an index, but to a unique key.

You can declare an object using `{}` curly brackets (object literals):

```js
const person = {
  name: "Max Paddington",
  age: 21,
  isStudent: false,
};
```

You can access the properties using the dot notation:

```js
person.name; //"Max Paddington"
```

You can also access the properties using the bracket notation:

```js
person["age"]; // 21
```

Objects can be nested:

```js
const person = {
  name: "Max Paddington",
  age: 21,
  isStudent: false,
  address: {
    street: "Berliner Str.",
    houseNumber: 42,
    city: "Leipzig",
    zipCode: "12345",
  },
};
```

Nested values can be accessed by chaining the dot notation and/or the bracket notation together.

```js
person.address.street; // "Berliner Str."
person.address["city"]; // "Leipzig"
```

You can change values of object properties by reassigning them using the dot or bracket notation:

```js
person.name = "Max Paddington";
person["age"] = 33;
```

You can add new properties in the same way:

```js
person.score = 15;
```

You can delete properties using the delete keyword:

```js
delete person.score;
```

## Nested Objects / Arrays

Arrays can contain objects and vice versa:

```js
const peopleArray = [
  {
    name: "John",
    age: 22,
  },
  {
    name: "Alex",
    age: 33,
  },
];
```

```js
const user = {
  userId: "1234",
  mail: "test@mail.com",
  shoppingCart: ["tomato", "banana", "chocolate"],
};
```

You can access elements via chained dot / bracket notation:

```js
peopleArray[1].name; // "Alex"
user.shoppingCart[0]; // "tomato"
```

---

## Resources

### Array

[MDN Docs: Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

### Object

[MDN Docs: Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)



# JS Array Methods


## Introduction to array methods

All array methods presented here have a lot in common and can be used in the same way.

- You provide a callback function with one parameter
- The array method iterates over an array
- The provided callback function gets called for each element in the array
- With each call to the function the current array element gets passed as first argument

This way you can write code and apply it to each element within an array

---

## `forEach`

The array method `forEach` executes some logic for each element within an array.

```js
const pets = ["bird", "cat", "dog", "ferret", "fish"];
pets.forEach((pet) => {
  const petElement = document.createElement("p");
  petElement.textContent = pet;
  document.body.append(petElement);
});
```

> ❗️ The callback function provided to `forEach` **must not** use a `return` statement. `forEach` >
> **does not return** a new array.

> ❗️ You **should** use `forEach` to use a side-effect, like `document.createElement`

![array-methods-forEach](./assets/array-methods-forEach.png)

---

## `map`

The array method `map` is used to apply a transformation to each element of an array.

The transformed elements are stored in the **newly created array** returned by `map`. The elements
in the original array are not being altered.

You can define the kind of transformation applied to each element in the callback function and
**return** the transformed element.

The created and the original array have the same length.

```js
const pets = ["bird", "cat", "dog", "ferret", "fish"];
const uppercasePets = pets.map((pet) => {
  return pet.toUpperCase();
});
console.log(uppercasePets); // ['BIRD', 'CAT', 'DOG', 'FERRET', 'FISH']
```

![array-methods-map](./assets/array-methods-map.png)

> ❗️ The callback function provided to `map` **must** use a `return` statement to return a
> transformed element. `map` **returns** a new array.

> ❗️ You **should not** use `map` to trigger a side-effect, like `document.createElement`

---

## `filter`

The array method `filter` is used to **create a new array** with a subset of the elements of the
original array.

The callback function **returns** a **boolean value** to define, if an element is being included in
the resulting array or not. The original array is not being altered.

The created array is likely to have a shorter length than the original array.

```js
const pets = ["bird", "cat", "dog", "ferret", "fish"];
const petsWithF = pets.filter((pet) => {
  return pet.startsWith("f");
});
console.log(petsWithF); // ['ferret', 'fish']
```

> ❗️ The callback function provided to `filter` **must** use a `return` statement to return a
> boolean value.

![array-methods-filter](./assets/array-methods-filter.png)

---

## Chaining array methods

Often times you need to combine multiple array methods to achieve a desired result. Array methods
like `map` and `filter`, that return a new array, can be **chained**. Instead of storing each array
in a separated variable, the methods can be called directly after another. This reduces the amount
of code and improves readable.

```js
const pets = ["bird", "cat", "dog", "ferret", "fish"];
const uppercasePetsWithF = pets
  .filter((pet) => {
    return pet.startsWith("f");
  })
  .map((pet) => {
    return pet.toUpperCase();
  });
console.log(uppercasePetsWithF); // ['FERRET', 'FISH']
```

---

## `document.querySelectorAll`

With `document.querySelectorAll` you can select a list of elements from the DOM. This is in contrast
to `document.querySelector`, which provides only the first occurrence of an element matching the
selector.

```js
const pets = document.querySelectorAll('[data-js="pet"]');
console.log(pets.length); // 5
```

The `NodeList` returned by `document.querySelectorAll` is an array-like object. You can use the
`forEach` method to iterate over the DOM elements.

```js
const pets = document.querySelectorAll('[data-js="pet"]');
pets.forEach((pet) => {
  pet.addEventListener("click", () => {
    // [...]
  });
});
```

> ❗️ A `NodeList` is not an array! Other array methods like `map` or `filter` can't be used. If you
> need to use array methods, you can convert the `NodeList` to an array using `Array.from()`

---

## Resources

- [MDN web docs: Array forEach](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)
- [MDN web docs: Array map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- [MDN web docs: Array filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
- [MDN web docs: NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList)



# JS Array Methods 2

## Learning Objectives

- [ ] Understanding advanced array methods
  - [ ] `includes`
  - [ ] `find` and `findIndex`
  - [ ] `sort` and `reverse`
    - [ ] know how to use `slice()` to make a copy
  - [ ] `some` and `every`
  - [ ] `reduce`

---

## `includes`

Use `array.includes()` to check whether the array contains the specified value. If it does, `true`
is returned, otherwise `false`.

```js
const colors = ["hotpink", "aquamarine", "granite"];

colors.includes("aquamarine"); // true
colors.includes("nemo"); // false
```

---

## `find` and `findIndex`

Use `find()` to receive **the first element** of the array that satisfies the provided testing
function. Otherwise, it returns `undefined`.

```js
const colors = ["hotpink", "aquamarine", "granite", "grey"];

colors.find((color) => color.startsWith("g")); // 'granite'
colors.find((color) => color.startsWith("b")); // undefined
```

Use `findIndex()` to receive the index **of the first element** of the array that satisfies the
provided testing function. If there is no such element, `-1` is returned.

```js
const colors = ["hotpink", "aquamarine", "granite", "grey"];

colors.findIndex((color) => color.startsWith("g")); // 2
colors.findIndex((color) => color.startsWith("b")); // -1
```

---

## `sort` and `reverse`

Use `sort()` to sort the elements of an array. You need to provide a callback function in order to
tell how the array is sorted.

### Sorting Numbers

```js
const numbers = [4, 42, 23, 1];

numbers.sort((a, b) => a - b); // [1, 4, 23, 42]
numbers.sort((a, b) => b - a); // [42, 23, 4, 1]
```

The sorted order is based on the return value of `a - b` / `b - a` :

| Return value of `a - b` | sort order                         |
| ----------------------- | ---------------------------------- |
| > 0                     | sort `a` after `b`                 |
| < 0                     | sort `a` before `b`                |
| === 0                   | keep original order of `a` and `b` |

> 💡 `sort()` converts the elements into strings, then compares their sequences of UTF-16 Code units
> values. This is why `array.sort()` without a callback is mostly useless.

### Sorting Strings

In order to sort strings, you need to tell the `sort()` method two things inside of the callback
function:

- lowercase both strings before comparing them (uppercase works as well)
- using if-statements, be explicit about the return values dependent on the result of the comparison
  (`nameA < nameB` and `nameA > nameB`)

```js
const strings = ["Xbox", "PlayStation", "GameBoy"];

strings.sort((a, b) => {
  const nameA = a.toLowerCase();
  const nameB = b.toLowerCase();
  if (nameA < nameB) {
    return -1;
  }
  if (nameA > nameB) {
    return 1;
  }
  return 0;
});

console.log(strings); // ['GameBoy', 'PlayStation', 'Xbox']
```

> 💡 In UTF-16, the upper- and lowercase version of the same letter do not have the same value. An
> uppercase 'H' has the UTF-16 decimal value of 72, while the lowercase 'h' has a value of 104.
>
> For example, an uppercase 'W' (87) and a lowercase 'd' (100) are sorted behind the uppercase 'H'
> (72), but before the lowercase 'h' (104); the result would look like ['H', 'W', 'd', 'h']. This is
> why it's necessary to upper- or lowercase all letters before sorting them.

### `reverse`

In order to reverse an array, simply use `array.reverse()`. This can be combined with `sort()` as
well:

```js
const numbers = [4, 42, 23, 1];

const reversedNumbers = numbers.reverse(); // [1, 23, 42, 4]
```

### `slice`

It's important to note that some array methods, as `sort()`, do not create a new array, but mutate
the original one.

```js
const numbers = [4, 42, 23, 1];

console.log(numbers); // [4, 42, 23, 1]

const sortedNumbers = numbers.sort((a, b) => a - b);

console.log(sortedNumbers); // [1, 4, 23, 42]
console.log(numbers); // [1, 4, 23, 42]

// What happens if sortedNumbers is reversed?

const reversedSortedNumbers = sortedNumbers.reverse();

console.log(reversedSortedNumbers); // [42, 23, 4, 1]
console.log(sortedNumbers); // [42, 23, 4, 1]
console.log(numbers); // [42, 23, 4, 1]
```

This behaviour will often cause errors. To prevent it, just make a copy of the original array using
`slice()`.

```js
const numbers = [4, 42, 23, 1];

console.log(numbers); // [4, 42, 23, 1]

const sortedNumbers = numbers.slice().sort((a, b) => a - b);

console.log(sortedNumbers); // [1, 4, 23, 42]
console.log(numbers); // [4, 42, 23, 1]
```

---

## `some` and `every`

Use `some()` to test whether **at least one element** in the array passes the provided test.

```js
const colors = ["hotpink", "aquamarine", "granite"];

colors.some((color) => color.startsWith("g")); // true
colors.some((color) => color.startsWith("i")); // false
```

In order to check if **all elements** pass the test, use `every()`.

```js
const colors = ["hotpink", "aquamarine", "granite"];

colors.every((color) => color.length > 5); // true
colors.every((color) => color.length < 3); // false
```

---

## `reduce`

`Array.reduce()` is an array method to reduce a list of values into a single value.

It has the following core features:

- starting from the beginning, it executes the callback function on each element of the array,
- the return value of each calculation is passed to the next calculation (i.e. it becomes the new
  starting value for the next iteration through the array)
- the final result is a single value.

It's main use case is to calculate the sum of an array of numbers.

```js
const numbers = [4, 42, 23, 1];

numbers.reduce((a, b) => a + b);

console.log(numbers); // 70
```

> ❗️ If you find yourself doing anything more complex than this with reduce (like reducing an array
> to an object, etc.) you should try to find another solution to your problem. Complex reduce
> functions are very hard to read and thus error prone.
>
> Example of reducing an array to an object without `reduce()`:
>
> ```js
> const myArray = [
>   { foo: 1, bar: "hi" },
>   { foo: 4, bar: "hey" },
>   { foo: 2, bar: "ho" },
> ];
> const myObject = {};
> myArray.forEach((element) => {
>   myObject[element.bar] = element.foo;
> });
>
> console.log(myObject); // {hi: 1, hey: 4, ho: 2}
> ```

---

## Resources

- [Searching Arrays (javascript.info)](https://javascript.info/array-methods#searching-in-array)
- [sort (javascript.info)](https://javascript.info/array-methods#sort-fn)
- [reduce (javascript.info)](https://javascript.info/array-methods#reduce-reduceright)



### 3 .- ASYNC FUNCTIONS

# JS Async Functions

## Learning Objectives

- Understanding how asynchronous code works
- Working with promises
- Using the `async` and `await` keywords

---

## Asynchronous Code

Asynchronous code is code that runs in the background. This is useful for tasks that can take a long
time to complete, but don't need to block the main thread.

JavaScript is a single-threaded language, meaning that only one thing can happen at a time.

Blocking the main thread is bad because it prevents the user from interacting with the page because
no other JavaScript code can be executed. Examples of asynchronous code include: network requests,
file system access, animations and timers.

## Promises

A Promise is an object that represents the eventual completion (or failure) of an asynchronous
operation, and its resulting value. Most of the time it is returned by a function that performs an
asynchronous operation.

The Promise object has the following properties and methods:

| Property / Method | Description                                                                                                                                             |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `state`           | the state of the Promise object, can be `"pending"`, `"resolved"` or `"rejected"`                                                                       |
| `result`          | the result of the asynchronous operation (you'll almost never need to access this directly)                                                             |
| `then()`          | a method that takes a callback function that will be called when the asynchronous operation is complete                                                 |
| `catch()`         | a method that takes a callback function that will be called when the asynchronous operation fails                                                       |
| `finally()`       | a method that takes a callback function that will be called when the asynchronous operation is complete, regardless of whether it was successful or not |

```js
functionThatReturnsAPromise().then((value) => {
  console.log(value);
});
```

> 💡 Promises are almost always created for you by other asynchronous APIs, only rarely do you
> create them yourself. If you create a Promise yourself (`new Promise()`), you either know exactly
> what you are doing, or you are probably doing something wrong.

---

## Asnyc Functions and the `await` Keyword

Asnyc functions are a syntactic sugar for Promises. Using the `await` keyword, you can write
asynchronous code that looks synchronous. Any function can be prefixed with the `async` keyword:

```js
async function myAsyncFunction() {
  // ...
}

const myAsyncArrowFunction = async () => {
  // ...
};
```

Inside an async function, you can use the `await` keyword to wait for a Promise to be resolved:

```js
async function myAsyncFunction() {
  const value = await functionThatReturnsAPromise();
  console.log(value);
}
```

This is can be easier to read than the Promise syntax especially when you have multiple asynchronous
operations that depend on each other.

```js
async function myAsyncFunction() {
  const value1 = await functionThatReturnsAPromise1();
  const value2 = await functionThatReturnsAPromise2(value1);
  const value3 = await functionThatReturnsAPromise3(value2);
  console.log(value3);
}
```

Compared to:

```js
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

> 💡 `async` functions always return a Promise. If the function returns a value, the Promise will be
> resolved with that value. Even if you're not using the `return` keyword the function will return a
> Promise that resolves to `undefined` when it reaches the end of it's scope. If the function throws
> an error, the Promise will be rejected with that error.

---

## Handling Errors

When using Promises, you can use the `catch()` method to handle errors. Using `async` functions, you
can use the `try`/`catch` syntax.

### `try`/`catch`

```js
async function myAsyncFunction() {
  try {
    const value = await functionThatReturnsAPromise();
    console.log(value);
  } catch (error) {
    console.error(error);
  }
}
```

The `try` block will be executed, and if an error is thrown, the `catch` block will be executed. The
`catch` block has access to the error that was thrown.

If any error is thrown in the `try` block, the `catch` block will be executed immediately aborting
the execution of any further code in the `try` block:

```js
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

### `finally`

You can also use a `finally` block after any `try` block to run code after the `try` block is
resolved, regardless of whether it was successful or not:

```js
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

### `try`/`catch` is not limited to `async` Functions

The `try`/`catch`/(`finally`) syntax is not limited to `async` functions, you can use it with any
JavaScript code that might throw an error.

```js
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

## Parallel Promises

### `Promise.all()`

If you have multiple asynchronous operations that you want to run in parallel, you can use
`Promise.all()`.

`Promise.all()` takes an array of Promises and returns a Promise that resolves to an array of the
results of the Promises in the same order.

```js
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

This will run all three asynchronous operations in parallel, and wait for all of them to complete
before continuing. If any of the asynchronous operations fail, `Promise.all()` will fail as well.

### Controlling when to Resolve or Reject Parallel Promises

There are advanced use cases where you might want to control when to resolve or reject a Promise.
`Promise.allSettled()` (does not care if Promises are rejected or resolved) and `Promise.any()`
(resolves once the first Promise is resolved) are two methods that allow you to do that.

## Asynchronous Browser APIs

Here are some examples of asynchronous browser APIs that return a Promise:

- `fetch()` — makes an HTTP request and returns a Promise that resolves to a `Response` object
- `element.animate().finished` — animates an element and returns a Promise that resolves when the
  animation is complete
- `navigator.getBattery()` — gets the current battery level and returns a Promise that resolves with
  the battery level

---

## Resources

- [Thread on mdn](https://developer.mozilla.org/en-US/docs/Glossary/Thread)
- [Asynchronous on mdn](https://developer.mozilla.org/en-US/docs/Glossary/Asynchronous)
- [Using Promises on mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
- [Async functions on mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [Promise.all() on mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all)
- [try...catch on mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch)



---

### 4 .- API and FETCH

# JS Fetch


## What is an API?

The term _API_ is short for _Application Programming Interface_.

An _API_ provides a way one software (the _application_) can interact with another software.
Therefore, an application can define a set of features and rules on how other software can interact
with it. This is called an _interface_. Think of a contract between two softwares that explains how
they can work together.

APIs can be seen from different perspectives and occur on various levels.

A browser provides a lot of [Web APIs](https://developer.mozilla.org/en-US/docs/Web/API). Each Web
API defines a way on how a JavaScript application can use a feature given by the browser, like:

- [Web Animations API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Animations_API)
- [Battery API](https://developer.mozilla.org/en-US/docs/Web/API/Battery_Status_API)
- [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

APIs running on a server environment are a different type of API. They are provided by a _server_,
opposing to the APIs provided by the browser (which is also called the _client_). A common use-case
for such APIs is to read / load data. Other operations like writing or deleting data is also
possible. There are common approaches regarding the architecture of a serve-side API. One such
approach are REST-APIs, which is explained later in this document.

---

## Fetch API (with async & await)

`fetch` is a [web API](https://developer.mozilla.org/en-US/docs/Web/API) to asynchronously fetch
(load) resources from the network, like text documents.

```js
async function fetchData() {
  const response = await fetch("/url/to/something");
  const data = await response.json();
  return data;
}
```

This is what happens in the example above:

1. We mark the function with the `async` keyword, because we want to use `await` inside the
   function.
2. We declare a variable named `response`. It stores the Response object that is returned by
   `fetch`.
3. Once this promise resolves (the network request is finished), we call the `.json` method on the
   `response` variable. This function returns another Promise.
4. This second promise resolves with the actual data (payload) converted from JSON (a formatted
   string) to a JavaScript value or object. This result is stored in the variable named `data`.
5. The function returns the value stored in the `data` variable.

> 💡 The `async` and `await` syntax helps with handling the two consecutive promises required to get
> the response data (opposing to the nested syntax using `.then()`)

> 💡The `Response` object features other useful methods (all returning promises), among which are
> the following:
>
> - `response.json()` returns a Promise that resolves to the downloaded data JSON-parsed as a
>   JavaScript value or object
> - `response.text()` returns a Promise that resolves to the downloaded data as raw text
> - `response.formData()` returns a Promise that resolves to the downloaded data parsed as FormData
> - `response.blob()` returns a Promise that resolves to the downloaded data as a raw blob (that's a
>   machine readable format using zeros and ones)

---

## JSON

JavaScript Object Notation (JSON) is a standard text-based format for representing structured data
based on JavaScript object syntax. It is commonly used for transmitting data between a client
(browser) and a server in web applications.

JSON is very close to being a subset of JavaScript syntax. Most valid JSON is also valid JavaScript
code. This means that you can copy JSON into any `.js` file, put a `const myData =` in front, and
watch Prettier make it look like _real_ JavaScript. On the flip side valid JavaScript is not valid
JSON. It looks like this:

```json
{
  "groupName": "Students",
  "groupSize": 100,
  "students": [
    {
      "name": "John Doe",
      "age": 42,
      "location": "Pleasantville",
      "member": true,
      "groups": ["students", "citizens", "new"]
    },
    {
      "name": "Jane Doe",
      "age": 44,
      "location": "Pleasantville",
      "member": true,
      "groups": ["students", "citizens", "new"]
    },
    {
      "name": "Sam Doe",
      "age": 24,
      "location": "Pleasantville",
      "member": true,
      "groups": ["students", "citizens", "new"]
    }
  ]
}
```

Even though it closely resembles JavaScript object literal syntax, it can be used outside of
JavaScript. Other programming languages often feature the ability to read (parse) JSON.

JSON exists as a string that needs to be converted to a native JavaScript object when you want to
access the data. No problem! - JavaScript provides a global JSON object that features conversion
methods in either direction.

> 💡 JSON Conversion Methods
>
> `JSON.parse()`
>
> This method parses a JSON string and constructs the JavaScript value or object described by the
> string.
>
> `JSON.stringify()`
>
> This methods converts a JavaScript value or object to a JSON string.

---

## HTTP Response Status Codes

HTTP response status codes usually indicate whether a specific HTTP request has been successfully
completed. For the most part, _any_ sort of response is considered a successful completion of the
request.

With the exception of custom server software, these responses are standardized. You can find a list
of HTTP response status codes [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status).

One of the most well-known HTTP response status codes is
[`404 not found`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/404), which most users of
the web might have already encountered at some point.

> 💡 Do you need a cute explanation of what the HTTP response codes mean? Just search for 'HTTP
> status dogs' (or cats if you like them better).

---

## Error Handling

It might be surprising that `fetch()` doesn't throw an error when the server returns a bad HTTP
status, e.g. client or server errors.

```js
async function fetchSomething() {
  const response = await fetch("/bad/url/oops");
  const something = await response.json();
  return something;
}
```

Assuming that in the above example `'bad/url/oops` doesn't lead to an existing location, the server
would respond with the status code `404` and the text `Page not found`. This is a **completed** HTTP
request.

A request will only register as rejected if a response cannot be retrieved. This may be due to
network problems, such as no internet connection, the host not being found, or the server not
responding.

We can separate _good_ from _bad_ HTTP response statuses by relying on the boolean `response.ok`
property. It is set to `true` only if the HTTP response code is between `200-299`.

In our example above, `response.ok` would be set to `false` and the response code would be `404`.

If something goes wrong that causes that we do not receive a response the fetch API throws an error.
Once an error is thrown execution stops and JavaScript looks for the closest `catch` block.

Any production `fetch` call should be inside a `try...catch` block:

```js
async function fetchSomething() {
  try {
    const response = await fetch("/bad/url/oops");

    if (response.ok) {
      // Success (Good Response)
      const data = await response.json();
      return data;
    } else {
      // Failure (Bad Response)
      console.error("Bad Response");
    }
  } catch (error) {
    // Failure (Network error, etc)
    console.error("An Error occurred");
  }
}
```

---

## REST API

When you create an API, you need to come up with ideas on how to structure your API, shape the
features you provide and which rules to apply. This is referred to as the architecture of your API.

There are different common approaches used across the web. A very popular one is REST API or RESTful
API.

REST is a set of architectural constraints, not a protocol or a standard. You as an API developer
can implement REST in a variety of ways.

> 💡 REST is short for REpresentational State Transfer

The overall idea is like this:

- A _client_ requests a _resource_ from a _server_ (like a document containing information on a
  specific topic)
- The _server_ formulates a response that represents the resource in a format the _client_
  understands (like JSON - other formats like HTML, XML oder plain text are also possible)
- This transfer of data changes the state of the web application.

Each resource has a unique address. The whole communication is done via HTTP and uses different HTTP
methods (like GET/POST/PUT/DELETE) to describe desired actions.

> 💡 This is a very basic and incomplete explanation. If you're interested in learning more about
> what makes an API RESTful, you can read about it [here](https://restfulapi.net/).

---

### 5 .- JS STRUCTURE

# JS Structure

## Learning Objectives

- [ ] Understanding JavaScript modules
- [ ] Using import and export statements
- [ ] Understanding how to structure a JavaScript project

---

## JavaScript Modules

JavaScript modules (sometimes also called "ECMAScript Modules" or "ESM") are a way to organize code
into separate files. To use modules you have to let the browser know that you are using modules.
This is done by adding the `type="module"` attribute to the `<script>` tag.

```html
<script type="module" src="./my-module.js"></script>
```

> 💡 Modules allow you to use `import` and `export` statements but also change a few other things
> about how the browser treats your code that differ from standard scripts: They have their own
> scope and are not accessible from the global scope (unless exported). They also do not require the
> `defer` attribute as they are deferred by default. The scripts are executed in the more modern
> [strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules#aside_%E2%80%94_.mjs_versus_.js)
> automatically.

> 💡 When reading about modules online you might stumble upon the file extension `.mjs` which is
> sometimes used for JavaScript modules. For modules both `.js` and `.mjs` work fine but we've
> decided to use the `.js` extension for consistency. There is a great
> [section discussing `.js` vs `.mjs` on mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules#aside_%E2%80%94_.mjs_versus_.js).

---

## Exporting using `export` Statements

Using the `export` statement you can export a variable or function to make it available to other
modules. You can use named exports to export multiple variables or functions or one `default` export
per module to export the main functionality of the module.

### Named Exports

Usally named exports are created by using the keyword `export` dircectly before `const`, `let` or
`function`.

```js
export const name = "Alex";
export const age = 26;
export function sayHello() {
  console.log("Hello");
}
```

It is also possible to export functions or variables after they have been declared.

```js
const name = "Alex";
const age = 26;
function sayHello() {
  console.log("Hello");
}

export { name, age, sayHello };
```

### `default` Exports

Default exports are created by using the keyword `export default`. **You can only have one default
export per module.**

Before a function declaration the syntax is similar to named exports.

```js
export default function sayHello() {
  console.log("Hello");
}
```

For directly exporting variables as default you only declare the value of the thing you're
exporting.

```js
export default "Alex";
```

This is the same for arrow functions.

```js
export default () => {
  console.log("Hello");
};
```

> 💡 Notice that there is no `const name =` or `const sayHello =` in the code above. Default exports
> are nameless and constant by default.

Just like with named exports you can export the default export after it has been declared.

```js
const name = "Alex";

export default name;
```

> 💡 Notice that since default exports have no clear name the should semantically correspond to the
> name of the module. The above example should have a module name like `name.js`.

### Mixing Named and `default` Exports

You can mix named and default exports.

```js
export const name = "Alex";
export default function sayHello() {
  console.log("Hello");
}
```

---

## Importing using `import` Statements

Code from other modules can be imported using the `import` statement. Import statements should
always be placed at the top of the file. Everything that can be exported from a module can also be
imported from another module.

### Importing Named Exports

If another module exports a named export you can import it as such.

```js
import { name, age } from "./my-module.js";
```

Now `name` and `age` are available in the current module.

### Importing `default` Exports

If another module exports a `default` export you have to give it a name when importing it.

```js
import myModule from "./my-module.js";
```

> 💡 Notice that the name you give it does not nessesarily have to match the name of the module or
> the original name of the thing that was exported. For example `myModule` could have the value of
> the `sayHello` function which is not clear from the name. Since you could import the same module
> in multiple files you can also give it a different name every time.

### Mixing Named and `default` Imports

You can mix named and default imports.

```js
import myModule, { name, age } from "./my-module.js";
```

### Renaming Named Imports

You can rename named imports explicitly by using the `as` syntax.

```js
import { name as firstName, age as yearsSinceBorn } from "./my-module.js";
```

The variables `firstName` and `yearsSinceBorn` are now available in the current module. This can be
useful if the name of an import conflicts with a local variable name.

In contrast to default imports, you have to be explicit that you are renaming and what the original
names were.

---

## Structuring JavaScript Code

### Utility Functions and Constants

Functions and constants can be grouped into files that are named after the functionality they
provide. For example `math.js` could contain functions like `add`, `subtract`, `multiply` and
`divide`.

The file should have a named export for each function.

We recommend to create a `utils` folder in your project and put all utility functions in there.

### Vanilla JavaScript Components

Vanilla JavaScript means that you are not using a framework like React (from vanilla being the most
basic variant of ice cream).

Even though there is no set standard for structuring vanilla JavaScript components, we recommend the
following:

- Create a folder for each component
- Make your component file and function names uppercase (PascalCase)
- Each component has a named export for the component function (e.g.
  `export function ButtonGroup()`)
- Components can take arguments that are called props or properties a convention (e.g.
  `export function ButtonGroup(props)`)
- Components should not depend on the outside world and create their own DOM elements
- Components should return a single DOM element

> 💡 **These are just recommendations**
>
> Another common convention is to use kabap-case names for component files. This way they are named
> after the BEM block class name. For example you could use `button-group/button-group.js` and
> `button-group/button-group.css` for a component that has a `.button-group` class. This is the same
> organizational style you are used to when working with just CSS.
>
> The name of the component function could also be `createButtonGroup()` or even
> `createButtonGroupElement()` to make it is clear that it is a function that creates a DOM element.
>
> Whatever style you choose, make sure you are consistent per project.

Here is an example of a component that creates a button:

```js
export function Button(props) {
  const button = document.createElement("button");
  button.classList.add("button");
  button.textContent = props.text;
  return button;
}
```

An advanced use case are components that call other components (composition):

```js
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
```

Here is how these components could be used in another file:

```js
import { ButtonGroup } from "./ButtonGroup/ButtonGroup.js";
import { Button } from "./Button/Button.js";

const myButtonGroup = ButtonGroup({
  buttons: [{ text: "Button 1" }, { text: "Button 2" }, { text: "Button 3" }],
});
document.body.append(myButtonGroup);

const myButton = Button({ text: "Button" });
document.body.append(myButton);
```

---

## Resources

- [Export and Import (javascript.info)](https://javascript.info/import-export)
- [A word against default exports (javascript.info)](https://javascript.info/import-export#a-word-against-default-exports)
- [Case Styles: Camel, Pascal, Snake, and Kebab Case](https://betterprogramming.pub/string-case-styles-camel-pascal-snake-and-kebab-case-981407998841)


---

### 6 .- MODERN SYNTAX

# JS Modern Syntax



## A Developing Language: JavaScript

JavaScript isn't _done_ – it is still being developed. The [tc39](https://tc39.es/) group is meeting
up on a bi-monthly schedule to discuss proposals regarding
[ECMAScript](https://developer.mozilla.org/en-US/docs/Glossary/ECMAScript) specifications, which
JavaScript is based on. [Here](https://github.com/tc39/proposals) you can find a list of active
proposals that are still in the process of being reviewed. You can take a look at some of the
finished proposals over [here](https://github.com/tc39/proposals/blob/main/finished-proposals.md).

---

## Destructuring Assignment

The destructuring assignment syntax is a JavaScript expression that makes it possible to unpack
values from arrays, or properties from objects, into distinct variables. Destructuring doesn't
mutate the original array or object.

### Destructuring Arrays

```js
const greekLetters = ["alpha", "beta", "gamma", "delta"];
```

If we want to declare the values of `greekLetters` as distinct variables, accessing them might turn
out to be quite tedious.

_Without_ Destructuring

```js
const firstLetter = greekLetters[0];
const secondLetter = greekLetters[1];
const thirdLetter = greekLetters[2];
const fourthLetter = greekLetters[3];
// firstLetter → 'alpha'
// secondLetter → 'beta'
// etc.
```

_With_ Destructuring

```js
const [firstLetter, secondLetter, thirdLetter, fourthLetter] = greekLetters;
// firstLetter → 'alpha'
// secondLetter → 'beta'
// etc.
```

The result of the two code snippets is the same but destructuring the array makes for more readable
and concise code.

If you don't need or want the second and the fourth value in our initial array `greekLetters`
there's an option to skip values during the process of destructuring.

```js
const [firstLetter, , thirdLetter] = greekLetters;
// firstLetter → 'alpha'
// thirdLetter → 'gamma'
```

`thirdLetter` now contains the _third_ value of `greekLetters`. The extra comma skips the value at
the respective position in `greekLetters`. The fourth value is ignored because the destructuring
assignment ended.

Skipping values with extra commas can quickly become unreadable. Imagine wanting to skip 5 values:
`const [a, , , , , , g] = x;`. General advice is to be very mindful with this feature.

### Destructuring Objects

```js
const coachObject = {
  name: "Sam",
  mood: "great",
  skills: "amazing",
  score: 9999,
};
```

You can use destructuring assignment like this:

```js
const { name, mood, skills, score } = coachObject;
// name → 'Sam'
// mood → 'great'
// etc.
```

Now you've got `name`, `mood`, `skills` and `score` available as distinct variables.

In contrast to array destructuring the variable names are not arbitrary and do not depend on the
order. Here the names of the variables have to match the keys of the object properties.

You can rename the variable while destructuring:

```js
const { name: firstName } = coachObject;
// firstName → 'Sam'
// name → undefined
```

You can also set a default value of a property in case it does not exist:

```js
const { isAdmin = true } = coachObject;
// isAdmin → true
```

---

## Rest and Spread Syntax

The rest and the spread syntax look deceptively similar. Both are identified by three dots: `...`.
They do two different things though, depending in which context `...` is used.

### Rest Syntax (`...`)

The rest syntax allows you to say: "Put the rest into this variable" when using destructuring
assignment or declaring function parameters.

You can use it with arrays:

```js
const greekLetters = ["alpha", "beta", "gamma", "delta"];
const [firstLetter, ...allTheOtherLetters] = greekLetters;
// firstLetter → "alpha"
// allTheOtherLetters → ["beta", "gamma", "delta"]
```

Or with objects:

```js
const coachObject = {
  name: "Sam",
  mood: "great",
  skills: "amazing",
  score: 9999,
};

const { name, score, ...theRestOfTheCoachObject } = coachObject;
// name → "Sam"
// score → 9999
// theRestOfTheCoachObject → { mood: 'great', skills: 'amazing' }
```

And even with function parameters:

```js
function logLetters(firstLetter, ...moreLetters) {
  console.log("the first letter is", firstLetter);
  console.log("even more letters", moreLetters);
}

logLetters("alpha", "beta", "gamma", "delta");
// logs:
// the first letter is alpha
// even more letters (3) ['beta', 'gamma', 'delta']
```

### Spread Syntax (`...`)

The spread syntax allows you to say: "spread everything inside this variable into here" when
declaring array or object literals or calling functions.

It works like this with array literal declarations:

```js
const greekLetters = ["alpha", "beta", "gamma", "delta"];
const moreGreekLetters = [...greekLetters, "epsilon", "zeta"];
// moreGreekLetters → ['alpha', 'beta', 'gamma', 'delta', 'epsilon', 'zeta']
```

You can spread two (or more) arrays into another array ...

```js
const redColors = ["crimson", "pink", "purple"];
const blueColors = ["navy", "teal", "sky"];
const mixedColors = [...redColors, ...blueColors];
// mixedColors → ['crimson', 'pink', 'purple', 'navy', 'teal', 'sky']
```

... and it matters where respectively you spread one array into another:

```js
const cats = ["cat", "cat", "cat"];
const dogs = ["dog", "dog", "dog"];

const catsAndDogs = [...cats, ...dogs];
// catsAndDogs → ['cat', 'cat', 'cat', 'dog', 'dog', 'dog']

const dogsAndCats = [...dogs, ...cats];
// dogsAndCats → ['dog', 'dog', 'dog', 'cat', 'cat', 'cat']

const catsBetweenBirds = ["bird", ...cats, "bird"];
// catsBetweenBirds → ['bird', 'cat', 'cat', 'cat', 'bird']
```

Here is how the spread syntax works with object declarations:

```js
const circle = { radius: 5, shape: "circle" };

const greenCircle = { ...circle, color: "green" };
// greenCircle → { radius: 5, shape: 'circle', color: 'green' }
```

Notice that the order of spread operations matters because you can override properties:

```js
const circle = { radius: 5, shape: "circle" };

const largeCircle = { ...circle, radius: 20 };
// largeCircle → { radius: 20, shape: 'circle' }

const notALargeCircle = { radius: 20, ...circle };
// notALargeCircle → { radius: 5, shape: 'circle' }
```

The spread syntax is very helpful for creating a shallow copy of arrays and objects:

```js
const book = { title: "Ulysses", author: "James Joyce" };
const shallowCopyOfBook = { ...book };
shallowCopyOfBook.year = "1920";

// book → { title: 'Ulysses', author: 'James Joyce' }
// shallowCopyOfBook → { title: 'Ulysses', author: 'James Joyce', year: '1920' }
```

```js
const greekLetters = ["alpha", "beta", "gamma", "delta", "epsilon", "zeta"];
const sortedGreekLetters = [...greekLetters].sort((a, b) => a.localeCompare(b));
// this is an alternative to greekLetters.slice() which also creates a shallow copy

// greekLetters → ['alpha', 'beta', 'gamma', 'delta', 'epsilon', 'zeta']
// sortedGreekLetters → ['alpha', 'beta', 'delta', 'epsilon', 'gamma', 'zeta']
```

You can also use the spread syntax when calling functions:

```js
const numbers = [4534, 3411, 2455, 4952];
const smallestNumber = Math.min(...numbers);
// smallestNumber → 2455
```

---

## Optional Chaining

The optional chaining operator `?.` is like the chaining operator `.`, except that instead of
throwing an error if a reference is _nullish_ (null or undefined), the expression 'short-circuits'
with a value of `undefined`. This is useful when you're not sure if a property, method or index
exists or if something is callable.

```js
function feedCats(cats) {
  return cats.forEach((cat) => console.log(cat, "says meow"));
}

feedCats(["Garfield", "Tom", "Grumpy Cat"]);
// logs:
// Garfield says meow
// Tom says meow
// Grumpy Cat says meow

feedCats();
// throws:
// Uncaught TypeError: Cannot read properties of undefined (reading 'forEach')
```

```js
function feedCats(cats) {
  return cats?.forEach((cat) => console.log(cat, "says meow"));
}

feedCats();
// logs nothing, but also does not throw
```

The `?.` short-circuits the expression and evaluates the return statement to `undefined`. This way
the error is avoided without the need to explicitly use if statements or ternaries to check the
values.

Optional chaining is useful when targeting a property in an object with a deeply nested structure.

```js
const person = {
  name: "Sam",
  skills: [
    {
      name: "HTML",
      level: 9999,
      category: {
        name: "coding",
      },
    },
    {
      name: "Agile",
      level: 1337,
      category: {
        name: "projects",
      },
    },
  ],
};

console.log(person.skills[1].category.name);
// logs: projects

console.log(person.skills[2].level);
// throws: Uncaught TypeError: Cannot read properties of undefined (reading 'level')

console.log(person.skills?.[2]?.level);
// logs: undefined

console.log(person.skills[0].partner.name);
// throws: Uncaught TypeError: Cannot read properties of undefined (reading 'name')

console.log(person.skills[0].partner?.name);
// logs: undefined
```

---

## Nullish Coalescing

The nullish coalescing operator `??` is a logical operator that returns its right-hand side operand
when its left-hand side operand is null or undefined, and otherwise returns its left-hand side
operand.

```js
const chocolate = true;

function chocolateCheck() {
  return chocolate ?? "No chocolate :(";
}

const result = chocolateCheck();
```

In this example, our function `chocolateCheck` will return the value of `chocolate` (in this
instance: `true`), because the value of `chocolate` is neither `null` or `undefined`.

```js
const chocolate = undefined;

function chocolateCheck() {
  return chocolate ?? "No chocolate :(";
}

const result = chocolateCheck();
```

In this example, our function would return `'No chocolate :('`, seeing as how the value of
`chocolate` is `undefined`. The same would happen if we declared the variable `chocolate` with the
value `null`.

Written as an `if/else` statement, the code would look like this:

```js
const chocolate = true;

function chocolateCheck() {
  if (chocolate === null || chocolate === undefined) {
    return "No chocolate :(";
  }

  return true;
}

const result = chocolateCheck();
```

## Resources

- [TC39 - Specifying JavaScript](https://tc39.es/)
- [async function (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [Destructuring assignment (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
- [Spread Syntax (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)
- [Rest parameters (MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters)


---

### 7 .- UNIT TESTING



---

## What are unit tests

When developing apps, errors inevitably emerge in your code. That's why apps must be tested
regularly to ensure that they work as expected. Since manual testing by clicking in the UI is very
time consuming and cumbersome, tests are automated.

Test automation can be performed in several ways. A good classification is provided by the
[Testing Trophy](https://kentcdodds.com/blog/the-testing-trophy-and-testing-classifications).

Static Testing refers to linting and can be understood as a spell checker for your code.

Unit tests check whether a single function works as intended. The goal is to test each individual unit
independently and isolated from other data and external influences. The test can be run
automatically after each modification to ensure latest changes won't break the app.

---

## Test Driven Development (TDD)

With Test driven development (TTD) the test is written first. Afterwards you write the function,
which should create a desired result.

Following this approach you get feedback as early as possible whether your work is going into the
right direction. In the beginning all tests will fail. Gradually more and more test will be
successful. The implementation of your function is finished as soon as all test runs are successful.

---

## How to test with jest

Tests are placed in a file next to the code you like to test, but with `.test.js` as filename
ending.

```
calculator.js			<--- Code used in your app
calculator.test.js		<--- Tests for this code
```

When writing tests, you build various different scenarios that check a certain desired result of a
function. Each of such test cases is wrapped into a function called
[test()](https://jestjs.io/docs/api#testname-fn-timeout). The first argument of the `test()`
function is a description of the test case in plain english.

Unit tests usually have a similar structure. First, the function to be tested is called and any
required arguments are passed. Afterwards the result of this function call is passed to the
[expect()](https://jestjs.io/docs/expect) function. Thus different
[matcher](https://jestjs.io/docs/using-matchers) functions like `toBe()` or `toEqual()` can be used.

This way the actually generated result of the function is checked against an expected result defined
in the test case.

```js
import { add } from "calculator";

test("adds the numbers 1, 2 and 3 correctly", () => {
  const result = add(1, 2, 3);
  expect(result).toBe(6);
});

test("adds the numbers 13, 28 and 42 correctly", () => {
  const result = add(13, 28, 42);
  expect(result).toBe(83);
});
```

---

## Run Tests locally

Run all tests:

```sh
npm run test
```

When executing this commands you will see the result of the test run: a list of all included tests
and whether they were successful or failed.

---

## Resources

- [Jest](https://jestjs.io/)
- [Testing Trophy and Testing Classifications](https://kentcdodds.com/blog/the-testing-trophy-and-testing-classifications)

---

### 8 .- NPM and LINTING BASICS
# npm and Linting Basics

## npm

It's a package registry that works like an app store for your project.

---

## `package.json`

Packages that are installed into your project are called dependencies. They are kept inside a
`package.json` file in your project root. The `package.json` file also contains information about
your project.

A `package.json` may look something like this:

```json
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

- `dependencies` are packages that your application source code directly depends on, like libraries
  or frameworks.
- `devDependencies` are packages that help you while developing your application, like linters or
  build tools.

### Installing dependencies

`dependencies` and `devDependencies` inside the `package.json` can be installed by running
`npm install` (or just `npm i` for short).

> 💡 Do not forget to run `npm install` after cloning a new repository that has a `package.json`
> file.

When installing, npm creates a `node_modules` folder and a `package-lock.json` file.

- `node_modules` must always be in your `.gitignore` and must not be committed to your repository!
- `package-lock.json` should be commited to your repository.

---

## Semantic Versioning

A semantic version is updated whenever a package changes and a new version is published.

It follows this schema: **`Major.Minor.Patch`** (e.g. `1.2.3`)

- **`Major`** → major version, changes when the public api of a package changes (breaking change)
- **`Minor`** → minor version, changes when new features are added
- **`Patch`** → patch version, changes when bugs are fixed

When defining dependencies in `package.json` npm uses version ranges to define which version of
package should be installed. npm always installs the newest version of package that still matches
the range description.

- `^` (e.g. `"^10.4.1"`) → Newer minor updates and patches can be installed, but major updates
  cannot.  
  (Here version `10.5.6` would be installed but not `11.0.0`)

- `~` (e.g. `"~10.4.1"`) → Newer patches can be installed, minor and major updates cannot.  
  (Here version `10.4.8` would be installed but not `10.5.0`)

- `>` (e.g. `">10.4.1"`) → Any newer version will be installed.  
  (Here any version newer than `10.4.1` would be installed)

Version ranges described with `^` are by far the most commmon choice because they are usally safe
and won't break your application.

---

## Linters

Linters are tools which analyze your code and show syntax errors, oversights like undeclared
variables, bugs and stylistic errors. Some important linters are Prettier (Code formatter), HTMLHint
(HTML), and ESLint (JavaScript).

To run these linters, we can define a script inside of the package.json as in the following example:

```json
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

Prettier makes sure that your code / the code of your team is formatted in the exact same way. There
are two important ways to use it:

- `npx prettier --check .` (checks for stylistic errors)
- `npx prettier --write .` (fixes stylistic errors)

The command `npx` (x = execute) starts prettier; the dot `.` at the end tells prettier to go through
all files. You can also choose to check only specific files or folders.

The flags `--check` and `--write` decide whether to only check for errors or immediately fixing
them.

We can also use the scripts called "prettier:check" and "prettier:write" in the package.json above
via `npm run prettier:check` or `npm run prettier:write`. It will do the exact same thing as
`npx prettier [...]`.

### HTMLHint

HTMLHint analyzes your HTML. You can use

- `npx htmlhint index.html` (analyzes the index.html file) or the script
- `npm run htmlhint`.

Note that, according to the above package.json, the script will run `npx htmlhint \"**/*.html\"` and
thus analyze all files ending with `.html`.

### ESLint

ESLint analyzes your JavaScript and highlights errors. You can use

- `npx eslint index.js` (analyzes the index.js file) or the script
- `npm run eslint`.

Note that, according to the above package.json, the script will run `npx eslint \"**/*.js\"` and
thus analyze all files ending with `.js`.

### Combining Scripts

We can write a script using several other scripts and thus running all linters at once. See the
above mentioned scripts `npm run test` and `npm run fix` which will run htmlhint, prettier and
eslint.

The `&&` means that the script will run one after another. The next script only is executed if the
one before found no issues.

### Setup Files for Linters

All linters come with a built-in ruleset, but we can configure these rules. We do this with files at
the root of our project called `.eslintrc.js`, `.htmlhintrc.json`, or `.prettierrc`. You can
recognize them by the "rc", but the file ending might differ.

We can also say which files the linter will ignore. This is done inside of `.eslintignore` or
`.prettierignore`.

## Error messages are your friends

> 💡 Error messages are your friends, that kindly point you towards errors. Learning to correctly
> read error messages is one of the most important skills you'll pick up as a developer.
>
> If you come across an error message, take your time to fully understand what it is saying. Then
> navigate to the place in code where it found the issue. This way you know exactly what to fix and
> where.

---

## Resources

About npm:

- [npm website](https://www.npmjs.com/)
- [package.json specification](https://docs.npmjs.com/cli/v8/configuring-npm/package-json)
- [npm install documentation](https://docs.npmjs.com/cli/v8/commands/npm-install)
- [Semantic Versioning specification](https://semver.org/)

Linters:

- [HTMLHint](https://htmlhint.com/docs/user-guide/getting-started)
- [Prettier](https://prettier.io/docs/en/install.html)
- [ESLint](https://eslint.org/docs/latest/user-guide/command-line-interface)

VSCode Plugins for Linters:

- [HTMLHint](https://marketplace.visualstudio.com/items?itemName=HTMLHint.vscode-htmlhint)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)


---
