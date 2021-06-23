---
description: Publishing AS packages to npm and more!
---

# Using NPM

## Publishing to NPM

#### _Publishing an AS project_

Publishing an AS package to NPM is quite simple. We need to provide `types` and an `ascMain` instead of main in our `package.json`.

{% hint style="info" %}
Make sure that the main as file is named `index.ts`.  
Also, don't include a `./`\` in front of your types/ascMain path.
{% endhint %}

{% code title="package.json" %}
```javascript
{
  "name": "as-example",
  "version": "1.0.0",
  "description": "Your Description Here",
- "main": "DELETE",
+ "types": "Main AS File",
+ "ascMain": "Main AS File"
  "scripts": {},
  "keywords": [],
  "author": "Author Name",
  "license": "MIT",
  "dependencies": {}
}
```
{% endcode %}

{% hint style="warning" %}
If you are publishing an AssemblyScript file, do not add the `main` property.
{% endhint %}

#### _Publishing the loader_

Publishing the loader file works if you are targeting JS modules. Keep in mind that this _Will Not Work_ with AssemblyScript projects.

{% code title="package.json" %}
```javascript
{
  "name": "as-example",
  "version": "1.0.0",
  "description": "Your Description Here",
+ "main": "Main JS File",
- "types": "DELETE",
- "ascMain": "DELETE"
  "scripts": {},
  "keywords": [],
  "author": "Author Name",
  "license": "MIT",
  "dependencies": {}
}
```
{% endcode %}

{% hint style="info" %}
Sometimes, things get really tricky. I'll extend this article further in the future.
{% endhint %}

