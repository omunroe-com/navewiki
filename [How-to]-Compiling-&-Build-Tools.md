## Prerequisites

`cake` is `coffee`'s little sister (or so I picture things). If you installed CoffeeScript using `npm` then you should already have access to it. If you used `cake install` you have in fact had first-hand experience with the tool.

If you have symlinked `bin/coffee` to a new location on your `$PATH` then you should also symlink `bin/cake`:

    $ ln -s /home/stan/public/coffee-script/bin/cake /usr/local/bin/cake

The above assumes `/usr/local/bin` is in your `$PATH`.

## A basic Cakefile

Running `cake` outside of Coffee's home directory is much likely to end up throwing an exception and printing out a stack trace. If you look closely, you can see why things don't work just yet:

    Error: Cakefile not found in /home/stan/

So, how about we create one:

    $ cd ~
    $ vim Cakefile

Leave the file empty for the time being. Run `cake` again:

    $ cd ~
    $ cake

This should return immediately without printing anything to `stdout`.
