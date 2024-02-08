# React Prerequisites
### What we will learn:
 - [ ] How our code is rendered in the browser.
 - [ ] How we use/manage external libraries with npm.
 - [ ] How ES6/Typescript works.

## Node JS
 - [NodeJS](https://nodejs.org/en): an open-source, cross-platform JavaScript runtime environment (JRE).

 - Alternatives to Node include: [Deno](http-s://deno.com/), [Bun](https://bun.sh/), and [TS-Node](https://www.npmjs.com/package/ts-node)

![V8 Engine](https://blogs.sap.com/wp-content/uploads/2020/04/1-55.png)

![Browser Engines](https://www.lambdatest.com/blog/wp-content/uploads/2019/08/browserrenders.jpg)

### Installation
 - To verify, run these commands to check your node/npm or other managers version.
```
node -v
v18.17.1
```
```
npm -v
9.98
```

## Node Package Manager (NPM)
 - The React application can be managed by a `package.json` file which can:
   - Control application scripts for: starting, building, testing, etc.
   - Manage external libraries (dependencies) and their versions.
 - Node comes with [npm](https://www.npmjs.com/) though we can use other package managers such as [pnpm](https://pnpm.io/), [yarn](https://classic.yarnpkg.com/en/) or , [bun](https://bun.sh/).
```bash
npm install --save jest
npm i jest

npm install --save-dev jest

# short-hand
npm i jest
npm i -D jest
```

```json
{
  "name": "find-my-arrows",
  "version": "1.0.0",
  "description": "An application that finds my arrows",
  "main": "index.js",
  "scripts": {
    "start": "node dist/index.js",
    "dev": "ts-node src/index.ts",
    "test": "jest"
  },
  "keywords": [],
  "author": "Clint Barton",
  "license": "ISC",
  "dependencies": {
    "react": "^17.0.1",
    "react-dom": "^17.0.1"
  },
  "devDependencies": {
    "jest": "^29.7.0"
  }
}
```

## Node Modules
 - When we install external libraries with npm, the dependencies are downloaded to a directory called '/nodes_modules'. This folder should only be modified in extremely rare cases.
 - We can create on own modules when additional files are need beyond the entry file.
 - The module will either be a default import or named, in which case you have the option to rename the module

### Modules
#### Default Imports
```ts
// ES5
export default function foo(param: any): any {
    ...
}

// usage somewhere else...
import foo from './foo'
```
```ts
// ES6+
const foo = (param: any): any => {
    ...
}

export default foo;

// usage somewhere else...
import bar from './foo'
```
Named Imports
```ts
// ES6+
export const foo = (param: any): any => {
    ...
}
export const bar = (param: any): any => {
    ...
}

// usage somewhere else...
import { foo, bar as baz } from './foo'
```

## Build Tools
 - A build tool will automatically perform specific tasks that we would otherwise do manually.
 - Some popular build tools include:
   - Webpack
   - Parcel
   - Babel
   - Vite
   - esbuild
   - Speedy Web Compiler (SWC)

## Typescript
 - TypeScript is a strongly typed programming language developed by Microsoft that builds on JavaScript, giving you better tooling at any scale.
 - It's a super set of JavaScript and thus any JavaScript is valid TypeScript.
 - To run your code in a browser you must first compile it into JavaScript using a build such as:
   - Webpack
   - Parcel
   - esBuild
   - Vite
   - Software Web Components (SWC)
   - and more
```js
// JavaScript
var age = 0
var name = 'Clark Kent'
var powers = ['Strength', 'Flight', 'Laser-Vision']
```

```ts
// TypeScript
let age: number = 0
let name = ['Clark Kent'][0] as string
let powers: Array<string>(3) = [] // Does not restrict size
let colors: string[] = ['Blue', 'Red', 'Yellow']
let league: [string, number] = ['rank', 1]
```

```ts
// Generics
const convertToArray = <Type>(input: Type): Type[] => {
    return [input]
}
```

## ES2015 (ES6)
 - ESis a scripting language standard and specification that includes:
   - JavaScript
   - JScript .NET (Microsoft)
   - ActionScript (Adobe)
 - ES6 is the 6th standardized version of JavaScript released in 2015 that dramatically changed the way the language is written.
 - The latest version is ES2023 with annual releases occurring every July

### Variables
 - The keywords `let` and `var` both declare new variables in JavaScript
 - The keyword `const` is used for immutable values.
 - The main difference is in the scope of the variables they create:
```ts
// ES5
function varScoping() {
    var x = 1

    if (true) {
        var x = 2
        console.log(x) // 2
    }

    console.log(x) // 2
}

// ES6+
function letScoping() {
    let x = 1

    if (true) {
        let x = 2
        console.log(x) // 2
    }

    console.log(x) // 1
}
```

### Numeric Separators
```ts
let amount = 1_234_500 // 1234500
```

### Arrow Functions
```ts
// ES6+
const myFunc = (greeting: string = 'Hello World'): void => {
    console.log(greeting)
}
```

### Spread Operator
```ts
const heros: string[] = ['Tony', 'Steve', 'Bruce']
const moreHeros: string[] = ['Donald', 'Natasha', 'Clint']

// ES5
const avengers: string[] = heros.concat(moreHeros)

// ES6+
const assemble = (...args) => args
const avengers: string[] = assemble(...heros, ...moreHeros)
```

### Arguments
```ts
// ES5
function printArgs() {
    return arguments.reduce((total, value) => total + value, 0)
}

console.log(printArgs(1, 2, 3, 4))
// 10
```
```ts
// ES6+
const printArgs = (...args) => {
    return args.reduce((total, value) => total + value, 0)
}

console.log(printArgs(1, 2, 3, 4))
// 10
```

### Ternary Operator
```ts
function getFee(isMember) {
  return isMember ? '$2.00' : '$10.00'
}

console.log(getFee(true))
// Expected output: "$2.00"

console.log(getFee(false))
// Expected output: "$10.00"

console.log(getFee(null))
// Expected output: "$10.00"
```

### Short Circuit Evaluation
```ts
true || true    // true
true || false   // true
false || false  // false
true || ****    // true
```

```ts
let person = {
  name: 'Jack',
  age: 34,
  job: 'Developer'
}
// console.log(person.job || 'unemployed') // 'unemployed'
console.log(person.job || getUnemploymentInfo()) // 'Developer'
```


### Null vs Undefined
 - Any value not instantiated will have a default value of `undefined` in JavaScript.
 - `null` is a value assigned by the developer to indicate that a variable has no value.
```ts
let a
let b = null
let c = undefined
let d = 4
let e = 'five'

let f = a || b || c || d || e

console.log(f)
```

### Destructuring
#### Arrays
```ts
// ES5
const myArray: string[] = ['valueOne', 'valueTwo', 'valueThree']
const valueOne: string = myArray[0]
const valueTwo: string = myArray[1]
const valueThree: string = myArray[2]
```
```ts
// ES6+
const [valueOne, valueTwo, valueThree]: string[] = ['valueOne', 'valueTwo', 'valueThree']
```

#### Objects
```ts
type Player = {
    jersey: number
    firstName: string 
    lastName: string
}
```
```ts
// ES5
const myPlayer: Player = { jersey: 15, firstName: 'Nikolai', lastName: 'Jokic' }
const jersey: string = myPlayer.jersey
const firstName: string = myPlayer.firstName
const lastName: string = myPlayer.lastName
```
```ts
// ES6+
const myPlayer = { jersey: 15, firstName: 'Nikolai', lastName: 'Jokic' }
const [jersey, firstName, lastName]: Player = myPlayer
```

### Loops & Template Strings
```ts
// ES5
const myArray = ['valueOne', 'valueTwo', 'valueThree']

for (let i = 0; i < myArray.length; i++) {
    console.log('Value: ' + myArray[i] + '\n')
}
```
```ts
// ES6+
const myArray = ['valueOne', 'valueTwo', 'valueThree']

myArray.forEach(value => console.log(`Value: ${value}\n`))
```
```ts
// ES6+
// The map method returns something for each iteration
const myMsgs: Messages = [
    { id: 1, msg: 'messageOne' },
    { id: 2, msg: 'messageTwo' },
    { id: 3, msg: 'messageThree' },
]

const myMsgIds: string[] = myMsgs.map(msg => msg.id as string)
```

### Async/Await
```ts
// ES5
fetch('/api/users/auth')
    .then(res => res.json())
    .then(data => console.log(data))
    .catch(err => console.error(err))
```
```ts
// ES6+
try {
    const res = await fetch('/api/users/auth')
    const data = await res.json()
    console.log(data)
} catch (err) {
    console.error(err)
}
```

## ES2022
### At
```ts
// ES2022
const scores: number[] = [94, 93, 87, 88, 95]
const secondToLastScore: number = scores.at(-2)
console.log(secondToLastScore) // 88
```

### Public/Private Fields
```ts
class Foo {
    publicField = 0
    #privateField = 'private field'
    #privateRequiredField

    constructor(value) {
        this.#privateRequiredField = value
    }
    
    checkPrivateValues() {
        console.log(this.#privateField1) // private field
        console.log(this.#privateField2) // ${value}
    }
}
```