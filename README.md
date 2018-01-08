# Functional Programming Jargon for JavaScripters
Unscientific and (Maybe) More Friendly Dummy Explanations of FP Jargons

## Immutability
You simple don't change the current variables (including their nested data) and
 the data you've got defined.

There there are many different ways to achieve and apply this with different
benefits.

You should start googling `immutable-js`, `redux`, `ramda` after checking this
vanilla JavaScript example:

```javascript
const data = {
  irrelavent: 'data',
  aPropDefinedByAnotherDev: 'dummy'
}

// mutable way
// another dev irresponsibly decides to change this
// without knowing whether he or she if this data
// affects somewhere else:
data['aPropDefinedByAnotherDev'] = 'yolo'

//immutable way
const newData = { ...data, aPropDefinedByAnotherDev: 'yolo' }
// or:
const newData = Object.assign({}, data, { aPropDefinedByAnotherDev: 'yolo' })
// (note the first empty object so we don't touch
// existing variables)
```


### Benefits
*Todo...*

Huge.

## Lenses
Getter and setter functions for your data
```javascript
const adelle = { so: { deep: { roll : { in : 'it' } } } }

// imperative way
const theDeepData = adelle.so.deep.roll.in.it

// through lens
import { lensProp, compose } from 'ramda'

//atomic selectors (lenses)
const [so, deep, roll, in , it] = ['so', 'deep','roll','in','it']
  .map(lensProp)

export soDeepSelector = compose(so, deep, roll, in , it)


```

### Benefits
aids immutability, composoble functions without defining and
exporting variables there and there. You can share these
functions and re-use later. Which for example helps sharing
of data path definitions between universal server and client
for an API.
