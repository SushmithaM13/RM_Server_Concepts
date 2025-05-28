# RM_Server_Concepts

# Understanding Node.js, Express, and HTTP Fundamentals

This document introduces the basics of servers using **Node.js** and **Express.js**, and helps to understand core HTTP concepts used in backend development.

---
## 📌 1. Node.js `http` Module vs. Express.js

| Feature            | Node.js `http` Module              | Express.js                          |
|--------------------|------------------------------------|-------------------------------------|
| Setup              | Manual, verbose                    | Simple and concise                  |
| Routing            | Needs manual implementation        | Built-in routing                    |
| Middleware         | Not available                      | Fully supported                     |
| Readability        | Less readable                      | More readable and maintainable     |
| JSON Support       | Manual JSON handling               | Automatic JSON parsing with middleware |
| Community Support  | Core Node.js feature               | Large community, many plugins      |
| Scalability        | Limited                            | Highly Scalable                    |

### Example: Hello World Server
**Node.js `http`**
```js
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello from Node.js');
});

server.listen(3000, () => console.log('Server running on port 3000'));

**Express.js**
```js
const express = require('express');
const app=express();

app.get('/', (req, res)=>{
    res.send('Hello from Express.js');
});

app.listen(3000, ()=>console.log('Server running on port 3000'));

