# ECMAScript proposal: __scope
- [Motivation](#motivation)
- [High-level API](#high-level-api)
- [FAQ](#faq)

## Motivation

To be able to grab all local variables to a hash in an easy way;

## High-level API

```js
// example code

var someFunction = () => {
  
  const firstScope = __scope; 
  /*
  so, far here
  firstScope will contain a hash:
  { someVar : undefined }
  */
  
  
  const someConst = true;
  let someEasy = 123;
  
  const secondScope = __scope; 
  /*
  secondScope will contain a hash
  {
    someVar : undefined,
    someEasy : 123,
    someConst : true
  }
  */
  
  
  if (someConst) {
    someEasy = 321;
    const thirdScope = __scope;
    /*
    thirdScope contains
    {
      someVar : undefined,
      someEasy : 321,
      someConst : true
    }
    */
  }
  
  const fourthScope = __scope; 
  /*
  fourthScope will contain
  {
    someVar : undefined,
    someEasy : 123,
    someConst : true
  }
  */
  
  var someVar = 'someVar';
  
  const fifthScope = __scope; 
  /*
  fifthScope will contain
  {
    someVar : 'someVar',
    someEasy : 123,
    someConst : true
  }
  */

}

```

### FAQ
#### For What?

-- transferring current local scope somewhere else

-- applying current  local scope somewhere else

-- testing

