<font color="red">**This page requires attention. Please help by fixing typos, broken examples, rewriting bits of text, etc. Consider editing this page and help us out in improving the Wiki!**</font>

The CoffeeScript grammar is pretty flexible when it comes to writing a DSL. Implicit parentheses, commas and objects combine to give you an expressive language which compiles to good old JavaScript. The examples on this page assume a good level of knowledge of CoffeeScript.

### Implicit objects can be nested below a function call

Let's look at an example of what we are trying to accomplish before we get started:

```coffeescript
# DSL
describe 'Whiskey'
  age: 18
  brand: 'Jack'

# Usage
glass = new Whiskey
console.log glass.age  # 18
```

To implement our custom `describe` function let's first look at the generated JavaScript for it:

```javascript
describe('Whiskey', {
  age: 18,
  brand: 'Jack'
});
```

The implicit object below the function call is concatenated to the arguments list. Simple enough:

```coffeescript
# Implementation
top = this  # usually window
describe = (name, properties) ->
  top[name] = class
    constructor: ->
      this[name] = value for own name, value of properties
```

### Implicit parentheses turn code into natural language

Example:

```coffeescript
# DSL and usage
foo = foo: 'I said foo!'
bar = bar: 'I said what?!'

extend bar, using foo

console.log bar.foo  # 'I said foo!'
```

This compiles to fairly simple JavaScript:

```javascript
extend(bar, using(foo));
```

To implement this we only need a few lines of CoffeeScript:

```coffeescript
# Implementation
using  = (obj) -> obj
extend = (obj, using) -> (obj[key] = value) for key, value of using
```

You can really go crazy with functional-style programming using the implicit nature of the language:

```coffeescript
SELECT = (map, results) -> map.call each for each in results
FROM   = (list, reduce) -> each for each in list when reduce each
WHERE  = (reduce)       -> (each) -> reduce.call each

# Find users between the age of 18 and 64
SELECT -> { @name }, 
FROM   Users, 
WHERE  -> 18 < @age < 64
```

### Going a step further

With just a few tips and you can already start building your own awesome DSL. How about classes with mixins?

```coffeescript
# Implementation
implements = (list) -> item.prototype for item in list
Class = (base, implements, properties) ->
  class _ extends base
  _::[name] = value for name, value of item for item in implements if implements
  _::[name] = value for name, value of properties if properties
  _

# Usage
class Animal
  name: 'Animal'
  say:  (what) -> console.log what

class Options
  set: (key, value) -> this[key] = value

class Huggable
  owner: 'none'
  hug:    -> @say "#{@name} hugs #{@owner}."

# DSL
Cat = Class Animal, implements [Options, Huggable],
  name: 'Cat'

# Usage
molly = new Cat
molly.set 'name', 'Molly'
molly.set 'owner', 'Stan'
molly.hug()  # Molly hugs Stan.
```

Nested classes 
```coffeescript

#Code
class AlertMyFriends 

class AlertMyFriends::Show
      constructor: ->
          alert "Hello Friends"
#Usage
amf = new AlertMyFriends

al = new amf.Show()
```