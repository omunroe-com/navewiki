The core of parsing CoffeeScript syntax into generated output JavaScript happens in four files: `lexer.coffee`, `rewriter.coffee`, `grammar.coffee` and `nodes.coffee`. When we implemented modules, we added support for new keywords `import` and `from` and `as`, among others. Below is a walkthrough of how support for these new keywords was added.

### `lexer.coffee`

`identifierToken` basically takes one word or symbol (read: `@chunk`) at a time, assigns it a name or type and creates a token in the form of a token tuple `[ tag, value, offsetInChunk, length, origin ]`. This is what the functions `token` and subsequently `makeToken` create.

In `identifierToken` there are a few key variables and functions that are needed:

* `@chunk`: the current string to handle, this is split up into `[input, id, colon]` with the `IDENTIFIER` regular expression at the bottom
* `id`: in case of a keyword like `import`, this is literally `'import'`
* `@tag()`: gets the `tag` (first value of the token tuple) of the last processed token. When processing `foo` (as in the second chunk of `import 'foo'`), `@tag()` will return `'IMPORT'`.
* `@value()`: gets the `value` (second value of the token tuple) of the last processed token. When processing `foo` (as in the second chunk of `import 'foo'`), `@value()` will return `import`, the very string that was held in `id` in the last chunk’s handling.

So basically what was added to `identifierToken` were the tags `IMPORT`, `IMPORT_AS`, and `IMPORT_FROM`. These three tags are then used in `grammar.coffee`.

### `grammar.coffee`

For this part we took a look at [the spec for imports](http://www.ecma-international.org/ecma-262/6.0/index.html#sec-imports) and basically copied the structure from there.

The DSL used here basically mixes and matches tags and named grammar forms. In this case the tags are `'IMPORT'`, `'IMPORT_AS`‘, `'IMPORT_FROM'` as replaced in `lexer.coffee`‘s `identifierToken`. The other parts of those strings are just other named grammar forms (`ImportSpecifierList`, `OptComma`, `String`, etc.).

The structure builds up through references to other grammar forms and functions that create and return data structures, like `-> new Import $2`. The “`$n`” variables are just references to the `n`th word in the string.

This process leads to an AST that is passed to the `ImportDeclaration` class defined in `nodes.coffee`.

`import 'lib'` will fit the grammar of `IMPORT String` which passes to `new ImportDeclaration null, $2`. The variable `$2` in this case is something like `StringLiteral { value: 'lib' }`

`import { foo } from 'lib'` will fit the grammar of `'IMPORT { ImportSpecifierList OptComma } FROM String'`. `ImportSpecifierList` will be further evaluated into `'ImportSpecifier'` which returns `[$1]`; so then the parent evaluates to `new ImportDeclaration new ImportClause(null, [$1]), $7`.

You can look at this AST quite easily by just prepending a `console.log` before calling `new ImportDeclaration`:

```coffee
Import: [
  o 'IMPORT String',                             -> console.log($2); new ImportDeclaration null, $2
  o 'IMPORT ImportDefaultSpecifier FROM String', -> console.log($4, $2); new ImportDeclaration new ImportClause($2, null), $4
]
```

### `nodes.coffee`

Taking the AST from `grammar.coffee`, the classes in `nodes.coffee` are supposed to create tuples of “code” through `@makeCode` and `compileNode` functions. Each node is compiled to a string by calling `compileNode` or `compileToFragments`. What `ImportDeclaration.compileNode` basically does is just look at the AST and either returns an array of strings passed through `@makdeCode` directly _or_ it calls the token’s `compileNode` function.

Many of the classes in `nodes.coffee` have common properties:

- `children` tells which properties to recurse into when tree walking. The `children` list *is* the structure of the AST. The `parent` pointer, and the pointer to the `children` are how you can traverse the tree.
- If `node.isComplex() is false`, it is safe to use `node` more than once. Otherwise you need to store the value of `node` in a variable and output that variable several times instead. Kind of like this: `5` is not complex. `returnFive()` is complex. It’s all about “do we need to cache this expression?”
- `makeReturn` is what we use to force an arbitrary node into the returned value from a function. Helpful for implicit returns — when any valid CoffeeScript statement or expression could need to be returned … something that doesn’t happen in JS. Most of these are simple. If/elses and for-loops are not.
- `jumps` tells you if an expression, or an internal part of an expression has a flow control construct (like `break`, or `continue`, or `return`, or `throw`) that jumps out of the normal flow of control and can’t be used as a value. This is important because things like this make no sense — we have to disallow them:

    ```coffeescript
    value = if condition
      100
    else
      return 5
    ```

- `isStatement` has to do with “everything is an expression”. A few things can’t be expressions, such as `break`. Things that `isStatement` returns `true` for are things that can’t be used as expressions. There are some error messages that come from `nodes.coffee` due to statements ending up in expression position.

### Further reading (or viewing)

In [this video](https://www.youtube.com/watch?v=DspYurD75Ns) Jeremy explains the concepts and the parts where “cheating” happens. 