# virtual-widget

[![NPM version][npm-image]][npm-url]
[![build status][travis-image]][travis-url]
[![Test coverage][codecov-image]][codecov-url]
[![Downloads][downloads-image]][downloads-url]
[![js-standard-style][standard-image]][standard-url]

Create a virtual-dom widget.

## Installation
```sh
$ npm install virtual-widget
```

## Usage
```js
// map.js
const virtualWidget = require('virtual-widget')

module.exports = virtualWidget({
  init: function () {
    var elem = document.createElement('div')
    this.map = GoogleMap(elem)
    this.map.setPosition(this.state.position)
    return elem
  },
  update: function (prev, el) {
    this.map = this.map || prev.map
    this.map.setPosition(this.position)
  }
})
```
```js
// view.js
const map = require('./map')

module.exports = view

function view (h, state) {
  return h('section.foo', [
    map(state)
  ])
}
```

## API
### render = virtualWidget(hooks)
Create a new `virtual-widget` using hooks. The following hooks are available:
- __init__: run when the element is first created. Define the instantiation
  logic here.
- __update__: run on a re-render. Gives a chance to update state.

## See Also
- [virtual-dom/docs/widgets](https://github.com/Raynos/mercury/blob/master/docs/widgets.md)
- [mercury/docs/how-to-do-custom-rendering](https://github.com/Raynos/mercury/blob/master/docs/faq.md#how-do-i-do-custom-rendering)

## License
[MIT](https://tldrlegal.com/license/mit-license)

[npm-image]: https://img.shields.io/npm/v/virtual-widget.svg?style=flat-square
[npm-url]: https://npmjs.org/package/virtual-widget
[travis-image]: https://img.shields.io/travis/yoshuawuyts/virtual-widget/master.svg?style=flat-square
[travis-url]: https://travis-ci.org/yoshuawuyts/virtual-widget
[codecov-image]: https://img.shields.io/codecov/c/github/yoshuawuyts/virtual-widget/master.svg?style=flat-square
[codecov-url]: https://codecov.io/github/yoshuawuyts/virtual-widget
[downloads-image]: http://img.shields.io/npm/dm/virtual-widget.svg?style=flat-square
[downloads-url]: https://npmjs.org/package/virtual-widget
[standard-image]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square
[standard-url]: https://github.com/feross/standard
