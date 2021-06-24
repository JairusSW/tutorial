---
description: How to access JavaScript from AssemblyScript
---

# Using imports

#### [Live Editor](https://stackblitz.com/edit/node-ebvcqs) ⚡

## Overview

Here is where this guide gets really exciting. Imports allow us to call a **JavaScript function from AssemblyScript code**. For example, if we wanted to make a console.log function, we would use imports to let AS access the function. Let's see an example.

## Using the imports

Here we go! Let's make an import!

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
declare function log(message: number): void;
// Import the JS log function. (console.log)

export function test(): void {
	log(3.14);
	// Log 3.14 to the console!
}
```

We're all set! Now, we need to set our imports.

```javascript
const imports = {
	index: {
		log: (message) => {
			console.log(message);
			// Log it to the console.
		}
	}
};
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

Awesome! Now, you can call JavaScript from AssemblyScript! In a later article, we'll enhance this function to be able to log whole strings as well.
