CoffeeScript does not support mixins that are needed in large projects. However they are easy to emulate.
Use:

	class Mixin1
		@staticProp   = 42
		dymamicMethod : -> "Mixin1 : #{@name}"

	class Mixin2
		dynamicMethod : -> "Mixin2 : #{@name}"

	class Class extends AnotherClass
		@implements Mixin1, Mixin2
		constructor : (@name) ->

	obj = new Class('Tim')

	Class.staticProp    == 42
	obj.dynamicMethod() == 'Mixin2 : Tim'

Implementation:

	implements = (classes...) ->
		for klass in classes
			# Statics
			for prop of klass
				@[prop] = klass[prop]

			# Dynamics
			for prop of klass::
				getter = klass::__lookupGetter__(prop)
				setter = klass::__lookupSetter__(prop)

				if getter || setter
					@::__defineGetter__(prop, getter) if getter
					@::__defineSetter__(prop, setter) if setter
				else
					@::[prop] = klass::[prop]
		return @

	if Object.defineProperty
		Object.defineProperty Function.prototype, "implements",
			value : implements
	else
		Function::implements = implements
