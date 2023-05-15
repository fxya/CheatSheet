# Essential Web Programming Principles

### HTTP Status Codes
- HTTP status codes provide information about the status of a web request and response. They are standardized codes that help in understanding the outcome of the request.

| Status Code | Description                                  | Example Usage                                     |
| ----------- | -------------------------------------------- | ------------------------------------------------- |
| 200         | OK - The request was successful               | `res.status(200).send('Success');`                |
| 201         | Created - The request resulted in a new resource being created | `res.status(201).json(newResource);`     |
| 400         | Bad Request - The request was invalid         | `res.status(400).send('Invalid request');`         |
| 404         | Not Found - The requested resource was not found | `res.status(404).send('Resource not found');` |
| 500         | Internal Server Error - An unexpected error occurred on the server | `res.status(500).send('Server error');` |

### RESTful APIs
- REST (Representational State Transfer) is an architectural style for building web services. It emphasizes stateless, client-server communication and resource-based URLs.

```javascript
// Example RESTful API endpoints
// GET /users - Get a list of users
// POST /users - Create a new user
// GET /users/:id - Get a specific user
// PUT /users/:id - Update a specific user
// DELETE /users/:id - Delete a specific user
```

### Input Validation
- Validating user input is crucial for security and data integrity. It helps prevent malicious input and ensures that the data meets the required criteria.

```javascript
// Example input validation using regular expressions
const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
if (!emailRegex.test(email)) {
  return res.status(400).send('Invalid email');
}
```

### Error Handling
- Proper error handling is essential to provide meaningful error messages and handle exceptions gracefully.

```javascript
// Example error handling in Express.js
app.get('/users/:id', (req, res) => {
  const userId = req.params.id;
  try {
    const user = getUserById(userId);
    res.json(user);
  } catch (error) {
    console.error('Error retrieving user:', error);
    res.status(500).send('Server error');
  }
});
```

### Security Best Practices
- Web applications should adhere to security best practices to protect user data, prevent unauthorized access, and defend against common vulnerabilities.

```javascript
// Example password hashing using bcrypt
const bcrypt = require('bcrypt');
const saltRounds = 10;

bcrypt.hash(password, saltRounds, (err, hash) => {
  if (err) {
    return res.status(500).send('Server error');
  }
  // Store the hashed password
});
```

### Authentication and Authorization
- Authentication is the process of verifying the identity of a user, while authorization is the process of verifying that the user has access to the requested resource.

```javascript
// Example authentication using Passport.js
const passport = require('passport');
const LocalStrategy = require('passport-local').Strategy;
```
