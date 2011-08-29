# Namespacing and modules with coffeescript.

Coffeescript does not have a native module system above that of enclosing
all source code files in an anonymous function. However with a bit of
simple trickery you can have modules that are the envy of Ruby.

````
I define my modules like below

@module "foo", ->
  @module "bar", ->
    class @Amazing
      toString: "ain't it"

Or as a short-cut, this is equivalent

@module "foo.bar", ->
  class @Amazing
    toString: "ain't it"
````

The implementation of the module helper is

````
window.module = (name, fn) ->
  [name, more...] = name.split "."
  unless @[name]?
    this[name] = {}
  unless @[name].module?
    @[name].module = @module
  if more.length
    @[name].module (more.join "."), fn
  else
    Function::call.call fn, @[name]
````

which you can put in another source file if you like. You can
then access your classes by namespaced modules

````
x = new foo.bar.Amazing
````
