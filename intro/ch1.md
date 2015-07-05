# Comparing Python to Javascript Intro
# Chapter 1: Basic Similarities

Welcome to the *Comparing Python to Javascript * (*CPTJ*) series.

*Intro* is an introduction to some of the most fundamental similarities (and differences) between the two languages.

Some of the comparisons are not exactly one-to-one since we are not comparing apples to apples at all times.  Some concepts are high level in nature and the implementation in each language varies.

The issues with JavaScript (js) is that it is built into a browser and the code one writes, must be compatible to run on older browsers as well.

Python (py) is used for server side programming so being aware of the version of Python you are using is important.  There is quite a distinction between Python 2 and 3.  We will discuss these differences as we come across them.

Lets jump right in...


### The Sandbox Environment

For running JavaScript code, we will use the *Chrome Browser's Developer Tools Console*.  There are many ways you can run JavaScript code such as from the *Node.js* (node) console but this is not as versatile and the assumption is made on running server-side code.

Lets stay on the client side for simplicity sake and not get into server side vs client side JavaScript code at this time.

Later on we may take a look at node and write some scripts that we can run from the terminal.

For running Python code, we will use the python console and at times write scripts we can run in the terminal. The version of python will be 2.7+ and python 3.x. Due to some differences in python 2.7.X and python 3.X, both code snippets will be illustrated when required, or an explanation of the differences will be noted as they come up.

For Python, you can also use IDLE (Integrated DeveLopment Environment), or iPython Notebook. When writing scripts, using an IDE like PyCharm will provide usable feedback and code completion as you write code.

Note that both JavaScript and Python can be compiled to *bytecode*, something we will explore later on.

At this point you should have a JavaScript console (Chrome Dev Tools) and Python console ready to go! Pick what you're comfortable with and lets go.


## Getting Help

In js, you can use online resources to get more information for whatever you are after:

* [Global Objects](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects)
* [Built in Functions](http://www.w3schools.com/jsref/jsref_obj_global.asp)
* [ES6 What's New](http://espadrine.github.io/New-In-A-Spec/es6/)

In py, you can also find very good resources, some to start:

* [Global Objects](https://docs.python.org/3/library/stdtypes.html)
* [Built in Functions](https://docs.python.org/3/library/functions.html)
* [Python 3 What's New](https://docs.python.org/3.0/whatsnew/3.0.html)

Use `help()` in the console to get documentation (doc) on almost anything e.g.

```python
help(input)
```

Use `dir()` in to get with an argument to get a list of valid attributes for that object.

```python
dir(input)
```

Note: Without arguments, return the list of names in the current local scope.


PEP 20 -- The Zen of Python
```python
import this
```

## Debugging your code

For js, use the "Sources" tab of "Developers Tools" to set Break Points in your code. In the "Console" set "preserve log" to view the output from when you reload the page.

This is advice for when your js code is served by a web server. For this book, you won't really need this.

For python, there are many options. Use of the *logging* module, use of *print* and the *pdb* (python debug module) are some of the basics you can use. Include  `import pdb; pdb.set_trace()` on the line where you want to set a break point and you will get a console when the line is executed. Run `continue` to exit the break point.

This advice is also for comparison purposes, we will not need it for this book.

There are many tools and libraries that can help you troubleshoot your code that are outside the scope of this book.


## Testing

Outside the scope of this book.  We may cover this in later books.


## Comments

In both languages, comments are best suited to describe why and how, instead of what is happening in the code.

In js, use `//` for single line comments, in py, use `#`.

Comments in js look like this:

```js
// This is a single-line comment

/* But this is
       a multiline
             comment.
                      */
```

The `//` single-line comment is appropriate if you're going to put a comment right above a single statement, or even at the end of a line. Everything on the line after the `//` is treated as the comment (and thus ignored by the compiler), all the way to the end of the line. There's no restriction to what can appear inside a single-line comment.

Consider:

```js
var a = 42;		// 42 is the meaning of life
```


In py, you can use triple-quoted strings as multi-line comments when they're not a docstring (first thing in a class/function/module), they are ignored.

```python
'''
This is a multi-line
comment.
'''
""" This is another one that can be a multi line but its not now """
```

In the console, these will be interpreted as strings if you try them out, so this only applies to code in a file.

It is also important to note that `docstring` is a special type of comment at the top of class/function/module that is used for built in documentation purposes, and testing using *doctest*.  This is out of scope of this book.

In js, multi-line comments can appear anywhere on a line, even in the middle of a line, because the `*/` ends it. For example:

```js
var a = /* arbitrary value */ 42;

console.log( a );	// 42
```

You can't do such a thing in python because the `"""` also means a multi line string. You can do something like this with it:

```python
x = """ This is a multi line
string
""" # x contains ' This is a multi line\nstring\n'
```

Best practice is to use # for all comments, and """ for docstrings and multi-line strings.


## Basic Output

Lets start with something really simple in both consoles to get started. In JavaScript:

```js
// a single-line comment

a = 21;

b = a * 2;

console.log( b );
```

And the same thing in Python:

```python
# a single-line comment
a = 21

b = a * 2

print(b)
```

The main difference in these statements is how output is handled.

In the JavaScript code you are logging the output to the console. In node, console.log is a wrapper around process.stdout.write, but lets not worry about node now.

There are two characteristics to explain in `console.log(..)`. The `log( b )` part is referred to as a function call. The `b` variable is being passed to that function log as a parameter, which becomes a local variable in that function and is printed to the screen.

The `console.` part is an object reference where the `log(..)` function is located. We will examine the differences between objects of the two languages at a later time.

Another way of creating output in js is the `alert(..)` statement. For example:

```js
alert( 'This is a test' );
```

This will pop up an alert in an alert box. We will stick to `console.log()` since it will not interfere with the browsers interface.

In Python you are using the print function (or statement in Python 2) to write to stdout. *print* is a wrapper around an objects write function and the default object is *sys.stdout*. So print will call sys.stdout.write by default and it also formats the input by putting a space between args and newline at the end.

So these are the same.

Python 2
```python
import sys
print 'hi'  # can also use print('hi')
print >> sys.stdout, 'hi'
```

Python 3
```python
import sys
print('hi')
print('hi', file=sys.stdout)
```

You can also import the python 3 function style *print* from futures and then your Python 3 code will run in Python2:

```python
from __future__ import print_function
# python 3 style code from above here ...
```

Lets see how we can use print with a file object instead:

```python
# Python 2
print >> open('file.txt', 'w'), 'Hello', 'World', 2+3

# Python 3
print('Hello', 'World', 2+3, file=open('file.txt', 'w'))
```

What was the output of file.txt? You can add '\n' for a new line character but notice print will add a space between each argument.

So as long as an object implements write, you can use it as the output file/object in your *print*.

That may be more than you need to know about print in python for now.



## Basic Input

In js, the most common way to get input is via HTML. An HTML page will show form elements (like text boxes) to a user that they can type into, and then using JS to read those values into your program's variables.

Lets use something simpler for this book, the `prompt(..)` function:

```js
num = prompt( "Please enter a number:" );

console.log( num );
```

In py, we can use either *input* or *raw_input*. Note that raw_input has been renamed to input in py 3 and the old input functionality is basically running `eval()` on your input.

Lets see py 2's input and raw_input differences:

```python
>>> x = input()
3+2
>>> x
5
>>> y = raw_input()
3+2
>>> y
'3+2'
```

As you can see, the py 2 input function evaluates the input which could be dangerous. Now in py 3:

```python
>>> x = input()
3+2
>>> x
'3+2'
>>> eval(x)
5
>>> y = raw_input()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'raw_input' is not defined
```

*input* also takes
In this book, we will not use these anymore.


## Operators

Here are some of the most common operators:

###Assignment

js:
```js
a = 3;
b = c = 4;
c = 2;
```

The exact thing can be done in py:
```python
a = 3
b = c = 4
c = 2
```

In both cases, b is now 4, but c is 2. The difference is that in python the variable gets attached to the current scope, while in js, without using the `var` to declare the variable, you are assigning it in the global scope. Adding `var` creates it in the current function scope ,e.g. `var a = 3;`. In py, if the variable is declared at the function level, it is in the functions local scope. If declared in a block but then re-used in the upper scope, it is best practice to declare it in the function before the block. There will be more on scope later on in the book.

Note that the use of semicolons is valid in py as well. So the above js example will execute same as py and js, and same goes with the py code. Best practice for python is not to use the semicolon, and for js it is best practice to do so.

By using the semicolon, you can combine many lines into one line. This is bad practice in python but it can be done:

js & py:
```python
a = 3; b = c = 4; c = 2
```

###Math

These will execute in both py and js:
```python
1 * 2
3 - 1
3 + 5
4 / 5
```

However, the result of `4/5` will vary depending on the py version. py 2 will return the int value since both 4 and 5 are ints, which will result in 0.

There is also something called floor division operator in py which always return the rounded down (floor) whole number i.e. `4//5` will return 0 in py 2 and py 3.

In js, you can take advantage of the *Math* object reference e.g. `Math.abs(-1)`

In py, you can also `import math` for some advanced math features.


To do power of in py, there are two basic ways:

```python
1 ** 3
# or
import math
math.pow(3,2)
```

Power of in js, you can do `Math.pow(3,2)`

###Compound Assignment

These will execute in both py and js:
```python
x = 5
x += 5
x -= 1
x *= 3
x /= 9
```
Notice the return type is different in py2 and py3, as py3 always returns float for division.

###Increment/Decrement:

Don't try these in py, they only work in js, e.g. `a++` or `a--`

In py, you have to do it the long way, `a+=1` which isn't all that bad.


###Object Property Access

 In js, `console.log()`.

 In py, `'str,str'.split()`.

###Comparison

 These are the same in both languages, `<` (less than), `>` (greater than), `<=` (less than or loose-equals), `>=` (greater than or loose-equals), as in `a <= b`.

###Equality

Things get interesting here as both languages handle equality a bit differently.


In js, its best practice to use strict equality when making comparisions unless you are comparing `typeof()`.


```js
0 == '0'  //true
0 === '0'  //false
0 == ''  //true
0 === '0' //false

1 === true //false
1 == true //true
0 == false //true
false == null //false
0 == !!(null) //true
```

Not equal
```js
1 != true //false
1 !== true //true
```


TODO: weird cases, on different sides of sign, where == returns true but != does not return false,  falsies .. truthies

In python, there is no loose or strict equality. For the most part it is pretty strict. You should be okay with Python's equality comparator as long as its clear to you that zero of any numeric type (0, 0L, 0.0, 0j) is always equal to False and 1 of any numeric type except complex numbers (1, 1L, 1.0) is True.

These are the only cases that return *True* when type is different:

```python
1 == True
1.0000000 == True
1L == True

0 == False
0.0 == False
0L == False
0j == False
```

###Logical & Bitwise And, Or


The idea here is the same in both languages, but syntax varies.

Bitwise applies only to diff when using boolean, bin, integer. The value is converted to binary, and bit evaluation is computed.

e.g. 0b1100100 & 0b1111101000 , same as 100 & 1000

js
```js
100 & 100;  // Bitwise AND
100 | 101;  // Bitwise OR
100 && 30;  // Logical AND
100 || 30;  // Logical OR
```

py
```python
100 & 100  # Bitwise AND
100 | 101  # Bitwise OR
100 and 30  # Logical AND
100 or 30  # Logical OR
```

Logical comparison (compound conditionals) short circuits as soon as it can (as soon as it establishes the result to be True or False).

Bitwise is a mathematical calculation between the two values.


## Variable Types & Values


JavaScript has built-in types for each of these so called *primitive* values:

* `number`.
* `string` (one or more characters, words, sentences).
* `boolean` (`true` or `false`).
* `date`
* `array`
* `object`
* `null`

Note `typeof` is a built in function in js, but `type` in py is the root `object` of all objects.

Python:

* Numbers: int, float, long, complex
* Sequences: str, unicode, list, tuple, bytearray, buffer, range
* Booleans: bool
* Sets: set, frozenset
* Mapping: dict
* Files: file
* None
* object
* type

There are other types in py that will not be covered here.

Literals are the same in both languages. `string` literals are surrounded by double quotes `"..."` or single quotes (`'...'`) its a preference in both languages.


### Converting Between Types

Converting numbers

js
```js
var a = "42";
var b = Number( a );

console.log( a );	// "42"
console.log( b );	// 42
```

py
```python
a = "42"
b = int(a)  # can cast to float, complex, int, long etc..

print(a) #  "42"
print(b) #  42
```

There is no implicit coercion in py, something that one would have to check explicitly by casting values to the same type.

## Variables

Both py and js use *dynamic typing*, meaning variables can hold values of any *type* without any *type* enforcement. There there's no other *type* information in the declaration.

In js, you declare a variable using the `var`, without the var statement the variable is decalred in the global scope.

```js
var price = 199.98;
console.log( price );		// 199.98 (implicit coercion)
var amount = "$" + String( price.toFixed(2) );
console.log( amount );		// "$199.98" (explicit coercion)
```

Same in py,
```python
price = 199.98;
print(price)		# 199.98 (implicit coercion)
amount = "$" + str(round(price, 2));
print(amount)		# "$199.98" (explicit coercion)
```

But no `var` is required in py, it creates the local variable in your current scope (method,function,global scope).

You can check what is available in globals and locals by running:
```python
globals()
locals()
```

In the top scope, they should return the same, i.e. `locals() == globals()`


*constant* declaration is:

js
```js
var TAX_RATE = 0.08;	// 8% sales tax
```

The newest version of JavaScript at the time of this writing (commonly called "ES6") includes a new way to declare *constants*, by using `const` instead of `var`:

```js
// as of ES6:
const TAX_RATE = 0.08;
```

py
```python
TAX_RATE = 0.08	# 8% sales tax
```


## Strict Mode

TODO:

This only applies to js, and not py

````js
"use strict";
````

ES5 added a "strict mode" to the language, which tightens the rules for certain behaviors. Generally, these restrictions are seen as keeping the code to a safer and more appropriate set of guidelines. Also, adhering to strict mode makes your code generally more optimizable by the engine. Strict mode is a big win for code, and you should use it for all your programs.


## Blocks

js supports this idea of general blocks but it is not commonly used:

```js
var amount = 99.99;
// a general block
{
	amount = amount * 2;
	console.log( amount );	// 199.98
}
```

Typically, blocks are attached to some other control statement, such as an `if` statement or a loop e.g.

```js
var amount = 99.99;
// is amount big enough?
if (amount > 10) {			// <-- block attached to `if`
	amount = amount * 2;
	console.log( amount );	// 199.98
}
```

A closure
```js
x = function(val){console.log(Math.pow(val,2)+5)}
x(3)
```

A block statement does not need a semicolon (`;`) to conclude it.


In py, an if block looks like so, and proper indentation of the same length is required:

```python
amount = 99.99
# is amount big enough?
if amount > 10:  # block indented below
	amount *= 2
	print(amount)
```

In py, the idea of blocks translates to anonymous functions/closures:

```python
f =lambda x: x**2 + 5
#is equivalent to
def f(x): return x**2 + 5
# and can be used as
f(3)
```

Indentation can be using tabs or spaces. Four spaces is a best practice, but varies for continuations, usually aligned with the parentheses etc..

## Conditionals

In both languages, an expression to evaluate to true or false is required.

js
```js
var bank_balance = 302.13;
var amount = 99.99;
if (amount < bank_balance) {
	console.log( "I want to buy this phone!" );
}
else if (amount == blank_balance){
    console.log( "I barely got enough!"
}
else{
    console.log("I can't afford it.");
}
```
JavaScript defines a list of specific values that are considered "falsy" because when coerced to a `boolean`, they become `false` -- these include values like `0` and `""`. Any other value not on the "falsy" list is automatically "truthy" -- when coerced to a `boolean` they become `true`.

js implements a `switch` statement can be used as a shorthand for a series of `if..else` statements, py does not have a switch/case.

```js
switch (a) {
    case 2:
        // do something
        break;
    case 10:
        // do another thing
        break;
    case 42:
        // do yet another thing
        break;
    default:
        // fallback to here
}
```
The break is important if you want only the statement(s) in one case to run. If you omit break from a case, and that case matches or runs, execution will continue with the next case's statements regardless of that case matching. This so called "fall through" is sometimes useful/desired.


python, if statement
```python
bank_balance = 302.13
amount = 99.99
if (amount < bank_balance):
    print("I want to buy this phone!")
elif (amount == blank_balance):
    print("I barely got enough!")
else:
    print("I can't afford it.")
```

In both languages, f you pass it something that's not already `boolean`, coercion will occur.


## Loops


while & do while in js
```js
var numOfCustomers = 3;

while (numOfCustomers > 0) {
	console.log( "How may I help you?" );

	// help the customer...

	numOfCustomers = numOfCustomers - 1;
}

// versus:

var numOfCustomers = 3;

do {
	console.log( "How may I help you?" );

	// help the customer...

	numOfCustomers = numOfCustomers - 1;
} while (numOfCustomers > 0);
```


while & do while in python, py does not support a do while but one can be simulated
```python
no_of_customers = 3

while no_of_customers > 0:
    print( "How may I help you?" )
    # help the customer...
    no_of_customers -= 1;

# versus:

no_of_customers = 3

def help_customer(no_of_customers):  # condition is a function
    print("How may I help you?")
	# help the customer...
    return no_of_customers - 1

no_of_customers = help_customer(no_of_customers)  # Run condition first

while (no_of_customers > 0):
    no_of_customers = help_customer(no_of_customers)
```


A forever loop, but it does break out:

```js
var i = 0;

// a forever loop with a break condition
while (true) {
	// stop the loop?
	if ((i <= 9) === false) {
		break;
	}

	console.log( i );
	i = i + 1;
}
// 0 1 2 3 4 5 6 7 8 9
```

py
```python
i = 0

# a forever loop with a break condition
while True:
    # stop the loop?
    if ((i <= 9) == False):
        break;

    print(i)
    i += 1

# 0 1 2 3 4 5 6 7 8 9
```


for loop in js
```js
for (var i = 0; i <= 9; i = i + 1) {
	console.log( i );
}
// 0 1 2 3 4 5 6 7 8 9
```

for loop in py
```python
for i in range(10):
    print(i)

# 0 1 2 3 4 5 6 7 8 9
```

## Functions

js
```js
function printAmount(amt) {
	console.log( amt.toFixed( 2 ) );
}

function formatAmount() {
	return "$" + amount.toFixed( 2 );
}

var amount = 99.99;

printAmount( amount * 2 );		// "199.98"

amount = formatAmount();
console.log( amount );			// "$99.99"
```

py
```python
def print_amount(amt):
    print(round(amt, 2))

def format_amount():
    return "$" + round(amount, 2)

amount = 99.99

print_amount(amount * 2)		# "199.98"

amount = format_amount()
print(amount)			# "$99.99"
```


### Scope

*lexical scope*, in JavaScript, each function gets its own scope, aka. "scoped" variables are local to the scope.

js
```js
function one() {
	// this `a` only belongs to the `one()` function
	var a = 1;
	console.log( a );
}

function two() {
	// this `a` only belongs to the `two()` function
	var a = 2;
	console.log( a );
}

one();		// 1
two();		// 2
```

py
```python
def one():
    #this `a` only belongs to the `one()` function
    a = 1
    print(a)

def two():
    #this `a` only belongs to the `two()` function
    a = 2
    print(a)

one() #  1
two() #  2
```

js, nested scopes
```js
function outer() {
	var a = 1;

	function inner() {
		var b = 2;

		// we can access both `a` and `b` here
		console.log( a + b );	// 3
	}

	inner();

	// we can only access `a` here
	console.log( a );			// 1
}

outer();
```


py, nested scopes
```python
def outer():
    a = 1;
    def inner():
        b = 2
        # we can access both `a` and `b` here
        print(a + b)  # 3
    inner()

    # we can only access `a` here
	print(a)  # 1

outer()
```


## Example Program


```js
const SPENDING_THRESHOLD = 200;
const TAX_RATE = 0.08;
const PHONE_PRICE = 99.99;
const ACCESSORY_PRICE = 9.99;

var bank_balance = 303.91;
var amount = 0;

function calculateTax(amount) {
	return amount * TAX_RATE;
}

function formatAmount(amount) {
	return "$" + amount.toFixed( 2 );
}

// keep buying phones while you still have money
while (amount < bank_balance) {
	// buy a new phone!
	amount = amount + PHONE_PRICE;

	// can we afford the accessory?
	if (amount < SPENDING_THRESHOLD) {
		amount = amount + ACCESSORY_PRICE;
	}
}

// don't forget to pay the government, too
amount = amount + calculateTax( amount );

console.log(
	"Your purchase: " + formatAmount( amount )
);
// Your purchase: $334.76

// can you actually afford this purchase?
if (amount > bank_balance) {
	console.log(
		"You can't afford this purchase. :("
	);
}
// You can't afford this purchase. :(
```


```python
SPENDING_THRESHOLD = 200
TAX_RATE = 0.08
PHONE_PRICE = 99.99
ACCESSORY_PRICE = 9.99

bank_balance = 303.91
amount = 0

def calculate_tax(amount):
    return amount * TAX_RATE;

def format_amount(amount):
    return "$" + round(amount, 2 )

# keep buying phones while you still have money
while (amount < bank_balance):
    # buy a new phone!
    amount = amount + PHONE_PRICE
    # can we afford the accessory?
    if (amount < SPENDING_THRESHOLD):
        amount = amount + ACCESSORY_PRICE

# don't forget to pay the government, too
amount = amount + calculate_tax(amount)

print("Your purchase: {}".format(format_amount(amount))

#Your purchase: $334.76

#can you actually afford this purchase?
if (amount > bank_balance):
    print("You can't afford this purchase. :(")

# You can't afford this purchase. :(
```


## Objects - Methods, Properties, & Attributes

Methods are just functions that belong to an object. They differ from functions because they have access to the objects scope and they are implicitly passed for the object for which it was called.

In js,

TODO

In py, attributes of an object include attributes, properties (special attributes) and methods:
```python
>>> class tester(object):
...     foo = 1 # normal attribute
...     @property
...     def p1(self):
...         return 'a property'
...     def f1(self):
...         return 'a function'
...
>>> t = tester()
>>> dir(t)
['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'f1', 'p1']
```

Properties are called without any parentheses so you cannot pass parameters to them. The return type is not function, but what the property returns:
```python
>>> t.p1
'a property'
>>> t.f1
<bound method tester.f1 of <__main__.tester object at 0x103905908>>
>>> t.f1()
'a function'
>>> t.p1()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object is not callable
```

Notice `t.f1` returns the method.

py 2 and py 3 object class slightly differ as one can see when examining them using `dir(object)`.


In general speaking terms a property and an attribute are the same thing. There is a property decorator in py which provides getter/setter access to an attribute (or other data).
```python
class MyObject(object):
    # This is a normal attribute
    foo = 1
    @property
    def bar(self):
        return self.foo
    @bar.setter
    def bar(self, value):
        self.foo = value

obj = MyObject()
assert obj.foo == 1
assert obj.bar == obj.foo
obj.bar = 2
assert obj.foo == 2
assert obj.bar == obj.foo
```

## Review


Most of the fundamentals of both languages were covered, including:

TODO


* Comments
* Input
* Output
* Operators
* Variables
* Blocks
* Conditionals
* Functions
* Loops
* Scope
* Example
