![https://wallpaperaccess.com/full/1555146.png](https://wallpaperaccess.com/full/1555146.png)

*Step one in learning about conditionals is making sure you have a good grasp on **[comparisons](http://javascript.info/comparison)**.*

# Conditional Statements

Very often when you write code, you want to perform different actions for different decisions.

You can use conditional statements in your code to do this.

In JavaScript we have the following conditional statements:

- Use `if` to specify a block of code to be executed, if a specified condition is true
- Use `else` to specify a block of code to be executed, if the same condition is false
- Use `else if` to specify a new condition to test, if the first condition is false
- Use `switch` to specify many alternative blocks of code to be executed

## The if Statement

Use the `if` statement to specify a block of JavaScript code to be executed if a condition is true.

```jsx
if (*condition*) { 
 //  *block of code to be executed if the condition is true*
}

//EXAMPLE
if (hour < 18) {
  greeting = "Good day";
}
```

<aside>
⚠️ Note that `if` is in lowercase letters. Uppercase letters (If or IF) will generate a JavaScript error.

</aside>

## The else Statement

Use the `else` statement to specify a block of code to be executed if the condition is false.

```jsx
if (*condition*) {  
//  *block of code to be executed if the condition is true*} else {  //  *block of code to be executed if the condition is false*
}

// EXAMPLE
if (hour < 18) {  
greeting = "Good day";
} else {  
greeting = "Good evening";
}
```

## The else if Statement

Use the `else if` statement to specify a new condition if the first condition is false.

```jsx
if (*condition1*) {  
//  *block of code to be executed if condition1 is true*
} 
else if (*condition2*) {  
//*code to be executed if the condition1 is false and condition2 is true*
} else {  
//*block of code to be executed if the condition1 is false & condition2 is false*
}

// EXAMPLE
if (time < 10) {  greeting = "Good morning";} else if (time < 20) {  greeting = "Good day";} else {  greeting = "Good evening";}
```

## Switch Statement

In addition to `if...else`, JavaScript has a feature known as a `switch` statement. `switch` is a type of conditional statement that will evaluate an expression against multiple possible cases and execute one or more blocks of code based on matching cases. The `switch` statement is closely related to a conditional statement containing many `else if` blocks, and they can often be used interchangeably.

- [Multiple Cases](https://www.notion.so/Conditionals-f4e33faa657c463589b6517dec8d006f)
- [Switch Ranges](https://www.notion.so/Conditionals-f4e33faa657c463589b6517dec8d006f)

The `switch` statement evaluates an expression and executes code as a result of a matching case. The basic syntax is similar to that of an `if` statement. It will always be written with `switch () {}`, with parentheses containing the expression to test, and curly brackets containing the potential code to execute.

Below is an example of a `switch` statement with two `case` statements, and a fallback known as `default`.

```jsx
switch (expression) {
	case x:
		// execute case x code block
		break;
	case y:
		// execute case y code block
		break;
	default:
		// execute default code block
}

```

Following the logic of the code block above, this is the sequence of events that will take place:

- The expression is evaluated.
- The first `case`, `x`, will be tested against the expression. If it matches, the code will execute, and the `break` keyword will end the `switch` block.
- If it does not match, `x` will be skipped and the `y` case will be tested against the expression. If `y` matches the expression, the code will execute and exit out of the `switch` block.
- If none of the cases match, the `default` code block will run.

Let’s make a working example of a `switch` statement following the syntax above. In this code block, we will find the current day of the week with the `new Date()` method, and `getDay()` to print a number corresponding to the current day. `0` stands for Sunday, all the way through `6` which stands for Saturday. We’ll start by setting up our variable.

```jsx
const day = new Date().getDay();
```

Using `switch`, we will send a message to the console each day of the week. The program will run in order from top to bottom looking for a match, and once one is found, the `break` command will halt the `switch` block from continuing to evaluate statements.

week.js

```jsx
// Set the current day of the week to a variable, with 0 being Sunday and 6 being Saturday
const day = new Date().getDay();

switch (day) {
	case 0:
		console.log("It's Sunday, time to relax!");
		break;
	case 1:
		console.log("Happy Monday!");
		break;
	case 2:
		console.log("It's Tuesday. You got this!");
		break;
	case 3:
		console.log("Hump day already!");
		break;
	case 4:
		console.log("Just one more day 'til the weekend!");
		break;
	case 5:
		console.log("Happy Friday!");
		break;
	case 6:
		console.log("Have a wonderful Saturday!");
		break;
	default:
		console.log("Something went horribly wrong...");
}

```

```jsx
Output
'Just one more day 'til the weekend!'
```

This code was tested on a Thursday, which corresponds to `4`, therefore the console output was `Just one more day 'til the weekend!`. Depending on what day of the week you are testing the code, your output will be different. We have included a `default` block at the end to run in case of an error, which in this case should not happen as there are only 7 days of the week. We also could have, for example, only printed results for Monday to Friday, and the `default` block could have had the same message for the weekend.

If we had omitted the `break` keyword in each statement, none of the other `case` statements would have evaluated to true, but the program would have continued to check until it reached the end. In order to make our programs faster and more efficient, we include the `break`.

### Switch Ranges

There might be an occasion in which you will need to evaluate a range of values in a `switch` block, as opposed to a single value as in our example above. We can do this by setting our expression to `true` and doing an operation within each `case` statement.

To make this easier to understand, we will use a familiar example. In the [conditional statements](https://www.digitalocean.com/community/tutorials/how-to-write-conditional-statements-in-javascript) tutorial, we made a grading app which would take a number score and convert it to a letter grade, with the following requirements.

- Grade of 90 and above is an **A**
- Grade of 80 to 89 is a **B**
- Grade of 70 to 79 is a **C**
- Grade of 60 to 69 is a **D**
- Grade of 59 or below is an **F**

Now we can write that as a `switch` statement. Since we’re checking a range, we will perform the operation in each `case` to check if each expression is evaluating to `true` then break out of the statement once the requirements for `true` have been satisfied.

grades.js

```jsx
// Set the student's grade
const grade = 87;

switch (true) {
	// If score is 90 or greater
	case grade >= 90:
		console.log("A");
		break;
	// If score is 80 or greater
	case grade >= 80:
		console.log("B");
		break;
	// If score is 70 or greater
	case grade >= 70:
		console.log("C");
		break;
	// If score is 60 or greater
	case grade >= 60:
		console.log("D");
		break;
	// Anything 59 or below is failing
	default:
		console.log("F");
}
```

```jsx
Output
'B'
```

The expression in parentheses to be evaluated is `true` in this example. This means that any `case` that evaluates to `true` will be a match.

Just like with `else if`, `switch` is evaluated from top to bottom, and the first true match will be accepted. Therefore, even though our `grade` variable is `87` and therefore evaluates to `true` for C and D as well, the first match is B, which will be the output.

### Multiple Cases

You may encounter code in which multiple cases should have the same output. In order to accomplish this, you can use more than one `case` for each block of code.

In order to test this, we are going to make a small application matching the current month to the appropriate season. First, we will use the `new Date()` method to find a number corresponding to the current month, and apply that to the `month` variable.

```jsx
const month = new Date().getMonth();
```

The `new Date().getMonth()` method will output a number from `0` to `11`, with `0` being January and `11` being December. At the time of this publication, the month is September, which will correspond to `8`.

Our application will output the four seasons with the following specifications for simplicity:

- **Winter**: January, February, and March
- **Spring**: April, May, and June
- **Summer**: July, August, and September
- **Autumn**: October, November, and December

Below is our code.

seasons.js

```jsx
// Get number corresponding to the current month, with 0 being January and 11 being December
const month = new Date().getMonth();

switch (month) {
	// January, February, March
	case 0:
	case 1:
	case 2:
		console.log("Winter");
		break;
	// April, May, June
	case 3:
	case 4:
	case 5:
		console.log("Spring");
		break;
	// July, August, September
	case 6:
	case 7:
	case 8:
		console.log("Summer");
		break;
	// October, November, December
	case 9:
	case 10:
	case 11:
		console.log("Autumn");
		break;
	default:
		console.log("Something went wrong.");
}
```

When we run the code, we’ll receive output identifying the current season based on the specifications above.

```jsx
Output
"Summer"
```

The current month at the time of publication was `8`, which corresponded to one of the `case` statements with the `"Summer"` season output.

## [Conditional operator ‘?’](https://javascript.info/ifelse#conditional-operator)

Sometimes, we need to assign a variable depending on a condition.

For instance:

```jsx
let accessAllowed;
let age = prompt('How old are you?', '');

*if (age > 18) {
  accessAllowed = true;
} else {
  accessAllowed = false;
}*alert(accessAllowed);
```

The so-called “conditional” or “question mark” operator lets us do that in a shorter and simpler way.

The operator is represented by a question mark `?`. Sometimes it’s called “ternary”, because the operator has three operands. It is actually the one and only operator in JavaScript which has that many.

The syntax is:

```jsx
let result = condition ? value1 : value2;
```

The `condition` is evaluated: if it’s truthy then `value1` is returned, otherwise – `value2`.

For example:

```jsx
let accessAllowed = (age > 18) ? true : false;
```

Technically, we can omit the parentheses around `age > 18`. The question mark operator has a low precedence, so it executes after the comparison `>`.

This example will do the same thing as the previous one:

```jsx
// the comparison operator "age > 18" executes first anyway
// (no need to wrap it into parentheses)
let accessAllowed = age > 18 ? true : false;
```

But parentheses make the code more readable, so we recommend using them.

**Please note:**

In the example above, you can avoid using the question mark operator because the comparison itself returns `true/false`:

```jsx
// the same
let accessAllowed = age > 18;
```

### [Multiple ‘?’](https://javascript.info/ifelse#multiple)

A sequence of question mark operators `?` can return a value that depends on more than one condition.

For instance:

```jsx
let age = prompt('age?', 18);

let message = (age < 3) ? 'Hi, baby!' :
  (age < 18) ? 'Hello!' :
  (age < 100) ? 'Greetings!' :
  'What an unusual age!';

alert( message );
```

It may be difficult at first to grasp what’s going on. But after a closer look, we can see that it’s just an ordinary sequence of tests:

1. The first question mark checks whether `age < 3`.
2. If true – it returns `'Hi, baby!'`. Otherwise, it continues to the expression after the colon ‘":"’, checking `age < 18`.
3. If that’s true – it returns `'Hello!'`. Otherwise, it continues to the expression after the next colon ‘":"’, checking `age < 100`.
4. If that’s true – it returns `'Greetings!'`. Otherwise, it continues to the expression after the last colon ‘":"’, returning `'What an unusual age!'`.

Here’s how this looks using `if..else`:

```jsx
if (age < 3) {
  message = 'Hi, baby!';
} else if (age < 18) {
  message = 'Hello!';
} else if (age < 100) {
  message = 'Greetings!';
} else {
  message = 'What an unusual age!';
}
```

### [Non-traditional use of ‘?’](https://javascript.info/ifelse#non-traditional-use-of)

Sometimes the question mark `?` is used as a replacement for `if`:

```jsx
let company = prompt('Which company created JavaScript?', '');

*(company == 'Netscape') ?
   alert('Right!') : alert('Wrong.');*
```

Depending on the condition `company == 'Netscape'`, either the first or the second expression after the `?` gets executed and shows an alert.

We don’t assign a result to a variable here. Instead, we execute different code depending on the condition.

**It’s not recommended to use the question mark operator in this way.**

The notation is shorter than the equivalent `if` statement, which appeals to some programmers. But it is less readable.

Here is the same code using `if` for comparison:

```jsx
let company = prompt('Which company created JavaScript?', '');

*if (company == 'Netscape') {
  alert('Right!');
} else {
  alert('Wrong.');
}*
```

Our eyes scan the code vertically. Code blocks which span several lines are easier to understand than a long, horizontal instruction set.

The purpose of the question mark operator `?` is to return one value or another depending on its condition. Please use it for exactly that. Use `if` when you need to execute different branches of code.
