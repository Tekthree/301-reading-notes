
### 301 Reading Notes

## Class -05


# Heroku

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

