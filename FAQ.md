Considering proposing a feature for CoffeeScript? Great! We'd love to hear your thoughts on how the language could be improved.

However, it's important that you make sure the proposal hasn't already been raised. This FAQ should contain most of the questions and suggestions that have come up multiple times, so have a read through them first. If you can't find it here, have a quick search through the Issue Tracker just to be totally sure, then go ahead.


## Static Analysis

*CoffeeScript uses a straight source-to-source compiler. No type checking is performed, and we can't work out if a variable even exists or not. This means that we can't implement features that other languages can build in natively without costly runtime checks. As a result, any feature which relies on this kind of analysis won't be considered.*

----

**Q:** Can I use negative array indices as in Ruby and Python?

**A:** No. In order to work out if the index passed was negative, we would have to perform a runtime check.

```coffeescript
index = -1
last = array[index]
```

  Every time this kind of property access appears, we would need to do: `array[index < 0 ? array.length + index : index]`, which is unacceptable, especially because we don't even know if `array` is an Array or not.

----

**Q:** What about only when the specifically passed a negative value, like this: `array[-index]`?

**A:** For consistency's sake, no. And if the value of `index` is negative itself, things start getting awfully confusing.

Read the following issues for earlier discussion:
[#272](http://github.com/jashkenas/coffee-script/issues/272),
[#681](http://github.com/jashkenas/coffee-script/issues/681),
[#621](http://github.com/jashkenas/coffee-script/issues/621)


## Functions

*CoffeeScript's syntax is big on reducing the size of function declarations, as evidenced by the replacing of the `function` keyword with the much shorter `->` glyph. Take this into consideration if you plan to propose anything around this declaration syntax.*

----

**Q:** Can I use default parameters like `(arg: 1) ->` or `(arg = 1) ->`?

**A:** Yes, however note `null` is also interpreted as a missing value and will receive the default:

```coffeescript
fn = (arg = 'default value') ->
  console.log arg
```

This is a much clearer format. These issues highlight the primary arguments for and against:
[#16](http://github.com/jashkenas/coffee-script/issues/16),
[#92](http://github.com/jashkenas/coffee-script/issues/92)

---

**Q:** Fat arrow, slim arrow ... How can I keep my context ? What's best for me to use, when ?

**A:** Use a fat arrow if you need to preserve context, unless you also need the new given context. In this case, bind the context yourself. You can regen to [this gist](https://gist.github.com/Nami-Doc/5541389) for detailed examples.


----

**Q:** Is there any way to name functions, for reflection and recursion?

**A:** Blame Microsoft for this one. Originally every function that could have a sensible name retrieved for it was given one, but IE versions 8 and down have scoping issues where the named function is treated as both a declaration and an expression. See [this](http://kangax.github.com/nfe/#jscript-memory-management) for more information. You can assign the function to a local variable if you want to safely work with recursion, like so:

```coffeescript
exports.func = func = (arg) -> func arg - 1 if arg > 0
```

Note that there is a solution to the scoping issue, and it is employed for class constructors, primarily for reflection purposes, but the resulting code is too verbose to use for every function.

The issue that originally brought about named functions was: [#15](http://github.com/jashkenas/coffee-script/issues/15)

The issue that saw them go:  [#366](http://github.com/jashkenas/coffee-script/issues/366)

Other related issues and proposals:
[#494](http://github.com/jashkenas/coffee-script/issues/494),
[#714](http://github.com/jashkenas/coffee-script/issues/714),
[#729](http://github.com/jashkenas/coffee-script/issues/729),
[#732](http://github.com/jashkenas/coffee-script/issues/732),
[#758](http://github.com/jashkenas/coffee-script/issues/758),
[#907](http://github.com/jashkenas/coffee-script/issues/907)


## Variable Importing

*It's difficult to deal with Javascript variables that aren't defined at compile time, so most forms of generic importing are off the table. Remember that you can always import specific values from an object using a destructuring assignment: `{compact, flatten} = require './helpers'`*

----

**Q:** Is there statement equivalent to Javascript's `with`?

**A:** No. [Douglas Crockford's advice](http://yuiblog.com/blog/2006/04/11/with-statement-considered-harmful/) should outline the main reasons why you should never use this statement, and you can view these older issues for the original discussions:
[#344](http://github.com/jashkenas/coffee-script/issues/344),
[#620](http://github.com/jashkenas/coffee-script/issues/620).

----

**Q:** Is there any way to import every variable from an object into the local scope?

**A:** Not without listing them out manually. In Javascript there is no way to place a variable into a local scope without knowing its name at compile time. You can read more about importing suggestions in these issues:

**TODO:** Find issues relating to importing.


## Classes

*It's important to keep in mind that CoffeeScript's classes are syntactic sugar only, and are intended only as a light wrapper of the prototypal concepts of Javascript. There is a long history and issue trail relating to classes in this language, and there have been many suggestions on how they should work. We've chosen a style that matches up to the expectations of a classic OO programmer, with almost every aspect mapping directly to a Javascript operation on a prototype or function. Overly complicated class semantics that add only a small amount of functionality are not what we're looking for.*

----

**Q:** Will you support multiple inheritance/mixins/imports/interfaces/traits or any other fancy class extensions?

**A:** No. You can do any of the above using helpers.

Solution (1) courtesy of [jashkenas](http://github.com/jashkenas):

```coffeescript
extend = (obj, mixin) ->
  for name, method of mixin
    obj[name] = method

include = (klass, mixin) ->
  extend klass.prototype, mixin

class Button
  onClick: -> # do stuff

include Button, Options
include Button, Events
```

Solution (2) courtesy of [sethaurus](http://github.com/sethaurus):

```coffeescript
implementing = (mixins..., classReference) ->
  for mixin in mixins
    for key, value of mixin::
      classReference::[key] = value
  classReference

Button = implementing Options, Events, class _Button
  onClick: -> # do stuff
```

These issues should cover the discussion on mixins:
[#218](http://github.com/jashkenas/coffee-script/issues/218),
[#327](http://github.com/jashkenas/coffee-script/issues/327),
[#344](http://github.com/jashkenas/coffee-script/issues/344),
[#452](http://github.com/jashkenas/coffee-script/issues/452) and
[#636](http://github.com/jashkenas/coffee-script/issues/636).

----

**Q:** Do class (static) properties get inherited?

**A:** They don't get prototypal inheritance, but CoffeeScript does copy static properties from the superclass to the subclass at the time of inheritance.

**TODO:** Find the issues on static property inheritance.

**TODO:** Add the following

* Executable class bodies
* Private properties


## Unsupported features

----

**Q:** Will you add feature **X** where feature **X** depends on a platform?

**A:** No, implementation-specific features are not allowed as a policy. Everything that you write in CoffeeScript should be supported and runnable on any current JavaScript implementation (in practice, this means the lowest common denominator is IE6). Thus, features such as the following will not be implemented: getters & setters, `yield`

----

**Q:** I need namespaces/modules, man!

**A:** Then you shall have them:

```coffeescript
# Code:
#
namespace = (target, name, block) ->
  [target, name, block] = [(if typeof exports isnt 'undefined' then exports else window), arguments...] if arguments.length < 3
  top    = target
  target = target[item] or= {} for item in name.split '.'
  block target, top

# Usage:
#
namespace 'Hello.World', (exports) ->
  # `exports` is where you attach namespace members
  exports.hi = -> console.log 'Hi World!'

namespace 'Say.Hello', (exports, top) ->
  # `top` is a reference to the main namespace
  exports.fn = -> top.Hello.World.hi()

Say.Hello.fn()  # prints 'Hi World!'
```
----

**Q:** What about extending native objects to allow for things such as `Array#forEach` and `Function#bind` ?

**A:** The rule here is to not extend native objects.


## Grammar

----

**Q:** How do I directly pass a function to another function that requires other arguments after it?

**A:** You can use parentheses around the function or a leading comma after it. i.e.:

```coffeescript
setTimeout (-> alert 'Woohoo!' ), 1000

navigator.geolocation.getCurrentPosition (pos) ->
  console.dir pos
, (err) ->
  console.log err.message
, enableHighAccuracy: on, timeout: 5000
```

----

**Q:** Why does `a + b` mean something different than `a +b`?

**A:** Because in both JavaScript and CoffeeScript, `+str` converts `str` to a number. CoffeeScript therefore interprets `+str` as a function argument: `func +str` means the same thing as `func(+str)`.

See discussion at issue [1036](https://github.com/jashkenas/coffee-script/issues/issue/1036).

----

**Q:** How do I denote an array of implicit objects?

**A:** Use an outdented comma or explicit braces

```coffeescript
[
  foo: 0
  bar: 1
,
  baz: 2
]

[
  {
    foo: 0
    bar: 1
  },
  {
    baz: 2
  }
]

[
  {} = foo: 0, bar: 1
  {} = baz: 2
]
```

----

**Q:** How do I get an index in a `for-in` loop?

**A:** Use `for value, index in array`

```coffeescript
languages = ["CoffeeScript", "JavaScript", "Ruby"]
for lang, i in languages
  alert "#{i} = #{lang}"
```

## Miscellaneous

--

**Q:** What are CoffeeScript's compilation priorities?

**A:** The output should be (in order from highest to lowest priority):

0. correct
0. DRY
0. performant
0. readable
0. small (byte-wise)