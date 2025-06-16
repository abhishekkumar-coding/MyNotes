### Ftech & Axios

## Fetch
The fetch API is a built-in web API in modern browsers that allows you to make HTTP requests (like GET, POST, etc.) to servers — similar to how you use axios, but without needing to install anything.

- Example:
```js
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

## Axios
Axios is a promise-based HTTP client for the browser and Node.js. It is used to make HTTP requests to APIs or servers, just like fetch, but with more powerful features and a cleaner syntax.
- Example:
```js
axios.get('https://api.example.com/data')
  .then(response => console.log(response.data))
  .catch(error => console.error(error));
```

## Comparison
Here's a comparison of the features and syntax of `fetch` and `axios`:

| Feature                  | `fetch` (Built-in)                                | `axios` (3rd-party library)                |
| ------------------------ | ------------------------------------------------- | ------------------------------------------ |
| **Availability**         | Built into modern browsers                        | Needs to be installed: `npm install axios` |
| **Request Syntax**       | Verbose                                           | Cleaner and more concise                   |
| **Default JSON Parsing** | ❌ Must call `.json()` manually                    | ✅ Automatically parses JSON                |
| **Timeout Support**      | ❌ No native timeout support                       | ✅ Has built-in timeout handling            |
| **Interceptors**         | ❌ Not available                                   | ✅ Can modify requests/responses globally   |
| **Error Handling**       | Only rejects on network error                     | Rejects on bad status codes (like 4xx/5xx) |
| **Progress Tracking**    | ❌ Requires manual implementation                  | ✅ Built-in progress tracking               |
| **Request Cancellation** | ❌ Limited (`AbortController`)                     | ✅ Easy with `CancelToken`                  |
| **Old Browser Support**  | Requires polyfill for older browsers              | ✅ Better support via polyfills             |
| **Response Schema**      | Response has to be parsed manually (`res.json()`) | Already parsed in `res.data`               |
