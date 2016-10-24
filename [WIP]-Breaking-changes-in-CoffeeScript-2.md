CoffeeScript 2 will be a breaking-change release of CoffeeScript that changes the CoffeeScript compiler’s output to produce ES2015+ syntax whenever possible. For more details, see [here](https://github.com/coffeescript6/discuss/issues/36) and [here](https://github.com/coffeescript6/discuss). This document is a running list of breaking changes that will need to be explained in the future release’s documentation.

## Breaking changes

### Function parameter default values

Per the [ES2015 spec regarding default parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters), default values are only applied when a parameter value is missing or `undefined`. In CoffeeScript 1.x, the default value would be applied in those cases but also if the parameter value was `null`.

```coffee
f = (a = 1) -> a
f(null) # Returns 1 in CoffeeScript 1.x, null in CoffeeScript 2
```

### Bound generator functions

Bound generator functions, a.k.a. generator arrow functions, [aren’t allowed in ECMAScript](http://stackoverflow.com/questions/27661306/can-i-use-es6s-arrow-function-syntax-with-generators-arrow-notation). You can write `function*` or `=>`, but not both. Therefore, CoffeeScript code like this:

```coffee
f = => yield this
```

Needs to be rewritten the old-fashioned way:

```coffee
self = this
f = -> yield self
```