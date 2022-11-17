![https://miro.medium.com/max/1400/1*lrq9keAv-dGD_gtb0TNknw.jpeg](https://miro.medium.com/max/1400/1*lrq9keAv-dGD_gtb0TNknw.jpeg)

## VARIABLES

You can think of variables as simply “storage containers” for data in your code. Until recently there was only one way to create a variable in JavaScript — the `var` statement. But in the newest JavaScript versions we have two more ways — `let` and `const`.

The statement below creates (in other words: *declares*) a variable with the name “message”:

`let message;`

Now, we can put some data into it by using the assignment operator `=`:

```jsx
let message;

*message = 'Hello'; // store the string 'Hello' in the variable named message*
```

The string is now saved into the memory area associated with the variable. We can access it using the variable name:

```jsx
let message;
message = 'Hello!';

*alert(message); // shows the variable content*
```

To be concise, we can combine the variable declaration and assignment into a single line:

```jsx
let message = 'Hello!'; // define the variable and assign the value

alert(message); // Hello!
```

We can also declare multiple variables in one line:

`let user = 'John', age = 25, message = 'Hello';`

We can also change it as many times as we want:

```jsx
let message;

message = 'Hello!';

message = 'World!'; // value changed
```

We can also declare two variables and copy data from one into the other.

```jsx
let hello = 'Hello world!';
let message;

*// copy 'Hello world' from hello into message
message = hello;*
```

<aside>
  
⚠️ **Declaring twice triggers an error**

A variable should be declared only once.

A repeated declaration of the same variable is an error:

```jsx
let message = "This";

// repeated 'let' leads to an error
let message = "That"; // SyntaxError: 'message' has already been declared
```

</aside>

# [Variable naming](https://javascript.info/variables#variable-naming)

There are two limitations on variable names in JavaScript:

1. The name must contain only letters, digits, or the symbols `$` and `_`.
2. The first character must not be a digit.

When the name contains multiple words, [camelCase](https://en.wikipedia.org/wiki/CamelCase) is commonly used. That is: words go one after another, each word except first starting with a capital letter: `myVeryLongName`.

What’s interesting – the dollar sign `'$'` and the underscore `'_'` can also be used in names. They are regular symbols, just like letters, without any special meaning.

<aside>
  
ℹ️ **Case matters**

Variables named `apple` and `APPLE` are two different variables.

</aside>

<aside>
  
ℹ️ **Reserved names**

There is a [list of reserved words](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords), which cannot be used as variable names because they are used by the language itself.

For example: `let`, `class`, `return`, and `function` are reserved.

</aside>

# [Constants](https://javascript.info/variables#constants)

To declare a constant (unchanging) variable, use `const` instead of `let`:

`const myBirthday = '18.04.1982';`

Variables declared using `const` are called “constants”. They cannot be reassigned. An attempt to do so would cause an error:

```jsx
const myBirthday = '18.04.1982';
myBirthday = '01.01.2001'; // error, can't reassign the constant!
```

When a programmer is sure that a variable will never change, they can declare it with `const` to guarantee and clearly communicate that fact to everyone.

Would it be right to use upper case for `birthday`? For `age`? Or even for both?

```jsx
const BIRTHDAY = '18.04.1982'; // make uppercase?

const AGE = someCode(BIRTHDAY); // make uppercase?
```

We generally use upper case for constants that are “hard-coded”. Or, in other words, when the value is known prior to execution and directly written into the code.

In this code, `birthday` is exactly like that. So we could use the upper case for it.

In contrast, `age` is evaluated in run-time. Today we have one age, a year after we’ll have another one. It is constant in a sense that it does not change through the code execution. But it is a bit “less of a constant” than `birthday`: it is calculated, so we should keep the lower case for it.
