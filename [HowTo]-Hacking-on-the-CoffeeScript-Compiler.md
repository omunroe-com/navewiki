If you would like to help with CoffeeScript development, or would just like to play around with the compiler to see how it works, follow this guide to prepare your system.

*Note: This has only been tested on Mac OS X.  Details may vary for your particular platform.*

## Quick Start

    git clone git://github.com/jashkenas/coffeescript.git
    cd coffeescript
    # …make your changes
    bin/cake build:full
    bin/coffee <your testing sample code>

For the full details, read on!

## 1. Prerequisites

Before you can play with the source, you’ll need a few things on your system first.

### [Node.js](https://github.com/joyent/node/wiki/Installation), including npm.

You need Node to run the CoffeeScript compiler.  

### The CoffeeScript Compiler

CoffeeScript is *self-hosting*.  This means that the CoffeeScript compiler is written in.... CoffeeScript.  If that makes your head hurt, welcome to the world of compilers and transpilers :)

    npm install -g coffeescript

*Note: You don’t technically need this, as CoffeeScript’s git repository includes a version of its own compiler in the bin directory that it uses during the build process.  However, installing this puts CoffeeScript on your path and gives you the “official” version for playing around with things outside of the source directory.*

## 2. Fetch the source

    cd your_projects_dir
    git clone git://github.com/jashkenas/coffeescript.git

## 3. Build the JavaScript files from the CoffeeScript source

    cake build

This will use the pre-built CoffeeScript compiler archived in the `bin/` folder to build all the CoffeeScript source files in `src/` into their compiled JavaScript form in `lib/`.

Note that the `bin/cake` and `bin/coffee` scripts are **not** fully-concatenated “finished” scripts.  In the source distribution as well as the installed version, these files simply point to the real source files in `lib/`.

## 4. Run a sanity check

When you make changes to the CoffeeScript source, it’s a good idea to do a

    cake build:full

What this does is run `cake build` twice so that the compiler compiles itself with all your latest changes, then runs the CoffeeScript test suite.  If you have broken something (and the test suite has adequate coverage), this should tell you. Note that this does *not* rebuild the parser; you need to also run `cake build:parser` to trigger that.

## 5. Backing out bad changes

When you’re working with a self-hosted compiler and using the latest version of the compiler to compile yourself, as CoffeeScript does, it’s easy to run into a situation where you can’t compile anymore because the compiler you just built has a fatal bug that you’ve introduced.  When this occurs, it will usually manifest itself as the `cake build` process suddenly throwing errors, failed tests during `cake test` or `cake build:full`, or (even more insidiously), weird behaviors in CoffeeScript or some other program you’re using to test.

If this happens, don’t panic, and **don’t start all over** by blowing away your local repository and giving up!  Just run 

    git checkout lib

This will revert the “built” CoffeeScript back to the way it was in the main repository.  From here, you can look for what caused the problem and try to fix it.  Just keep running the above command to get a working compiler until your compiler starts working, too.

## 6. Build the Parser

As stated in the prerequisites section, if you make any changes to `src/grammar.coffee`, you will need to build the parser from that grammar definition.  To do this, run

    cake build:parser

Be sure to run this **after** running `cake build`. When cake builds the parser, it puts it in the `lib/` directory, so you don’t need to run `cake build` again.

## 7. Running tests

As you are hacking on the source, it’s a good idea to make sure you haven’t broken anything.  Run

    cake test

periodically for a sanity check.  If you intend to submit a patch to the main CoffeeScript repository, make sure you add new tests to the `test/` folder as necessary.  Just follow an example that’s closest to what you are trying to do.  The new tests will be picked up automatically by `cake`.

## 8. Installation

If you would like to make your compiler the official CoffeeScript compiler on your system, then

    sudo cake install

ought to do the trick.  A word of caution, though: only do this when you’re sure your compiler is in a stable state.  Otherwise you will have to reinstall your official version.

## 9. Guidelines for submitting changes back to the master repository

1. Don’t submit anything under the `docs` folder. The files under there will be rebuilt by the CoffeeScript team when a release is tagged.
2. Changes without tests will generally not be accepted unless it’s a fix to a regression or you can make the argument that a test is more trouble than it’s worth

## 10. Preparing a new release

0. Make sure that new features are properly documented. If not, try to do so
   by sending PRs. After those have been merged or otherwise fixed, proceed
   with the following steps.

1. Update the version number in `package.json`.

2. Write a change log entry in `documentation/sections/changelog.md`. The easiest way is
   to copy the previous entry and then adjust it.

   It is handy to base the change log entry on the commit log since the last
   version. If the last version is `1.9.9` you may run the following:

   ```sh
   git log 1.9.9.. –reverse –no-merges –pretty=medium >changes
   ```

   That’ll give you a nice little list of things that has happened since `1.9.9`
   in chronological order. Edit the `changes` file to remove commits that do not
   need to be mentioned explicitly in the change log and reduce related commits
   to single entries. Then turn them into nice little summarizing bullet points
   and move them over to `documentation/sections/changelog.md`. It helps visiting
   related issues and PRs on GitHub while doing this.

3. Run `cake release` to rebuild the JavaScript files from the CoffeeScript
   source, which should include the new version number. It also runs the tests
   just to make sure that everything is good to go. It also rebuilds the
   documentation, including test.html and the annotated source. In short,
   everything.

4. Commit all the changes. If you’re updating to `9.0.0`, `CoffeeScript 9.0.0`
   is a good commit message.

5. Send a PR! (Amend and force-push changes requested by reviewers if needed.)
