This repository works in yarn v1 but not in yarn v2.  The following will run yarn-berry PR 539:

```
yarn install
yarn test
```

I'm running node.js 12.11.0 on Linux x86_64.  The results under yarn v2 on my machine:
```
internal/modules/cjs/loader.js:783
    throw err;
    ^

Error: Cannot find module 'pnpapi'
Require stack:
- internal/preload
    at Function.Module._resolveFilename (internal/modules/cjs/loader.js:780:15)
    at Function.Module._load (internal/modules/cjs/loader.js:685:27)
    at Module.require (internal/modules/cjs/loader.js:838:19)
    at Module._preloadModules (internal/modules/cjs/loader.js:1114:12)
    at loadPreloadModules (internal/bootstrap/pre_execution.js:429:5)
    at prepareMainThreadExecution (internal/bootstrap/pre_execution.js:53:3)
    at internal/main/run_main_module.js:7:1 {
  code: 'MODULE_NOT_FOUND',
  requireStack: [ 'internal/preload' ]
}
----------|---------|----------|---------|---------|-------------------
File      | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s 
----------|---------|----------|---------|---------|-------------------
All files |       0 |        0 |       0 |       0 |                   
----------|---------|----------|---------|---------|-------------------
```

Now switch to yarn v1 and run tests again:

```
rm .yarnrc*
yarn install
yarn test
```

This results in success:
```
yarn run v1.19.1
$ nyc node test.js
function
----------|---------|----------|---------|---------|-------------------
File      | % Stmts | % Branch | % Funcs | % Lines | Uncovered Line #s 
----------|---------|----------|---------|---------|-------------------
All files |     100 |      100 |     100 |     100 |                   
 index.js |     100 |      100 |     100 |     100 |                   
----------|---------|----------|---------|---------|-------------------
Done in 0.52s.
```
