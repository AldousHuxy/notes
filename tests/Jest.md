# Jest
 - [Jest](https://jestjs.io/) is a JavaScript Testing Framework built by Facebook with a focus on simplicity.
```bash
npm i -D jest
```

## Example
```ts
export const sum = (a, b) => {
    return a + b;
}
```
```ts
import { sum } from ('./sum');

test('adds 1 + 2 to equal 3', () => {
    expect(sum(1, 2)).toBe(3)
})
```
```json
// package.json
{
  "scripts": {
    "test": "jest"
  }
}
```