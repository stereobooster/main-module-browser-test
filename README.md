# Experiment

discussion happens here https://github.com/stereobooster/package.json/issues/2

```sh
yarn

# node

node src/index.js
CommonJS

node --experimental-modules src/index.esm.js
SyntaxError: Unexpected token import

node --experimental-modules src/index.mjs
(node:21541) ExperimentalWarning: The ESM module loader is experimental.
CommonJS

# webpack

npx webpack src/index.js build/main.js --target web
node build/main.js
{ default: 'ES module browser' }

npx webpack src/index.esm.js build/main.js --target web
node build/main.js
ES module browser

npx webpack src/index.js build/main.js --target node
node build/main.js
{ default: 'ES module' }

npx webpack src/index.esm.js build/main.js --target node
node build/main.js
ES module

# @std/esm

node -r @std/esm src/index.mjs
CommonJS

node -r @std/esm src/index.esm.js
SyntaxError: 'import' and 'export' may only be used in ES modules

# with "@std/esm": { "esm": "js" } in package.json

node -r @std/esm src/index.js
CommonJS

node -r @std/esm src/index.esm.js
CommonJS

# with "@std/esm": { "esm": "all" } in package.json

node -r @std/esm src/index.js
ReferenceError: require is not defined

node -r @std/esm src/index.esm.js
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

[List of targets](https://webpack.js.org/configuration/target/).
