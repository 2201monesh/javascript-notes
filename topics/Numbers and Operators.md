![https://miro.medium.com/max/1400/1*KEQpF2Ud3D9yfNKmaBgD9A.jpeg](https://miro.medium.com/max/1400/1*KEQpF2Ud3D9yfNKmaBgD9A.jpeg)

### [Terms: “unary”, “binary”, “operand”](https://javascript.info/operators#terms-unary-binary-operand)

Before we move on, let’s grasp some common terminology.

- *An operand* – is what operators are applied to. For instance, in the multiplication of `5 * 2` there are two operands: the left operand is `5` and the right operand is `2`. Sometimes, people call these “arguments” instead of “operands”.
- An operator is *unary* if it has a single operand. For example, the unary negation `` reverses the sign of a number:
    
    ```jsx
    let x = 1;
    
    *x = -x;*alert( x ); // -1, unary negation was applied
    ```
    
- An operator is *binary* if it has two operands. The same minus exists in binary form as well:
    
    ```jsx
    let x = 1, y = 3;
    alert( y - x ); // 2, binary minus subtracts values
    ```
    
    Formally, in the examples above we have two different operators that share the same symbol: the negation operator, a unary operator that reverses the sign, and the subtraction operator, a binary operator that subtracts one number from another.
    

# NUMBERS

JavaScript has only one type of number. Numbers can be written with or without decimals.

```jsx
let x = 3.14;    // A number with decimalslet 
y = 3;       // A number without decimals
```

Extra large or extra small numbers can be written with scientific (exponent) notation:

```jsx
let x = 123e5;    // 12300000
let y = 123e-5;   // 0.00123
```

## Integer Precision

Integers (numbers without a period or exponent notation) are accurate up to 15 digits.

Example

```jsx
let x = 999999999999999;   // x will be 999999999999999
let y = 9999999999999999;  // y will be 10000000000000000
```

The maximum number of decimals is 17.

### Floating Precision

Floating point arithmetic is not always 100% accurate:

`let x = 0.2 + 0.1;`

To solve the problem above, it helps to multiply and divide:

`let x = (0.2 * 10 + 0.1 * 10) / 10;`

### NaN - Not a Number

`NaN` is a JavaScript reserved word indicating that a number is not a legal number.

Trying to do arithmetic with a non-numeric string will result in `NaN` (Not a Number)

```jsx

let x = 100 / "Apple";// = Nan

// However, if the string contains a numeric value, the result will be a number:
let x = 100 / "10"; // = 10

```

If you use `NaN` in a mathematical operation, the result will also be `NaN`

NaN can also be concatenated with string. 

### Infinity

`Infinity` (or `-Infinity`) is the value JavaScript will return if you calculate a number outside the largest possible number.

Division by 0 (zero) also generates `Infinity`

### Hexadecimal

JavaScript interprets numeric constants as hexadecimal if they are preceded by 0x.

<aside>
⚠️ Never write a number with a leading zero (like 07).

Some JavaScript versions interpret numbers as octal if they are written with a leading zero.

</aside>

By default, JavaScript displays numbers as **base 10** decimals.

But you can use the `toString()` method to output numbers from **base 2** to **base 36**.

<aside>
ℹ️ Hexadecimal is **base 16**. Decimal is **base 10**. Octal is **base 8**. Binary is **base 2**.

</aside>

---

# Operators

### Operators and Operands

The numbers (in an arithmetic operation) are called **operands**.

The operation (to be performed between the two operands) is defined by an **operator**.

**There are different types of JavaScript operators:**

- Arithmetic Operators.
- Assignment Operators.
- Comparison Operators.
- Logical Operators.
- Conditional Operators.
- Type Operators.

## Arithmetic Operators

Arithmetic operators perform arithmetic on numbers (literals or variables).

```jsx
let x = 5;
let y = 2;
```

| Operator | Description | Usage |
| --- | --- | --- |
| + | Addition | let z = x + y; = 7 |
| - | Subtraction | let z = x - y; = 3 |
| * | Multiplication | let z = x * y; = 10 |
| ** | Exponentiation (ES2016) | let z = x ** y; = 25
x ** y produces the same result as Math.pow(x,y) |
| / | Division | let z = x / y; = 2.5 |
| % | Modulus (Remainder) | let z = x % y; = 1 |
| ++ | Increment | x++;
let z = x; = 6 |
| -- | Decrement | x--;
let z = x; = 4 |

### Operator Precedence

Operator precedence describes the order in which operations are performed in an arithmetic expression.

Multiplication (*) and division (/) have higher precedence than addition (+) and subtraction (-).

When using parentheses () , the operations inside the parentheses are computed first. Expressions in parentheses are fully computed before the value is used in the rest of the expression.

<aside>
ℹ️ When many operations have the same precedence (like addition and subtraction), they are computed from left to right.

</aside>

<aside>
⚠️ **JavaScript uses the + operator for both addition and concatenation.**

Numbers are added. Strings are concatenated.

JavaScript strings can have numeric content. JavaScript will try to convert strings to numbers in all numeric operations.

```jsx
let x = "100";
let y = "10";
let z = x / y; // 10
let z = x * y; // 1000
let z = x - y; // 90

*let z = **x + y**; // THIS WILL NOT WORK*
```

If you add two strings, the result will be a string concatenation.

If you add a number and a string or a string and a number, the result will be a string concatenation.

👉 **The JavaScript interpreter works from left to right.**

```jsx
let x = 10;
let y = 20;
let z = "30";
let result = x + y + z; // Result is => 3030
```

First 10 + 20 is added because x and y are both numbers.

Then 30 + "30" is concatenated because z is a string.

```jsx
let x = 10;
let y = 20;
let z = "The result is: " + x + y; // Result is => The result is: 1020
```

First "The result is: " + 10 is concatenated because "The result is: " is a string.

Then 20 (y) is also concantenated.

</aside>

## Assignment Operators

Assignment operators assign values to JavaScript variables.

| Operator | Example | Same As |
| --- | --- | --- |
| = | x = y | x = y |
| += | x += y | x = x + y |
| -= | x -= y | x = x - y |
| *= | x *= y | x = x * y |
| /= | x /= y | x = x / y |
| %= | x %= y | x = x % y |
| **= | x **= y | x = x ** y |
- Double equals (`==`) will perform a type conversion when comparing two things, and will handle `NaN`, `0`, and `+0` specially to conform to IEEE 754 (so `NaN != NaN`, and `0 == +0`);
- Triple equals (`===`) will do the same comparison as double equals (including the special handling for `NaN`, `0`, and `+0`) but without type conversion; if the types differ, `false` is returned.

`**==` →** compare the only DATA , not TYPE

→ `0(int) == "0"(string))` ⇒ true (not checking DATATYPE)

**`===`** compare strictly  DATA and TYPE

→ `0 === "0"` ⇒ false (checking the DATATYPE first)

```jsx
0 == false   // true
0 === false  // false, because they are of a different type
1 == "1"     // true, automatic type conversion for value only
1 === "1"    // false, because they are of a different type
null == undefined // true
null === undefined // false
'0' == false // true
'0' === false // false
```

### Shift Assignment Operators

| Operator | Example | Same As |
| --- | --- | --- |
| <<= | x <<= y | x = x << y |
| >>= | x >>= y | x = x >> y |
| >>>= | x >>>= y | x = x >>> y |

### Logical Assignment Operators

| Operator | Example | Same As |
| --- | --- | --- |
| &= | x &= y | x = x & y |
| ^= | x ^= y | x = x ^ y |
| |= | x |= y | x = x | y |

## Comparison Operators

Comparison and Logical operators are used to test for `true` or `false`.

Comparison operators are used in logical statements to determine equality or difference between variables or values.

Given that `x = 5`, the table below explains the comparison operators:

| Operator | Description | Comparing | Returns |
| --- | --- | --- | --- |
| == | equal to | x == 8
x == 5
x == "5" | false
true
true |
| === | equal value and equal type | x === 5
x === "5" | true
false |
| != | not equal | x != 8 | true |
| !== | not equal value or not equal type | x !== 5
x !== "5"
x !== 8 | false
true
true |
| > | greater than | x > 8 | false |
| < | less than | x < 8 | true |
| >= | greater than or equal to | x >= 8 | false |
| <= | less than or equal to | x <= 8 | true |

We know many comparison operators from maths.

In JavaScript they are written like this:

- Greater/less than: `a > b`, `a < b`.
- Greater/less than or equals: `a >= b`, `a <= b`.
- Equals: `a == b`, please note the double equality sign `==` means the equality test, while a single one `a = b` means an assignment.
- Not equals: In maths the notation is `≠`, but in JavaScript it’s written as `a != b`.

### [Boolean is the result](https://javascript.info/comparison#boolean-is-the-result)

All comparison operators return a boolean value:

- `true` – means “yes”, “correct” or “the truth”.
- `false` – means “no”, “wrong” or “not the truth”.

For example:

```jsx
alert( 2 > 1 );  // true (correct)
alert( 2 == 1 ); // false (wrong)
alert( 2 != 1 ); // true (correct)
```

A comparison result can be assigned to a variable, just like any value:

```jsx
let result = 5 > 4; // assign the result of the comparison
alert( result ); // true
```

### [String comparison](https://javascript.info/comparison#string-comparison)

To see whether a string is greater than another, JavaScript uses the so-called “dictionary” or “lexicographical” order.

In other words, strings are compared letter-by-letter.

For example:

```jsx
alert( 'Z' > 'A' ); // true
alert( 'Glow' > 'Glee' ); // true
alert( 'Bee' > 'Be' ); // true
```

The algorithm to compare two strings is simple:

1. Compare the first character of both strings.
2. If the first character from the first string is greater (or less) than the other string’s, then the first string is greater (or less) than the second. We’re done.
3. Otherwise, if both strings’ first characters are the same, compare the second characters the same way.
4. Repeat until the end of either string.
5. If both strings end at the same length, then they are equal. Otherwise, the longer string is greater.

In the first example above, the comparison `'Z' > 'A'` gets to a result at the first step.

The second comparison `'Glow'` and `'Glee'` needs more steps as strings are compared character-by-character:

1. `G` is the same as `G`.
2. `l` is the same as `l`.
3. `o` is greater than `e`. Stop here. The first string is greater.

**Not a real dictionary, but Unicode order**

The comparison algorithm given above is roughly equivalent to the one used in dictionaries or phone books, but it’s not exactly the same.

For instance, case matters. A capital letter `"A"` is not equal to the lowercase `"a"`. Which one is greater? The lowercase `"a"`. Why? Because **the lowercase character has a greater index in the internal encoding table JavaScript uses** (Unicode). We’ll get back to specific details and consequences of this in the chapter [Strings](https://javascript.info/string).

### [Comparison of different types](https://javascript.info/comparison#comparison-of-different-types)

When comparing values of different types, JavaScript converts the values to numbers.

For example:

```jsx
alert( '2' > 1 ); // true, string '2' becomes a number 2
alert( '01' == 1 ); // true, string '01' becomes a number 1
```

For boolean values, `true` becomes `1` and `false` becomes `0`.

For example:

```jsx
alert( true == 1 ); // true
alert( false == 0 ); // true
```

**A funny consequence**

It is possible that at the same time:

- Two values are equal.
- One of them is `true` as a boolean and the other one is `false` as a boolean.

For example:

```jsx
let a = 0;
alert( Boolean(a) ); // false

let b = "0";
alert( Boolean(b) ); // true

alert(a == b); // true!
```

From JavaScript’s standpoint, this result is quite normal. An equality check converts values using the numeric conversion (hence `"0"` becomes `0`), while the explicit `Boolean` conversion uses another set of rules.

## **Logical operators**

There are four logical operators in JavaScript: `||` (OR), `&&` (AND), `!` (NOT), `??` (Nullish Coalescing).

# [|| (OR)](https://javascript.info/logical-operators#or)

The “OR” operator is represented with two vertical line symbols:

`result = a || b;`

In classical programming, the logical OR is meant to manipulate boolean values only. If any of its arguments are `true`, it returns `true`, otherwise it returns `false`.

In JavaScript, the operator is a little bit trickier and more powerful. But first, let’s see what happens with boolean values.

There are four possible logical combinations:

```jsx
alert( true || true );   // true
alert( false || true );  // true
alert( true || false );  // true
alert( false || false ); // false
```

As we can see, the result is always `true` except for the case when both operands are `false`.

If an operand is not a boolean, it’s converted to a boolean for the evaluation.

For instance, the number `1` is treated as `true`, the number `0` as `false`:

```jsx
if (1 || 0) { // works just like if( true || false )
  alert( 'truthy!' );
}
```

Most of the time, OR `||` is used in an `if` statement to test if *any* of the given conditions is `true`.

For example:

```jsx
let hour = 9;

*if (hour < 10 || hour > 18) {*alert( 'The office is closed.' );
}
```

We can pass more conditions:

```jsx
let hour = 12;
let isWeekend = true;

if (hour < 10 || hour > 18 || isWeekend) {
  alert( 'The office is closed.' ); // it is the weekend
}
```

### [OR "||" finds the first truthy value](https://javascript.info/logical-operators#or-finds-the-first-truthy-value)

- The logic described above is somewhat classical. Now, let’s bring in the “extra” features of JavaScript.
    
    The extended algorithm works as follows.
    
    Given multiple OR’ed values:
    
    `result = value1 || value2 || value3;`
    
    The OR `||` operator does the following:
    
    - Evaluates operands from left to right.
    - For each operand, converts it to boolean. If the result is `true`, stops and returns the original value of that operand.
    - If all operands have been evaluated (i.e. all were `false`), returns the last operand.
    
    A value is returned in its original form, without the conversion.
    
    In other words, a chain of OR `||` returns the first truthy value or the last one if no truthy value is found.
    
    For instance:
    
    ```jsx
    alert( 1 || 0 ); // 1 (1 is truthy)
    
    alert( null || 1 ); // 1 (1 is the first truthy value)
    alert( null || 0 || 1 ); // 1 (the first truthy value)
    
    alert( undefined || null || 0 ); // 0 (all falsy, returns the last value)
    ```
    
    - This leads to some interesting usage compared to a “pure, classical, boolean-only OR”.
        1. **Getting the first truthy value from a list of variables or expressions.**
            
            For instance, we have `firstName`, `lastName` and `nickName` variables, all optional (i.e. can be undefined or have falsy values).
            
            Let’s use OR `||` to choose the one that has the data and show it (or `"Anonymous"` if nothing set):
            
            ```jsx
            let firstName = "";
            let lastName = "";
            let nickName = "SuperCoder";
            
            *alert( firstName || lastName || nickName || "Anonymous"); // SuperCoder*
            ```
            
            If all variables were falsy, `"Anonymous"` would show up.
            
        2. **Short-circuit evaluation.**
            
            Another feature of OR `||` operator is the so-called “short-circuit” evaluation.
            
            It means that `||` processes its arguments until the first truthy value is reached, and then the value is returned immediately, without even touching the other argument.
            
            The importance of this feature becomes obvious if an operand isn’t just a value, but an expression with a side effect, such as a variable assignment or a function call.
            
            In the example below, only the second message is printed:
            
            ```jsx
            *true* || alert("not printed");
            *false* || alert("printed");
            ```
            
            In the first line, the OR `||` operator stops the evaluation immediately upon seeing `true`, so the `alert` isn’t run.
            
            Sometimes, people use this feature to execute commands only if the condition on the left part is falsy.
            

<aside>
ℹ️ **Precedence of AND `&&` is higher than OR `||`**

The precedence of AND `&&` operator is higher than OR `||`.

So the code `a && b || c && d` is essentially the same as if the `&&` expressions were in parentheses: `(a && b) || (c && d)`.

</aside>

# [&& (AND)](https://javascript.info/logical-operators#and)

The AND operator is represented with two ampersands `&&`:

`result = a && b;`

In classical programming, AND returns `true` if both operands are truthy and `false` otherwise:

```jsx
alert( true && true );   // true
alert( false && true );  // false
alert( true && false );  // false
alert( false && false ); // false
```

An example with `if`:

```jsx
let hour = 12;
let minute = 30;

if (hour == 12 && minute == 30) {
  alert( 'The time is 12:30' );
}
```

Just as with OR, any value is allowed as an operand of AND:

```jsx
if (1 && 0) { // evaluated as true && false
  alert( "won't work, because the result is falsy" );
}
```

### [AND “&&” finds the first falsy value](https://javascript.info/logical-operators#and-finds-the-first-falsy-value)

- Given multiple AND’ed values:
    
    `result = value1 && value2 && value3;`
    
    The AND `&&` operator does the following:
    
    - Evaluates operands from left to right.
    - For each operand, converts it to a boolean. If the result is `false`, stops and returns the original value of that operand.
    - If all operands have been evaluated (i.e. all were truthy), returns the last operand.
    
    In other words, AND returns the first falsy value or the last value if none were found.
    
    The rules above are similar to OR. The difference is that AND returns the first *falsy* value while OR returns the first *truthy* one.
    
    Examples:
    
    ```jsx
    // if the first operand is truthy,
    // AND returns the second operand:
    alert( 1 && 0 ); // 0
    alert( 1 && 5 ); // 5
    
    // if the first operand is falsy,
    // AND returns it. The second operand is ignored
    alert( null && 5 ); // null
    alert( 0 && "no matter what" ); // 0
    ```
    
    We can also pass several values in a row. See how the first falsy one is returned:
    
    ```jsx
    alert( 1 && 2 && null && 3 ); // null
    
    // When all values are truthy, the last value is returned:
    alert( 1 && 2 && 3 ); // 3, the last one
    ```
    

# [! (NOT)](https://javascript.info/logical-operators#not)

The boolean NOT operator is represented with an exclamation sign `!`.

The syntax is pretty simple:

`result = !value;`

The operator accepts a single argument and does the following:

1. Converts the operand to boolean type: `true/false`.
2. Returns the inverse value.

For instance:

```jsx
alert( !true ); // false
alert( !0 ); // true
```

**A double NOT `!!` is sometimes used for converting a value to boolean type:**

```jsx
alert( !!"non-empty string" ); // true
alert( !!null ); // false
```

That is, the first NOT converts the value to boolean and returns the inverse, and the second NOT inverses it again. In the end, we have a plain value-to-boolean conversion.

There’s a little more verbose way to do the same thing – a built-in `Boolean` function:

```jsx
alert( Boolean("non-empty string") ); // true
alert( Boolean(null) ); // false
```

<aside>
ℹ️ The precedence of NOT `!` is the highest of all logical operators, so it always executes first, before `&&` or `||`.

</aside>
