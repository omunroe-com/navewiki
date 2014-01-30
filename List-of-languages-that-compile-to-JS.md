#### CoffeeScript Family (& Friends)

* [[CoffeeScript|http://jashkenas.github.com/coffee-script/]] Unfancy JavaScript
* [[CoffeeScript II: The Wrath of Khan|https://github.com/michaelficarra/CoffeeScriptRedux]] Rewrite of the CS compiler

###### Family (share genes with CoffeeScript)

* [[Coco|https://github.com/satyr/coco]] A CoffeeScript dialect that aims to be more radical and practical, also acts as a test bed for features that get imported in CoffeeScript.
    * [[LiveScript|http://livescript.net]] is a fork of Coco that is much more compatible with CoffeeScript, more functional, and with more features.
* [[IcedCoffeeScript|http://maxtaco.github.com/coffee-script/]] A CoffeeScript dialect that adds support for `await` and `defer` keywords which simplify async control flow.
* [[Parsec CoffeeScript|https://github.com/fab13n/parsec-coffee-script]] CS based on parser combinators. The project's aim is to add static metaprogramming (i.e. macros + syntax extensibility) to Coffee Script (CS), similar to how Metalua adds such features to Lua. The resulting compiler, once merged with the official compiler, should be usable as a drop-in replacement for it.
* [[Contracts.coffee|https://github.com/disnet/contracts.coffee]] A dialect of CoffeeScript that adds built-in support for contracts.
* [[Uberscript|https://github.com/jstrachan/coffee-script/blob/master/TypeAnnotations.md]], a CoffeeScript fork that adds type annotations which are compiled to Google closure compiler type annotation comments.
* [[ToffeeScript|https://github.com/jiangmiao/toffee-script]] A dialect of CoffeeScript that support Asynchronous Syntax and Regexp operator =~
* [[Caffeine|https://github.com/ich/caffeine]] A dialect of CoffeeScript that support packages and classes import, useful for browser applications
* [[heap.coffee|https://github.com/syg/heap.coffee]] A dialect of CoffeeScript that offers a C-like type system with manual memory management
* [[EmberScript|http://emberscript.com]] Ember.js-infused CoffeeScript.

###### Friends (philosophically related)

* [[Kaffeine|https://github.com/weepy/kaffeine]] Enhanced Syntax for JavaScript.
* [[Jack|https://github.com/creationix/jack]] Making programming playful.
* [[move|https://github.com/rsms/move]] A simpler and cleaner programming language.
* [[Moescript|https://github.com/moescript/moescript]] Indent-based language
* [[pogoscript|http://pogoscript.org/]] language that emphasises readability, handles async control flow nicely, is friendly to domain specific languages and compiles to regular JavaScript
* [[LispyScript|http://lispyscript.com/]] A JavaScript with Lispy syntax and Macros.
* [[Wisp|http://github.com/Gozala/wisp]] Wisp is a homoiconic JavaScript dialect with clojure syntax, s-expressions and macros.
* [[Hot Cocoa Lisp|https://github.com/olleicua/hcl]] A Lisp-like language that compiles to JavaScript.
* [[Sibilant|http://sibilantjs.info]] JavaScript with a lisp.
* [[Ham|https://github.com/jameskeane/ham-script]] looks very similar to Javascript at first, but offers (hopefully) many useful features
* [[GorillaScript|http://ckknight.github.com/gorillascript/]]  Compile-to-JavaScript language designed to empower the user while attempting to prevent some common errors, offers Macros and optional Typing
* [[RedScript|https://github.com/AdamBrodzinski/RedScript]] Ruby flavored JavaScript.
* [[Daonode|https://github.com/chaosim/daonode]] functional logic solver, compiler.

#### JavaScript Extensions

###### Security enforcing JavaScript

* [[Caja|http://code.google.com/p/google-caja/]] Compiles ES5/strict to ES3 and supports object-capabilities
* [[ADsafe|http://www.adsafe.org/]] Client-side static verifier and API, making third party scripts safe.
* [[FBJS|http://developers.facebook.com/docs/fbjs]] Facebook JavaScript, used for scripting FBML (Facebook Markup Language) gadgets.
* [[Jacaranda|http://jacaranda.org/]] Static verifier supporting object-capabilities.
* [[Microsoft Web Sandbox|http://websandbox.livelabs.com/]] Technology preview of securing web content through isolation.
* [[Gatekeeper|http://research.microsoft.com/en-us/projects/gatekeeper/]] Microsoft Research project.
* [[Dojo Secure|http://www.sitepen.com/blog/2008/08/01/secure-mashups-with-dojoxsecure/]] Framework for building secure mashups.
* [[Local.js|http://grimwire.com/local/]] uses Web Workers to sandbox applications and a RESTful messaging protocol called HTTPL (HTTP Local) to communicate between them

###### Static typing

* Some of the ones listed below are also statically typed, such as mobl, GWT, JSIL, NS Basic, and Haxe.
* [[Dart|http://www.dartlang.org/]] by Google. C/Java-like syntax with optional typing.
* [[TypeScript|http://www.typescriptlang.org/]] by Microsoft. Typed superset of JavaScript.
* [[TeJaS|http://www.jswebtools.org/]] from Brown PLT. Types for JavaScript (itself).
* [[asm.js|http://asmjs.org/]] - subset of JavaScript that can be used as a low-level, efficient target language for compilers.  Now included in Firefox.
* [[JavaScript++|http://jspp.javascript.am/]] adds pluggable type system and type inference, among other features
* [[MileScript|http://milescript.org/]] [commercial] A strongly-typed language similar to C# and Java, but which compiles to JS. free for non-profit, educational use.
* [[Mascara|http://www.mascaraengine.com/]] [commercial] Enhances JavaScript with powerful features like classes, namespaces and type-checking.
* [[Roy|http://roy.brianmckenna.org/]] tries to meld JavaScript semantics with some features common in static functional languages
* [[Elm|http://elm-lang.org/]] type-safe functional language that compiles to HTML, CSS, and JavaScript.
* [[JSX|http://jsx.github.com/]] a faster, safer, easier alternative to JavaScript
* [[Este.js|https://github.com/Steida/este/]] Google Closure written in CoffeeScript statically compiled to JavaScript (and much more).
* [[Swym|http://cheersgames.com/swym/wiki/index.php?title=Main_Page]] - statically typed, with type inference and generics
* [[Typecast.js|http://typecastjs.org]] - Javascript platform for statically typed variables without a custom compiler.
* [[purescript|https://github.com/paf31/purescript]] - statically typed compile-to-JS language with basic extensible records and type-safe block

###### Synchronous to Asynchronous JavaScript Compilers (CPS)
* [[Streamline.js|https://github.com/Sage/streamlinejs]] Uses underscore (_) to stand for callbacks. This [[fork|https://github.com/willconant/streamlinejs]] preserves line numbers for debugging.
* [[mobl|http://www.mobl-lang.org]] The new language for programming the mobile web.
* [[StratifiedJS|http://onilabs.com/stratifiedjs/]] JavaScript + structured concurrency.
* [[NarrativeJS|http://www.neilmix.com/narrativejs/doc/]] JavaScript extension with asynchronous futures and promises.
* [[jwacs|http://chumsley.org/jwacs/]] JavaScript With Advanced Continuation Support.
* [[Wind.js|https://github.com/JeffreyZhao/wind]] Wind.js is an advanced library which enable us to control flow with plain JavaScript for asynchronous programming (and more) without additional pre-compiling steps.
* [[TameJS|http://tamejs.org/]] adds new keywords 'await' and 'defer'
* [[async.js|https://github.com/caolan/async]] Async utilities for node and the browser
* [[Continuation.js|https://github.com/BYVoid/continuation]] A lightweight JIT compiler for simplifying asynchronous JavaScript programming with no runtime dependences. It supports both Node.js and browser-side JavaScript and is compatible with CoffeeScript (also TypeScript, and any other scripts compile to js).
* [[Kal|http://rzimmerman.github.io/kal/]] makes asynchronous programming easy and clean by allowing functions to pause and wait for I/O, replacing an awkward callback syntax with a clean, simple syntax
* [[JSPipe|http://jspipe.org]] provides JavaScript primitives to write async code without callbacks or chained functions. Inspired by Goroutines and Channels found in Go and in Clojure. For Web and NodeJS. ES5 and ES6. 

###### JavaScript Language Extensions

* [[ContextJS|https://www.hpi.uni-potsdam.de/hirschfeld/trac/Cop/wiki/ContextJS]] is an implementation of [[Context-oriented Programming|http://www.hpi.uni-potsdam.de/hirschfeld/cop/]] for JavaScript.
* [[Objective-J|http://en.wikipedia.org/wiki/Objective-J]] Shares with JavaScript the same relationship that Objective-C has with the C programming language: that of being a strict, but small, superset.
* [[Mochiscript|https://github.com/jeffsu/mochiscript]] Object-oriented JavaScript with syntactic sugar. Released as a Ruby gem.
* [[jangaroo|http://www.jangaroo.net/home/]] AS3 (ActionScript) to JavaScript.
* [[Flapjax|http://flapjax-lang.org/]] Event-driven, reactive evaluation.
* [[jLang|http://jlang.org/]] adds object oriented syntax, namespaces, operators overriding
* [[Restrict Mode|http://restrictmode.org/]]
* [[TIScript|http://www.codeproject.com/KB/recipes/TIScript.aspx]] gentle extension of JavaScript
* [[Six|https://github.com/matthewrobb/six]] Six is a language super-set of JavaScript that enables new syntactic features from the 6th edition of ECMAScript to be used, through a transpiler, in your scripts today.
* [[js--|https://github.com/janpaul123/jsdares/tree/master/app/jsmm-applet/jsmm]] Javascript subset for [[interactive/visual programming|http://www.jsdares.com/blindfold]].

#### Ruby

* [[Opal|http://opalrb.org]] Ruby to Javascript compiler.
* [[HotRuby|http://hotruby.yukoba.jp/]] Runs opcode, compiled by YARV on Ruby inside a web browser or in Flash.
* [[ColdRuby|https://github.com/whitequark/coldruby]] Compiler of Ruby 1.9 MRI bytecode, and a runtime written in JavaScript to aid in execution of Ruby code.
* [[rb2js|http://rb2js.rubyforge.org/]] Converts Ruby to JavaScript.
* [[RubyJS|http://www.ntecs.de/blog/articles/2007/01/08/rubyjs-javascript-no-thank-you/]] A successor to rb2js
* [[Red|https://github.com/jessesielaff/red]] Writes like Ruby and runs like JavaScript
* [[Quby|http://www.playmycode.com/docs/quby]] Used for game coding site, [[open source|https://github.com/PlayMyCode/Quby]].
* [[8ball|https://github.com/mattknox/8ball]] ruby-to-javascript source-to-source transformer

#### Python

* [[PYXC-PJ|http://pyxc.org/]] [CS friend] Python to JS. Can generate a (line/col)-number mappings file.
* [[Pyjamas|http://pyjs.org/]] Python to JS.
* [[Pyjaco|http://pyjaco.org/demo]] Python to JavaScript compiler with module support.
* [[Pyjs|https://github.com/anandology/pyjs]] Python to (readable) JS.
* [[Skulpt|http://www.skulpt.org/]] Python. Client side.
* [[PyCow|https://github.com/p2k/PyCow]] Python to MooTools JS.
* [[PyvaScript|http://www.allbuttonspressed.com/blog/django/2010/07/PyvaScript-Pythonic-syntax-for-your-browser]] Python-like syntax to JavaScript.
* [[RapydScript|https://bitbucket.org/pyjeon/rapydscript]] Improved PyvaScript
* [[Brython|http://brython.info/]] browser python
* [[PythonScript|http://apppyjs.appspot.com/]] Python-like compiled to Javascript
* [[pythonscript|https://github.com/DenerosArmy/pythonscript]] Python compiled to readable Javascript using  the AST. (proof of concept) 

#### Erlang
* [[LuvvieScript|http://luvv.ie]] a browser-based dom-scripting language that is a strict sub-set of Erlang which is AST-to-AST transpiled to Javascript ([[code |https://github.com/hypernumbers/luvviescript]])

#### Perl

* [[Perlito|https://github.com/fglock/Perlito]] Project to compile Perl 5/6 to JavaScript, Ruby, SBCL, and Go.

#### Java/JVM

* [[GWT|http://code.google.com/webtoolkit/]] Google Web Toolkit, compiles Java to JavaScript.
* [[Java2Script|http://j2s.sourceforge.net/]] Eclipse Java to JavaScript compiler plugin and JavaScript version of SWT.
* [[j2js|http://www.j2js.com/]] Java bytecode to JavaScript.
* [[Strongly-Typed JavaScript (STJS)|http://st-js.sourceforge.net/]] - JavaScript code generator from Java source. It is built as a Maven plugin.
* [[BicaJVM|https://github.com/nurv/BicaVM]] JavaScript implementation of JVM.
* [[Doppio|http://int3.github.com/doppio/about.html]] JVM interpreter on Coffeescript.
* [[Processing|http://processingjs.org/]], a Java-based visualization language that interprets to JavaScript.
* [[Kotlin|http://confluence.jetbrains.net/display/Kotlin/Welcome]] has a nascent JavaScript backend.
* [[Ceylon|http://ceylon-lang.org/]] a modular static-typed JVM language compilable to JavaScript.
* [[GrooScript|http://grooscript.org/]] a framework to convert Groovy code to Javascript.
* [[node-jvm|https://github.com/YaroslavGaponov/node-jvm]] java virtual machine in pure node.js
* [[Bck2Brwsr|http://wiki.apidesign.org/wiki/Bck2Brwsr]] Run "browserified" Java Code in, well, the browser.
* [[QWT|http://qooxdoo.org/contrib/project/qwt]] QWT consists of a Java-to-JavaScript compiler, a prepared library of Qooxdoo componente (version 0.7.x) and some other tools. Similar to GWT

#### Scala

* [[Scala.js|http://www.scala-js.org/]] A Scala to JavaScript compiler
* [[js-scala|https://github.com/js-scala/js-scala]] JavaScript as an embedded DSL in Scala 
* [[scalagwt|http://code.google.com/p/scalagwt/]] enhanced GWT (accepts jribble as well as Java) plus Scala to jribble.
* [[JScala|http://jscala.org]] Scala macro that produces JavaScript from Scala code.

#### C#, F#, .NET related languages

* [[jsc|http://jsc.sourceforge.net/]] [experimental] Recompile your .NET assembly to JavaScript, ActionScript, PHP or Java.
* [[JSIL|https://github.com/kevingadd/JSIL]] MSIL (.NET bytecode) to Javascript
* [[Script#|http://scriptsharp.com]] Compiles C# to JS.
* [[Prefix|http://www.toptensoftware.com/prefix/]] in development
* [[Blade|https://github.com/vannatech/blade]] Visual Studio add-on for converting C# to JavaScript
* [[SharpKit|http://sharpkit.net/]] [commercial] C# to JavaScript Cross-Compiler
* [[Saltarelle|http://www.saltarelle-compiler.com/]] C# to JavaScript Compiler
* [[FunScript|https://github.com/ZachBray/FunScript/]] F# to JavaScript compiler with JQuery etc. mappings through a TypeScript type provider
* [[Pit|https://github.com/fsharp/pitfw]] F# to Javascript compiler
* [[WebSharper|http://www.websharper.com/]] Lets you compile F# to JS.
* [[NemerleWeb|https://github.com/NemerleWeb/NemerleWeb/]] Nemerle language compiled to JS.
* [[Blue Storm|https://www.assembla.com/spaces/bluestorm/wiki/]] F# to JavaScript (and some other languages).
* [[JScriptSuite|http://jscriptsuite.com/]] .NET to JavaScript compiler (cross browser API, client site controls and components).

#### Lisp, Scheme

* [[BiwaScheme|http://www.biwascheme.org/]] Scheme(R6RS) in JavaScript
* [[ClojureScript|https://github.com/clojure/clojurescript]] Clojure to JS, the official version. Supports the majority of Clojure including persistent datastructures.
* [[clojurejs|https://github.com/kriyative/clojurejs]] Subset of Clojure to JS.
* [[Chlorinejs|https://github.com/chlorinejs/chlorine]] A fork of ClojureJs with a port of clojure.core library.
* [[wisp|https://github.com/Gozala/wisp]] Homoiconic JS with clojure syntax, s-expressions & macros.
* [[EdgeLisp|https://github.com/manuel/edgelisp]] A Lisp in the tradition of Common Lisp
* [[Fargo|https://github.com/jcoglan/fargo]] Scheme in JavaScript  
* [[Moby Scheme|https://github.com/dyoo/moby-scheme]] A Scheme running in JS.
* [[nconc|https://github.com/patrickdlogan/nconc]] scheme interpreter in javascript with stack-friendly tail calls and full call/cc
* [[Parenscript|http://common-lisp.net/project/parenscript/]] Subset of Common Lisp to JS.
* [[Ralph|https://github.com/turbolent/ralph]] Lisp-1 dialect that compiles to JavaScript, inspired by Dylan
* [[scheme2js|http://www-sop.inria.fr/indes/scheme2js/]] Scheme to JavaScript.
* [[Scriptjure|https://github.com/arohner/scriptjure]] Library for generating JavaScript from Clojure forms.
* [[Spock|http://wiki.call-cc.org/eggref/4/spock]] A Scheme to JavaScript compiler that uses Henry Baker's Cheney-on-the-MTA compilation strategy  
* [[Whalesong|http://hashcollision.org/whalesong/]] Racket to JS compiler
* [[Oppo|https://github.com/benekastah/oppo]] A javascripter's lisp. Inspired by javascript, clojure and coffeescript. Compiler built using [[Jison|http://zaach.github.com/jison/docs/]].
* [[Outlet|https://github.com/jlongster/outlet]] A simple Lisp that supports CPS and in-browser stepping debugging, and other things. In development.

#### OCaml

* [[Ocamljs|https://github.com/jaked/ocamljs]] OCaml to JS.
* [[O'Browser|http://www.pps.jussieu.fr/~canou/obrowser/tutorial/]] OCaml bytecode interpreter in JS.
* [[Js_of_ocaml|http://ocsigen.org/js_of_ocaml/]] OCaml bytecode to JS compiler.

#### Haskell

* [[UHC|http://www.cs.uu.nl/wiki/bin/view/Ehc/UhcUserDocumentation#5_7_3_jscript_Core_based_JavaScr]] (Utrecht Haskell Compiler) backend converts UHC core to JavaScript, allowing the compiling of Haskell code to JS.
* [[ghcjs|https://github.com/ghcjs/ghcjs]] Compile normal Haskell into JS
* [[jmacro|http://hackage.haskell.org/package/jmacro]] Quasi-Quoted JS that you can insert Haskell values into (there is also [[shakespeare-js|http://hackage.haskell.org/package/shakespeare-js]] for that purpose), but also supports a more haskellish syntactic version of javascript.
* [[https://github.com/aculich/lambdascript|]] Compile a subset of Haskell into JS
* [[YHC|http://www.haskell.org/haskellwiki/Yhc/Javascript]] (York Haskell Compiler) backend, as above but with YHC core language.
* [[jshaskell|http://code.google.com/p/jshaskell/]]
* [[haste|https://github.com/valderman/haste-compiler]]
* [[fay|http://fay-lang.org/]] A proper subset of Haskell that compiles to JavaScript
* [[forml|http://texodus.github.io/forml/index.html]] A contemporary programming language intended to approximate the safety of Haskell and the expressiveness of Ruby.

#### Smalltalk

* [[Amber|http://amber-lang.net/]] - formerly known as Jtalk
* [[Clamato|http://clamato.net/]] a Smalltalk dialect that is designed to operate within the JavaScript runtime.
* [[Silver Smalltalk|http://silversmalltalk.wordpress.com/]] [commercial?] Smalltalk in the browser. (Still active?)
* [[Lively Kernel|http://www.lively-kernel.org/]] - smalltalk/squeak-like development environment in the browser.  See also [[Avocado|http://avocadojs.com/]], built on top of it.
* [[Little Smallscript|https://github.com/ympbyc/LittleSmallscript]] Little Smalltalk to Javascript translator.

#### C/C++

* [[Emscripten|http://emscripten.org/]] LLVM to JavaScript compiler.  LLVM is "an aggressive open-source compiler for C and C++," as well as other languages.
* [[Duetto|http://leaningtech.com/duetto/]] LLVM to JavaScript compiler. "compiles C++ applications to binary code and Javascript"
* [[maja|http://lethalman.hostei.com/maja/index.html]] vala (gobject) to javascript
* [[Clue|http://cluecc.sourceforge.net/]] C language compiler to different runtimes (Lua, JS, Perl 5, C, Java, CL).
* [[LLJS|http://lljs.org/]] typed dialect of JavaScript that offers a C-like type system with manual memory management
* [[Mandreel|http://mandreel.com/]]  Can convert C++ and Objective-C applications based on OpenGL ES to JavaScript or Action Script 3 web application. 

#### Basic

* [[NS Basic/App Studio|http://www.nsbasic.com/app/]] [commercial] Visual Basic-style BASIC to JavaScript compiler. Includes IDE. Targets iOS and Android
* [[qb.js|http://stevehanov.ca/blog/index.php?id=92/]] An implementation of QBASIC in Javascript

#### Pascal

* [[Smart Mobile Studio|http://op4js.optimalesystemer.no/]] [commercial] Object Pascal to JavaScript compiler and Delphi like IDE that brings classes, inheritance, interfaces and more to JavaScript
* [[Elevate Web Builder|http://www.elevatesoft.com/products?category=ewb]] [commercial]  Visual development tool for web applications that compiles standard Object Pascal source code into JavaScript

#### Go

* [[Go2js|https://github.com/kless/go2js]] Line-to-line translator from Go to JavaScript.
* [[GopherJS|https://github.com/neelance/gopherjs]] A transpiler from Go to JavaScript.


#### Multitarget

* [[Haxe|http://haxe.org/]] compiles to several platforms (C++, Flash, JS, Neko, PHP).
* [[Fantom|http://fantom.org/]] Evolutionary object-oriented language emphasizing succinct and effective APIs (JVM, CLR, JS).
* [[LZX (Laszlo XML)|http://labs.openlaszlo.org/trunk-nightly/laszlo-explorer/index.html?lzr=swf10#_lzbookmark=Laszlo%20in%2010%20Minutes]] LZX is [[OpenLaszlo's|http://www.openlaszlo.org]] declarative user interface language, which is compiled into JavaScript 2 as an intermediary format, and further compiled into either JavaScript 1.5 or ActionScript 3.
* Clue and jsc above target multiple runtimes in addition to javascript
* [[Nimrod|http://nimrod-lang.org]] compiles to C and JavaScript
* [[Monkey|http://monkeycoder.co.nz/]] [commercial] compiles to several platforms (JavaScript, ActionScript 3, C++, Java, CSharp).

#### Tierless languages (produce both client & server)

* [[Fun|https://github.com/marcuswestin/fun]] A programming language for realtime webapps - compiles to client-side and server-side JS.
* [[Ur|http://impredicative.com/ur/]] In the tradition of ML and Haskell.
* [[mobl|http://www.mobl-lang.org]] The new language for programming the mobile web.
* [[E|http://wiki.erights.org/wiki/E-on-JS]] Compiles E to JS. E is a secure distributed persistent pure object language.
* [[Sugar|https://github.com/sebastien/sugar]] new programming language designed to replace JavaScript
for client-side (and server-side) web development
* [[Opa|http://www.opalang.org/]] write your complete application in just one language, and the compiler will transform it into a self-sufficient executable

#### Visual programming tools
* [[Waterbear|http://waterbearlang.com/]]
* [[Snap|http://snap.berkeley.edu/snapsource/snap.html]] - Javascript of BYOB, which is a fork of [[Scratch|http://alpha.scratch.mit.edu/]]
* [[ScriptBlocks|http://code.google.com/p/scriptblocks/]]
* [[Illumination|http://radicalbreeze.com/]] [Commercial] Visual, cross-platform tool creates apps for Android, iPhone, iPad, Desktops and HTML5 or Flash websites.  [[The I language|http://blog.radicalbreeze.com/?p=213]] underlies the tool.
* [[JsMaker|http://jsmaker.com/jsmaker/]] visual JavaScript programming
* [[Meemoo|http://meemoo.org/]] flow-based visual programming framework for hackable web apps
* [[NoFlo|http://noflojs.org/]] JavaScript implementation of Flow-Based Programming. Programs (network graphs) can be visually created with [[DrawFBP|http://www.jpaulmorrison.com/cgi-bin/wiki.pl?DrawFBP]]
* [[Blockly|http://code.google.com/p/google-blockly/]] web-based, graphical programming language. Users can drag blocks together to build an application
* [[Maeda Block|http://maedablock.com/]] - visual game programming language powered by enchant.js and Google Blockly.  See also the [[Japanese version|http://maedablock.jp/]].

#### SQL
* [[sql-parser|https://github.com/forward/sql-parser]]
* [[sqld3|https://github.com/steveyen/sqld3]]

#### PHP
* [[phype|http://code.google.com/p/phype/]] run PHP code directly in your browser
* [[uniter|https://github.com/asmblah/uniter]] run PHP code in Node.js or the browser

#### Others

* [[Oia|https://github.com/stevedekorte/oia]] A port of Io to JavaScript.
* [[Plaid|http://www.plaid-lang.org]] A gradually-typed, typestate-oriented language designed as a better Java.
* [[Quixe|https://github.com/erkyrath/quixe]] a Glulx VM interpreter written in Javascript
* [[Gnusto|https://github.com/curiousdannii/gnusto]] a Z-Machine VM interpreter written in Javascript
* [[Logo Interpreter|http://www.calormen.com/logo/]]
* [[p2js|https://github.com/urandom/p2js]] perl to javascript converter
* [[Reb2Static|https://github.com/jankom/RebToStatic]] Rebol to Javascript
* [[RPN|https://github.com/adrusi/rpn]] Interpreter for a language with a Reverse Polish Notation syntax.
* [[jsForth|http://forthfreak.net/jsforth80x25.html]]
* [[wForth|http://solidcoding.blogspot.com/2008/12/wforth-javascript-forth-interpreter.html]]
* [[Agda|http://wiki.portal.chalmers.se/agda/pmwiki.php]] a dependently typed functional programming language and mechanized proof assistant
* [[XLCC|https://github.com/baxtree/xlcc]] Interpret LCC into Javascript on node
* [[SMLtoJs|http://www.smlserver.org/smltojs/]] SML to Javascript compiler
* [[lua.js|https://github.com/mherkender/lua.js]] Lua parser
* [[Brozula|https://github.com/creationix/brozula]] Lua bytecode interpreter
* [[Pygmy|http://peterolson.github.com/Pygmy/Docs/index.html]] a dynamic language that compiles to Javascript designed to be readable but concise enough to be competitive in code golf.
* [[browserl|http://svahne.github.com/browserl/]] An Erlang Emulator written in javascript
* [[ErlyJS|https://github.com/hassy/erlyjs]] (abandoned) Javascript to Erlang compiler
* [[Topaz|https://github.com/giesse/Project-SnowBall]] Rebol inspired language on top of Javascript
* [[NGN APL|https://github.com/ngn/apl]] an APL-to-JavaScript compiler written in CoffeeScript
* [[CobolScript|https://github.com/ajlopez/CobolScript]] COBOL language compiler to Javascript.
* [[Idris|https://github.com/edwinb/Idris-dev]] Dependently typed functional language with a JavaScript backend.
* [[dogescript|http://zachbruggeman.me/dogescript/]]
* [[Wortel|https://github.com/atennapel/Wortel]] J/APL inspired language with Polish Notation, compiles to JavaScript.
* [[JEnglish|http://jenglish.org/]] interprets regular English statements into HTML/CSS

#### Tools for Compiler Writers

#### JavaScript Parsers and Extensions

* [[Narcissus|https://github.com/mozilla/narcissus/]] Mozilla's experimental JavaScript compiler in JavaScript by Brendan Eich and others.  
    * [[CommonJS version in DoctorJS|https://github.com/mozilla/doctorjs/tree/master/lib/jsctags/narcissus]]
    * [[Jasy: Python port of Narcissus with some enhancements|https://github.com/wpbasti/jasy/tree/master/lib/jasy/parser]]
    * [[PyNarcissus|http://code.google.com/p/pynarcissus/]] Narcissus's parser ported to Python (used in [[pyjon|http://code.google.com/p/pyjon/]])
    * [[rbnarcissus|http://code.google.com/p/rbnarcissus/]] Narcissus' parser ported to Ruby.
* [[Traceur|http://code.google.com/p/traceur-compiler/]] Google's vehicle for Javascript Language Design Experimentation
* [[EcmaScript 5 Parser (es-lab)|http://es-lab.googlecode.com/svn/trunk/site/esparser/index.html]]
* [[EcmaScript 5 Parser (qfox)|http://esparser.qfox.nl/]]
* [[reflect.js|https://github.com/zaach/reflect.js]] Implementation of Mozilla's (SpiderMonkey) [[Parser API|https://developer.mozilla.org/en/SpiderMonkey/Parser_API]] in JavaScript
* [[bdParse|https://github.com/altoviso/bdParse]] a JavaScript LL(1) parser in JavaScript
* [[parse-js|http://marijnhaverbeke.nl/parse-js/]] common lisp javascript parser
* [[ZeParser|https://github.com/qfox/ZeParser]]
* [[Esprima|http://esprima.org]] Educational (but fast) ECMAScript parser with output compatible to [[Mozilla Parser API|https://developer.mozilla.org/en/SpiderMonkey/Parser_API]]
* [[js.js|https://github.com/jterrace/js.js]] A JavaScript JavaScript interpreter. Instead of trying to create an interpreter from scratch, SpiderMonkey is compiled into LLVM and then emscripten translates the output into JavaScript.

###### Javascript Optimizers

* [[Closure Compiler|http://code.google.com/closure/compiler/]] An optimizing compiler. Can generate a (line/col)-number mappings file.
* [[UglifyJS|https://github.com/mishoo/UglifyJS]]

###### Javascript Parser Generators

* [[jison|https://github.com/zaach/jison]] Bison in javascript, used by Coffeescript
* [[OMeta/JS|http://tinlizzie.org/ometa-js/#Sample_Project]] ([[source|https://github.com/veged/ometa-js]]) metacompiler for many languages to many targets, including js.
* [[PEG.js|http://pegjs.majda.cz/]] parser generator for JavaScript based on the parsing expression grammar formalism
* [[languagejs|https://github.com/tolmasky/language]] - PEG parser written in JavaScript with first class errors
* [[Canopy|https://github.com/jcoglan/canopy]] Self-hosting PEG parser compiler for JavaScript, influenced by Ruby parser generators such as Treetop and Citrus
* [[JS/CC|http://jscc.jmksf.com/]] LALR(1) parser generator
* [[jsparse|https://github.com/doublec/jsparse]] PEG by Grandmaster Chris Double
* [[ReParse|https://github.com/weaver/ReParse]] parser combinator library for Javascript like Haskell's Parsec
* [[p4js|https://github.com/asmyczek/p4js]] Monadic parser library for JavaScript
* [[JSGLR|http://blog.kalleberg.org/post/1256702765/prototype-of-a-scannerless-generalized-left-to-right]] Scannerless, Generalized Left-to-right Rightmost (SGLR) derivation parser for JavaScript
* [[antlr|https://github.com/antlr/examples-v3]] has a javascript target
* [[Cruiser.Parse|http://code.google.com/p/cruiser/wiki/Parse]] LL(k) parser
* [[MetaCoffee|https://github.com/xixixao/meta-coffee]] PEG parser using CoffeeScript and white-space-significant syntax

###### Javascript AST, Semantics
* [[Closure Compiler AST Documentation|https://docs.google.com/viewer?url=http%3A%2F%2Fclosure-compiler.googlecode.com%2Ffiles%2Fclosure-compiler-ast.pdf]]
* [[Spidermonkey Parser API|https://developer.mozilla.org/en/SpiderMonkey/Parser_API]] - see also reflect.js above
* [[JsonML AST|http://code.google.com/p/es-lab/wiki/JsonMLASTFormat]] format used by the es5 parser 
* [[treehugger|https://github.com/zefhemel/treehugger]] Javascript AST transformation tools
* [[JavaScript Shaper|http://jsshaper.org/]] JavaScript syntax tree shaping
* [[burrito|https://github.com/substack/node-burrito]] & [[js-traverse|https://github.com/substack/js-traverse]] - see [[this post|http://substack.net/posts/eed898]] for more info, as well as [[node-stackedy|https://github.com/substack/node-stackedy]] for an example and [[node-browserify|https://github.com/substack/node-browserify]] for running it in a browser instead of node
* [[javascript types|http://cs.brown.edu/~joe/public/types/types.html]] - lambdajs, flow typing
* [[SourceMap|https://github.com/mozilla/source-map]] map javascript debugger output to original source 
* [[Zeon|https://github.com/qfox/Zeon]] A static visual JavaScript analyzer / editor.  See also [[ZeParser|https://github.com/qfox/ZeParser]].
* [[escodegen|https://github.com/Constellation/escodegen]] - Javascript code generator
* [[esmangler|https://github.com/Constellation/esmangle]] mangler / minifier for Mozilla Parser API AST