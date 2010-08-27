<font color="red">**This page is work-in-progress. Please check back later**</font>

## Prerequisites

`cake` is `coffee`'s little sister (or so I picture things). If you installed CoffeeScript using `npm` then you should already have access to it. If you used `cake install` you have in fact had first-hand experience with the tool.

If you have symlinked `bin/coffee` to a new location on your `$PATH` then you should also symlink `bin/cake`:

    $ ln -s /home/stan/public/coffee-script/bin/cake /usr/local/bin/cake

The above assumes `/usr/local/bin` is in your `$PATH`.

## An empty Cakefile

Running `cake` outside of CoffeeScript's main directory is much likely to end up throwing an exception and printing out a stack trace. If you look closely, you can see why things don't work just yet:

    Error: Cakefile not found in /home/stan/

So, how about we create one:

    $ cd ~
    $ vim Cakefile

Leave the file empty for the time being. Run `cake` again:

    $ cd ~
    $ cake

This should return immediately without printing anything to `stdout`.

## Hello World!

Yes, we are doing the infamous *Hello World* example but with a spin -- inside a `Cakefile`. If you have worked with `rake` or `make` then you should already have an idea of how things work. You define a task and use `cake [task name]` to execute it. Let's get started:

    $ cd ~
    $ vim Cakefile

Define the task as `say:hello`:

```coffeescript
task 'say:hello', 'Description of task', ->
  puts 'Hello World!'
```

Save and exit back to the shell. Next, let's run our newly created task:

    $ cake say:hello
    Hello World!

Running `cake` again but without any arguments you get a list of all available tasks and their description:

    $ cake

    cake say:hello             # Description of task

Try running `cake` inside CoffeeScript's main directory, observe the output.

## Setting Up a Task to Compile Scripts (server-side applications)

Using `coffee` on the command-line allows you to compile a directory recursively and output all resulting JavaScript files to another directory. Let's see how we can do that:

    $ cd ~/public/coffee-script
    $ coffee --compile --output lib/ src/

The above command will compile all `src/*.coffee` files to `lib/*.js`. While working on your application you may have different directories from the ones used above, but for the sake of this example we will assume `src` and `lib`.

Let's move on and create our compile task inside a new `Cakefile` under our project's main directory:

    $ cd ~/projects/my-coffee-script-project
    $ vim Cakefile

Paste the following code inside:

```coffeescript
{exec} = require 'child_process'
task 'build', 'Build project from src/*.coffee to lib/*.js', ->
  exec 'coffee --compile --output lib/ src/', (err, stdout, stderr) ->
    throw err if err
    print stdout + stderr
```

The `build` task launches the command we used earlier and waits for it to complete. Upon successful compilation it prints any output (usually none so add your own) or throws an exception should `coffee` have exited with a status code greater than **0** (indicating a compilation failure).

## Concatenating Files (client-side applications)

If you are working on a browser application you may want to concatenate all your files into one and serve that instead. The caveat here is you should concatenate all your source `*.coffee` files before you compile them. If you simply concatenate the resulting `*.js` files, you end up with a closure for each file and duplication of utility functions (CoffeeScript produces these when extending classes, binding functions, etc.)

When we are dealing with multiple files, ordering usually matters unfortunately. We could iterate the `src/` directory looking for all `*.coffee` files using node.js, but the API is asynchronous and the results we get back are not ordered in any way. Instead, we should define a list of files we want to process to build our application file:

```coffeescript
fs     = require 'fs'
{exec} = require 'child_process'

appFiles  = [
  'content/scripts/statusbar'
  'content/scripts/command/quickMacro'
  'content/scripts/command/selectionTools/general'
]

task 'build', 'Build single application file from source files', ->
  appContents = new Array remaining = appFiles.length
  for file, index in appFiles
    fs.readFile "src/#{file}.coffee", 'utf8', (err, fileContents) ->
      throw err if err
      appContents[index] = fileContents
      process() if --remaining is 0
  process = ->
    fs.writeFile 'lib/app.coffee', appContents.join('\n\n'), 'utf8', (err) ->
      throw err if err
      exec 'coffee --compile lib/app.coffee', (err, stdout, stderr) ->
        throw err if err
        print stdout + stderr
        fs.unlink 'lib/app.coffee', (err) ->
          throw err if err
          puts 'Done.'
```

We start off by defining our `appFiles` which we want to concatenate and then process. The `build` task starts by reading all of the files asynchronously and calls `process()` when all files have been read. `process()` in turn writes a temporary file under `lib/` and compiles that to `lib/app.js`. Study the source and modify it as you see fit for your own needs.

## Minifications/Compress Your Files

You can easily extend your `Cakefile` to include a task which calls to a compression utility once your `*.js` files have been generated:

```coffeescript
task 'minify', 'Minify the resulting application file after build', ->
  exec 'java -jar "/home/stan/public/compiler.jar" --js lib/app.js --js_output_file lib/app.production.js', (err, stdout, stderr) ->
    throw err if err
    print stdout + stderr
```

The above executes [Google's Closure Compiler](http://code.google.com/closure/compiler/). You can easily tweak it to call the [YUI Compressor](http://developer.yahoo.com/yui/compressor/) or any other command-line utility.

## Task Options

Tasks in `Cakefile`s can have options. This is important if you want to be able to provide parameters such as the target environment (production, development, etc.), source or target directory, etc. For more information, [check out CoffeeScript's own Cakefile](http://github.com/jashkenas/coffee-script/blob/master/Cakefile#L21).
