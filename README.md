# Redis Utilities

Utilities for Redis functionality

# Publishling to npm

To update the module on npm:

1. Ensure `package.json`'s version number has been incremented.
2. Checkout the main branch
3. Pull and update the main branch
4. `npm run publish` to publish the package to npm.


# Examples

## MessageStream

Stream for publishing and consuming data using redis

```js
const stream = new MessageStream('testing');
await stream.connect();
await stream.addMessage({ hello: 'world' });
let { message } = await stream.consumeMessage();
console.log(message); // { hello: 'world' }
await disconnect();
```

## MessageQueue

A redis implementation of a queue

```js
let queue = new MessageQueue('testing');
await queue.connect();
await queue.push({ someKey: 'Some data' });

while (await queue.size()) {
    console.log(await queue.pop()); // { someKey: 'Some data' }
}

await queue.disconnect();
```
