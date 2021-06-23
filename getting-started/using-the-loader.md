---
description: 'The loader allows you to pass strings, arrays, and function between AS and JS.'
---

# Using the loader

#### [Live Editor](https://stackblitz.com/edit/node-xsacin) ⚡

## Overview

The AS loader allows you to pass multiple types \(string, array, ect..\) between AssemblyScript and JavaScript. It provides a layer on top of the native `WebAssembly` interface that makes interaction much simpler.

## Passing strings

Lets extend our `console.log` function from the previous article to include strings. 

{% code title="index.js" %}
```javascript
const fs = require('fs');
const loader = require('@assemblyscript/loader');
// Import the loader
const imports = {
  /* imports go here */
};
const wasmModule = loader.instantiateSync(
  fs.readFileSync(__dirname + '/build/optimized.wasm'),
  imports
);
// Instantiate the AS program

wasmModule.exports.test()
// Run the app!

module.exports = wasmModule.exports
```
{% endcode %}

Now, our main AS file.

```javascript
declare function log(message: string): void
// Import the JS log function. (console.log)

export function test(): void {
    log('Hello World!')
    // Log 'Hello World!' to the console!
}
```

Lastly, we modify our imports

```javascript
const imports = {
  index: {
    log: (message) => {
      const content = wasmModule.exports.__getString(message)
      // Convert message to string
      console.log(content)
      // Log it to the console.
    }
  }
};
```

Almost there! Make sure to rebuild!

```javascript
~ npm run asbuild
```

And lastly, run!

```javascript
~ node index.js
'Hello World!'
```

It worked! 😀

