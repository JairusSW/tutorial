---
description: How to write and access the console from AS.
---

# Write to the console

## Installation

```bash
~ npm install as-console
```

## Usage

JavaScript

```javascript
...
const loader = require('@assemblyscript/loader')
+ const ConsoleImport = require('as-console/imports')
+ const Console = new ConsoleImport()
const imports = {
+     ...Console.wasmImports
}
const wasmModule = loader.instantiateSync(..., imports);
+ Console.wasmExports = wasmModule.exports
...
```

AssemblyScript

```javascript
import { console } from 'as-console'

console.log('Hello World')

console.log(3.14)
```

