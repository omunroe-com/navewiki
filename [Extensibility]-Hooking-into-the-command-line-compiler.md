Since version [0.9.1](http://github.com/jashkenas/coffee-script/tree/0.9.1) the compiler takes a `--require` flag, which specifies files to include before compilation. Let's create a simple script that would prepend a license header when code is compiled successfully (either via the command-line, `stdin` or a file):

    $ cd ~
    $ vim ext.coffee

Paste the following contents into `ext.coffee`:

```coffeescript
# This is the file that gets required by the compiler
CoffeeScript.on 'success', (task) ->
  task.output = """
    // The MIT License
    // Copyright (c) #{ new Date().getFullYear() } Your Name\n
   """ + task.output
```

CoffeeScript emits three events during compilation: `compile`, `success` and `failure`. Each event receives a `task` parameter -- in the case of `failure` it is the second parameter where the first one is the exception that was thrown. The task object is a collection of properties: `file`, `input` and `options` -- after compilation, `output` is also available:

[[http://yuml.me/diagram/scruffy;/class/[emit%20'compile'%7C[task;-%20file;-%20input;-%20options]-success%20%3E[emit%20'success'%7C[task;-%20file;-%20input;-%20options;-%20output%7Bbg:green%7D],%20[emit%20'compile'%7C[task;-%20file;-%20input;-%20options%7Bbg:cornsilk%7D]-exception%20%3E[emit%20'failure'%7C[err%7Ctask;-%20file;-%20input;-%20options%7Bbg:orange%7D].png]]

In the script above we modify the `output` property before it is printed to `stdout` or a file. Let's invoke the command-line compiler and require our script:

    $ cd ~
    $ coffee -ep --require ./ext.coffee '1 + 1'
    // The MIT License
    // Copyright (c) 2010 Your Name
    (function() {
      1 + 1;
    })();

and sure enough we can see our header merged to the output. In case you are wondering what `-ep` is, it is a shorthand for `--eval --print`. You can also short-type `--require`:

    $ coffee -epr ./ext.coffee '1 + 1'

The path to `ext.coffee` is resolved using node.js hence the need to prepend it with `./`. If you want to avoid that, you can:

  * create all extensions under `~/.node_libraries/`
  * create a new directory under your profile `coffee_libraries` and add it to your `NODE_PATH`:

        export NODE_PATH="/home/your_username/.coffee_libraries:$NODE_PATH"

If you do any of the above, you can omit the `.coffee` extension as well:

    $ coffee -epr ext '1 + 1'
