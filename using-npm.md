---
description: Publishing AS packages to npm and more!
---

# Using NPM

## Publishing to NPM

### _Publishing an AssemblyScript project_

Publishing an AS package to NPM is quite simple. We need to delete the `main` key and provide the `types` and `ascMain` keys in our `package.json`.

{% hint style="info" %}
Make sure that the main AssemblyScript file is named `index.ts`.\
Don't include a `./`\` in front of your types/ascMain path.
{% endhint %}

{% code title="package.json" %}
```javascript
{
  "name": "as-example",
  "version": "1.0.0",
- "main": "DELETE",
+ "types": "Main AssemblyScript file path",
+ "ascMain": "Main AssemblyScript file path"
  "scripts": {},
  "keywords": [],
  "license": "MIT",
  "dependencies": {}
}
```
{% endcode %}

{% hint style="warning" %}
Both ascMain and types MUST point to an `index.ts` file. If not, AssemblyScript will panic.
{% endhint %}

### _Publishing the loader_

Publishing the loader file works if you are targeting JS modules. Keep in mind that this _**will not work**_ with AssemblyScript projects.

{% code title="package.json" %}
```javascript
{
  "name": "as-example",
  "version": "1.0.0",
+ "main": "Main JS File",
- "types": "DELETE",
- "ascMain": "DELETE"
  "scripts": {},
  "keywords": [],
  "license": "MIT",
  "dependencies": {}
}
```
{% endcode %}

{% hint style="info" %}
Sometimes, things get really tricky. I'll extend this article further in the future.
{% endhint %}
