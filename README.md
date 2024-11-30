# Why use Express

### Simplifies the HTTP Handling

Node.js provides a low-level `http` module for handling HTTP requests and responses. Routing in raw Node involves:

- Parsing the request URL.
- Checking the HTTP method.
- Manually writing conditional logic to determine how to handle each route.

For example, in pure Node:
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  if (req.url === '/' && req.method === 'GET') {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Hello, World!');
  } else if (req.url === '/about' && req.method === 'GET') {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('About Us');
  } else {
    res.writeHead(404, { 'Content-Type': 'text/plain' });
    res.end('Not Found');
  }
});

server.listen(3000, () => console.log('Server running on port 3000'));
```

### Provides a Clean Routing Interface

Express simplifies routing with a declarative API. Instead of manually checking URLs and methods, you define routes and handlers directly using methods like `.get`(), `.post()`, `.put()`, etc.

With Express:

```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello, World!');
});

app.get('/about', (req, res) => {
  res.send('About Us');
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

### Middleware for Pre/Post-Processing
Express introduces the concept of middleware—functions that run before or after a request handler. Middleware simplifies tasks like:

- Logging.
- Parsing request bodies (e.g., JSON or URL-encoded data).
- Handling authentication.

Example:
```javascript
const express = require('express');
const app = express();

// Middleware
app.use((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
});

app.get('/', (req, res) => {
  res.send('Hello, Middleware!');
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

### Express builds on Node by:

- Simplifying routing with a declarative API.
- Introducing middleware for extensibility.
- Streamlining request parsing, error handling, and routing parameters.
- Supporting view engines and modular architecture.

### Install Express
Install Express as a dependency in your project:
```bash
npm install express
```
This will create a `node_modules` folder and add Express to your `package.json` dependencies.

### Run the Server
```bash
node server.js
```
You should see the following message in your terminal:
```bash
Server running on http://localhost:3000
```