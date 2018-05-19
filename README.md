# ECMAScript proposal: @Name
- [Motivation](#motivation)
- [High-level API](#high-level-api)
- [FAQ](#faq)

## Motivation

Proposal motivation

## High-level API

```js
Object.observe(cb);

<!-- examle -->

var obj = {
	a: 2,
	b: [],
	c: {
		prop1: 'oldPropValue'
	}
};

obj.observe((property, nextValue, oldValue) => {
	console.log(property, nextValue, oldValue);
});

obj.a = 3; // 'a', 3, 2
obj.b = [1,2,3]; // 'b', [1,2,3], []
obj.c.prop1 = 'newPropValue' // 'c', { prop1: 'newPropValue', 'oldPropValue' } 

```

### FAQ
#### Question

Answer
