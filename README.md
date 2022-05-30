# Deploy-Your-Json-Server to Heroku or any free hosting sites
Here you can see how to deploy you mock-server(db.json) file to heroku.

### You can clone this repo and change your db.json data with your data and start deploying or

## Create Your Own Fake Server.

1. Create a folder and name it any name or fake_server.
2. Create a file and make the entry point server.js
3. Open the folder in editor and open terminal and let's Start
4. ```npm init``` 
5. ```npm i json-server```
6. Add a ```start``` script in ```package.json```
7. Your ```package.json``` should look like this or you can paste this code in your ```package.json```
```json
{
  "name": "fake-server",
  "version": "1.0.0",
  "description": "fake server with fake database",
  "main": "server.js",
  "scripts": { // <=== 
    "start": "node server.js" // <===
  },
  "author": "Akshay Kumar",
  "license": "ISC",
  "dependencies": {
    "json-server": "^0.16.3" 
  }
}
```
8. create ```.gitignore``` file and add ```node_modules``` ```.gitignore```
9. Open ```server.js``` file and paste the following code
```js
const jsonServer = require('json-server');
const server = jsonServer.create();
const router = jsonServer.router('db.json'); // file name of your database
const middlewares = jsonServer.defaults();
const port = process.env.PORT || 4000; // You can change the port

server.use(middlewares);
server.use(router);

server.listen(port);
```
10. Create ***db.json*** file
Fill in any data you like, or use [Mockaroo](https://www.mockaroo.com/?target=_blank) which is a great and easy way to generate dummy data.
```json
{
  "users": [
    {
      "id": 1,
      "first_name": "Justina",
      "last_name": "Ginglell",
      "email": "jginglell0@networkadvertising.org",
      "gender": "Female"
    },
    {
      "id": 2,
      "first_name": "Marion",
      "last_name": "Jenman",
      "email": "mjenman1@surveymonkey.com",
      "gender": "Male"
    },
    {
      "id": 3,
      "first_name": "Alfy",
      "last_name": "Begin",
      "email": "abegin2@list-manage.com",
      "gender": "Female"
    },
    {
      "id": 4,
      "first_name": "Karney",
      "last_name": "Zanussii",
      "email": "kzanussii3@hao123.com",
      "gender": "Male"
    },
    {
      "id": 5,
      "first_name": "Reid",
      "last_name": "Schapero",
      "email": "rschapero4@timesonline.co.uk",
      "gender": "Male"
    },
    {
      "id": 6,
      "first_name": "Dorine",
      "last_name": "Braybrookes",
      "email": "dbraybrookes5@gov.uk",
      "gender": "Female"
    },
    {
      "id": 7,
      "first_name": "Sarena",
      "last_name": "Frape",
      "email": "sfrape6@alexa.com",
      "gender": "Female"
    },
    {
      "id": 8,
      "first_name": "Malva",
      "last_name": "Pierse",
      "email": "mpierse7@usda.gov",
      "gender": "Female"
    },
    {
      "id": 9,
      "first_name": "Rania",
      "last_name": "Dablin",
      "email": "rdablin8@state.gov",
      "gender": "Female"
    },
    {
      "id": 10,
      "first_name": "Ingrim",
      "last_name": "Offen",
      "email": "ioffen9@slideshare.net",
      "gender": "Male"
    }
  ]
}
```

## Deploy to **Heroku**

<img align="right" width="100px" height="auto" src="https://cdn.worldvectorlogo.com/logos/heroku.svg" alt="Heroku">

Heroku is a free hosting service for hosting small projects. Easy setup and deploy from the command line via _git_.

###### Pros

* Easy setup
* Free

###### Cons

* App has to sleep a couple of hours every day.
* "Powers down" after 30 mins of inactivity. Starts back up when you visit the site but it takes a few extra seconds. Can maybe be solved with [**Kaffeine**](http://kaffeine.herokuapp.com/)

---

### Install Heroku

1 . [Create your database](#create-your-database)

2 . Create an account on <br/>[https://heroku.com](https://heroku.com)

3 . Install the Heroku CLI on your computer: <br/>[https://devcenter.heroku.com/articles/heroku-cli](https://devcenter.heroku.com/articles/heroku-cli)

4 . Connect the Heroku CLI to your account by writing the following command in your terminal and follow the instructions on the command line:
```bash
heroku login
```

5 . Then create a remote heroku project, kinda like creating a git repository on GitHub. This will create a project on Heroku with a random name. If you want to name your app you have to supply your own name like `heroku create project-name`:
```bash
heroku create my-cool-project
```

6 . Push your app to __Heroku__ (you will see a wall of code)
```bash
git push heroku master
```

7 . Visit your newly create app by opening it via heroku:
```bash
heroku open
```

8 . For debugging if something went wrong:
```bash
heroku logs --tail
```

---

#### How it works

Heroku will look for a startup-script, this is by default `npm start` so make sure you have that in your `package.json` (assuming your script is called `server.js`):
```json
 "scripts": {
    "start" : "node server.js"
 }
```

You also have to make changes to the port, you can't hardcode a dev-port. But you can reference herokus port. So the code will have the following:
```js
const port = process.env.PORT || 4000;
```


