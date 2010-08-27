Welcome to the CoffeeScript Wiki!

[[Want to help CoffeeScript? Read about contributing!|Contributing]]


## Extensibility

 * [[Hooking into the command-line compiler|[Extensibility] Hooking into the command-line compiler]]


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

  If you are thinking of opening up a new issue, please read these first: #218, #327, #344, #452 and #636.
