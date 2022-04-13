---
description: How to run our first AssembyScript program!
---

# Running the program

### [Live Editor](https://stackblitz.com/edit/node-y9qnxy) ⚡

## Setting it up

Navigate to the `index.js` file in your project folder. Replace it with this code.

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

// CODE-GOES-HERE

module.exports = wasmModule.exports;
```
{% endcode %}

Now, add these lines of code right below `// CODE-GOES-HERE`.

```javascript
const add = wasmModule.exports.add;
// Grab the add function from the exports.

console.log(`Add: ${add(3, 6)}`);
// Run the add function. Sum is 9.
```

Lastly, run `node index.js`. It will run the AS function, get the result, and log it.

```javascript
~ node index.js
Add: 9
```

Yay! You made your first AssemblyScript app! Now, try and see if you can make a a **subtraction** function!

Here's a few hints:

1. Make sure to recompile: `npm run asbuild`
2. Rewrite the add function to do subtraction
3. Make sure to change the index.js file
