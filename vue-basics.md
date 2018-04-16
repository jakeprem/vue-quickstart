# Vue Basics
Quick notes on Vue.js

  * [Basics](#basics)
  * [Computed Properties](#computed-properties)

## Basics

### The simplest Vue app

```html
<div id="app">
  {{ message}}
</div>
```
```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello world!'
  }
})
```
Output
```html
<div id="app">
  Hello World!
</div>
```
A Vue instance is created by invoking `new Vue()` and passing in an object with certain properties defined.
#### el
The `el` property specifices whate element on the page Vue should bind to. In this simple example, Vue uses the existing HTML at this location as its template.
#### data
The `data` property holds the local state of this instance. Properties of this data can be referenced in the template (HTML generally) or in Javascript. For example, the `{{ message }}` in the HTML above will be replaced with the contents of `message`

Data properties are reactive. That means if the message property is updated, the HTML rendered at `{{ message }}` will be updated as well.  
There are some limitations to how this works, and understanding those limits is an important part of using Vue.

## Computed Properties
On a Vue object you might see something like
```js
...,
computed: {
  message() {
    return `Hello ${this.name}!`
  }
},
...
```
This is a computed property. Computed properties are implemented as functions that return a value.  
They are accessed just like you would access a normal data property. Computed properties are only reevaluated when the underlying data changes (`this.name` in this case).  
Computed properties should be used instead of methods wherever possible.