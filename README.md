***More than u wanna know about es6 modules***
* a best practice for module definition is providing the public
interface to that module on a single export, like so:
```javascript
const lifeAndTheUniverse = 42

function add(a, b) {
  return a + b
}

function subtract(a, b) {
  return a - b
}

export {add, subtract, lifeAndTheUniverse}

// use in another file:
import {add, subtract, lifeAndTheUniverse} from './list-of-exports'
```
* alt version with default
```javascript
// in this export file
export { subtract, now, chewie as default }
// to import in another file -------------------
import chewie, {subtract, now} from './multiple-things'

```
* mixed named and default exports
```javascript
//------ underscore.js ------
export default function (obj) {
    ...
};
export function each(obj, iterator, context) {
    ...
}
export { each as forEach };

//------ main.js ------
import _, { each } from 'underscore';
// same as
import { each, default as _ } from 'underscore';
...
```

* combine exports into a single interface
* only exports the named exports (not default)
```javascript
// ./module
/*
 * // ./other-module
 * export const foo = 'foo'
 *
 * // ./another-other-module
 * export const bar = 'bar'
 */
export * from './other-module'
export * from './another-other-module'

/*
 * import {foo, bar} from './module'
 * console.assert(foo === 'foo')
 */
```

* see export-example.jpg for pattern useing index.js to define a folder interface
