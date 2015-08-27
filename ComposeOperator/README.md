# Pipe Operator
In functional programming, it is very common to compose functions. In JS it is commonly done like this

```js
third(second(first(10)))
```
Several libraries have made it easier to compose with a `compose` method
```js
compose(third, second, first);
```

I propose a new operator `:>` to compose functions,
```
first :> second :> third
```

The above statement is equivalent to this
```js
function (...args) {
    return third(second(first(...args));
}
```

If the first argument is not a function, it is evaluated
```js
10 :> first :> second :> third
```
That will result in
```js
third(second(first(10));
```

With the proposed partial application operator
```js
const arr = [1,2,3];

arr 
  :> map:(x => x + 1)
  :> filter:(x => x % 2 === 0)
  :> reduce:((prev, val) => prev + val, 0);
// 6
```