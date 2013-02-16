This page lists common gotchas you may encounter when working with CoffeeScript.
You can refer to this page for general answers on "why does CoffeeScript acts that way"

**Q:** Why does CoffeeScript requires "foo" to be defined when doing `foo ?= value` or `foo ||= value`
**A:** Otherwise, it'd create a global, which is not what we want (if that *is* what you want, use `window.foo ?= value`)
 If you're declaring the variable in the current scope, you know for sure it doesn't exist - Javascript has no mecanic like php's static keyword.
 Note that it works perfectly when used with classes :

```coffee
class Foo
 getCache: ->
  @cache ?= "value"
```
 If you want an alternative to PHP's `static` keyword, you can use a closure : 

```coffee
do (staticVariable = theValueYouWant) ->
 (args...) ->
  #you now have a "static"-like access to "staticVariable"
```

----

**Q:** Why is CoffeeScript sometimes using `["bar"]` notation over `.bar` ?
**A:** CoffeeScript detects reserved keywords (as the auto-quoting of keywords in array notation) and prefer to use the array-access syntax (`[]`), because in ES3, reserved keywords (`throw`, `class`, ...) reserved words were not allowed as the right operand in a member access. See [this comment](https://github.com/jashkenas/coffee-script/issues/2314#issuecomment-5654411) for more information.

----

**Q:** Why is the existential "?" operator only checking `this.foo != null`, shouldn't it also check for `typeof === 'undefined'` ?
**A:** `X == null` tests that either X is null or undefined, assuming _it is in scope_. If we can't make that assumption, we need to do a `typeof` test to avoid `ReferenceError`s. See [the Abstract Equality Comparaison Algorithm (section 11.9.3)](http://es5.github.com/#x11.9.3) for more informations (especially steps 2 and 3).

---

**Q:** Why is `foo +a` different from `foo + a` ?
**A:** CoffeeScript is a whitespace-significant language. `foo<space>` starts an implicit call, you must either dually-space your operator or dually-unspace it.