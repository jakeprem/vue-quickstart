# Vue Medium
Some more complex things about Vue

  * [Change Detection Caveats](#change-detection-caveats)

## Change Detection Caveats
Vue can't track property additions or deletions at runtime,
nor does Vue allow you to dynamically add new root level properties (i.e. data.property).  
If you must add a property to a nested object, you'll need to use `Vue.set` to make it reactive.  
```js
...
data() {
  return {
    nestedObj: {
      a: 'Apple',
      b: 'Bannana'
    }
  }
},
methods: {
  addOrange() {
    Vue.set(this.nestedObj, 'o', 'Orange')
  }
}
```
[https://vuejs.org/v2/guide/reactivity.html#Change-Detection-Caveats]()

## Async Update Queue
Vue does some stuff with buffering changes. We can pass a callback function to be executed after the changes are written to the DOM like so:
```js
this.$nextTick(function() {})
```

We should avoid this wherever possible. But it might be necessary,
particularly in the text editing component.

[https://vuejs.org/v2/guide/reactivity.html#Async-Update-Queue]()