---
description: EventEmitters for AssemblyScript
---

# Make an EventEmitter

## Installation

```bash
~ npm install as-events
```

## Usage

```javascript
import { EventEmitter } from 'as-events'

const emitter = new EventEmitter<string>()

emitter.on('event', (data) => {

    //...

})

emitter.emit('event', 'Hello Event Emitter!')
```

{% hint style="info" %}
This isn't so practical at the moment because you run into issues with closures. 
{% endhint %}

## Benchmarks

I ran a few benchmarks and found that `as-events` is over 2x faster than NodeJS's Events. However, it slowed down at around one million ops/s. 😃

