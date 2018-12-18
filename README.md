# Geoblocks


## Description

Geoblocks are pieces of code:
- with minimal dependencies;
- independant;
- easy to use;
- maintained by the people who use them;
- written in plain ES6 or typescript;
- distributed as ES6 modules source code.

See [technical requirements](#technical-requirements).


## Github / Npm

Each block is maintained in its own independant `github` repository in the
`geoblocks` organisation: https://github.com/geoblocks.

Blocks are published on `npm` in the `geoblocks` organisation:
https://www.npmjs.com/org/geoblocks.


## Usage

The `proj` block exposes `OpenLayers` projections. To use them:
- `npm i --save @geoblocks/proj`
- `import EPSG_2056 from '@geoblocks/proj/src/EPSG_2056.js';`
- you are done!


## Contributing

- Create issue / PR in the block;
- A block maintainer will review and merge;
- To create new blocks [get in touch with us](guillaume.beraudo@camptocamp.com).


## Technical requirements

- write code as plain ES6 modules or typescript;
- distribute as ES6 modules + typescript d.ts;
- define a typescript interface for blocks implementing a generic feature;
- enable CI with tests and coverage;
- publish a documentation;
- eventually publish examples.
