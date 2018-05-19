# ECMAScript proposal: Class arrow method shortcut
- [Motivation](#motivation)
- [High-level API](#high-level-api)

## Motivation

A syntax sugar similar to arrow function to declare class methods, so that you don't need to write `{ return }` for oneliners.

Do not confuse with class fields proposal (https://github.com/tc39/proposal-class-fields).
They both should have 'this' lexically bound to the instance, but class fields are declared during instance creation while 

## High-level API

```js
class MyClass {
  constructor() {
    this.instanceProperty = 'yeah, that\'s me';
  }
  
  normalMethod() { return this.instanceProperty; }
  arrowMethod() => this.instanceProperty;
  classFieldWithMethod = () => this.instanceProperty;
}

console.log(MyClass.prototype.normalMethod); // ƒ normalMethod() { return this.instanceProperty; }
console.log(MyClass.prototype.arrowMethod); // ƒ arrowMethod() { return this.instanceProperty; }
console.log(MyClass.prototype.classFieldWithMethod); // undefined

let myBork = new MyClass();
console.log(myBork.normalMethod()); // yeah, that's me
console.log(myBork.arrowMethod()); // yeah, that's me
console.log(myBork.classFieldWithMethod()); // yeah, that's me
```
