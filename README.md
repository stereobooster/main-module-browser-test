# Experiment

discussion happens here https://github.com/stereobooster/package.json/issues/2

```sh
node src/index.js
CommonJS

yarn

npx webpack src/index.js build/main.js
node build/main.js
{ default: 'ES module browser' }

npx webpack src/index.esm.js build/main.js
node build/main.js
ES module browser

node --experimental-modules src/index.mjs
(node:21541) ExperimentalWarning: The ESM module loader is experimental.
CommonJS
```

structure of `package.json`

```json
{
  "name": "main-module-browser",
  "main": "dist/index.js",
  "module": "dist/index.esm.js",
  "browser": {
    "./dist/index.js": "./dist/index.browser.js",
    "./dist/index.esm.js": "./dist/index.browser.esm.js"
  }
}
```
