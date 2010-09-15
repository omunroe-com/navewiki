The CoffeeScript grammar is pretty flexible when it comes to writing a DSL. Implicit parentheses, commas and objects combine to give you an expressive language which compiles to good old JavaScript. Here are a few tricks to get you started.

### Implicit objects can be nested below a function call

```coffeescript
# DSL
describe 'Whiskey'
  age: 18
  brand: 'Jack'

# Usage
glass = new Whiskey()
puts glass.age  # 18
```

To implement our custom `describe` function let's first look at the generated JavaScript for it.

```javascript
describe('Whiskey')({
  age: 18,
  brand: 'Jack'
});
```

We have the call to the function itself and another one to the returned value (we could have as many of these as we want). CoffeeScript makes it easy to implement such chaining:

````coffeescript
# Implementation
describe = (name) -> (properties) ->
  window[name] = class
    constructor: ->
      (@[name] = value) for name, value of properties
````

