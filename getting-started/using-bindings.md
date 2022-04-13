---
description: How to access JavaScript from AssemblyScript
---

# Using bindings

## Overview

Here is where this AssembyScript gets really exciting. Bindings allow us to call a **JavaScript function from AssemblyScript code**. For example, if we wanted to make a console.log function, we would use auto-generated bindings to let AS access the function. Let's see an example.

## Using bindings

Here we go!

{% code title="index.js" %}
```javascript
const fs = require("fs");
const loader = require("@assemblyscript/loader");
// Import the loader
const imports = {
    /* imports go here */
};
const wasmModule = loader.instantiateSync(
    fs.readFileSync(__dirname + "/build/optimized.wasm"),
    imports
);
// Instantiate the AS program

wasmModule.exports.test();
// Run the app!

module.exports = wasmModule.exports;
```
{% endcode %}

Insert this code into our main AS file.

```javascript
@external("env", "console.log")
// "env" refers to the environment, so global functions
declare function log(message: string): void;
// Import the JS log function. (console.log)

export function test(): void {
    log("Yo, waddup?");
    // Log "Yo, waddup?" to the console!
}
```

Almost there! Make sure to recompile!

```javascript
~ npm run asbuild
```

And lastly, run!

```javascript
~ node index.js
3.14
```

Awesome! Now, you can call JavaScript from AssemblyScript!
