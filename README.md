# @erboladaiorg/ullam-dolorem-repellat

[![npm](https://img.shields.io/npm/v/@erboladaiorg/ullam-dolorem-repellat.svg)](https://www.npmjs.com/package/@erboladaiorg/ullam-dolorem-repellat)
[![npm](https://img.shields.io/npm/dw/@erboladaiorg/ullam-dolorem-repellat.svg)](https://www.npmjs.com/package/@erboladaiorg/ullam-dolorem-repellat)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)
[![CI Status](https://github.com/erboladaiorg/ullam-dolorem-repellat/actions/workflows/test.yaml/badge.svg?branch=main)](https://github.com/erboladaiorg/ullam-dolorem-repellat/actions/workflows/test.yaml)

Ignore keys with undefined value to compare from a deep equal operation with chai [expect](http://chaijs.com/api/bdd/).

## Why?

Sometimes you will have properties which have undefined value. This plugin helps to ignore those properties from comparison.

Works with both objects and array of objects with or without circular references.

## Installation

```bash
npm install @erboladaiorg/ullam-dolorem-repellat --save-dev
```

```bash
yarn add @erboladaiorg/ullam-dolorem-repellat --dev
```

## Usage

### Require

```js
const chai = require("chai");
const chaiIgnoreUndefinedProperties = require("@erboladaiorg/ullam-dolorem-repellat");

chai.use(chaiIgnoreUndefinedProperties);
```

### ES6 Import

```js
import chai from "chai";
import chaiIgnoreUndefinedProperties from "@erboladaiorg/ullam-dolorem-repellat";

chai.use(chaiIgnoreUndefinedProperties);
```

### TypeScript

```js
import * as chai from "chai";
import chaiIgnoreUndefinedProperties from "@erboladaiorg/ullam-dolorem-repellat";

chai.use(chaiIgnoreUndefinedProperties);

// The typings for @erboladaiorg/ullam-dolorem-repellat are included with the package itself.
```

## Examples

All these examples are for JavaScript.

### a) excluding

1. Ignore a top level property from an object

```js
expect({ aa: undefined, bb: "b" }).to.equal({
  bb: "b",
  cc: undefined,
});
```

2. Ignore properties within array with undefined values

```js
const expectedArray = [{ aa: undefined, bb: "b" }];
const actualArray = [{ cc: undefined, bb: "b" }];
expect(actualArray).to.deep.equal(expectedArray);
```

3. Ignore a nested properties with undefined value (only for deep equal comparison)

```js
expect({
  topLevelProp: { aa: undefined, bb: "b" },
}).to.deep.equal({
  topLevelProp: { bb: "b", cc: undefined },
});
```

4. Works with circular dependencies

```js
const actualObject = { aa: undefined, bb: "b" };
actualObject.c = actualObject;

const expectedObject = { bb: "b", cc: undefined };
expectedObject.c = expectedObject;

expect(actualObject).to.deep.equal(expectedObject);
```

## Contributing

Contributions are welcome. If you have any questions create an issue [here](https://github.com/erboladaiorg/ullam-dolorem-repellat/issues).

## License

[MIT](LICENSE)
