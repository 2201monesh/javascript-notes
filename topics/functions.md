![https://miro.medium.com/max/560/1*3cuBMOgJaOShxNpKMYoTpw.png](https://miro.medium.com/max/560/1*3cuBMOgJaOShxNpKMYoTpw.png)

Functions are the main “building blocks” of the program. They allow the code to be called many times without repetition.

## [Invoking functions](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Functions#invoking_functions)

You are probably clear on this by now, but just in case, to actually use a function after it has been defined, you've got to run — or **invoke** (a fancy word for run, or execute) — it. This is done by including the name of the function in the code somewhere, followed by parentheses.

```jsx
function myFunction() {
  alert('hello');
}

myFunction();
// calls the function once
```

<aside>
ℹ️ **Note:** This form of creating a function is also known as *function declaration*. It is always hoisted, so you can call function above function definition and it will work fine.

</aside>

# [Local variables](https://javascript.info/function-basics#local-variables)

A variable declared inside a function is only visible inside that function.

For example:

```jsx
function showMessage() {
  *let message = "Hello, I'm JavaScript!"; // local variable*alert( message );
}

showMessage(); // Hello, I'm JavaScript!

alert( message ); // <-- Error! The variable is local to the function
```

# [Outer variables](https://javascript.info/function-basics#outer-variables)

A function can access an outer variable as well, for example:

```jsx
let *userName* = 'John';

function showMessage() {
  let message = 'Hello, ' + *userName*;
  alert(message);
}

showMessage(); // Hello, John
```

The function has full access to the outer variable. It can modify it as well.

For instance:

```jsx
let *userName* = 'John';

function showMessage() {
  *userName* = "Bob"; // (1) changed the outer variable

  let message = 'Hello, ' + *userName*;
  alert(message);
}

alert( userName ); // *John* before the function call

showMessage();

alert( userName ); // *Bob*, the value was modified by the function
```

The outer variable is only used if there’s no local one.

If a same-named variable is declared inside the function then it *shadows* the outer one. For instance, in the code below the function uses the local `userName`. The outer one is ignored:

```jsx
let userName = 'John';

function showMessage() {
  *let userName = "Bob"; // declare a local variable*let message = 'Hello, ' + userName; // *Bob*alert(message);
}

// the function will create and use its own userName
showMessage();

alert( userName ); // *John*, unchanged, the function did not access the outer variable
```

<aside>
ℹ️ **Global variables**

Variables declared outside of any function, such as the outer `userName` in the code above, are called *global*.

Global variables are visible from any function (unless shadowed by locals).

It’s a good practice to minimize the use of global variables. Modern code has few or no globals. Most variables reside in their functions. Sometimes though, they can be useful to store project-level data.

</aside>

## [Function parameters](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Functions#function_parameters)

Some functions require **parameters** to be specified when you are invoking them — these are values that need to be included inside the function parentheses, which it needs to do its job properly.

<aside>
ℹ️ **Note:** Parameters are sometimes called arguments, properties, or even attributes.

</aside>

<aside>
ℹ️ **Note:** When you need to specify multiple parameters, they are separated by commas.

</aside>

<aside>
ℹ️ **Note:**

- A **parameter** is the variable listed inside the parentheses in the function declaration (it’s a declaration time term).
- An **argument** is the value that is passed to the function when it is called (it’s a call time term).

We declare functions listing their parameters, then call them passing arguments.

</aside>

### [Optional parameters](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Functions#optional_parameters)

Sometimes parameters are optional — you don't have to specify them. If you don't, the function will generally adopt some kind of default behavior. As an example, the array [join()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) function's parameter is optional:

```jsx
const myArray = ['I', 'love', 'chocolate', 'frogs'];
const madeAString = myArray.join(' ');
console.log(madeAString);
// returns 'I love chocolate frogs'

const madeAnotherString = myArray.join();
console.log(madeAnotherString);
// returns 'I,love,chocolate,frogs'
Copy to Clipboard
```

If no parameter is included to specify a joining/delimiting character, a comma is used by default.

### [Default values](https://javascript.info/function-basics#default-values)

If a function is called, but an argument is not provided, then the corresponding value becomes `undefined`.

For instance, the aforementioned function `showMessage(from, text)` can be called with a single argument:

```jsx
showMessage("Ann");
```

That’s not an error. Such a call would output `"*Ann*: undefined"`. As the value for `text` isn’t passed, it becomes `undefined`.

We can specify the so-called “default” (to use if omitted) value for a parameter in the function declaration, using `=`:

```jsx
function showMessage(from, *text = "no text given"*) {
  alert( from + ": " + text );
}

showMessage("Ann"); // Ann: no text given
```

Now if the `text` parameter is not passed, it will get the value `"no text given"`.

The default value also jumps in if the parameter exists, but strictly equals `undefined`, like this:

```jsx
showMessage("Ann", undefined); // Ann: no text given
```

Here `"no text given"` is a string, but it can be a more complex expression, which is only evaluated and assigned if the parameter is missing. So, this is also possible:

```jsx
function showMessage(from, text = anotherFunction()) {
  // anotherFunction() only executed if no text given
  // its result becomes the value of text
}
```

**Evaluation of default parameters**

In JavaScript, a default parameter is evaluated every time the function is called without the respective parameter.

In the example above, `anotherFunction()` isn’t called at all, if the `text` parameter is provided.

On the other hand, it’s independently called every time when `text` is missing.

**Default parameters in old JavaScript code**

Several years ago, JavaScript didn’t support the syntax for default parameters. So people used other ways to specify them.

Nowadays, we can come across them in old scripts.

For example, an explicit check for `undefined`:

```jsx
function showMessage(from, text) {
  *if (text === undefined) {
    text = 'no text given';
  }*alert( from + ": " + text );
}
```

…Or using the `||` operator:

```jsx
function showMessage(from, text) {
  // If the value of text is falsy, assign the default value
  // this assumes that text == "" is the same as no text at all
  text = text || 'no text given';
  ...
}
```

### [Alternative default parameters](https://javascript.info/function-basics#alternative-default-parameters)

Sometimes it makes sense to assign default values for parameters at a later stage after the function declaration.

We can check if the parameter is passed during the function execution, by comparing it with `undefined`:

```jsx
function showMessage(text) {
  // ...

  *if (text === undefined) { // if the parameter is missing
    text = 'empty message';
  }*alert(text);
}

showMessage(); // empty message
```

…Or we could use the `||` operator:

```jsx
function showMessage(text) {
  // if text is undefined or otherwise falsy, set it to 'empty'
  text = text || 'empty';
  ...
}
```

Modern JavaScript engines support the [nullish coalescing operator](https://javascript.info/nullish-coalescing-operator) `??`, it’s better when most falsy values, such as `0`, should be considered “normal”:

```jsx
function showCount(count) {
  // if count is undefined or null, show "unknown"
  alert(count ?? "unknown");
}

showCount(0); // 0
showCount(null); // unknown
showCount(); // unknown
```

## [Anonymous functions and arrow functions](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Functions#anonymous_functions_and_arrow_functions)

So far we have just created a function like so:

```jsx
function myFunction() {
  alert('hello');
}
Copy to Clipboard
```

But you can also create a function that doesn't have a name:

```jsx
(function () {
  alert('hello');
})
Copy to Clipboard
```

This is called an **anonymous function**, because it has no name. You'll often see anonymous functions when a function expects to receive another function as a parameter. In this case the function parameter is often passed as an anonymous function.

**Note:** This form of creating a function is also known as *function expression*. Unlike function declaration, function expressions are not hoisted.

### [Anonymous function example](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Functions#anonymous_function_example)

For example, let's say you want to run some code when the user types into a text box. To do this you can call the `[addEventListener()](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)` function of the text box. This function expects you to pass it (at least) two parameters:

- the name of the event to listen for, which in this case is `[keydown](https://developer.mozilla.org/en-US/docs/Web/API/Element/keydown_event)`
- a function to run when the event happens.

When the user presses a key, the browser will call the function you provided, and will pass it a parameter containing information about this event, including the particular key that the user pressed:

```jsx
function logKey(event) {
  console.log(`You pressed "${event.key}".`);
}

textBox.addEventListener('keydown', logKey);
Copy to Clipboard
```

Instead of defining a separate `logKey()` function, you can pass an anonymous function into `addEventListener()`:

```jsx
textBox.addEventListener('keydown', function(event) {
  console.log(`You pressed "${event.key}".`);
});
Copy to Clipboard
```

### [Arrow functions](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Functions#arrow_functions)

If you pass an anonymous function like this, there's an alternative form you can use, called an **arrow function**. Instead of `function(event)`, you write `(event) =>`:

```jsx
textBox.addEventListener('keydown', (event) => {
  console.log(`You pressed "${event.key}".`);
});
Copy to Clipboard
```

If the function only has one line in the curly brackets, you omit the curly brackets:

```jsx
textBox.addEventListener('keydown', (event) => console.log(`You pressed "${event.key}".`));
Copy to Clipboard
```

If the function only takes one parameter, you can also omit the brackets around the parameter:

```jsx
textBox.addEventListener('keydown', event => console.log(`You pressed "${event.key}".`));
Copy to Clipboard
```

Finally, if your function needs to return a value, and contains only one line, you can also omit the `return` statement. In the following example we're using the `[map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)` method of `Array` to double every value in the original array:

```jsx
const originals = [1, 2, 3];

const doubled = originals.map((item) => item * 2);

console.log(doubled); // [2, 4, 6]
Copy to Clipboard
```

The `map()` method takes each item in the array in turn, passing it into the given function. It then takes the value returned by that function and adds it to a new array.

So in the example above, `(item) => item * 2` is the arrow function equivalent of:

```jsx
function doubleItem(item) {
  return item * 2;
}
Copy to Clipboard
```

We recommend that you use arrow functions, as they can make your code shorter and more readable. To learn more, see the [section on arrow functions in the JavaScript guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions#arrow_functions), and our [reference page on arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions).

# [Returning a value](https://javascript.info/function-basics#returning-a-value)

A function can return a value back into the calling code as the result.

The simplest example would be a function that sums two values:

```jsx
function sum(a, b) {
  *return* a + b;
}

let result = sum(1, 2);
alert( result ); // 3
```

The directive `return` can be in any place of the function. When the execution reaches it, the function stops, and the value is returned to the calling code (assigned to `result` above).

There may be many occurrences of `return` in a single function. For instance:

```jsx
function checkAge(age) {
  if (age >= 18) {
    *return true;*} else {
    *return confirm('Do you have permission from your parents?');*}
}

let age = prompt('How old are you?', 18);

if ( checkAge(age) ) {
  alert( 'Access granted' );
} else {
  alert( 'Access denied' );
}
```

It is possible to use `return` without a value. That causes the function to exit immediately.

For example:

```jsx
function showMovie(age) {
  if ( !checkAge(age) ) {
    *return;*}

  alert( "Showing you the movie" ); // (*)
  // ...
}
```

In the code above, if `checkAge(age)` returns `false`, then `showMovie` won’t proceed to the `alert`.

<aside>
ℹ️ **A function with an empty `return` or without it returns `undefined`**

If a function does not return a value, it is the same as if it returns `undefined`:

```jsx
function doNothing() { /* empty */ }

alert( doNothing() === undefined ); // true
```

An empty `return` is also the same as `return undefined`:

```jsx
function doNothing() {
  return;
}

alert( doNothing() === undefined ); // true
```

</aside>

<aside>
⚠️ **Never add a newline between `return` and the value**

For a long expression in `return`, it might be tempting to put it on a separate line, like this:

```jsx
return
 (some + long + expression + or + whatever * f(a) + f(b))
```

That doesn’t work, because JavaScript assumes a semicolon after `return`. That’ll work the same as:

```jsx
return*;*(some + long + expression + or + whatever * f(a) + f(b))
```

So, it effectively becomes an empty return.

If we want the returned expression to wrap across multiple lines, we should start it at the same line as `return`. Or at least put the opening parentheses there as follows:

```jsx
return (
  some + long + expression
  + or +
  whatever * f(a) + f(b)
  )
```

And it will work just as we expect it to.

</aside>

## [Naming a function](https://javascript.info/function-basics#function-naming)

Functions are actions. So their name is usually a verb. It should be brief, as accurate as possible and describe what the function does, so that someone reading the code gets an indication of what the function does.

It is a widespread practice to start a function with a verbal prefix which vaguely describes the action. There must be an agreement within the team on the meaning of the prefixes.

For instance, functions that start with `"show"` usually show something.

Function starting with…

- `"get…"` – return a value,
- `"calc…"` – calculate something,
- `"create…"` – create something,
- `"check…"` – check something and return a boolean, etc.

Examples of such names:

```jsx
showMessage(..)     // shows a message
getAge(..)          // returns the age (gets it somehow)
calcSum(..)         // calculates a sum and returns the result
createForm(..)      // creates a form (and usually returns it)
checkPermission(..) // checks a permission, returns true/false
```

With prefixes in place, a glance at a function name gives an understanding what kind of work it does and what kind of value it returns.

<aside>
ℹ️ **One function – one action**

A function should do exactly what is suggested by its name, no more.

Two independent actions usually deserve two functions, even if they are usually called together (in that case we can make a 3rd function that calls those two).

A few examples of breaking this rule:

- `getAge` – would be bad if it shows an `alert` with the age (should only get).
- `createForm` – would be bad if it modifies the document, adding a form to it (should only create it and return).
- `checkPermission` – would be bad if it displays the `access granted/denied` message (should only perform the check and return the result).

These examples assume common meanings of prefixes. You and your team are free to agree on other meanings, but usually they’re not much different. In any case, you should have a firm understanding of what a prefix means, what a prefixed function can and cannot do. All same-prefixed functions should obey the rules. And the team should share the knowledge.

</aside>

<aside>
ℹ️ **Ultrashort function names**

Functions that are used *very often* sometimes have ultrashort names.

For example, the [jQuery](https://jquery.com/) framework defines a function with `$`. The [Lodash](https://lodash.com/) library has its core function named `_`.

These are exceptions. Generally function names should be concise and descriptive.

</aside>

## [Functions == Comments](https://javascript.info/function-basics#functions-comments)

Functions should be short and do exactly one thing. If that thing is big, maybe it’s worth it to split the function into a few smaller functions. Sometimes following this rule may not be that easy, but it’s definitely a good thing.

A separate function is not only easier to test and debug – its very existence is a great comment!

For instance, compare the two functions `showPrimes(n)` below. Each one outputs [prime numbers](https://en.wikipedia.org/wiki/Prime_number) up to `n`.

The first variant uses a label:

```jsx
function showPrimes(n) {
  nextPrime: for (let i = 2; i < n; i++) {

    for (let j = 2; j < i; j++) {
      if (i % j == 0) continue nextPrime;
    }

    alert( i ); // a prime
  }
}
```

The second variant uses an additional function `isPrime(n)` to test for primality:

```jsx
function showPrimes(n) {

  for (let i = 2; i < n; i++) {
    *if (!isPrime(i)) continue;*alert(i);  // a prime
  }
}

function isPrime(n) {
  for (let i = 2; i < n; i++) {
    if ( n % i == 0) return false;
  }
  return true;
}
```

The second variant is easier to understand, isn’t it? Instead of the code piece we see a name of the action (`isPrime`). Sometimes people refer to such code as *self-describing*.

So, functions can be created even if we don’t intend to reuse them. They structure the code and make it readable.
