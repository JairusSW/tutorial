---
description: How to use the fetch() api from AS.
---

# Make a HTTP request



## Installation

```bash
~ npm install as-fetch
```

## Usage

Add `--exportTable --exportRuntime` flag

JavaScript

```javascript
+ const FetchImport = require("as-fetch/imports")
+ const Fetch = new FetchImport()
const imports = {
+  ...Fetch.wasmImports,
}
const wasmModule = loader.instantiateSync(...)
+ Fetch.wasmExports = wasmModule.exports
```

AssemblyScript

```javascript
import { fetch } from 'as-fetch'

fetch("https://example.com/get", {
  method: "GET",
  mode: "no-cors",
  headers: [],
}).then((response) => {
  const text = response.text();
  console.log("Response: " + text);
});
```

## Performance

When **as-fetch** is used in the browser, it used the native `fetch()` which is extremely slow. However, in NodeJS it relies on `cross-fetch` or `undici-fetch`. Undici fetch is the fastest by far.

* Browser Fetch \(Slowest\)
* Cross-Fetch \(Fast\)
* Undici-Fetch \(Fastest\)

