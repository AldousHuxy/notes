# Node JS
 - REST API's & Microservices
 - Real Time Service (Chat, Live Updates)
 - CRUD Applications - Blogs, Shopping Carts, Social Networks.
 - Tools & Utilities.
 - 
## Non-blocking I/O
 - Works on a single thread using non-blocking I/O calls.
 - Supports tens of thousands of concurrent connections.
 - Optimizes throughput & scalability in apps with many I/O operations.
 - 
## The Event Loop
 - Single threaded.
 - Supports concurrency via events & callbacks.
 - EventEmitter class is used to bind events and listeners.
![Event Emitter](https://qph.cf2.quoracdn.net/main-qimg-f163cab2ec436d8963c62a070b20464e-pjlq)

## Events
```ts
import { EventEmitter } from 'node:events';

class MyEmitter extends EventEmitter {}

const myEmitter = new MyEmitter()

myEmitter.on('event', () => {
  console.log('an event occurred!')
})

myEmitter.emit('event')
```

## Path
```ts
import path from 'path';

path.basename('C:\\temp\\myfile.html')
// Returns: 'myfile.html' 
```

## File System
```ts
import { unlink } from 'node:fs/promises';

try {
  await unlink('/tmp/hello')
  console.log('successfully deleted /tmp/hello')
} catch (error) {
  console.error('there was an error:', error.message)
}
```

## Readline
```ts 
import * as readline from 'node:readline/promises';
import { stdin as input, stdout as output } from 'node:process';

const rl = readline.createInterface({ input, output })

const answer = await rl.question('What do you think of Node.js? ')

console.log(`Thank you for your valuable feedback: ${answer}`)

rl.close()
```