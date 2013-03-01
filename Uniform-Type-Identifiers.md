Wikipedia defines a [Uniform Type Identifier](http://en.wikipedia.org/wiki/Uniform_Type_Identifier) is “a text string used on software provided by Apple Inc. to uniquely identify a given class or type of item.” Applications should use the appropriate UTI (as defined below) when creating a CoffeeScript or Literate CoffeeScript file.

## CoffeeScript UTI

```coffeescript
identifier: 'public.coffeescript'
conforms_to: ['public.shell-script']
content_types: ['text/coffeescript']
extensions: ['.coffee']
```

## Literate CoffeeScript UTI

```coffeescript
identifier: 'public.literate-coffeescript'
conforms_to: ['public.shell-script', 'net.daringfireball.markdown']
content_types: ['text/literate-coffeescript']
extensions: ['.coffee.md', '.litcoffee']
```
