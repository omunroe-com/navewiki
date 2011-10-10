#### CoffeeScript Family (& Friends)

* [[CoffeeScript|http://jashkenas.github.com/coffee-script/]] Unfancy JavaScript

###### Family (share genes with CoffeeScript)

* [[Coco|https://github.com/satyr/coco]] A CoffeeScript dialect that aims to be more radical and practical, also acts as a test bed for features that get imported in CoffeeScript.
* [[Parsec CoffeeScript|https://github.com/fab13n/parsec-coffee-script]] CS based on parser combinators. The project's aim is to add static metaprogramming (i.e. macros + syntax extensibility) to Coffee Script (CS), similar to how Metalua adds such features to Lua. The resulting compiler, once merged with the official compiler, should be usable as a drop-in replacement for it.
* [[Contracts.coffee|https://github.com/disnet/contracts.coffee]] A dialect of CoffeeScript that adds built-in support for contracts.
* A [[coffeescript extension|https://github.com/jstrachan/coffee-script/blob/master/TypeAnnotations.md]] that you can declare types with. They get converted into google closure type annotation comments that the closure compiler can use to type check your javascript.

###### Friends (philosophically related)

* [[JS11|http://js11.org/]] JavaScript with augmented semicolon insertion, reduced punctuation, and limited sugar. Debugs line-for-line.
* [[Kaffeine|https://github.com/weepy/kaffeine]] Enhanced Syntax for JavaScript.
* [[Jack|https://github.com/creationix/jack]] Making programming playful.
* [[move|https://github.com/rsms/move]] A simpler and cleaner programming language.

#### JavaScript Parsers and Extensions

* [[Narcissus|https://github.com/mozilla/narcissus/]] Mozilla's experimental JavaScript compiler in JavaScript by Brendan Eich and others.  
    * [[CommonJS version in DoctorJS|https://github.com/mozilla/doctorjs/tree/master/lib/jsctags/narcissus]]
    * [[Jasy: Python port of Narcissus with some enhancements|https://github.com/wpbasti/jasy/tree/master/lib/jasy/parser]]
* [[Traceur|http://code.google.com/p/traceur-compiler/]] Google's vehicle for Javascript Language Design Experimentation
* [[EcmaScript 5 Parser (es-lab)|http://es-lab.googlecode.com/svn/trunk/site/esparser/index.html]]
* [[EcmaScript 5 Parser (qfox)|http://esparser.qfox.nl/]]
* [[reflect.js|https://github.com/zaach/reflect.js]] Implementation of Mozilla's (SpiderMonkey) [[Parser API|https://developer.mozilla.org/en/SpiderMonkey/Parser_API]] in JavaScript
* [[bdParse|https://github.com/altoviso/bdParse]] a JavaScript LL(1) parser in JavaScript
* [[parse-js|http://marijnhaverbeke.nl/parse-js/]] common lisp javascript parser
* [[ZeParser|https://github.com/qfox/ZeParser]]

###### Javascript Optimizers

* [[Closure Compiler|http://code.google.com/closure/compiler/]] An optimizing compiler. Can generate a (line/col)-number mappings file.
* [[UglifyJS|https://github.com/mishoo/UglifyJS]]

###### Security enforcing JavaScript

* [[Caja|http://code.google.com/p/google-caja/]] Compiles ES5/strict to ES3 and supports object-capabilities
* [[ADsafe|http://www.adsafe.org/]] Client-side static verifier and API, making third party scripts safe.
* [[FBJS|http://developers.facebook.com/docs/fbjs]] Facebook JavaScript, used for scripting FBML (Facebook Markup Language) gadgets.
* [[Jacaranda|http://jacaranda.org/]] Static verifier supporting object-capabilities.
* [[Microsoft Web Sandbox|http://websandbox.livelabs.com/]] Technology preview of securing web content through isolation.
* [[Gatekeeper|http://research.microsoft.com/en-us/projects/gatekeeper/]] Microsoft Research project.
* [[Dojo Secure|http://www.sitepen.com/blog/2008/08/01/secure-mashups-with-dojoxsecure/]] Framework for building secure mashups.

###### Static typing

* Some of the ones listed below are also statically typed, such as mobl, GWT, JSIL, NS Basic, and Haxe.
* [[Dart|http://www.dartlang.org/]] by Google. C/Java-like syntax with optional typing.
* [[SafeJS|https://github.com/safejs/SafeJS]]
* [[MileScript|http://milescript.org/]] [commercial] A strongly-typed language similar to C# and Java, but which compiles to JS. free for non-profit, educational use.
* [[Mascara|http://www.mascaraengine.com/]] [commercial] Enhances JavaScript with powerful features like classes, namespaces and type-checking.
* [[Roy|http://roy.brianmckenna.org/]] tries to meld JavaScript semantics with some features common in static functional languages
* A [[coffeescript extension|https://github.com/jstrachan/coffee-script/blob/master/TypeAnnotations.md]] that you can declare types with. They get converted into google closure type annotation comments that the closure compiler can use to type check your javascript.

###### Synchronous to Asynchronous JavaScript Compilers (CPS)
* [[Streamline.js|https://github.com/Sage/streamlinejs]] Uses underscore (_) to stand for callbacks. This [[fork|https://github.com/willconant/streamlinejs]] preserves line numbers for debugging.
* [[mobl|http://www.mobl-lang.org]] The new language for programming the mobile web.
* [[StratifiedJS|http://onilabs.com/stratifiedjs/]] JavaScript + structured concurrency.  See also apollo on that site.
* [[NarrativeJS|http://www.neilmix.com/narrativejs/doc/]] JavaScript extension with asynchronous futures and promises.
* [[jwacs|http://chumsley.org/jwacs/]] JavaScript With Advanced Continuation Support.
* [[Jscex|https://github.com/JeffreyZhao/jscex]] Write simple JavaScript code, execute it asynchronously by compiling to monadic form.
* [[TameJS|http://tamejs.org/]] adds new keywords 'twait' and 'mkevent'

###### JavaScript Language Extensions

* [[ContextJS|https://www.hpi.uni-potsdam.de/hirschfeld/trac/Cop/wiki/ContextJS]] is an implementation of [[Context-oriented Programming|http://www.hpi.uni-potsdam.de/hirschfeld/cop/]] for JavaScript.
* [[Objective-J|http://en.wikipedia.org/wiki/Objective-J]] Shares with JavaScript the same relationship that Objective-C has with the C programming language: that of being a strict, but small, superset.
* [[JS2|https://github.com/jeffsu/js2]] Object-oriented JavaScript with syntactic sugar (curry, foreach, property). Released as a Ruby gem.
* [[jangaroo|http://www.jangaroo.net/home/]] AS3 (ActionScript) to JavaScript.
* [[Flapjax|http://flapjax-lang.org/]] Event-driven, reactive evaluation.
* [[jLang|http://jlang.org/]] adds object oriented syntax, namespaces, operators overriding
* [[Restrict Mode|http://restrictmode.org/]]
* [[TIScript|http://www.codeproject.com/KB/recipes/TIScript.aspx]] gentle extension of JavaScript

#### Ruby

* [[HotRuby|http://hotruby.yukoba.jp/]] Runs opcode, compiled by YARV on Ruby inside a web browser or in Flash.
* [[rb2js|http://rb2js.rubyforge.org/]] Converts Ruby to JavaScript.
* [[RubyJS|http://www.ntecs.de/blog/articles/2007/01/08/rubyjs-javascript-no-thank-you/]] A successor to rb2js
* [[Red|https://github.com/jessesielaff/red]] Writes like Ruby and runs like JavaScript
* [[Quby|http://www.playmycode.com/docs/quby]] Used for game coding site, not open source.
* [[Opal|https://github.com/adambeynon/opal]] Ruby to Javascript compiler.
* [[8ball|https://github.com/mattknox/8ball]] ruby-to-javascript source-to-source transformer

#### Python

* [[PYXC-PJ|http://pyxc.org/]] [CS friend] Python to JS. Can generate a (line/col)-number mappings file.
* [[Pyjamas|http://pyjs.org/]] Python to JS.
* [[Pyjs|https://github.com/anandology/pyjs]] Python to (readable) JS.
* [[Skulpt|http://www.skulpt.org/]] Python. Client side.
* [[PyCow|https://github.com/p2k/PyCow]] Python to MooTools JS.
* [[PyvaScript|http://www.allbuttonspressed.com/blog/django/2010/07/PyvaScript-Pythonic-syntax-for-your-browser]] Python-like syntax to JavaScript.

#### Java

* [[GWT|http://code.google.com/webtoolkit/]] Google Web Toolkit, compiles java to javascript
* [[Java2Script|http://j2s.sourceforge.net/]] Eclipse Java to JavaScript compiler plugin and JavaScript version of SWT
* [[j2js|http://www.j2js.com/]] Java bytecode to JavaScript.

#### Scala

* [[scalagwt|http://code.google.com/p/scalagwt/]] enhanced GWT (accepts jribble as well as java) plus scala to jribble.

#### C#, .NET

* [[jsc|http://jsc.sourceforge.net/]] [experimental] Recompile your .NET assembly to JavaScript, ActionScript, PHP or Java.
* [[JSIL|https://github.com/kevingadd/JSIL]] MSIL (.NET bytecode) to Javascript
* [[Script#|http://projects.nikhilk.net/ScriptSharp]] [commercial] Compiles C# to JS.
* [[Prefix|http://www.toptensoftware.com/prefix/]] in development

#### Lisp, Scheme

* [[BiwaScheme|http://www.biwascheme.org/]] Scheme in JavaScript
* [[ClojureScript|https://github.com/clojure/clojurescript]] Clojure to JS, the official version. Supports the majority of Clojure including persistent datastructures.
* [[clojurejs|https://github.com/kriyative/clojurejs]] Subset of Clojure to JS.
* [[EdgeLisp|https://github.com/manuel/edgelisp]] A Lisp in the tradition of Common Lisp
* [[Fargo|https://github.com/jcoglan/fargo]] Scheme in JavaScript  
* [[Moby Scheme|https://github.com/dyoo/moby-scheme]] A Scheme running in JS.
* [[nconc|https://github.com/patrickdlogan/nconc]] scheme interpreter in javascript with stack-friendly tail calls and full call/cc
* [[Parenscript|http://common-lisp.net/project/parenscript/]] Subset of Common Lisp to JS.
* [[Ralph|https://github.com/turbolent/ralph]] Lisp-1 dialect that compiles to JavaScript, inspired by Dylan
* [[scheme2js|http://www-sop.inria.fr/indes/scheme2js/]] Scheme to JavaScript.
* [[Scriptjure|https://github.com/arohner/scriptjure]] Library for generating JavaScript from Clojure forms.
* [[Sibilant|http://sibilantjs.info]] JavaScript with a lisp.
* [[Spock|http://wiki.call-cc.org/eggref/4/spock]] A Scheme to JavaScript compiler that uses Henry Baker's Cheney-on-the-MTA compilation strategy  

#### OCaml

* [[Ocamljs|https://github.com/jaked/ocamljs]] OCaml to JS.
* [[O'Browser|http://www.pps.jussieu.fr/~canou/obrowser/tutorial/]] OCaml bytecode interpreter in JS.
* [[Js_of_ocaml|http://ocsigen.org/js_of_ocaml/]] OCaml bytecode to JS compiler.

#### Haskell

* [[ghcjs|https://github.com/pedromartins/ghcjs]] Compile normal Haskell into JS
* [[jmacro|http://hackage.haskell.org/package/jmacro]] Quasi-Quoted JS that you can insert Haskell values into, also supports a more haskellish version of javascript.

The rest of these probably don't work, particularly with code written for the common GHC compiler.

* [[https://github.com/aculich/lambdascript|]] Compile a subset of Haskell into JS
* [[UHC|http://www.cs.uu.nl/wiki/bin/view/Ehc/UhcUserDocumentation#5_7_3_jscript_Core_based_JavaScr]] (Utrecht Haskell Compiler) backend converts UHC core to JavaScript, allowing the compiling of Haskell code to JS.
* [[YHC|http://www.haskell.org/haskellwiki/Yhc/Javascript]] (York Haskell Compiler) backend, as above but with YHC core language.
* [[jshaskell|http://code.google.com/p/jshaskell/]]

#### Smalltalk

* [[Amber|http://amber-lang.net/]] - formerly known as Jtalk
* [[Clamato|http://clamato.net/]] a Smalltalk dialect that is designed to operate within the JavaScript runtime.
* [[Silver Smalltalk|http://www.silversmalltalk.com/]] [commercial] Smalltalk in the browser.
* [[Lively Kernel|http://www.lively-kernel.org/]] - smalltalk/squeak-like development environment in the browser.  See also [[Avocado|http://avocadojs.com/]], built on top of it.

#### C/C++

* [[Emscripten|http://code.google.com/p/emscripten/]] LLVM to JavaScript compiler.  LLVM is "an aggressive open-source compiler for C and C++," as well as other languages.
* [[mala|http://lethalman.hostei.com/maja/index.html]] vala (gobject) to javascript
* [[Clue|http://cluecc.sourceforge.net/]] C language compiler to different runtimes (Lua, JS, Perl 5, C, Java, CL).

#### Basic

* [[NS Basic/App Studio|http://www.nsbasic.com/app/]] [commercial] Visual Basic-style BASIC to JavaScript compiler. Includes IDE. Targets iOS and Android.
* [[qb.js|http://stevehanov.ca/blog/index.php?id=92]] An implementation of QBASIC in Javascript

#### Multitarget

* [[Haxe|http://haxe.org/]] compiles to several platforms (C++, Flash, JS, Neko, PHP).
* [[Fantom|http://fantom.org/]] Evolutionary object-oriented language emphasizing succinct and effective APIs (JVM, CLR, JS).
* [[LZX (Laszlo XML)|http://labs.openlaszlo.org/trunk-nightly/laszlo-explorer/index.html?lzr=swf10#_lzbookmark=Laszlo%20in%2010%20Minutes]] LZX is [[OpenLaszlo's|http://www.openlaszlo.org]] declarative user interface language, which is compiled into JavaScript 2 as an intermediary format, and further compiled into either JavaScript 1.5 or ActionScript 3.
* Clue and jsc above target multiple runtimes in addition to javascript

#### Tierless languages (produce both client & server)

* [[Fun|https://github.com/marcuswestin/fun]] A programming language for realtime webapps - compiles to client-side and server-side JS.
* [[Ur|http://impredicative.com/ur/]] In the tradition of ML and Haskell.
* [[WebSharper|http://www.websharper.com/]] Lets you compile F# to JS.
* [[mobl|http://www.mobl-lang.org]] The new language for programming the mobile web.
* [[E|http://wiki.erights.org/wiki/E-on-JS]] Compiles E to JS. E is a secure distributed persistent pure object language.
* [[Sugar|https://github.com/sebastien/sugar]] new programming language designed to replace JavaScript
for client-side (and server-side) web development
* [[Opa|http://www.opalang.org/]] (in private beta) write your complete application in just one language, and the compiler will transform it into a self-sufficient executable

#### Visual, Blocks-based Languages
* [[Waterbear|http://waterbearlang.com/]]
* [[JsMorphic|http://chirp.scratchr.org/dl/experimental/JsMorphic/]] - [[demo|http://chirp.scratchr.org/dl/experimental/JsMorphic/snap.html]] - also called Snap!
* [[ScriptBlocks|http://code.google.com/p/scriptblocks/]]

#### Others

* [[Oia|https://github.com/stevedekorte/oia]] A port of Io to JavaScript.
* [[Quixe|https://github.com/erkyrath/quixe]] a Glulx VM interpreter written in Javascript
* [[Gnusto|https://github.com/curiousdannii/gnusto]] a Z-Machine VM interpreter written in Javascript
* [[Logo Interpreter|http://www.calormen.com/logo/]]
* [[p2js|https://github.com/urandom/p2js]] perl to javascript converter
* [[Reb2Static|https://github.com/jankom/RebToStatic]] Rebol to Javascript
* [[RPN|https://github.com/adrusi/rpn]] Interpreter for a language with a Reverse Polish Notation syntax.
* [[phype|http://code.google.com/p/phype/]] run PHP code directly in your browser
* [[OP4JS|http://delphimax.wordpress.com/2011/07/18/op4js-low-level-or-high-level-you-choose/]] object pascal for javascript, in development
* [[jsForth|http://forthfreak.net/jsforth80x25.html]]
* [[wForth|http://solidcoding.blogspot.com/2008/12/wforth-javascript-forth-interpreter.html]]

#### Tools for Compiler Writers

###### Javascript Parser Generators

* [[jison|https://github.com/zaach/jison]] Bison in javascript, used by Coffeescript
* [[OMeta/JS|http://tinlizzie.org/ometa-js/#Sample_Project]] ([[source|https://github.com/veged/ometa-js]]) metacompiler for many languages to many targets, including js.
* [[PEG.js|http://pegjs.majda.cz/]] parser generator for JavaScript based on the parsing expression grammar formalism
* [[languagejs|https://github.com/tolmasky/language]] - PEG parser written in JavaScript with first class errors
* [[Canopy|https://github.com/jcoglan/canopy]] Self-hosting PEG parser compiler for JavaScript, influenced by Ruby parser generators such as Treetop and Citrus.  Depends on JS.Class library
* [[JS/CC|http://jscc.jmksf.com/]] LALR(1) parser generator
* [[jsparse|https://github.com/doublec/jsparse]] PEG by Grandmaster Chris Double
* [[ReParse|https://github.com/weaver/ReParse]] parser combinator library for Javascript like Haskell's Parsec
* [[p4js|https://github.com/asmyczek/p4js]] Monadic parser library for JavaScript
* [[JSGLR|http://blog.kalleberg.org/post/1256702765/prototype-of-a-scannerless-generalized-left-to-right]] Scannerless, Generalized Left-to-right Rightmost (SGLR) derivation parser for JavaScript
* [[antlr|https://github.com/antlr/examples-v3]] has a javascript target
* [[Cruiser.Parse|http://code.google.com/p/cruiser/wiki/Parse]] LL(k) parser

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

#### See Also

* [[altJS|http://altjs.org/]] a [[Google group|http://groups.google.com/group/altjs]] and #altjs IRC channel for those interested in alternative languages for javascript  ('transpilers').  There is a [[Try altJS|http://altjs.org/try/]] feature, too, to test out various compilers in the browser.
* [[jswiki|https://github.com/bebraw/jswiki/wiki]] another github wiki with listings of various javascript libraries
