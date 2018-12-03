# ECMAScript proposal: Support union of "types" by `|` operator

- [Motivation](#motivation)
- [High-level API](#high-level-api)
- [FAQ](#faq)

## Motivation

i current world

```js
if (a instanceof UnknownError || a instanceof UnexpectedError) {
}
```

## High-level API

Example 1:

```js
if (a instanceof UnknownError|UnexpectedError) {
}
```

Example 2:

If https://github.com/mike1pol/holyjs-tcXX/pull/7 will be accepted (syntax ver 2), we can do

```
try {
   doStuff();
} catch (e instaceof UnknownError|UnexpectedError) {

}
```
