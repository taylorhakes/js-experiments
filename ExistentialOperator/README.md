# Existential Operator
This idea is pulled straight from Coffeescript. Here is the definition in Coffeescript.

`?.` can be used to soak up null references in a chain of properties. Use it instead of the dot accessor `.` 
in cases where the base value may be null or undefined. If all of the properties exist then you'll get the
expected result, if the chain is broken, undefined is returned instead of the TypeError that would be raised otherwise.

This
```
zip = lottery.drawWinner?().address?.zipcode
```

is compiled to this
```
var ref, zip;

zip = typeof lottery.drawWinner === "function" ? (ref = lottery.drawWinner().address) != null ? ref.zipcode : void 0 : void 0;
```