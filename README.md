# 🎬 Vidly

A RESTful video rental service API built with **Node.js**, **Express**, and **MongoDB**. Vidly lets you manage genres, movies, customers, and rentals, with JWT-based authentication and role-based authorization.

##  Features

- **Genres** — create, list, update, and delete movie genres
- **Movies** — manage a catalog of movies, each linked to a genre, with stock and daily rental rate
- **Customers** — manage customer records, including gold-membership status
- **Rentals** — rent movies out to customers and track active rentals
- **Returns** — process movie returns and automatically calculate rental fees
- **Auth** — user registration and login secured with JWT and hashed passwords (bcrypt)
- **Validation** — request payloads validated with Joi
- **Logging** — request and error logging via Morgan and Winston (with MongoDB transport)
- **Security** — HTTP headers hardened with Helmet

##  Tech Stack

| Layer          | Technology                          |
| -------------- | ------------------------------------ |
| Runtime        | Node.js                              |
| Framework      | Express                              |
| Database       | MongoDB with Mongoose                |
| Auth           | jsonwebtoken, bcrypt                 |
| Validation     | Joi, joi-objectid                    |
| Logging        | Winston, winston-mongodb, Morgan     |
| Security       | Helmet                               |
| Dev tooling    | Nodemon                              |

##  Project Structure

```
Vidly/
├── bin/            # App entry / server startup script
├── config/         # Environment configuration
├── middleware/      # Express middleware (auth, error handling, validation, etc.)
├── models/         # Mongoose schemas and models
├── public/          # Static assets (stylesheets)
├── routes/         # Express route handlers (API endpoints)
├── startup/        # App bootstrap logic (db, logging, routes, config, etc.)
├── views/          # View templates
└── app.js          # Application entry point
```

##  Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v14+ recommended)
- [MongoDB](https://www.mongodb.com/) running locally or a connection URI to a hosted instance

### Installation

1. Clone the repository

   ```bash
   git clone https://github.com/majeedahmed9379/Vidly.git
   cd Vidly
   ```

2. Install dependencies

   ```bash
   npm install
   ```

3. Configure environment variables

   Vidly uses [`config`](https://www.npmjs.com/package/config) for configuration and requires a JWT private key at minimum:

   ```bash
   export vidly_jwtPrivateKey=your_jwt_secret_key
   ```

   On Windows (cmd):

   ```cmd
   set vidly_jwtPrivateKey=your_jwt_secret_key
   ```

   Adjust database connection settings and other environment-specific values in the `config/` folder as needed.

4. Start MongoDB

   Make sure a MongoDB instance is running and accessible at the connection string configured in `config/`.

5. Run the app

   ```bash
   npx nodemon app.js
   ```

   The API will be available at `http://localhost:3000` (or the configured port).

## 📡 API Endpoints

| Method | Endpoint             | Description                          |
| ------ | --------------------- | ------------------------------------- |
| GET    | `/api/genres`         | List all genres                       |
| POST   | `/api/genres`         | Create a new genre                    |
| PUT    | `/api/genres/:id`     | Update a genre                        |
| DELETE | `/api/genres/:id`     | Delete a genre                        |
| GET    | `/api/movies`         | List all movies                       |
| POST   | `/api/movies`         | Add a new movie                       |
| PUT    | `/api/movies/:id`     | Update a movie                        |
| DELETE | `/api/movies/:id`     | Delete a movie                        |
| GET    | `/api/customers`      | List all customers                    |
| POST   | `/api/customers`      | Add a new customer                    |
| PUT    | `/api/customers/:id`  | Update a customer                     |
| DELETE | `/api/customers/:id`  | Delete a customer                     |
| GET    | `/api/rentals`        | List all rentals                      |
| POST   | `/api/rentals`        | Create a new rental                   |
| POST   | `/api/returns`        | Process a movie return                |
| POST   | `/api/users`          | Register a new user                   |
| POST   | `/api/auth`           | Log in and receive a JWT              |

> Most write operations (POST/PUT/DELETE) require a valid JWT in the `x-auth-token` header.

## 🧪 Testing

```bash
npm test
```



## 🙋 About

This project was built as a hands-on exercise in structuring a production-style Node.js/Express REST API with authentication, validation, logging, and MongoDB integration.
