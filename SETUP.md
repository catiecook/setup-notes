##NODE + EXPRESS SET UP
`npm init -y` - init the npm and set all values to yes

`express --hbs --git` - add hbs and .gitignore with defaults

`npm install`

`npm i [other modules you want] -S`

##KNEX
`npm install knex pg -S`

`knex init`

`creatdb [database name]`- create database

`psql [dbname] -f sql/seed.sql` - seed the databse with the seen file

`mkdir database`

`touch database/knex.js`

`seed:make [name]` - create seed directory and file with the name specified

`migrate:make [name]` - make a migration file, name should be specific

`migrate:latest` - migrate the data into a table

_add migrations as I need to add more data_

`migrate:rollback` - sequentially rolls back migrations and deletes changes.

_if columns or data needs to be edited, not just added, rollbacks have to happen_

##MOCHA
_after express, hbs, git are added_

`mkdir test` - make directory for the tests

`cd test`

`touch canary-spec.js` - generic spec test file name

`npm i --save-dev chai` - bring in chai to test for truthiness of mocha tests

`--save-dev` tells it to save into development part of package.json because this is used specifically in development, and not needed for deployment

*in the canary-spec.js files*

```javascript
const chai = require('chai');
const should = chai.should();
```
*to test with mocha*
`cd` into main directory
`mocha` - will run all available tests

##MOCHA and API TESTS
`npm i supertest -S-dev` - install module that allows for API tests

`touch api-test.js` - name doesn't really matter

*inside the file testing api, include app.js:*

```javascript
const app = require('../app.js');
```
##HEROKU
`npm i dotenv -S` - install .env file
*in app.js include the following:*
```javascript
require('dotenv').config();

const express = require('express')
const port = process.env.PORT;
let app = express();

app.get('/', function(req, res){
     res.json({message: 'I am working'});
});

console.log(process.env);

app.listen(3000, () =>{
     console.log("listening on port", port);
});
```

*in .env file:*
```javascript
PORT=8743 //random 4 digits over 3000
```

*in package.json:*
```javascript
"scripts": {
     "test": "echo \"Error: no test specified\" && exit 1",
     "start": "node app.js"
 },
//make sure the “start” is added
```

`heroku create`

`git init`

`git remote add origin`

`git add`

`git commit -m "dafadsa"`

`git push origin master`

`git push heroku master`


*Debugging*

`heroku log` - logs all the problems
