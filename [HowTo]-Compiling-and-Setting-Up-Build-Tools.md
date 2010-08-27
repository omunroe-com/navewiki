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

Yes, we are going for the infamous *Hello World* example, but with a spin -- inside a `Cakefile`. If you have worked with `rake` or `make` then you should already have an idea of how things work. You define a task and use `cake [task name]` to execute it. Let's get started:

    $ cd ~
    $ vim Cakefile

Define our task as `say:hello`:

```coffeescript
task 'say:hello', 'Description of task say:hello', ->
  puts 'Hello World!'
```

Save and exit back to the shell. Next, let's run our newly created task:

    $ cake say:hello
    Hello World!

If you run `cake` without any arguments, i.e., no task name you would get a list of all available tasks and their description, neat!

    $ cake

    cake say:hello             # Description of task say:hello

Try running `cake` inside CoffeeScript's main directory, observe the same behaviour (but different tasks).
