---
sidebar_label: 'Create a Node.JS backend'
sidebar_position: 2
---

# Create a Node.JS backend app

## A. Preparation
We will create a backend app using Node.js to communicate with Vidus for user registration, authorization, and token retrieval.

1. Create an index.js file and install the required dependencies: In this sample we use Express.js as a Node.js web application framework to build our backend app and BodyParser and Cors midleware packages for parse incoming request bodies and handle cross-origin resource sharing.

```bash
touch index.js
npm i express body-parser cors
```
2. Install the Vidus Node.js package.
```bash
npm i vidus-node
```

## B. Create the App
In index.js, import the necessary packages.
```js title="Test title for code?"
const express = require('express');
const cors = require('cors');
const bodyParser = require('body-parser');
const getToken = require('vidus-node');
```
Initialize the Express app and configure middleware:
```js
const app = express();

app.use(cors());
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));
```
Create a root endpoint to test the application:
```js
app.all('/', (req, res) => {
  res.status(200).send({ status: 'ok' });
});
```

Add an endpoint to register a user and retrieve a token from Vidus by use Vidus node package. In this point we use trial project app_id and app_secret when we got in last step [Create a Vidus account](./step1_create_vidus_account).

You can add your own authentication logic *(e.g., database checks)*, before the getToken call, thats up to you.
Also we pass username by request 

```js
app.post('/getToken', function (req, res) {
  const { username } = req.body;
  const vidus = {
    app_id: 'app_id',
    app_secret: 'app_secret'
  }


  if (!username) {
    return res.status(403).send({
      message: 'Username cannot be empty and must be in email format.'
    });
  }
  // Your authentication logic

  getToken(vidus.app_id, vidus.app_secret, username)
    .then(response => {
      res.status(200).send(response);
    })
    .catch(error => {
      res.status(error.status || 403).send({
        message: error.message || error
      });
    });
});
```

Start the server on port 3000:

```js
app.listen(3000, () => {
  console.log('Vidus NodeJS app listening on port 3000');
});
```

## C. Run the Backend App

Start the backend server:
```bash
node .
```

The backend app is now running and listening for requests on port 3000.

We can check by enter [http://localhost:3000](http://localhost:3000/) url in browser and get status: OK message and retrive the user token from Vidus by [http://localhost:3000/getToken](http://localhost:3000/getToken). url
