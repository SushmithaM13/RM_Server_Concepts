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
const express = require('express');
const app=express();

app.get('/', (req, res)=>{
    res.send('Hello from Express.js');
});

app.listen(3000, ()=>console.log('Server running on port 3000'));

📌 2. res.send() vs res.json()
**res.send()**: Can send various types of responses such as a string (HTML), a Buffer, an object, or even an array. If you pass an object or array, Express will automatically convert it to JSON, but this is not as explicit as using res.json().

**res.json()**: Specifically used to send a JSON response. It sets the appropriate headers (Content-Type: application/json) and stringifies the object.

app.get('/text' (req, res)=>{
    res.send("hello world"); // Plain text
});

app.get('/json' (req, res)=>{
    res.json({"message": "hello world"}); // JSON response
});


📌 3. HTTP Methods: GET vs POST vs PUT vs DELETE
**GET**: Used to retrieve data from the server. It is a safe method.
**POST**: Used to send data to the server to create a new resource.
**PUT**: Used to update an existing resource on the server.
**DELETE**: Used to delete a resource from the server.

app.get('/users' (req,res()=>{
    res.json([{id: 1, name:'Alice'}]);
}));

app.post('/users' (req,res()=>{
    res.json({message: 'User created'});
}));

app.put('/users/:id' (req,res()=>{
    res.json({message: `User ${req.params.id} updated`});
}));

app.delete('/users/:id' (req,res()=>{
    res.json({message: `User ${req.params.id} updated`});
}));