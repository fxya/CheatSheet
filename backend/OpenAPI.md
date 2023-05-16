# Swagger/OpenAPI cheat sheet

```yaml
# Swagger/OpenAPI Cheat Sheet

# OpenAPI Version
openapi: 3.0.0

# Information about the API
info:
  title: Sample API
  version: 1.0.0
  description: This is a sample API.

# API base path
servers:
  - url: https://api.example.com/v1

# Define components
components:
  schemas:
    User:
      type: object
      properties:
        id:
          type: integer
        name:
          type: string
      required:
        - id
        - name

# Define paths and operations
paths:
  /users:
    get:
      summary: Get all users
      responses:
        '200':
          description: OK
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/User'

    post:
      summary: Create a new user
      requestBody:
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/User'
        required: true
      responses:
        '201':
          description: Created

  /users/{userId}:
    get:
      summary: Get a user by ID
      parameters:
        - in: path
          name: userId
          schema:
            type: integer
          required: true
      responses:
        '200':
          description: OK
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/User'

    put:
      summary: Update a user by ID
      parameters:
        - in: path
          name: userId
          schema:
            type: integer
          required: true
      requestBody:
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/User'
        required: true
      responses:
        '200':
          description: OK

    delete:
      summary: Delete a user by ID
      parameters:
        - in: path
          name: userId
          schema:
            type: integer
          required: true
      responses:
        '204':
          description: No Content
```


