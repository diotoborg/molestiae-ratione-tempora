# @diotoborg/molestiae-ratione-tempora <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Map.groupBy` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.github.io/proposal-array-grouping/).

## Getting started

```sh
npm install --save @diotoborg/molestiae-ratione-tempora
```

## Usage/Examples

```js
var groupBy = require('@diotoborg/molestiae-ratione-tempora');
var assert = require('assert');

var arr = [0, 1, 2, 3, 4, 5];
var parity = function (x) { return x % 2 === 0 ? 'even' : 'odd'; };

var results = groupBy(arr, function (x, i) {
    assert.equal(x, arr[i]);
    return parity(x);
});

assert.deepEqual(results, new Map([
    ['even', [0, 2, 4]],
    ['odd', [1, 3, 5]],
]));
```

```js
var groupBy = require('@diotoborg/molestiae-ratione-tempora');
var assert = require('assert');
/* when Map.groupBy is not present */
delete Map.groupBy;
var shimmed = groupBy.shim();

assert.equal(shimmed, groupBy.getPolyfill());
assert.deepEqual(Map.groupBy(arr, parity), groupBy(arr, parity));
```

```js
var groupBy = require('@diotoborg/molestiae-ratione-tempora');
var assert = require('assert');
/* when Array#group is present */
var shimmed = groupBy.shim();

assert.equal(shimmed, Map.groupBy);
assert.deepEqual(Map.groupBy(arr, parity), groupBy(arr, parity));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@diotoborg/molestiae-ratione-tempora
[npm-version-svg]: https://versionbadg.es/diotoborg/molestiae-ratione-tempora.svg
[deps-svg]: https://david-dm.org/diotoborg/molestiae-ratione-tempora.svg
[deps-url]: https://david-dm.org/diotoborg/molestiae-ratione-tempora
[dev-deps-svg]: https://david-dm.org/diotoborg/molestiae-ratione-tempora/dev-status.svg
[dev-deps-url]: https://david-dm.org/diotoborg/molestiae-ratione-tempora#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@diotoborg/molestiae-ratione-tempora.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@diotoborg/molestiae-ratione-tempora.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@diotoborg/molestiae-ratione-tempora.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@diotoborg/molestiae-ratione-tempora
[codecov-image]: https://codecov.io/gh/diotoborg/molestiae-ratione-tempora/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/diotoborg/molestiae-ratione-tempora/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/diotoborg/molestiae-ratione-tempora
[actions-url]: https://github.com/diotoborg/molestiae-ratione-tempora/actions
