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
````

The implementation of the module helper is

````
window.module = (name, fn)->
  if not @[name]?
    this[name] = {}
  if not @[name].module?
    @[name].module = window.module
  fn.apply(this[name], [])
````

which you can put in another source file if you like. You can
then access your classes by namespaced modules

````
x = new foo.bar.Amazing
````
