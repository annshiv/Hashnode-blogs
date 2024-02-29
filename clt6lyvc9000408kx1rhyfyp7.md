---
title: "Building a Simple Form with Express.js"
datePublished: Thu Feb 29 2024 02:30:29 GMT+0000 (Coordinated Universal Time)
cuid: clt6lyvc9000408kx1rhyfyp7
slug: building-a-simple-form-with-expressjs
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/tYvZUVEve6s/upload/11be6b8306bc0fa4eb97dae3a591f19e.jpeg
tags: express, developer, frontend-development

---

Express.js is a popular Node.js framework used for building web applications and APIs. Our form will allow users to input their first name and submit it to the server.

### Setting Up the Project

Let's start by creating a new directory for our project and initializing a new Node.js project. Open your terminal and run the following commands:

```bash
mkdir express-form-example
cd express-form-example
npm init -y
```

Next, install Express.js and EJS (Embedded JavaScript) as dependencies:

```bash
npm install express ejs
```

### Creating the Server

First, let's set up our Express server in server.js:

```javascript
// server.js
const express = require("express");
const app = express();

// Middleware and configuration
app.use(express.static("public"));
app.use(express.urlencoded({ extended: true }));
app.use(express.json());
app.set("view engine", "ejs");

// Define routes
const userRouter = require("./routes/users");
app.use("/users", userRouter);

// Start the server
app.listen(3000, () => {
  console.log("Server is running on port 3000");
});
```

### Setting Up the User Routes

Now, let's define the user routes in routes/users.js:

```javascript
// routes/users.js
const express = require("express");
const router = express.Router();

// Middleware function for logging
function logger(req, res, next) {
  console.log(req.originalUrl);
  next();
}

// Dummy data for users
const users = [{ name: "Kyle" }, { name: "Sally" }];

// Route to render the user creation form
router.get("/new", (req, res) => {
  res.render("users/new");
});

// Route to handle form submission
router.post("/", (req, res) => {
  const isValid = false;
  if (isValid) {
    // Logic for valid submission (not implemented)
    res.redirect(`/users/${users.length - 1}`);
  } else {
    // Logic for invalid submission
    console.log("Error");
    res.render("users/new", { firstName: req.body.firstName });
  }
});

// Route parameters for user ID
router
  .route("/:id")
  .get((req, res) => {
    console.log(req.user);
    res.send(`Get User With ID ${req.params.id}`);
  })
  .put((req, res) => {
    res.send(`Update User With ID ${req.params.id}`);
  })
  .delete((req, res) => {
    res.send(`Delete User With ID ${req.params.id}`);
  });

// Middleware function to handle user ID parameter
router.param("id", (req, res, next, id) => {
  req.user = users[id];
  next();
});

// Apply logger middleware to all routes
router.use(logger);

module.exports = router;
```

### Creating the User Interface

In the views/users/new.ejs file, let's create a form for user input:

```xml
<!-- views/users/new.ejs -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>User Form</title>
</head>
<body>
  <form action="/users" method="POST">
    <label>First Name
      <input type="text" name="firstName" />
    </label>
    <button type="submit">Submit</button>
  </form>
</body>
</html>
```

We can expand upon this example by adding validation, storing user data, or integrating additional features. Express.js provides a powerful and flexible framework for building web applications and APIs, making it an excellent choice for a wide range of projects.

Special thanks to the "Web Dev Simplified" YouTube channel for their insightful tutorials.

If you'd like to dive deeper into the code or contribute to its improvement, you can find the complete code repository on GitHub at [annshiv/expressJs](https://github.com/annshiv/expressJs).