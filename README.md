# Craco TS Loader

This is an adaptation of [craco-babel-loader](https://github.com/rjerue/craco-babel-loader), but for [ts-loader](https://github.com/TypeStrong/ts-loader).

If you are here, you've followed the [use-ts-loader](https://github.com/gsoft-inc/craco/blob/master/recipes/use-ts-loader/craco.config.js) recipe, but things are not working as expected and your `craco.config.js` imports [craco-babel-loader](https://github.com/rjerue/craco-babel-loader).

**NOTE: The text below was adapted from [craco-babel-loader](https://github.com/rjerue/craco-babel-loader)**

## Install

```sh
$ yarn add craco-ts-loader
# npm v5+
$ npm install craco-ts-loader
# before npm v5
$ npm install --save craco-ts-loader
```

## Usage

```js
// crago.config.js
// see: https://github.com/sharegate/craco

const path = require("path");
const fs = require("fs");

const rewireTsLoader = require("craco-ts-loader");

// helpers

const appDirectory = fs.realpathSync(process.cwd());
const resolveApp = relativePath => path.resolve(appDirectory, relativePath);

module.exports = {
  plugins: [
        //This is a craco plugin: https://github.com/sharegate/craco/blob/master/packages/craco/README.md#configuration-overview
        { plugin: rewireTsLoader, 
          options: { 
            includes: [resolveApp("node_modules/isemail")], //put things you want to include in array here
            excludes: [/(node_modules|bower_components)/] //things you want to exclude here
            //you can omit include or exclude if you only want to use one option
          }
        }
    ]
}

```


Development
===========

- `node.js` and `npm`. See: https://github.com/creationix/nvm#installation
- `yarn`. See: https://yarnpkg.com/en/docs/install
- `npm` dependencies. Run: `yarn install`

## Chores

- Lint: `yarn run lint`
- Prettier: `yarn run pretty`
- Test: `yarn run test`
- Pre-publish: `yarn run prepublish`
- Build: `yarn run build`

License
=======

MIT.
