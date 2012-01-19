There is no official style guide for CoffeeScript, but the following guide should at least provide a nice framework for discussion:

https://github.com/polarmobile/coffeescript-style-guide

Probably the most important consideration for public code is whitespace.  The best convention to follow is the CoffeeScript code itself:

http://coffeescript.org/documentation/docs/nodes.html

It uses two-space indents, with actual spaces (no tabs).

Another consideration is snake_case vs. camelCase.  The strong argument for camelCase is that it is already a fairly strong convention in the greater JavaScript ecosystem.  Folks working in multi-language environments may decide that they prefer snake_case despite the JavaScript convention, especially if they are writing lots of Ruby and Python code as well.

