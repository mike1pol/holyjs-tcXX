# ECMAScript proposal: Support specified catch by object name

- [Motivation](#motivation)
- [High-level API](#high-level-api)
- [FAQ](#faq)

## Motivation

Example in our world

```js
try {
   doStuff();
} catch (e) {
    if (e instaceof MySuperError) {
        // we are not interested to write if...
    }
}
```

## High-level API

Due a required compatibility with @flow or @typescript I suggest different versions of syntax

## without operator

```js
try {
   doStuff();
} catch (e MySuperError) {
}
```

Attention: `e MySuperError` is not similiar to `e: MySuperError` (no `:`)

## with instanceof

```js
try {
   doStuff();
} catch (e instaceof MySuperError) {

}
```
