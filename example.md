# ECMAScript proposal: Add fibers support
- [Motivation](#motivation)
- [High-level API](#high-level-api)
- [FAQ](#faq)

## Motivation

Pausable stackfull coroutines (fibers) will add ability to write siple but responsive and cuncurrency code.
We can use it for:
1. Automatic pause long task every 16 ms to ensure 60fps.
2. Concurent execution of different tasks (not serial).
3. Abort not completed execution by reactions to events.
4. Abstract of asynchrony. Synchronous code is simplier.

## High-level API

```typescript
interface Fiber< Result > implements Promise, Observable {
  new( handler : ( fiber : Fiber )=> Result ) // creates new fiber
  wait() : Result // wait for sub fiber result, rethrow any exceptions from it
  detach() : Promise< Result > // run fiber in next tick (like Promise)
  abort() : void // abort not completed fiber
}
```

## Usage example

```typescript
const fiber = new Fiber( task )

function task() {
  return subtask()
}

function subtask() {
  if( Math.random() > .5 ) sleep() // random asynchrony
  return 1
}

function sleep( timeout ) {
  const fiber = new Fiber( fiber => setTimeout( fiber.done ) )
  fiber.wait()
}
```
