# ECMAScript proposal: Optional type notations

* [Motivation](#motivation)
* [High-level API](#high-level-api)
* [FAQ](#faq)

## Motivation

JavaScript need an optional runtime type checking with short syntax.
For example:

If developer need strict checking for function he will use third-party software or will write checking like this:

1.  Simple type check

```js
const mul = (a, b) => {
  if (typeof a !== 'number') {
    throw new TypeError('"a" variable must be an number');
  }
  if (typeof b !== 'number') {
    throw new TypeError('"b" variable must be an number');
  }
  return a * b;
};
```

2.  Object type check

```js
const sayHi = user => {
  if (
    typeof user === 'object' &&
    user !== null &&
    typeof user.name === 'string' &&
    typeof user.age === 'number'
  ) {
    console.log(`Hi, I am ${user.name} and I am ${user.age} age old`);
  } else {
    throw new TypeError('"user" is not compatible with User type');
  }
};
```

This checks take a lot of place in code and it is not declarative.

## High-level API

I propose short and well-known syntax sugar for this checking:

1.  Simple type check

```js
const mul = (a: number, b: number) => a * b;
```

2.  Object type checking

```js
type User = {
  name: number,
  age: number,
};
const sayHi = (user: User) =>
  console.log(`Hi, I am ${user.name} and I am ${user.age} age old`);
```

And type notations are optional which save backward compatibility for previous versions of ECMAScript.
