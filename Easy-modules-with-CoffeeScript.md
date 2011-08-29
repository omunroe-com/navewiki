# Namespacing and Modules

CoffeeScript does not have a native module system above that of enclosing
all source code files in an anonymous function. However with a bit of
simple trickery you can have modules that are the envy of Ruby.

I define my modules like below

````
@module "foo", ->
  @module "bar", ->
    class @Amazing
      toString: "ain't it"
````

Or as a short-cut, this is equivalent

````
@module "foo.bar", ->
  class @Amazing
    toString: "ain't it"
````

The implementation of the module helper is

````
@module = (names, fn) ->
  names = names.split '.' if typeof names is 'string'
  space = @[names.shift()] ||= {}
  space.module ||= @module
  if names.length
    space.module names, fn
  else
    fn.call space
````

which you can put in another source file if you like. You can
then access your classes by namespaced modules

````
x = new foo.bar.Amazing
````
