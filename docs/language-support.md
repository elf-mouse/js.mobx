### TypeScript or ES6 + Instance Fields + Decorators

```js
import {observable} from 'mobx';

class Todo {
    id = Math.random();
    @observable title = "";
    @observable finished = false;
}
```

Instance fields and decorators can can be enabled in Babel via the [transform-class-properties](https://www.npmjs.com/package/babel-plugin-transform-class-properties) and [transform-decorators-legacy](https://www.npmjs.com/package/babel-plugin-transform-decorators-legacy) plugin.

```
$ npm install babel-plugin-transform-class-properties
$ npm install babel-plugin-transform-decorators-legacy

// .babelrc

/// WRONG
"plugins": [
  "transform-class-properties",
  "transform-decorators-legacy"
]

// RIGHT
"plugins": [
  "transform-decorators-legacy",
  "transform-class-properties"
]
```

### ES6

```js
import {extendObservable} from 'mobx';

class Todo {
    constructor() {
        this.id = Math.random();
        extendObservable(this, {
            title: "",
            finished: false
        });
    }
}
```

### ES5

```js
var m = require('mobx');

var Todo = function() {
    this.id = Math.random();
    m.extendObservable(this, {
        title: "",
        finished: false
    });
}
```
