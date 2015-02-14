## Netflix OSS on Heroku Demo: Eureka Server

This project demonstrates the use of Netflix OSS with Spring Cloud on Heroku. It defines a Eureka server
that can be used for service discovery. Once this project is up and running, you can connect the 
[Eureka client demo](https://github.com/kissaten/heroku-eureka-client-demo) to it.

## Quickstart

[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

Once it's deployed, Eureka will prompt you for credentials. The defaults are `user` and `password`.

## Production Deployment

First, [create a Heroku account](http://dashboard.heroku.com)
and then [download and install the Heroku toolbelt](http://toolbelt.heroku.com).

Now clone this project and move into it's root directory.

```
$ git clone git@github.com:kissaten/heroku-eureka-server-demo.git
$ cd heroku-eureka-demo/
```

Then create a Heroku application by running this command:

````sh-session
$ heroku create
Creating fast-beach-5250... done, stack is cedar-14
https://fast-beach-5250.herokuapp.com/ | https://git.heroku.com/fast-beach-5250.git
Git remote heroku added
```

Now create a configuration variable to set the default user's
password. Run this command, but substitute a unique password for `<PASSWORD>`:

```
$ heroku config:set EUREKA_USER_PASSWORD=<PASSWORD>
```

You're ready to deploy. There are two methods you can choose from: Git deployment and
Maven deployment. The former compiles the application remotely, while the latter
uses locally compiled artifacts and pushes them to Heroku.

### Deploying with Git

With you're application prepared (as describe above), simply run this command to
deploy via Git:

```sh-session
$ git push heroku master
```

Your code will be pushed to the remote Git repository, and the Maven process
will execute on the Heroku servers.

### Deploying with Maven

With you're application prepared, simply run this command to
deploy (but replace `<appname>`  with the name of the Heroku application you created):

```sh-session
$ mvn -Dheroku.appName=<appname> heroku:deploy
...
[INFO] ---> Packaging application...
[INFO]      - app: <appname>
[INFO]      - including: ./target/eureka-server-demo-0.0.1-SNAPSHOT.jar
[INFO]      - installing: OpenJDK 1.8
[INFO] ---> Creating slug...
[INFO]      - file: ./target/heroku/slug.tgz
[INFO]      - size: 79MB
[INFO] ---> Uploading slug...
[INFO]      - stack: cedar-14
[INFO]      - process types: [web]
[INFO] ---> Releasing...
[INFO]      - version: 4
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 01:29 min
[INFO] Finished at: 2015-02-14T11:38:11-06:00
[INFO] Final Memory: 27M/579M
[INFO] ------------------------------------------------------------------------
```

## Viewing Your Application

When your chosen deployment method is finished, run this command to view
your application:

```
$ heroku open
```

The browser will prompt you for credentials. Enter "user" for the username,
and the unique password you set as a configuration variable.

## Further Reading

+  [Spring Cloud Netflix documentation](http://projects.spring.io/spring-cloud/spring-cloud.html#_spring_cloud_netflix)
+  [Netflix Eureka](https://github.com/netflix/eureka)
