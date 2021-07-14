{% include _includes/nav.md %}

## Javascript

### JS Technologies:
- ES6
- Babel
- Class Object definition

Use `class` when possible. "Classes are a template for creating objects. They encapsulate data with code to work on that data. Classes in JS are built on prototypes but also have some syntax and semantics that are not shared with ES5 class-like semantics." [Moz Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

### JS Folder Structure
```js
├── js
│   ├── _actions
│   ├── _helpers
│   ├── global
│   ├── modules
│   ├── app.js
```

#### js/modules
Modules are js components that are lazy-loaded depending on if needed on the page. To call a js module that a certain element needs in order to function, it is required to add the data attribute `data-js-module` and the class `js-module`

##### Use camel-case folders for modules
```javascript
// Bad
'src/js/modules/MyModule.js'

// Good
'src/js/modules/MyModule/index.js'
```
##### Basic module file structure.
```js
// js/modules/MyModule/index.js

import { handleEvent } from "../../_helpers"

export default class {
 /** constructor(el) Required **/
 constructor(el) {
  // Setup inital Vars
  this.DOM = {}
  this.DOM.el = el
  this.DOM.childElement = el.querySelector('.other-element')
  this.DOM.globalElement = el.querySelector('.global-element')

  this.genre = el.dataset.jsGenre // Jazz
 }
 
 /** init() Required **/
 init() {
  // Break up code for different functionality
  this.handleEvents()
 }
 
 handleEvents() {
  handleEvent('click', {
   el: this.DOM.el,
   callback: () => { this.clickEvent() }
  })
 }

 clickEvent() {
  console.log(`change something about ${this.DOM.globalElement}`)
 }

 /** destroy() Required **/
 destroy() {
  /* 
   - Destroy any event handler or tickers
   - Generally you don't have to worry about destroying element. 
     Only if you are ajaxing something or need to rebuild the module for some reason.
  */
 }
}
```

##### Let's attached `MyModule` to an element!
```html
<div class="js-module" data-js-module="MyModule"></div>
```

##### Data Attributes
When adding data attributes to HTML elements to pass data to `JS`, always define `data-js` so signify that it is used in JS and not CSS.
```html
<div [...] data-js-genre="Jazz"></div>
```

#### js/globals
Globals are modules that are used on every page of the site. This could be to handle global functionality in the Footer, Header, etc. These classes should be imported directly into `js/app.js`

```js
let header = import('./globals/Header').then((x) => new x.default())
header.then((x) => x.init())
```

#### js/_actions
Actions are small helper functions that help when needing to import, fetch, or post data. For example, you could have a `fetchData` function, where you could pass a URL into `fetchData('/foo/bar')` which would handle the fetch request. These generally are imported directly into different modules/globals when needed.

#### js/_helpers
Helpers are functions that help with smaller tasks that are used through the site. I would suggest going through them and checkout what is available. Some commonly used functions are: 
- `js/_helpers/throttle` - Used to throttle resize, etc.
- `js/_helpers/handleEvent` - Used to handle click event instead of using `addEventListener`.
- `js/_helpers/getBounds` - Used to to get the `getBoundingClientRect` of an element.

```js
import {throttle, handleEvent, getBounds} from '../../_helpers'
```

## Arrow Functions
Use Arrow Functions to define a function.
```javascript
// Bad
function() {}

// Good
() => {}
```

## Dynamically import js packages
When possible, try to lazyload js using dynamic imports if it's not needed on page load. For example, if a piece of functionality isn't needed until a button click or something becomes visible.

Code Example:
1. Clicking the `this.DOM.button1` element will import `ModuleTwo`, if it has already been imported, then it skips the import and uses the already imported reference.
2. Click the `this.DOM.button2` element, call the destroy method of `ModuleTwo`; This will not destroy the instance of `this.moduleTwo`, you will need to do that manually if you need to unbind it from the parent class.

Use the **_action** function (`_actions/getModule`) to import new modules.

```javascript
import {getModule} from '../_actions'

export default class {

  [...]

  /**
   * Handle event listeners
  */
  handleEvents() {
    this.DOM.button1.addEventListener('click' () => {
      this.moduleTwo = this.moduleTwo ? this.moduleTwo : getModule('ModuleTwo').then((x) => new x.default());
      this.moduleTwo.then((x) => x.init())
    });

    this.DOM.button2.addEventListener('click' () => {
      this.moduleTwo & this.moduleTwo.then((x) => x.destroy())
    });
  }
}
```