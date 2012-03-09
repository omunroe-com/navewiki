This page requires attention. Please help by fixing typos, broken examples, rewriting bits of text, etc. Consider editing this page and help us out in improving the Wiki!

The CoffeeScript grammar is pretty flexible when it comes to writing a domain-specific language (DSL). Implicit parentheses, commas and objects combine to give you an expressive language that compiles to good old JavaScript. The examples on this page assume a good level of knowledge of CoffeeScript.

Implicit objects can be nested below a function call. Let's look at an example of what we are trying to accomplish before we get started:

```coffeescript
# DSL
describe 'Whiskey'
  age: 18
  brand: 'Jack'

# Usage
glass = new Whiskey
console.log glass.age  # 18
```

To implement our custom `describe` function, let's first look at the generated JavaScript for it:

```coffeescript
describe('Whiskey', {
  age: 18,
  brand: 'Jack'
});
```

The second and third items are converted to an Object and sent as the second argument to the `describe` function. In other words, the implicit object below the function call is concatenated to the arguments list. Simple enough:

```coffeescript
# Implementation
GLOBAL = window ? this  # usually window except on server side JavaScript

describe = (name, properties) ->
  GLOBAL[name] = class
    constructor: ->
      this[name] = value for own name, value of properties
```

Implicit parentheses can turn code into natural language (with some of the ambiguity of natural languages as well).

Example:

```coffeescript
# DSL and usage
foo = foo: 'I said foo!'
bar = bar: 'I said what?!'

extend bar, using foo

console.log bar.foo  # 'I said foo!'
```

This compiles to fairly simple JavaScript:

```coffeescript
extend(bar, using(foo));
```

To implement this, we only need a few lines of CoffeeScript:

```coffeescript
# Implementation
using  = (obj) -> obj
extend = (obj, using) -> (obj[key] = value) for key, value of using
```

You can really go crazy with functional-style programming, using the implicit nature of the language:

```coffeescript
SELECT = (mapper, results) -> mapper.call eachItem for eachItem in results
FROM   = (list, reduced)   -> fromItem for fromItem in list when reduced fromItem
WHERE  = (reducer)         -> (whereItem) -> reducer.call whereItem

# Find users between the age of 18 and 64
SELECT -> { @name, @age },
FROM   Users, 
WHERE  -> 18 < @age < 64

```

Going a step further

With just a few tips, you can already start building your own awesome DSL. How about classes with mixins?

```coffeescript
# Implementation
implements = (list) -> item.prototype for item in list

Class = (base, implemented, properties) ->
  class SUB extends base
  SUB::[name] = value for name, value of item for item in implemented if implemented
  SUB::[name] = value for name, value of properties if properties
  SUB

# Usage
class Animal
  name: 'Animal'
  say:  (what) -> console.log what

class Options
  set: (key, value) -> this[key] = value

class Huggable
  owner: 'nobody'
  hug:    -> @say "#{@name} hugs #{@owner}."

# DSL
Cat = Class Animal, implements([Options, Huggable]),
  name: 'Cat'
  lives: 9

# Usage
molly = new Cat
molly.set 'name', 'Molly'
molly.set 'owner', 'Stan'
molly.hug()  # Molly hugs Stan.

wildcat = new Cat
wildcat.hug() # Cat hugs nobody.

# Nested classes

# Code
class AlertMyFriends 

class AlertMyFriends::Show
  constructor: ->
    alert "Hello Friends"

# Usage
amf = new AlertMyFriends

al = new amf.Show()
```