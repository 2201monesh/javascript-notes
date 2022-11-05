![https://res.cloudinary.com/practicaldev/image/fetch/s--9KL3OWyZ--/c_imagga_scale,f_auto,fl_progressive,h_900,q_auto,w_1600/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ya12vxbldjanxdt2s1pj.png](https://res.cloudinary.com/practicaldev/image/fetch/s--9KL3OWyZ--/c_imagga_scale,f_auto,fl_progressive,h_900,q_auto,w_1600/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ya12vxbldjanxdt2s1pj.png)

A JavaScript string is zero or more characters written inside quotes. You can use single or double quotes. 

```jsx
let carName1 = "Volvo XC60";  // Double quotes
let carName2 = 'Volvo XC60';  // Single quotes
```

You can use quotes inside a string, as long as they don't match the quotes surrounding the string.

```jsx
let answer1 = "It's alright";
let answer2 = "He is called 'Johnny'";
let answer3 = 'He is called "Johnny"';
```

## [Concatenating strings](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Strings#concatenating_strings)

Concatenate just means "join together". To join together strings in JavaScript you can use a different type of string, called a *template literal*.

A template literal looks just like a normal string, but instead of using single or double quote marks (`'` or `"`), you use backtick characters (```):

```jsx
const greeting = `Hello`;
```

This can work just like a normal string, except you can include variables in it, wrapped inside `${ }` characters, and the variable's value will be inserted into the result:

```jsx
const name = 'Chris';
const greeting = `Hello, ${name}`;
console.log(greeting); // "Hello, Chris"
```

You can use the same technique to join together two variables:

```jsx
const one = 'Hello, ';
const two = 'how are you?';
const joined = `${one}${two}`;
console.log(joined); // "Hello, how are you?"
```

### [Concatenation using "+"](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Strings#concatenation_using)

You can also concatenate strings using the `+` operator:

```jsx
const greeting = "Hello";
const name = "Chris";
console.log(greeting + ", " + name); // "Hello, Chris"
```

However, template literals usually give you more readable code:

```jsx
const greeting = "Hello";
const name = "Chris";
console.log(`${greeting}, ${name}`); // "Hello, Chris"
```

### ESCAPE Characters

The backslash (`\`) escape character turns special characters into string characters.

| Code | Result |
| --- | --- |
| \' | ' |
| \" | " |
| \\ | \ |
| \b | Backspace |
| \f | Form Feed |
| \n | New Line |
| \r | Carriage Return |
| \t | Horizontal Tabulator |
| \v | Vertical Tabulator |

## STRING INDEXING.. (to write)

# String Methods

<aside>
ℹ️ **JavaScript counts positions from zero.**

First position is 0.

Second position is 1.

**If a parameter is negative, the position is counted from the end of the string.**

</aside>

## `.length`

The `length` property returns the length of a string:

```jsx
let txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
let length = txt.length; // 26
```

# Extracting String Parts

There are 3 methods for extracting a part of a string:

[FULL COMPARISON BETWEEN THE THREE](https://stackoverflow.com/a/31910656/13515764)

- `**slice(*start*, *end*)`**
    
    `slice()` extracts a part of a string and returns the extracted part in a new string.
    
    The method takes 2 parameters: the start position, and the end position (end not included).
    
    ```jsx
    //Slice out the portion of a string from the position 7 to position 13 (13 is not included):
    let str = "Apple, Banana, Kiwi";
    let part = str.slice(7, 13); // Banana
    
    // This slices out a portion of a string from position -12 to position -6, ( that is starting counting from the end):
    let str = "Apple, Banana, Kiwi";
    let part = str.slice(-12, -6); // Banana
    
    //If you omit the second parameter, the method will slice out the rest of the string:
    let part = str.slice(7); // Banana, Kiwi
    
    // or, counting from the end: 
    let part = str.slice(-12); // Banana, Kiwi
    ```
