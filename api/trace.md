# trace

## About

The `trace()` method in AssemblyScript was build  to provide a simple C-like interface that it can be implemented across multiple platforms. It lets you log any string \(with `trace:`  appended\) to the standard out.

## Usage

Using trace is actually quite simple. However, make sure that you do not use `console.trace` because it requires WASI support.

```javascript
trace('Hello World!')
// trace: Hello World!
```

Overall, the trace function is a great way to keep track and debug your code. Keep in mind that it is not suitable for production usage.

