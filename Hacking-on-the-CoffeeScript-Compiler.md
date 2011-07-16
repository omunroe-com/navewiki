If you would like to help with CoffeeScript development, or would just like to play around with the compiler to see how it works, follow this guide to prepare your system.

*Note: This has only been tested on Mac OS X.  Details may vary for your particular platform.*

## 1. Prerequisites

Before you can play with the source, you'll need a few things on your system first.

### [Node.Js](https://github.com/joyent/node/wiki/Installation)

You need Node to run the CoffeeScript compiler.  

### [NPM](http://npmjs.org/) (Node Package Manager)

NPM is like Ruby Gems for Node.  It will let us download the rest of the packages we need to make all of this work.

*Note: DON'T install NPM using sudo.  Really, don't.  It is designed to be installed and used without sudo.*

### The CoffeeScript Compiler

CoffeeScript is *self-hosting*.  This means that the CoffeeScript compiler is written in.... CoffeeScript.  If that makes your head hurt, welcome to the world of compilers and language translators :)

    npm install -g coffee-script

*Note: You don't technically need this, as CoffeeScript's git repository includes a version of its own compiler in the bin directory that it uses during the build process.  However, installing this puts CoffeeScript on your path and gives you the "official" version for playing around with things outside of the source directory.*

### [Jison](http://zaach.github.com/jison/docs/#installation)

    npm install -g jison

If you intend to mess around with the actual grammar rules (in `src/grammar.coffee`), you'll need to install the Jison parser generator.  CoffeeScript's parser is not hand-written; instead, Jison is used to convert the `src/grammer.coffee` grammar definition DSL into an LALR parser.  This is equivalent to what Yacc/Bison does, but the resulting code is JavaScript rather than C.

## 2. Fetch the source

    cd your_projects_dir
    git clone git://github.com/jashkenas/coffee-script.git

## 3. Fetch the coffee-script TM (TextMate) Bundle Source

This is required to build the documentation because it has the syntax-highlighting rules for CoffeeScript.

    git clone git://github.com/jashkenas/coffee-script-tmbundle.git

If you don't want to update the documentation, you don't need this.

## 4. Build the JavaScript files from the CoffeeScript source

    cake build

This will use the pre-built CoffeeScript compiler archived in the `bin/` folder to build all the CoffeeScript source files in `src/` into their compiled JavaScript form in `lib/`.

Note that the `bin/cake` and `bin/coffee` scripts are **not** fully-concatenated "finished" scripts.  In the source distribution as well as the installed version, these files simply point to the real source files in `lib/`.

## 5. Run a sanity check

When you make changes to the CoffeeScript source, it's a good idea to do a

    cake build:full

What this does is run `cake build` twice so that the compiler compiles itself with all your latest changes, then runs the CoffeeScript test suite.  If you have broken something (and the test suite has adequate coverage), this should tell you.

## 6. Backing out bad changes

When you're working with a self-hosted compiler and using the latest version of the compiler to compile yourself, as CoffeeScript does, it's easy to run into a situation where you can't compile anymore because the compiler you just built has a fatal bug that you've introduced.  When this occurs, it will usually manifest itself as the `cake build` process suddenly throwing errors, the resulting compiler failing tests during `cake test` or `cake build:full`, or (even more insidiously), CoffeeScript or some other program you're using to test your changes starts behaving weirdly.

If this happens, don't panic, and **don't start all over** by blowing away your local repository and giving up!  Just run 

    git checkout lib/* && git checkout/bin*

This will revert the "built" CoffeeScript back to the way it was in the main repository.  From here, you can look for what caused the problem and try to fix it.  Just keep running the above command to get a working compiler until your compiler starts working, too.

## 7. Build the Parser

As stated in the prerequisites section, if you make any changes to `src/grammar.coffee`, you will need to build the parser from that grammar definition.  To do this, run

    cake build:parser

Be sure to run this **after** running `cake build`.

*Note: Depending on your system setup, you may get an error message that cake `Cannot find module 'jison'`.  If it does, run*

    npm install jison

*without the `-g` option, and try again.*

When cake builds the parser, it puts it in the `lib/` directory, so you don't need to run `cake build` again.

## 8. Running tests

As you are hacking on the source, it's a good idea to make sure you haven't broken anything.  Run

    cake test

periodically for a sanity check.  If you intent to submit a patch to the main CoffeeScript repository, make sure you add new tests to the `test/` folder as necessary.  Just follow an example that's closest to what you are trying to do.  The new tests will be picked up automatically by `cake`.

## 9. Installation

If you would like to make your compiler the official CoffeeScript compiler on your system, then

    sudo cake install

ought to do the trick.  A word of caution, though: only do this when you're sure your compiler is in a stable state.  Otherwise you will have to reinstall your official version.

## 10. A Rakefile, too??

You've probably noticed that there is a Rakefile in addition to the Cakefile.  The Rakefile serves two purposes:

1. It builds the main index.html page (the page that you see when you go to the CoffeeScript home page) from the `documentation/index.html.erb` template
2. It creates (but does not publish) the CoffeeScript Ruby Gem

If you don't need to do either of these things, then you don't have to worry about the Rakefile.  If you would like to change the documentation, however, read on...

## 11. Changing and Building the Documentation

The documentation for CoffeeScript is a bit more complex to build and requires a few more dependencies than those listed in the prerequisites section.

### Ruby

This should be on your system already.

### [Homebrew](https://github.com/mxcl/homebrew/wiki/installation)

Homebrew is the new package manager for OS X that's taken the world by storm.  Much better than MacPorts or Fink.  Try it, you'll like it!

### RubyGems

You already have RubyGems on your system, but it may be out of date.  To check, run

    sudo gem update --system

If it needs updating, it will take care of itself.

### [Oniguruma](http://www.geocities.jp/kosako3/oniguruma/)

Oniguruma is a regular expressions library with nice Ruby bindings.  It's needed by Ultraviolet.

    brew install oniguruma

### [Ultraviolet](http://ultraviolet.rubyforge.org/)

Ultraviolet is a syntax highlighter that uses TextMate bundles as specification files.  The CoffeeScript documentation is run through this to produce the pretty syntax highlighting you see on the introduction page.

    sudo gem install ultraviolet

### Installing the CoffeeScript Ultraviolet Syntax

Now that Ultraviolet is installed, run

    cake build:ultraviolet

To install the syntax file into the Ultraviolet gem location.

*Note: The path to the gem is hard-coded in the Cakefile.  You may have to update the Cakefile to point to your installation of Ultraviolet.  In my case, the gem is installed in...*

    /System/Library/Frameworks/Ruby.framework/Versions/1.8/usr/lib/ruby/user-gems/1.8/gems/ultraviolet-0.10.2/

### Running the documentation task

If all the prerequisites are met, you should be able to run 

    cake doc:site

To build the documentation from the source templates.  Note that this spawns a continuous Rake task that watches the file system for changes to the documentation template and rebuilds the target HTML on demand.  You can always call `cake doc:site`, wait a few seconds, and then `ctrl+c` out of it if you just want to call it to build it once.
