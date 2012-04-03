This page details trials and tribulations of getting CoffeeScript to run on Java (via the Rhino JavaScript engine).

There is [this](https://github.com/tbatchelli/cljs) old-ish clojure based route, not tried it and its more than a year old now.

### Issues/Features/Opportunities:
* there is a 64k byte code limit in Java for compiled code, and as both the full/minimised coffee-script.js and the individual files break this when compiled, you have to go down the interpreted javascript route, which means optimisation level -1 (ie its slower than it could be).
* the Rhino engine has no **require** facility, but the library [RingoJS](http://ringojs.org/) is a way to get some CommonsJS facilities.
* using RingoJS requires a newer/full Rhino engine - [see here](http://www.mozilla.org/rhino/) (1.7 as of writing, April 2012).
* using CoffeeScript = require('coffee-script.js') // where this is the full/minimised version, loads ok but does not seem to expose a compile or eval method.  Presume its due to how its expecting to be called and where its attaching things...
* ideally, we'd use the command.coffee/js script to drive the compiling, but I get an issue with the EventEmitter - raised it with StackOverflow - http://stackoverflow.com/questions/9994033/using-ringojs-eventemitter-or-how-to-use-coffeescript-compiler-with-ringojs

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

and so this JS code (hello.js) works :

    var CoffeeScript = require('coffee-script');

    var compiled_cs = CoffeeScript.compile("print 'cs-boo'");
    eval(compiled_cs);

and this JS code will compile a directory of .coffee files into the specified target directory:

    var fs = require("fs");
    var CoffeeScript = require("coffee-script");

    var src_path = "src-coffee-script/";
    var src_files = fs.list(src_path);

    for (var i=0; i<src_files.length; i++)
    {
        var src_file = src_files[i];
        var js_file = "js-compiled/"+fs.base(src_file,".coffee")+".js";
        print("Processing file:"+src_file+", compiling into:"+js_file);
        var src = fs.read(src_path+"/"+src_file);
        var js = CoffeeScript.compile(src);
        fs.write(js_file, js);
    }

