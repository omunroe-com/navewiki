You can generate the docs via `cake doc:site` or `cake doc:site:watch`.

A convenient workflow is to run `cake doc:site:watch`, and then, from another tab, run `sudo http-server -p 80` from the docs folder (`/docs/`). (You may need to install `http-server` if you don’t yet have it: `npm install --global http-server`.) Then go to http://localhost in a browser.