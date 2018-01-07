# Experiment

```
node src/index.js
CommonJS

yarn

npx webpack src/index.js build/main.js
node build/main.js
{ default: 'ES module browser' }

npx webpack src/index.esm.js build/main.js
node build/main.js
ES module browser
```
