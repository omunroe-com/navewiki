# CoffeeScript In The Wild
(Please use only a single line and try keep things in alphanumerical order) :)

## Applications

### Web
[Annotateit](http://annotateit.org/) - Web annotations and higlights

[Apiary.io](http://apiary.io/) - API prototyping & debugging

[Bonnevoy](http://bonnevoy.com/) - Dutch travel search engine (CoffeeScript + Spine)

[BusyConf](http://busyconf.com/) - Conference scheduling app (CoffeeScript + jQuery + Sencha Touch)

[CloudApp](http://getcloudapp.com) - Share. Files. Fast. (CoffeScript + Backbone.js [annotated source](http://cloudapp.github.com/engine))

[EtherCalc](http://ethercalc.org/) - Massively multiplayer online spreadsheet. (CoffeeScript + Zappa.js)

[HelpShelf](http://helpshelf.com/) - Upload and Organize your technical PDFs with full text search

[Heroscale](http://heroscale.com/) - Tool that monitors and scales your Heroku dynos/workers

[Kodingen](http://kodingen.com/) - Cloud Development Environment with php/ruby/perl/python support.

[PixieEngine](http://pixieengine.com) - Web based IDE focusing on HTML5 game development.

[Posterous](https://posterous.com/) - Blogging platform. Used CoffeeScript to create its revamped "Spaces" front-end. ([source](http://twitter.com/#!/adamsingy/status/114760397982146560))

[Showbomber](http://showbomber.com/) - A mash-up of upcoming concerts and videos.

[Solitr](http://www.solitr.com/) - Solitaire game ([GitHub](https://github.com/joliss/solitr))

[Tzigla](http://tzigla.com/) - Collaborative drawing application. Includes a [pixel art editor](http://tzigla.com/editor).

[Widescript](http://widescript.com) - Digital textbook platform

[WordSquared](http://wordsquared.com) - Massively multiplayer online scrabble (previously known as Scrabb.ly)

### Mobile (iOS/Android)
[Airbnb Mobile](http://m.airbnb.com) - Mobile web version of Airbnb (Backbone + CoffeeScript)

[Album Plus](http://iphone.albumpl.us) - Native iPhone Photo app (Pure CoffeeScript compiled with Titanium)

[Ars Technica iPad application](http://itunes.apple.com/us/app/ars-technica/id393859050?mt=8) - Official Ars Technica application for the iPad

[Basecamp Mobile](http://basecamphq.com/mobile/) - Mobile web version of 37signals' Basecamp (Backbone + CoffeeScript + Eco)

[Chalk](http://chalk.37signals.com) - A simple drawing application for the iPad.

[CrowdGame Trivially](http://itunes.apple.com/us/app/crowdgame-trivially/id477571106?mt=8) - Multi-player iPad game. Players interact via their smartphone browsers. Appcelerator-based. Written in CoffeeScript, with an Objective-C HTTP server, which serves pages to remote users written in CoffeeScript.

[HotelTonight](http://www.hoteltonight.com) - Hotel finder.  Both the iPhone app and Android app are written in CoffeeScript.  For the iPhone app, it is an Appcelerator Titanium based app, and the Android app is an HTML5 app (using Backbone.js and jQuery Mobile).

### Tech Demos
[Conway's Game Of Life](https://github.com/jhogendorn/Game-of-Life-in-CoffeeScript) - An implementation of Conway's Game of Life using OOP CoffeeScript.

[Conway's Game Of Life](https://github.com/showell/Game-Of-Life) - A small simulation of Conway's Game of Life.

[Conway's Game Of Life](http://willbailey.name/conway/index.html) - Conway's game of life with [annotated source](http://willbailey.name/conway/docs/conway.html).

[cortex](http://github.com/feisty) - "core technologies" - MMO game platform written on node.js and WebGL.

[Eight Queens](http://shpaml.webfactional.com/misc/game_page.htm) - Eight Queens, animated and annotated

[Gates of Olympus](http://gatesofolympus.com) - A browser based 3d tower defense game, using webgl ([source](http://github.com/rehno-lindeque/Gates-of-Olympus))

[Viper](https://github.com/bjornharrtell/viper) - Remake of an old Amiga game, a variant of a Snake, using Canvas and WebSockets for multiplayer support.

## Tools and Frameworks

### Build and Deployment
[Buildr](http://github.com/balupton/buildr.npm) - The (Java|Coffee)Script and (CSS|Less) (Builder|Bundler|Packer|Minifier|Merger|Checker) 

[Brunch](http://brunch.io) - a lightweight approach to building HTML5 applications with emphasis on elegance and simplicity on top of Backbone.js, eco, jQuery, Stitch & Stylus.

[settings](https://github.com/mgutz/node-settings) - Simple, hierarchical environment-based app settings.

### Database
[riak-js](https://github.com/frank06/riak-js) - Node.js [Riak](http://riak.basho.com) client
[query-engine](https://github.com/balupton/query-engine.npm) - A NoSQL (and MongoDB compliant) Query Engine coded in CoffeeScript for Server-Side use with Node.js and Client-Side use with Web-Browsers

### Design Patterns
[WebActors](http://github.com/mental/webactors) - Actors for JavaScript
[meta_code](https://github.com/clyfe/meta_code) CoffeeScript metaprogramming tools

### Documentation Generators
[CoffeeDoc](http://github.com/omarkhan/coffeedoc) - an API documentation generator for CoffeeScript

[Docco](http://jashkenas.github.com/docco/) - a quick-and-dirty literate-programming-style documentation generator for CoffeeScript. Used to produce the annotated source.

[Codo](http://github.com/netzpirat/codo) - CoffeeScript API documentation generator. It's like YARD but for CoffeeScript!

### Flow Control
[seq](http://github.com/substack/node-seq) - chainable asynchronous flow control; written in javascript, works with coffee (methods ending in underscores added specifically to work with coffee to thread along `this` explicitly)

[SCION](https://github.com/jbeard4/SCION) - StateCharts Interpretation and Optimization eNgine (SCION) is an implementation of SCXML/Statecharts targeting JavaScript environments.

### Module Loaders - CommonJS
[browserify](http://github.com/substack/node-browserify) - Mix and match coffee and javascript in your browser-side require()s

[nibjs](http://github.com/blambeau/nib.js) - Compile and Concatenate your CoffeeScript files for the browser

[Stitch](http://github.com/sstephenson/stitch) - Stitch CommonJS modules together for the browser. Includes support for CoffeeScript and Eco modules.

### Templating
[Cupcake](http://github.com/twilson63/cupcake) - Web App Template Generator for CoffeeScript

[DOMBrew](http://github.com/glebm/DOMBrew) - Eloquent DOM Builder

[eco](http://github.com/sstephenson/eco) - Embedded CoffeeScript templates (the erb of CoffeeScript)

[CoffeeKup](http://github.com/mauricemach/coffeekup) - Markaby in CoffeeScript

[haml-coffee](https://github.com/9elements/haml-coffee) - Haml templates where you can write inline CoffeeScript.

### Testing
[coffee-spec](https://github.com/gfxmonk/coffee-spec) - An event-driven unit testing library.

[Twerp](http://github.com/philjackson/twerp) - Synchronous class-based unit testing framework.

[Zombie.js](http://zombie.labnotes.org) - headless full-stack testing using node.js

### Node.js Web App Frameworks
[Coffee4Clients](http://github.com/balupton/coffee4clients.npm) - Renders .coffee files into javascript when requested on a Express.js server

[coffeemate](http://github.com/kadirpekel/coffeemate) - the coffee creamer! Push coffeescript into web development.

[CouchCover](http://github.com/zdzolton/couch-cover) - mock evironment for testing CouchDB design document functions

[DocPad](http://github.com/bevry/docpad) - a language agnostic document management system, which includes built-in support for coffeescript to javascript compilation

[Kiss.js](https://github.com/stanislavfeldman/kiss.js) - Web framework for Node.js. Object-oriented, simple and sexy.

[SocketStream](https://github.com/socketstream/socketstream) - real-time web framework developed by AOL

[zappa](http://github.com/mauricemach/zappa) - DSL for [CoffeeKup](http://github.com/mauricemach/coffeekup), [socket.io](http://github.com/LearnBoost/Socket.IO), [express](http://github.com/visionmedia/express)

### Node.js Server Apps
[camo](https://github.com/atmos/camo) - Asset Proxy for Secure Embedding (used internally by GitHub)

[diaspora-x2](http://github.com/bnolan/diaspora-x2) - Diaspora ported to XMPP and CoffeeScript.

[Nack](http://github.com/josh/nack) - Serve Rack applications from Node.js

[Pixel Ping](http://documentcloud.github.com/pixel-ping/) - DocumentCloud's pixel tracker for embedded documents.

[Pow](http://pow.cx/) - Rack web server for Mac OS X, from 37signals

### Other Node.js Libraries
[Math](http://github.com/feisty/math) - high performance 2D/3D extensions for CommonJS's "Math" module

[NowPad](http://github.com/balupton/nowpad) - Realtime Text Collaboration for Node.js apps

[PDFKit](http://devongovett.github.com/pdfkit/) - A powerful PDF generation library for Node.js

### Miscellaneous
[Blocky](https://github.com/zmcartor/Blocky) - Clientside QR code generation

[coffeecoffee](https://github.com/showell/CoffeeCoffee) - CoffeeScript interpreter (no JS compilation required)

[CoffeeLint](http://www.coffeelint.org) - A CoffeeScript style checker.

[Courier](http://github.com/feisty/courier) - npm packages in CoffeeScript - (package.coffee) -> (package.json)

[Curator.js](https://github.com/clvv/Curator.js) - A flexible process monitoring and management framework

[Curtains](https://github.com/mirekm/curtains) - A keyframe & event-driven, general purpose animation tool.

[FilePad](http://github.com/balupton/filepad) - Edit your local files in your browser with realtime collaboration

[Jim](http://github.com/misfo/jim) - Vim mode for Ace, the editor in Github & Cloud9 ([annotated source](http://misfo.github.com/jim/docs/jim.html))

[Open Tweet Filter](https://github.com/rstuven/OpenTweetFilter) - A browser extension to filter tweets. (CoffeeScript + CoffeeKup + Knockout + jQuery)

[Tag](http://github.com/feisty/tag) - Simple Terminal.app window titles

[ToE](https://github.com/feisty/ToE) - Theory of Everything - MMORPG written in CoffeeScript on node.js and HTML (WebGL, WebSocket)