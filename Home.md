Welcome to the CoffeeScript Wiki!

[[Want to help CoffeeScript? Read about contributing!|[Contributing] Help CoffeeScript]]


## How-To's

 * [[Compiling, Concatenating and Setting Up Build Tools Using Cake|[HowTo] Compiling and Setting Up Build Tools]]


## Extensibility

 * [[Hooking into the Command-Line Compiler|[Extensibility] Hooking into the Command-Line Compiler]]


## FAQs
*(these will be separated in a new page as content gets added)*

  * **Q:** Will you support multiple inheritance/mixins/imports/interfaces/traits or any other fancy class extensions?

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
      (classReference::)[key] = value
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
