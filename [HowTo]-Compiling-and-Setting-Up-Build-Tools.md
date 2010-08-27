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

## Setting Up a Task to Compile Scripts

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
