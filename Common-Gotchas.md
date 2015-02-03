This page lists common gotchas you may encounter when working with CoffeeScript.
You can refer to this page for general answers on "why does CoffeeScript act that way"

##### **Q:** Why is the existential "?" operator only checking `this.foo != null`, shouldn't it also check for `typeof === 'undefined'` ?

**A:** `X == null` tests that either X is null or undefined, assuming _it is in scope_. If we can't make that assumption, we need to do a `typeof` test to avoid `ReferenceError`s. See [the Abstract Equality Comparaison Algorithm (section 11.9.3)](http://es5.github.com/#x11.9.3) for more information (especially steps 2 and 3).

----

##### **Q:** Why does CoffeeScript require "foo" to be defined when doing `foo ?= value` or `foo ||= value`

**A:** Otherwise, it'd create a global, which is not what we want (if that *is* what you want, use `window.foo ?= value`)
 If you're declaring the variable in the current scope, you know for sure it doesn't exist.

 Note that it works perfectly when used with classes :

```coffee
class Foo
 getCache: ->
  @cache ?= "value"
```

----

##### **Q:** Why is CoffeeScript sometimes using `["bar"]` notation over `.bar` ?

**A:** CoffeeScript detects reserved keywords (as the auto-quoting of keywords in array notation) and prefer to use the array-access syntax (`[]`), because in ES3, reserved keywords (`throw`, `class`, ...) were not allowed as the right operand in a member access. See [this comment](https://github.com/jashkenas/coffee-script/issues/2314#issuecomment-5654411) for more information.

----

##### **Q:** Why is `foo +a` different from `foo + a` ?

**A:** CoffeeScript is a whitespace-significant language. `foo<space>` starts an implicit call, you must either dually-space your operator or dually-unspace it.

----

##### **Q:** Why is `foo / a/g` or `foo /= a/g` different from `foo /a/g` or `foo /=a/g` ?

**A:** All four cases may look like calling a function named `foo` with a regex as the argument. However, the first two are division: They compile to `foo / a / g` and `foo /= a / g`. To make them compile into regexes instead, you can use escapes (`foo /\ a/g`, `foo /\= a/g`, `foo /=\ a/g`) or parentheses (`foo(/ a/g)`, `foo(/= a/g)`) to disambiguate. You can also assign the regex to a variable: `regex = / a/g; foo regex`.

On the other hand, if you want the two latter cases to compile to division you must either dually-space your operator or dually-unspace it (`foo/a/g`, `foo/=a/g`, `foo / a/g`, `foo /= a/g`). Again, CoffeeScript is a whitespace-significant language.

In summary, if your regex starts with `/ ` or `/= ` and there’s something that’s both callable and divisible before it, then the regex will be treated as division instead. In all other cases there should be no trouble. This is an unfortunate clash between parentheses-less calls, JavaScript’s regex syntax and the `/` and `/=` operators.