# ES6 Syntax
A collection of ES6 features that might be unusual if you've mostly worked with older Javascript

  * [Spread Operator](#spread-operator)
  * [Object Shorthand](#object-shorthands)
  * [let and const](#let-and-const)
  * [Arrow functions](#arrow-functions)
  * [Object Destructuring](#object-destructuring)
  * [Export and Import](#export-and-import)
  * [Template Literals](#template-literals)

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
Similar to Python Lambdas and C# LINQ expressions.

A shorthand for declaring Javascript functions. 
```javascript
// One line arrow functions have an implicit return, i.e. the result of the expression will be returned
let doTheThing = (firstname, lastname) => firstname + lastname

doTheThing = () => 'Whatever'
doTheThing = _ => 'Whatever'
doTheThing = param1 => param1.name
doTheThing = aParam => {
  let bReturn = aParam * 2
  return bReturn
}
// Usage on object methods is not recommended in normal Javascript but okay in Vue/Vuex
// Related to potential confusion with binding 'this'
const getters = {
  fullname: state => state.firstname + state.lastname
}
```
Be mindful of your `{}` and `()` if you're doing a one liner with implicit return.
```javascript
// The brackets here get interpreted as block brackets not object brackets
let doTheThing = (firstname, lastname) => { fullname: firstname + lastname }
```

Unlike other Javascript functions, arrow functions don't bind `this`. This is less relevant when dealing with functions on Vue objects, e.g. in the `methods` property since Vue binds this for us behind the scenes. If we end up using prototypes or other forms of `this` in our library code then it might be relevant.

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions

## Object Destructuring
Pull properties out of objects.

This is an example of what you might see in Vuex. When Vuex calls an action method, the first parameter is a context object (https://vuex.vuejs.org/en/actions.html).  
The context object has all of the vuex modules properties and commit (`commit`, `state`, `getters`, and `actions`)
```javascript
const actions = {
  doTheThing({ commit }) {
    // The commit function will be available here but not the rest of context
    commit('MY_MUTATION', payload)
  },
  // is equivalent to
  doTheOtherThing(context) {
    context.commit('MY_MUTATION', payload)
  }
}
```
This is probably the most complicated thing on this page. The way we use it in Vue is pretty straight forward though.
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment

## Export and Import
Export makes code available to other files/modules  
Import brings in code from other files/modules

### export default
```javascript
// File: thing.js
let thisIsAThing = param => param*2

export default {
  doTheThing() {
    // Do something
  },
  name: 'The Thing',
  thisIsAThing
}
```
```javascript
// File: client.js (or whatever)

// Since we used export default, you can call it whatever you want,
// in this case I've chosen TheThing
import TheThing from 'thing.js'

TheThing.name
TheThing.doTheThing()
TheThing.thisIsAThing(5)
```

### export
```javascript
// File: things.js
export const NAME = 'The Thing'
export function doTheThing() {
  // Do something
}
export let x = 5
```
```javascript
// File: client.js (or whatever)
import { NAME, doTheThing, x } from 'things'
NAME
// 'The Thing'
doTheThing()
// Executes function
x
// 5
```

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export  
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