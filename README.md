# Experiment

discussion happens here https://github.com/stereobooster/package.json/issues/2

```sh
yarn

# node

node src/index.js
CommonJS

node --experimental-modules src/index.esm.js
src/index.esm.js:1
(function (exports, require, module, __filename, __dirname) { import test from "main-module-browser";
                                                              ^^^^^^

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
