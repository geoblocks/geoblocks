# Geoblocks


## Description

Geoblocks are pieces of code:
- with minimal dependencies [choosing versions](#choosing-dependency-versions);
- independant;
- easy to use;
- tested and documented [testing](#testing);
- maintained by the people who use them;
- written in plain ES6 or typescript;
- distributed as ES6 modules + typescript d.ts [typing](#typing).


## Github / Npm

Each block is maintained in its own independant `github` repository in the
[github geoblocks organisation](https://github.com/geoblocks).

Blocks are published on `npm` in the
[npm geoblocks organisation](https://www.npmjs.com/org/geoblocks).


## Usage

The `proj` block exposes `OpenLayers` projections. To use them:
- `npm i --save @geoblocks/proj`
- `import EPSG_2056 from '@geoblocks/proj/src/EPSG_2056.js';`
- you are done!


## Contributing

- Create issue / PR in the block;
- A block maintainer will review and merge;
- To create new blocks [get in touch with us](mailto:guillaume.beraudo@camptocamp.com).


## Choosing dependency versions

Each block has a `package.json` file specifying the dependencies of the block.
For each dependency, the block author must specify a range starting at the smallest usable version.

Let's take an example.
The `proj` block depends on OpenLayers 5. It is usable with all the versions in
the range [5.3.0, current] so the package.json file must contain:
```
ol": ">=5.3.0",
```

During the CI tests, both version 5.3.0 and the latest version are tested.
[Here is how it is handled](https://github.com/geoblocks/proj/commit/15f12c755d50f0129f1e4ef1b990e0864d74926d).


## Typing

Blocks can be written as plain ES6 modules. But to catch errors early and to benefit from modern Javascript editing in code
editors like VSCode, it is required to:
- publish typescript definition files (d.ts);
- define typescript interfaces when implementing a generic feature.

With proper annotations, note that plain ES6 modules blocks can use typescript
as a [typechecker](https://github.com/geoblocks/proj/blob/15f12c755d50f0129f1e4ef1b990e0864d74926d/package.json#L7).


## Testing

- enable CI with tests and coverage [example with JEST](https://github.com/geoblocks/proj/commit/96db2d43f8d093b262421ac9b527764af1fa9893);
- publish a documentation;
- eventually publish examples.

See the [sources block](https://github.com/geoblocks/sources).


## Publication

To accomodate different use cases, blocks are published with:
- a "geoblocks_src" entry pointing to modern code written in the latest Ecmascript standard;
- "main" and "module" entries pointing to ES6 modules + ES5 language (Typescript / Angular).

Specifically, with `webpack` the following configuration will make use of the `geoblocks_src` entry:
- `mainFields: ["geoblocks_src", "module", "main"]` [resolve config](https://webpack.js.org/configuration/resolve/#resolve-mainfields);
- `babel` rule `{test: /\.js$/, exclude: /node_modules\/(?!(@geoblocks|ANOTHER-MODULE)\/).*/,},` [exclude](https://github.com/webpack/webpack/issues/2031).
