This page details trials and tribulations of getting CoffeeScript to run on Java (via the Rhino JavaScript engine).

There is [this](https://github.com/tbatchelli/cljs) old-ish clojure based route, not tried it and its more than a year old now.

### Issues/Features/Opportunities:
* there is a 64k byte code limit in Java for compiled code, and as both the full/minimised coffee-script.js and the individual files break this when compiled, you have to go down the interpreted javascript route, which means optimisation level -1 (ie its slower than it could be).
* the Rhino engine has no **require** facility, but the library [RingoJS](http://ringojs.org/) is a way to get some CommonsJS facilities.
* using RingoJS requires a newer/full Rhino engine - [see here](http://www.mozilla.org/rhino/) (1.7 as of writing, April 2012).
* using CoffeeScript = require('coffee-script.js') // where this is the full/minimised version, loads ok but does not seem to expose a compile or eval method.  Presume its due to how its expecting to be called and where its attaching things...

I have had some success doing the following:
* using Rhino 1.7 (see above)
* with RingoJS (also above)

Then this Java code:

        RingoRunner runner = new RingoRunner();
        String[] config = {
                "-o", "-1",
                "-m", "js",
                "-m", "js/coffee-script",
                "-m", "js/commonjs-stubs",
                "hello.js"};
        runner.run(config);

and this JS code (hello.js):

    var CoffeeScript = require('coffee-script');

    var compiled_cs = CoffeeScript.compile("print 'cs-boo'");
    eval(compiled_cs);

Works!