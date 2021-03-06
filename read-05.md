
### 301 Reading Notes

## Class -05


# Heroku

- how to deploy an app, change its configuration, view logs, scale, and attach add-ons

- install heroku

```

$ sudo snap install heroku --classic

$ heroku login

```

- clone your git repository to your local folder.

```
$ git clone https://github.com/heroku/node-js-getting-started.git
$ cd node-js-getting-started

```

- deploy the app to Heroku

```
$ heroku create
```

- now deploy code

```
$ git push heroku main

```

- ensure the application is running

```
$ heroku ps:scale web=1
```

- open desployed server

```
$ heroku open
```

- In order to scale you have to upgrade to a pro account. By default, your app is deployed on a free dyno. Free dynos will sleep after a half hour of inactivity (if they don’t receive any traffic). This causes a delay of a few seconds for the first request upon waking. Subsequent requests will perform normally. Free dynos also consume from a monthly, account-level quota of free dyno hours - as long as the quota is not exhausted, all free apps can continue to run.

To avoid dyno sleeping, you can upgrade to a hobby or professional dyno type as described in the Dyno Types article. For example, if you migrate your app to a professional dyno, you can easily scale it by running a command telling Heroku to execute a specific number of dynos, each running your web process type.

- to install dependencies Run this command in your local directory to install the dependencies, preparing your system for running the app locally:

```
$ npm install
```

- you can now run your app locally with this command, then open browser and go to localhost:PORT

```
$heroku local web
```

# Push Local Changes

- how to push to heroku

```

$ git add .

$ git commit -m "add cool face api"

$ git push heroku main

$ heroku open cool

```

- Provisions and add-ons

- Add-ons are third-party cloud services that provide out-of-the-box additional services for your application, from persistence through logging to monitoring and more.

```
$ heroku addons:create papertrail
```

- to list addons

```
$ heroku addons
```

- Define config vars : Heroku lets you externalize configuration - storing data such as encryption keys or external resource addresses in config vars.

- In the index.js, Under the existing get() call, add another:

```
.get('/times', (req, res) => res.send(showTimes()))
```

- At the end of the file, add the following definition for the new function

```
showTimes = () => {
  let result = '';
  const times = process.env.TIMES || 5;
  for (i = 0; i < times; i++) {
    result += i + ' ';
  }
  return result;
}
```
- heroku local will automatically set up the environment based on the contents of the .env file in your local directory. In the top-level directory of your project, there is already a .env file that has the following contents:

```
TIMES=2
```

- If you run the app with heroku local, you’ll see two numbers will be generated every time.

To set the config var on Heroku, execute the following:

```
$ heroku config:set TIMES=2

$ heroku config
```

## Adding Postgres and other database

- The add-on marketplace has a large number of data stores, from Redis and MongoDB providers, to Postgres and MySQL.

- add the database

```
$ heroku addons:create heroku-postgresql:hobby-dev


$ heroku config
```

- to add postgress to your dependencies

```
$ npm install pg


 "dependencies": {
    "cool-ascii-faces": "^1.3.4",
    "ejs": "^2.5.6",
    "express": "^4.15.2",
    "pg": "^8.1.0"
  },

```


- Now edit your index.js file to use this module to connect to the database specified in your DATABASE_URL environment variable. Add this near the top

```
const { Pool } = require('pg');
const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  ssl: {
    rejectUnauthorized: false
  }
});
```

- Now add another route, /db, by adding the following just after the existing .get('/', ...)


```
.get('/db', async (req, res) => {
    try {
      const client = await pool.connect();
      const result = await client.query('SELECT * FROM test_table');
      const results = { 'results': (result) ? result.rows : null};
      res.render('pages/db', results );
      client.release();
    } catch (err) {
      console.error(err);
      res.send("Error " + err);
    }
  })
  
  ```
  
  - use the heroku pg:psql command to connect to the remote database, create a table and insert a row:
  
  ```
  $ heroku pg:psql
  ```
  

![https://howtonode.org/deploy-blog-to-heroku]
