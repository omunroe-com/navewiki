Considering proposing a feature for Coffeescript? Great! We'd love to hear your thoughts on how the language could be improved. However, it's important that you make sure the proposal hasn't already been raised. This FAQ should contain most of the questions and suggestions that have come up multiple times, so have a read through them first. If you can't find it here, have a quick search through the Issue Tracker just to be totally sure, then go ahead.

## Static Analysis

*Coffeescript uses a straight source-to-source compiler. No type checking is performed, and we can't work out if a variable even exists or not. This means that we can't implement features that other languages can build in natively without costly runtime checks. As a result, any feature which relies on this kind of analysis won't be considered.*

* **Q:** Can I use negative array indices as in Ruby and Python?

  **A:** No. In order to work out if the index passed was negative, we would have to perform a runtime check.

```coffeescript
index = -1
last = array[index]
```

  Every time this kind of property access appears, we would need to do: `array[index < 0 ? array.length + index : index]`, which is unacceptable, especially because we don't even know if `array` is an Array or not.
  
* **Q:** What about only when the specifically passed a negative value, like this: `array[-index]`?

  **A:** For consistency's sake, no. And if the value of `index` is negative itself, things start getting awfully confusing.

  Read the following issues for earlier discussion:
  [#272](http://github.com/jashkenas/coffee-script/issues/272), 
  [#681](http://github.com/jashkenas/coffee-script/issues/681),
  [#621](http://github.com/jashkenas/coffee-script/issues/621)

## Functions

*Coffeescript's syntax is big on reducing the size of function declarations, as evidenced by the replacing of the `function` keyword with the much shorter `->` glyph. Take this into consideration if you plan to propose anything around this declaration syntax.*

  * **Q:** Can I use default parameters like `(arg: 1) ->` or `(arg = 1) ->`?

    **A:** No. Adding these adds too much potential for assignment confusion and bulks out the arguments list too much. Use the following instead:

```coffeescript
(arg) ->
  arg or= 1
```

This is a much clearer format. These issues highlight the primary arguments for and against:
[#16](http://github.com/jashkenas/coffee-script/issues/16),
[#92](http://github.com/jashkenas/coffee-script/issues/92)

  * **Q:** Is there language support for function binding or currying?

    **A:** There was, but it was removed. It was decided that binding belonged outside of the realm of the language. Use an appropriate library like Prototype's `Function::bind`, or roll your own:

```coffeescript
unless Function::bind?
  Function::bind = (scope,args...) ->
    self = this
    -> self.apply scope, args.concat.apply(args,arguments)
```

## Misc

   **Q:** Why can't I use `with`?

   **A:** [Because Douglas Crockford says so](http://yuiblog.com/blog/2006/04/11/with-statement-considered-harmful/) and [#344](http://github.com/jashkenas/coffee-script/issues/344), 
[#620](http://github.com/jashkenas/coffee-script/issues/620)

## Classes
   **Q:** Will you support multiple inheritance/mixins/imports/interfaces/traits or any other fancy class extensions?

   **A:** The short answer is **no**. You can do any of the above using helpers.

  Solution (1) courtesy of [jashkenas](http://github.com/jashkenas):

```coffeescript
extend = (obj, mixin) ->
  for name, method of mixin
    obj[name] = method

include =  (klass, mixin) ->
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

  If you want to learn more, please read these issues on the tracker: 
[#218](http://github.com/jashkenas/coffee-script/issues/218), 
[#327](http://github.com/jashkenas/coffee-script/issues/327), 
[#344](http://github.com/jashkenas/coffee-script/issues/344), 
[#452](http://github.com/jashkenas/coffee-script/issues/452) and 
[#636](http://github.com/jashkenas/coffee-script/issues/636). They should have all the pros and cons and why mixins are not part of the core language.


### 


   **Q:** Do class methods work with inheritance?

   **A:** No, class methods do not get inherited b/c JS has no prototype chain for class methods, only for object methods. You can add a simple hook to mimic class-method inheritance, however, by defining an "extended" method on your class.

 **TODO:** Add the following

* Executable class bodies
* Private properties


## Unsupported features
   **Q:** Will you add feature X where feature X depends on a platform?
 
   **A:** No, implementation-specific features are not allowed as a policy. Everything that you write in CoffeeScript should be supported and runnable on any current JavaScript implementation (in practice, this means the lowest common denominator is IE6). Thus, features such as the following will not be implemented: getters & setters, `yield`

   **Q:** What about extending native objects to allow for things such as `Array#forEach` and `Function#bind` ?

   **A:** The rule here is to not extend native objects.

