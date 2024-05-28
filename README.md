# ironhack-lab-8
Repositorio de Laboratorio 8 de Bootcamp IronHack

# Lab Overview and Setup

## Introduction to the Scenario

Participants are tasked with designing an API for an e-commerce system. The system’s requirements include managing user accounts, processing orders, and handling customer interactions efficiently.

## Tools and Resources

Participants will use SwaggerHub, an integrated API design and documentation platform, to create their API specifications. They will be provided with access to SwaggerHub and any necessary guides on its usage.

# API Design Session

## Endpoint Design

Participants will define RESTful API endpoints for user management, order processing, and customer service interactions.

## Resource Modeling

Define the data structures and resource models required to support the API functionality, such as user profiles, order details, and customer tickets.

## Documentation

Document each API endpoint, specifying required parameters, possible responses, and error codes to ensure clarity and completeness. Emphasis will be placed on adherence to best practices in API documentation to enhance ease of use and maintainability.

---

### Swagger API Specification

```yaml
openapi: 3.0.1
info:
  title: E-commerce API
  description: API for managing user accounts, processing orders, and handling customer interactions in an e-commerce system.
  version: 1.0.0
servers:
  - url: http://api.yourdomain.com/v1
paths:
  /users:
    get:
      summary: Get a list users
      responses:
        '200':
          description: list users
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/User'
        '500':
          description: Server error
    post:
      summary: Create a new user
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/NewUser'
      responses:
        '201':
          description: User created successfully
        '400':
          description: Invalid input
  /users/{userId}:
    get:
      summary: Get user details
      parameters:
        - name: userId
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: User details
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/User'
        '404':
          description: User not found
    put:
      summary: Update user details
      parameters:
        - name: userId
          in: path
          required: true
          schema:
            type: string
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/UpdateUser'
      responses:
        '200':
          description: User updated successfully
        '400':
          description: Invalid input
        '404':
          description: User not found
  /orders:
    get:
      summary: Get list orders
      responses:
        '200':
          description: list orders
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Order'
        '500':
          description: Server error
    post:
      summary: Create a new order
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/NewOrder'
      responses:
        '201':
          description: Order created successfully
        '400':
          description: Invalid input
  /orders/{orderId}:
    get:
      summary: Get order details
      parameters:
        - name: orderId
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Order details
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Order'
        '404':
          description: Order not found
    put:
      summary: Update order details
      parameters:
        - name: orderId
          in: path
          required: true
          schema:
            type: string
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/UpdateOrder'
      responses:
        '200':
          description: Order updated successfully
        '400':
          description: Invalid input
        '404':
          description: Order not found
  /tickets:
    get:
      summary: Get list customer service tickets
      responses:
        '200':
          description: list ickets
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Ticket'
        '500':
          description: Server error
    post:
      summary: Create a new customer service ticket
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/NewTicket'
      responses:
        '201':
          description: Ticket created successfully
        '400':
          description: Invalid input
  /tickets/{ticketId}:
    get:
      summary: Get ticket details
      parameters:
        - name: ticketId
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Ticket details
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Ticket'
        '404':
          description: Ticket not found
    put:
      summary: Update ticket details
      parameters:
        - name: ticketId
          in: path
          required: true
          schema:
            type: string
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/UpdateTicket'
      responses:
        '200':
          description: Ticket updated successfully
        '400':
          description: Invalid input
        '404':
          description: Ticket not found
components:
  schemas:
    User:
      type: object
      properties:
        id:
          type: string
        name:
          type: string
        email:
          type: string
    NewUser:
      type: object
      properties:
        name:
          type: string
        email:
          type: string
        password:
          type: string
    UpdateUser:
      type: object
      properties:
        name:
          type: string
        email:
          type: string
    Order:
      type: object
      properties:
        id:
          type: string
        userId:
          type: string
        items:
          type: array
          items:
            type: string
        total:
          type: number
    NewOrder:
      type: object
      properties:
        userId:
          type: string
        items:
          type: array
          items:
            type: string
    UpdateOrder:
      type: object
      properties:
        items:
          type: array
          items:
            type: string
        total:
          type: number
    Ticket:
      type: object
      properties:
        id:
          type: string
        userId:
          type: string
        issue:
          type: string
        status:
          type: string
    NewTicket:
      type: object
      properties:
        userId:
          type: string
        issue:
          type: string
    UpdateTicket:
      type: object
      properties:
        issue:
          type: string
        status:
          type: string
```

## Reflection Report

### Desafíos

Durante el diseño de la API, se tomaron en cuenta varios factores, incluyendo la necesidad de asegurar que los endpoints fueran claros y eficientes, la definición de modelos de recursos detallados para manejar diferentes aspectos del sistema y la documentación de cada endpoint para asegurar su usabilidad y mantenibilidad.

### Aplicación de Principios API First

Se aplican principios de API First para asegurar que la API sea robusta y alineada con las necesidades del negocio.

### Mejoras Futuras

Este ejercicio se trata de aplicar y practicar la importancia de una planificación y documentación.
