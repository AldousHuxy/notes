# TanStack Query
> "There are only two hard things in Computer Science: cache invalidation and naming things." - Phil Karlton

## AJAX
 - AJAX stands for Asynchronous JavaScript and XML
 - It is a set of web technologies that enable JavaScript to send and receive data asynchronously

### XML Http Request
```ts
function getMovies() {
  var xhr = new XMLHttpRequest()
  xhr.open('GET', 'http://example.com/movies.json', true)
  xhr.onreadystatechange = function(){
    if (this.readyState === 4 && this.status === 200) {
      console.log(this.response)
    }
  }
  xhr.send()
}
```

### Fetch API
```ts
const getMovies = () => {
  fetch('http://example.com/movies.json')
    .then(res => res.json())
    .then(movies => console.log(movies))
    .catch(err => console.error(err))
}
```

### Fetch API with Async/Await
[Post Example](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
```ts
const getMovies = (data = {}) => {
  try {
    const res = await fetch('http://example.com/movies.json')
    const movies = await res.json()
    console.log(movies)
    return movies
  } catch (err) {
    console.error(err)
  }
}
```

### Axios
```ts
const getMovies = async () => {
  try {
    const response = await axios.get('http://example.com/movies.json')
    const movies = await res.json()
    console.log(movies)
    return movies
  } catch (err) {
    console.error(err)
  }
}
```
 - TanStack Query (FKA React Query) is often described as the missing data-fetching library for web applications, but in more technical terms, it makes fetching, caching, synchronizing and updating server state in your web applications a breeze.
## Queries

### Query Basics
 - A query is a declarative dependency on an asynchronous source of data that is tied to a unique key. A query can be used with any Promise based method (including GET and POST methods) to fetch data from a server. If your method modifies data on the server, we recommend using Mutations instead.
 - To subscribe to a query in your components or custom hooks, call the useQuery hook with at least:
   - A **unique key for the query**
   - A function that returns a promise that:
     - Resolves the data, or
     - Throws an error

```ts
import { useQuery } from '@tanstack/react-query'

function App() {
  const info = useQuery({ queryKey: ['todos'], queryFn: fetchTodoList })
}
```