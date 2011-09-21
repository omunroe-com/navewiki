If you are writing CoffeeScript (CS) that you intend to run in the browser, read this first:

* Generate JavaScript (JS) files on the server with "coffee -c".
* Serve the JS files just like you would serve any other JS files on your project.

Most of the rest of this article pertains to JS directly, and CS only indirectly.  Once you've used "coffee -c" to transcompile CS to JS, you are fundamentally dealing with JS.  CS does nothing (yet) to fundamentally change how JS files get loaded in the browser.

When you are serving up JS to a client, you want to follow these rules:

* Load script tags in the order that you want them executed. (CS users: you want to serve up the .js files here).
* Protect each script with a top-level function safety wrapper. (CS users: you get this for free when you run "coffee -c".)
* Within each script, if you want variables to be accessible from other scripts, assign them to be members of the "window" object, which will usually be "this" at the high level.  For example, this.myInterface = myInterface.  (CS users: you can say "@myInterface = myInterface").


