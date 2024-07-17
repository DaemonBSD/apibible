# REST

REST (Representational State Transfer) is the foundation of countless web applications, known for its simplicity and stateless nature.

## Key Features

- **Simplicity**: Uses standard HTTP methods (GET, POST, PUT, DELETE).
- **Stateless**: Each client request contains all the information needed.
- **Scalability**: Easily scalable due to its simple architecture.

## Example Usage

A common example of using REST is in APIs that provide user data.

### Setting Up a REST API

1. **REST Server**: Create a server to provide data.

```javascript
const express = require('express');
const app = express();
app.use(express.json());

let users = [
  { id: 1, name: 'John Doe', email: 'john.doe@example.com' },
  { id: 2, name: 'Jane Doe', email: 'jane.doe@example.com' },
];

// Get all users
app.get('/users', (req, res) => {
  res.json(users);
});

// Get a user by ID
app.get('/users/:id', (req, res) => {
  const user = users.find((u) => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found.');
  res.json(user);
});

// Create a new user
app.post('/users', (req, res) => {
  const user = {
    id: users.length + 1,
    name: req.body.name,
    email: req.body.email,
  };
  users.push(user);
  res.status(201).json(user);
});

// Update an existing user
app.put('/users/:id', (req, res) => {
  const user = users.find((u) => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found.');
  user.name = req.body.name;
  user.email = req.body.email;
  res.json(user);
});

// Delete a user
app.delete('/users/:id', (req, res) => {
  const user = users.find((u) => u.id === parseInt(req.params.id));
  if (!user) return res.status(404).send('User not found.');
  const index = users.indexOf(user);
  users.splice(index, 1);
  res.json(user);
});

app.listen(3000, () =>
  console.log('REST server running at http://localhost:3000')
);
```

# Applicability and Use Cases

## Applicability

REST is ideal for applications that need a simple and straightforward interface to interact with web-based resources.

## Use Cases

1. **Web Applications**:

   - Provides a clear interface for CRUD (Create, Read, Update, Delete) operations on web resources.

2. **Backend Services**:

   - Exposes backend data and functionalities for consumption by frontends or other services.

3. **Mobile Applications**:

   - Provides a simple and efficient API for communication between the mobile app and the server.

# Testing REST

To test REST APIs, you can use tools like Postman or CURL.

## Using CURL

1. **Get all users**:

```bash
curl -X GET http://localhost:3000/users
```

2. **Get a user by ID**:

```bash
curl -X GET http://localhost:3000/users/1
```

3. **Create a new user**:

```bash
curl -X POST http://localhost:3000/users -H "Content-Type: application/json" -d '{"name": "Alice", "email": "alice@example.com"}'
```

4. **Update an existing user**:

```bash
curl -X PUT http://localhost:3000/users/1 -H "Content-Type: application/json" -d '{"name": "John Smith", "email": "john.smith@example.com"}'
```

5. **Delete a user**:

```bash
curl -X DELETE http://localhost:3000/users/1
```

# Additional Resources

[Official REST Documentation](https://restfulapi.net/)

## Credits

Created by [Carlos Costa](https://www.linkedin.com/in/carlos-costa-0b548675/).

#

[Back to Home](README.en.md)
