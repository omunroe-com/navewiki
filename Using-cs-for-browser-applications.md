If you are writing CoffeeScript (CS) that you intend to run in the browser, read this first:

* Generate JavaScript (JS) files on the server with "coffee -c".
* Serve the JS files just like you would serve any other JS files on your project.

Most of the rest of this article pertains to JS directly, and CS only indirectly.  Once you've used "coffee -c" to compile CS to JS, you are fundamentally dealing with JS.  CS does nothing (yet) to fundamentally change how JS files get executed in the browser.

When you are serving up JS to a client, you want to follow these rules:

* Load script tags in the order that you want them executed. (CS users: you want to serve up the .js files here, NOT the .coffee files).
* Protect each script with a top-level function safety wrapper. (CS users: you get this for free when you run "coffee -c".)
* Within each script, if you want variables to be accessible from other scripts, assign them to be members of the "window" object, which will usually be "this" at the top level.  For example, in JS you might say "this.myInterface = myInterface".  (CS users: you can say "@myInterface = myInterface").  Use a specific name for your interface that won't interfere with names exported by other modules in the web page.

Those are the basics.

Once you get a simple program up and running, there are more advanced topics that are not covered in great depth here.  Just some things to think about:

* You can set up your dev environment to generate .js scripts automatically after every change, using the "coffee -wc" option.
* For production deployments, there are packaging/deployment solutions in various frameworks to manage your JS assets more efficiently, and some of these have good CS integration.
* Naming conflicts can mostly be avoided by using unique names, but conflicts are inevitable, especially when brevity is key (think "$" and "_").  If you want to use short names by default, while playing nice with others, implement a noConflict() feature.  A good library to mimic is the underscore.js library.

