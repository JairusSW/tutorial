# Use JSON (de)serialization

[https://github.com/JairusSW/as-json/](https://github.com/JairusSW/as-json/) provided a performant, spec-compatible, and ts-like api for (de)serialization of JSON. Here is a basic usage example.

{% hint style="info" %}
as-json is currently going through a major rewrite. It should stay stable throughout the rewrite, but I cannot assure you it will not break. Please file an issue if you find any problems. It would be most helpful! :D
{% endhint %}



### Installation

Install the library:

```
npm install json-as
```

Install dependency for a transformer:

```
npm install --save-dev visitor-as
```

Add a transform to the `asc` command (e.g. in `package.json`):

```
--transform json-as/transform
```

### Usage

```
import { JSON } from 'json-as'
@json
class JSONSchema {
    firstName: string
    lastName: string
    age: i32
}

const data: JSONSchema {
    firstName: 'Jairus',
    lastName: 'Tanaka',
    age: 14
}

const stringified = JSON.stringify(data)
// '{"firstName":"Jairus","lastName":"Tanaka","age":14}'

const parsed = JSON.parse<JSONSchema>(stringified)
// { firstName: "Jairus", lastName: "Tanaka", age: 14 }
```
