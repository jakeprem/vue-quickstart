# Vue Components
Information specific to Vue components

  * [Data Property](#data-property)
  * [Props](#props)
  * [Slots](#slots)


## Data Property
This is the same as the root level Vue data property, except that in a component, the data property *must* be a function that returns an object. Returning an object lets every instance of the component have it's own instance of the state. If you don't return an object then every instance will share the same state.

## Props

## Slots