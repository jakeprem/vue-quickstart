# ES6 Syntax
A collection of ES6 features that might be unusual if you've mostly worked with older Javascript

## Spread Operator
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax

## Object Shorthands
### Properties
A shortcut for assigning variables to object properties when you're assigning variables to an object property with the same name.  
```javascript
let name = 'Jake'
let language = 'Javascript'

let obj = {
  name,
  language
}
// is equivalent to
obj = {
  name: name,
  language: language
}
```
### Method names
A shorthand for defining methods on an object.
```javascript
let obj = {
  doTheThing() {
    // Method implmentation
  },
  // is equivalent to
  doTheOtherThing: function() {
    // Method implementation
  }
}
```
### Computed property names
Let's you set a property name that will be determined by a variable or expression at runtime.
```javascript
let propName = 'TheThing'

var obj = {
  [propName]: 'The key for this property will be "TheThing"',
  ['Also' + propName]: 'The key for this property will be "AlsoTheThing"',
  ['do' + propName]() {
    // This is the doTheThing function
  }
}

obj.TheThing
obj.AlsoTheThing
obj.doTheThing()
```
(https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#New_notations_in_ECMAScript_2015)

## let and const
### let
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let
### const
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const

## Arrow functions
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions

## Object Destructuring
This is probably the most complicated thing on this page. The way we use it in Vue is pretty straight forward though.
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment

## Export and Import
### Export
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export

### Import
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import

## Template Literals
A way to do string interpolation.

Uses `` ` `` (backticks) as quotes.  
Instances of `${...}` will be evaluated as an expression and inserted into the string (e.g. a variable will have its value inserted).  

```javascript
let firstName = 'Jake'
let jsVersion = 'ES6'

let greeting = `Hello ${firstName}! Welcome to ${jsVersion}.`
```
Is equivalent to
```
var firstName = 'Jake'
var jsVersion = 'ES5'

var greeting = 'Hello ' + firstName + '! Welcome to ' + jsVersion + '!'
```
(https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)