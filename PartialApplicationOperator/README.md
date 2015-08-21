# Partial Application Operator
It is very common to use `Function.prototype.bind` in javascript for partial application programming. Unfortunately, it is
based around javascript object oriented features and in can be long winded. `map.bind(null, x => x / 2)`
In some other functional languages, functions are curried or partially applied by default. Since we can't make a major breaking
change to javascript. I propose the a new operator to partially apply parameters.
```
map:(x => x / 2)
``
The colon before the parenthesis means the params are partially applied. It doesn't execute the function. I think other
operators could work, but the colon feels natural and is pleasing to look at. There may be problems with object literal
```
{ map : ( x /  2 ) }
```

Other options
```
map@(x => x / 2)
map<-(x => x / 2)
```

The operator would be the equivalent of this in ES6, but the `this` wouldn't change or be bounded
```
map.bind(undefined, x => x / 2)
```