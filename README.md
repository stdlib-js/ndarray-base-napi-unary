<!--

@license Apache-2.0

Copyright (c) 2021 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->

# Unary

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> C API for registering a Node-API module exporting an ndarray interface for applying a unary callback to an input ndarray.

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/ndarray-base-napi-unary
```

</section>

<section class="usage">

## Usage

```javascript
var headerDir = require( '@stdlib/ndarray-base-napi-unary' );
```

#### headerDir

Absolute file path for the directory containing header files for C APIs.

```javascript
var dir = headerDir;
// returns <string>
```

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

```javascript
var headerDir = require( '@stdlib/ndarray-base-napi-unary' );

console.log( headerDir );
// => <string>
```

</section>

<!-- /.examples -->

<!-- C interface documentation. -->

* * *

<section class="c">

## C APIs

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- C usage documentation. -->

<section class="usage">

### Usage

```c
#include "stdlib/ndarray/base/napi/unary.h"
```

#### stdlib_ndarray_napi_unary( env, info, \*obj )

Invokes an ndarray interface which applies a unary callback to an input ndarray based on provided JavaScript arguments.

```c
#include "stdlib/ndarray/base/function_object.h"
#include <node_api.h>

// ...

static const struct ndarrayFunctionObject obj = {...};

// ...

/**
* Receives JavaScript callback invocation data.
*
* @param env    environment under which the function is invoked
* @param info   callback data
* @return       Node-API value
*/
napi_value addon( napi_env env, napi_callback_info info ) {
    stdlib_ndarray_napi_unary( env, info, &obj );
    return NULL;
}

// ...
```

The function accepts the following arguments:

-   **env**: `[in] napi_env` environment under which the function is invoked.
-   **info**: `[in] napi_callback_info` callback data.
-   **obj**: `[in] struct ndarrayFunctionObject*` ndarray [function object][@stdlib/ndarray/base/function-object].

```c
void stdlib_ndarray_napi_unary( napi_env env, napi_callback_info info, const struct ndarrayFunctionObject *obj );
```

#### STDLIB_NDARRAY_NAPI_MODULE_UNARY( obj )

Macro for registering a Node-API module exporting an ndarray interface for applying a unary callback to an input ndarray.

```c
#include "stdlib/ndarray/base/function_object.h"

// ...

// Create an ndarray function object:
static const struct ndarrayFunctionObject obj = {...};

// ...

// Register a Node-API module:
STDLIB_NDARRAY_NAPI_MODULE_UNARY( obj );
```

The macro expects the following arguments:

-   **obj**: `struct ndarrayFunctionObject` ndarray [function object][@stdlib/ndarray/base/function-object].

When used, this macro should be used **instead of** `NAPI_MODULE`. The macro includes `NAPI_MODULE`, thus ensuring Node-API module registration.

</section>

<!-- /.usage -->

<!-- C API usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

### Notes

-   The function expects that the callback `info` argument provides access to the following JavaScript arguments:

    -   `X`: input ndarray data buffer (i.e., [typed array][mdn-typed-array]).
    -   `metaX`: `X` [serialized meta data][@stdlib/ndarray/base/serialize-meta-data].
    -   `Y`: destination ndarray data buffer (i.e., [typed array][mdn-typed-array]).
    -   `metaY`: `Y` [serialized meta data][@stdlib/ndarray/base/serialize-meta-data].

</section>

<!-- /.notes -->

<!-- C API usage examples. -->

<section class="examples">

</section>

<!-- /.examples -->

</section>

<!-- /.c -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2022. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/ndarray-base-napi-unary.svg
[npm-url]: https://npmjs.org/package/@stdlib/ndarray-base-napi-unary

[test-image]: https://github.com/stdlib-js/ndarray-base-napi-unary/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/ndarray-base-napi-unary/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/ndarray-base-napi-unary/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/ndarray-base-napi-unary?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/ndarray-base-napi-unary.svg
[dependencies-url]: https://david-dm.org/stdlib-js/ndarray-base-napi-unary/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://gitter.im/stdlib-js/stdlib/

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/ndarray-base-napi-unary/main/LICENSE

[mdn-typed-array]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypedArray

[@stdlib/ndarray/base/function-object]: https://github.com/stdlib-js/ndarray-base-function-object

[@stdlib/ndarray/base/serialize-meta-data]: https://github.com/stdlib-js/ndarray-base-serialize-meta-data

</section>

<!-- /.links -->
