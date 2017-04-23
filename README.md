#   Angular 4 with Webpack

Implementation of the guide on angular.io docs


Tutorial: [WEBPACK: AN INTRODUCTION](https://angular.io/docs/ts/latest/guide/webpack.html)

####    Bugs Removed:

*   `tsconfig.json` when in different folder than the one which has the `node_modules` cannot find `@types` folder in `node_modules` by default.

SOLUTION:

Add Following Options to `tsconfig`:

    "types": [
       "node",
       "jasmine"
    ],
    "typeRoots": [
       "../node_modules/@types"
    ],

*   Upgraded zone.js from 0.8.4 to 0.8.5 to remove "TypeError cannot read apply of undefined"

*   The request of dependency is an injection !Warning from webpack

>   Warning: Critical dependency: the request of a dependency is an expression

SOLUTION:
Change Context Replacement Plugin option in webpack config files from this:

    new ContextReplacementPlugin(
       /angular(\\|\/)core(\\|\/)(esm(\\|\/)client|client)(\\|\/)linker/,
       helpers.root('client') // location of your client
     ),

to this:

    new webpack.ContextReplacementPlugin(
      /angular(\\|\/)core(\\|\/)@angular/,
      helpers.root('./src'), // location of your src
      {} // a map of your routes
    ),


Author: Shafiq Ahmad
