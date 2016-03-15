# Comparing Python & Javascript Intro
# Chapter 2: More Fundamentals

In the previous chapter, we introduced the basics and fundamental concepts of both languages, such as variables, loops, conditionals, and functions.

In this chapter, more fundamentals will be introduced. Some of the concepts introduced won't get into much detail until later in the series. This chapter will serve an overview of the topics covered in detail throughout the series.

If you're new to either of the languages, take the time reviewing the concepts and code examples here in depth. Some concepts need to by reviewed multiple times to grasp.


TODO

## Values & Types

TODO


## Strict Mode

TODO:

This only applies to js, and not py

````js
"use strict";
````

ES5 added a "strict mode" to the language, which tightens the rules for certain behaviors. Generally, these restrictions are seen as keeping the code to a safer and more appropriate set of guidelines. Also, adhering to strict mode makes your code generally more optimizable by the engine. Strict mode is a big win for code, and you should use it for all your programs.

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


## Constructors

TODO

constructor  is a property of the internal prototype property, which could be overridden by code.


## Instance Of Comparison

TODO

isinstance in python

instanceof is another js operator that check in all the prototypes chain the constructor it returns true if it’s found and false if not.

```javascript
var arr = ["a", "b", "c"];
typeof arr;   // return "object" 
arr  instanceof Array // true
arr.constructor();  //[]
```

## Array Access

Getting a random element

js
```js
var items = [1,3,4,5,6];
var  randomItem = items[Math.floor(Math.random() * items.length)];
// specific range
var max = 10; var min = 1;
var x = Math.floor(Math.random() * (max - min + 1)) + min;
```

py
```
import random
items = [1,3,4,5,6]
random_item = random.choice(items)
# specific range
max, min = 10, 1
x = random.choice(range(min,max+1))
```

TODO:
## Lambda and Immediately Invoked Function Expression (IIFE)

js
```js
(function(a, b) {
  return a + b
})(1, 5);

This is as close as you can 
py
```
func = lambda x, y: x + y
func(1, 5)
