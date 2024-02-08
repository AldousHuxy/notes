# Prerequisites
## HTTP Status Codes
   - 1xx - Informational Response
   - 2xx - Success
   - 3xx - Redirection
   - 4xx - Client Errors
   - 5xx - Server Errors

Type   | Number | Code
------ | ------ | ----
Informational Response  | 100 | Continue
Success                 | 200 | OK
Success                 | 201 | Created 
Redirection             | 300 | Multiple Choices
Client Error            | 400 | Bad Request
Client Error            | 401 | Unauthorized
Client Error            | 402 | Payment Required
Client Error            | 403 | Forbidden
Client Error            | 404 | Not Found
Server Error            | 500 | Internal Server Error
Server Error            | 502 | Bad Gateway

## JSON
```json
{
  "string": "my string",
  "number": 13,
  "array": ["value 1", 3 , "value 2"],
  "object": {
    "field1": 4,
    "field2": [
      "field value1"
    ]
  }
}
```

## JavaScript high order array methods (forEach, map, filter, etc.)
```ts
const numbers = [65, 44, 12, 4];
const newArr = numbers.map(myFunction)

function myFunction(num) {
  return num * 10;
}
```

## Arrow functions
```ts
const foo = () => console.log('bar')
```