# ECMAScript proposal: Static property accessors
- [Motivation](#motivation)
- [High-level API](#high-level-api)
- [FAQ](#faq)

## Motivation

Using the static property accessors, you can write `@@method()`
instead of `this.constructor.method()` or `MyClass.method()`

## High-level API

```js
class FirstClass {
  static staticMethod() {
    console.log('staticMethod called');
  }
}

class SecondClass extends FirstClass {
  constructor() {
    console.log(@@staticMethod()); // staticMethod called
  })
}
```

### FAQ
#### Question
