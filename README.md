JavaScript Arrow Functions
---

## Problem Statement

You're familiar by now with the standard style of declaring functions in
JavaScript.

```js
function foo() {
  return 'bar';
}
```

But JavaScript has two other ways to write functions that are common in
iteration and in writing event-handling code ("on click of this button, do
that"). This lesson will teach those styles before you learn advanced iteration
or event creation so that the syntax doesn't get in our way.

## Objectives

1. Declare a function using a function expression
2. Declare a function using an arrow function
3. Describe situations where arrow functions come in handy

## Declare a Function Using a Function Expression

Thus far we've only ever used a _function declaration_:

```js
function foo() {
  return 'bar';
}
```

A function can also be written:

```js
let foo = function() {
  return 'bar';
}
```

The `function() {...}` is called a _function expression_. The best way to
understand what a function expression is is by analogy.

```js
let sum = 1 + 1
```

EVALUATE the expression `1 + 1`, RETURNING `2` and ASSIGN it to the variable `sum`

```js
let difference = 10 - 1;
```

EVALUATE the expression `10 - 1`, RETURNING `9` and ASSIGN it to the variable
`difference`.

```js
let foo = function() {
  return 'bar';
}
```

EVALUATE the expression `function() { return 'bar' }`, RETURNING a thing that
can be called and ASSIGN it to the variable `foo`. Since `foo` holds a callable
thing, it can be called with `foo()`.

The function expression to the right of `=`  is known as "an anonymous
function." It doesn't have a name associated with it like you see in a
_function declaration_. However, when we assign an anonymous function to a name
(that is, a variable), we now have a "named function," a function that's no
longer anonymous.

There are a few subtle differences between _function declarations_ and
_function expressions_, but they are very minute. Neither is really better than
the other. JavaScript supports variety. Neither is better or more preferred
than the other.

## Declare a Function Using An Arrow Function

Around 2015, developers got tired of typing `f-u-n-c-t-i-o-n` over and over.
They lobbied the ECMAScipt body for a way to write functions in a very short
way. Here is the result, the "Arrow Function."

```js
let add = (param1, param2) => param1 + param2
add(2,3) //=> 5
```

Yes, this works! Really! This builds on the syntax of the named function we
just covered. `add` is the name to which the following _anonymous function_ is
assigned:

```js
(param1, param2) => param1 + param2
```

This is a very short function! It adds `param1` and `param2`, and, without any
braces, it **automatically** returns the result. Functions like this are very
common in JavaScript's advanced iterators that we'll cover in a future lesson.
If you have only _one_ parameter, JavaScript will even let you drop the `()`
around the parameter:

```js
let twoAdder = x => x + 2;
```

If we need to do more work than return a mere single expression, we'll need
`{}` to wrap the multiple lines of code **and** we'll have to declare a
`return`.

```js
let sum = (param1, param2) => {
  console.log(`Adding ${param1}`);
  console.log(`Adding ${param2}`);
  return param1 + param2;
}
sum(1,2) //=> 3
```

At this point one might debate whether the "arrow function" is better than the
"function expression." There's no solid answer here. Neither is "better" or
"best practice."

## Describe Situations Where Arrow Functions Come In Handy

In JavaScript, functions are 'first class objects'. They can be passed,
declared, handled, and have properties and methods just like any other object.
This is amazing and leads to some strange and beautiful code. Consider:

```js
const caller = fn = fn();
caller(() => console.log("What is the Matrix?"))
//=> LOG: What is the Matrix?
```

Whoa.

As a foreshadow of advanced iteration in JavaScipt, we'll show the `.map()`
function iterates through one `Array`, passes each element to a function that's
passed in as an argument, takes that functions return value, and stacks it into
a new array.

```js
const nums = [1,2,3];
const squares = nums.map( x => x ** 2);
const doubles = nums.map( x => x * 2);
```

If all this math stuff seems a bit too, textbook-y, realize that a similar
pattern could be done with DOM elements:

finishedItems = overdueTodoItems.map( item => item.className = "complete" );
header.innerText = `You fnished ${finishedItems.length} items!`;

Or billing software:

lapsedUserAccounts( u => sendBillTo(u.address) )

In subsequent lesson we'll show the power of arrow functions with certain
special iterators.

## Conclusion

In this lesson you saw two different styles for declaring functions: function
expressions and arrow functions. Neither is "better" than the standard function
declaration we've been using. Arrow functions excel when a simple change or
opration needs to be used repeatedly. But they're certainly used to write long,
full functions too!

## Resources

- [MDN: Arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

