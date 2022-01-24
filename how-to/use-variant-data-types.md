# Use Variant data types

\[as-variant]\([https://github.com/](https://github.com/MaxGraey/as-variant)) allows you to have the possibility of mixing types and returning multiple types from a function. It allows a certain amount of dynamicness while maintaining strict typing.

### Basic Usage



```
import { Variant } from 'as-variant'

class Foo { }

let vNum = Variant.from(123)      // stored as i32
let vStr = Variant.from('hello')  // stored as string
let vFoo = Variant.from(new Foo)  // stored as Foo reference

vNum.set(2.0)                     // now stored as f64

assert(vNum.is<f64>())            // ok
assert(!vStr.is<f64>())           // ok
assert(vStr.is<string>())         // ok
assert(vFoo.is<Foo>())            // ok

let valF64   = vNum.get<f64>()    // safely extract value
let willFail = vNum.get<string>() // will throw exception!
```

#### Unsafe Usage



```
let vNum = Variant.from(123)
// `getUnchecked` skips all checks. It may be danger.
assert(vNum.getUnchecked() == 123)
```

#### Use as value for dynamic map



```
const dict = new Map<string, Variant>()

dict.set('str', Variant.from('hello'))
dict.set('num', Variant.from(124.0))

dict.set('arr', Variant.from([1, 2, 3]))

assert(dict.get('arr').get<i32[]>()[2] == 3)
// or
assert(dict['arr'].get<i32[]>()[2] == 3)
```

Which is the equivalant in JavaScript:

```
const dict = {
  str: 'hello',
  num: 124.0,
}

dict.arr = [1, 2, 3]

assert(dict.arr[2] == 3)
```
