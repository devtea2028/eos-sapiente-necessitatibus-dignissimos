# @devtea2028/eos-sapiente-necessitatibus-dignissimos <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES7/ES2016 spec-compliant `Array.prototype.includes` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://262.ecma-international.org/6.0/).

Because `Array.prototype.includes` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

Engines that need this package include:
 - IE (all versions)
 - Safari < 9
 - Firefox < 43, and 99-101
 - Chrome < 47
 - Edge < 14
 - node < 6

## Getting started

```sh
npm install --save @devtea2028/eos-sapiente-necessitatibus-dignissimos
```

## Usage

Basic usage: **includes(array, value[, fromIndex=0])**

```js
var includes = require('@devtea2028/eos-sapiente-necessitatibus-dignissimos');
var assert = require('assert');
var arr = [ 'one', 'two' ];

includes(arr, 'one'); // true
includes(arr, 'three'); // false
includes(arr, 'one', 1); // false
```



## Example

```js
var arr = [
	1,
	'foo',
	NaN,
	-0
];

assert.equal(arr.indexOf(0) > -1, true);
assert.equal(arr.indexOf(-0) > -1, true);
assert.equal(includes(arr, 0), true);
assert.equal(includes(arr, -0), true);

assert.equal(arr.indexOf(NaN) > -1, false);
assert.equal(includes(arr, NaN), true);

assert.equal(includes(arr, 'foo', 0), true);
assert.equal(includes(arr, 'foo', 1), true);
assert.equal(includes(arr, 'foo', 2), false);
```

```js
/* when Array#includes is not present */
delete Array.prototype.includes;
var shimmedIncludes = includes.shim();

assert.equal(shimmedIncludes, includes.getPolyfill());
assert.equal(arr.includes('foo', 1), includes(arr, 'foo', 1));
```

```js
/* when Array#includes is present */
var shimmedIncludes = includes.shim();

assert.equal(shimmedIncludes, Array.prototype.includes);
assert.equal(arr.includes(1, 'foo'), includes(arr, 1, 'foo'));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@devtea2028/eos-sapiente-necessitatibus-dignissimos
[npm-version-svg]: https://versionbadg.es/es-shims/@devtea2028/eos-sapiente-necessitatibus-dignissimos.svg
[deps-svg]: https://david-dm.org/es-shims/@devtea2028/eos-sapiente-necessitatibus-dignissimos.svg
[deps-url]: https://david-dm.org/es-shims/@devtea2028/eos-sapiente-necessitatibus-dignissimos
[dev-deps-svg]: https://david-dm.org/es-shims/@devtea2028/eos-sapiente-necessitatibus-dignissimos/dev-status.svg
[dev-deps-url]: https://david-dm.org/es-shims/@devtea2028/eos-sapiente-necessitatibus-dignissimos#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@devtea2028/eos-sapiente-necessitatibus-dignissimos.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@devtea2028/eos-sapiente-necessitatibus-dignissimos.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@devtea2028/eos-sapiente-necessitatibus-dignissimos.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@devtea2028/eos-sapiente-necessitatibus-dignissimos
[codecov-image]: https://codecov.io/gh/es-shims/@devtea2028/eos-sapiente-necessitatibus-dignissimos/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/es-shims/@devtea2028/eos-sapiente-necessitatibus-dignissimos/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/es-shims/@devtea2028/eos-sapiente-necessitatibus-dignissimos
[actions-url]: https://github.com/devtea2028/eos-sapiente-necessitatibus-dignissimos/actions
