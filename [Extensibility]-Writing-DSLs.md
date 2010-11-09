<font color="red">**This page requires attention. Please help by fixing typos, broken examples, rewriting bits of text, etc. Consider editing this page and help us out in improving the Wiki!**</font>

The CoffeeScript grammar is pretty flexible when it comes to writing a DSL. Implicit parentheses, commas and objects combine to give you an expressive language which compiles to good old JavaScript. The examples on this page assume a good level of knowledge of CoffeeScript.

### Implicit objects can be nested below a function call

Let's look at an example of what we are trying to accomplish before we get started:

```coffeescript
# DSL
describe('Whiskey')
  age: 18
  brand: 'Jack'

# Usage
glass = new Whiskey
puts glass.age  # 18
```

To implement our custom `describe` function let's first look at the generated JavaScript for it:

```javascript
describe('Whiskey')({
  age: 18,
  brand: 'Jack'
});
```

We have a call to the function itself and a following one to its returned value. CoffeeScript makes it easy to implement such chaining:

```coffeescript
# Implementation
describe = (name) -> (properties) ->
  window[name] = class
    constructor: ->
      (@[name] = value) for name, value of properties
```

### Implicit parentheses turn code into natural language

Example:

```coffeescript
# DSL and usage
a = keyA: 'valueA'
b = keyB: 'valueB'

extend b, using a

puts b.keyA  # 'valueA'
```

This compiles to fairly simple JavaScript:

```javascript
extend(a, using(b));
```

To implement this we only need a few lines of CoffeeScript:

```coffeescript
# Implementation
using  = (obj) -> obj
extend = (obj, using) -> (obj[key] = value) for key, value of using
```

### Going a step further

With just a few tips and you can already start building your own awesome DSL. How about classes with mixins?

```coffeescript
# Implementation
implements = (list) -> item:: for item in list
Class = (base, implements) -> (properties) ->
  class _ extends base
  (_::[name] = value) for name, value of item for item in implements if implements
  (_::[name] = value) for name, value of properties if properties
  _

# Usage
class Animal
  name: '<Animal>'
  say:  (what) -> puts what

class Options
  set: (key, value) -> @[key] = value

class Huggable
  owner: '<null>'
  hug:    -> @say "#{@name} hugs #{@owner}."

# DSL
Cat = Class Animal, implements [Options, Huggable]
  name: '<Cat>'

# Usage
molly = new Cat
molly.set 'name', 'Molly'
molly.set 'owner', 'Stan'
molly.hug()  # Molly hugs Stan.
```