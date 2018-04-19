# Gambit Configuration Server

Use this server to configure all of your favorite Gambit microservices.

## Setting up Gambit Configuration Server

Right now Gambit Configuration Server has a `manifest.yml` that it uses to
upload to Pivotal Cloud Foundry. Someday we're going to adjust this to deploy
via Docker Swarm Mode.

## Using Your Gambit Configuration Server

The following set up assumes that you are building your new microservice for
the Revature Gambit ecosystem using Spring Boot. Certainly, if you are
determined to write your microservice in COBOL, no one's going to stop you
from using our config server except for yourself.

In order to use the Gambit Configuration Server your microservice is going to
need a bootstrap.yml or bootstrap.properties file. In that file you need to
define the following attributes:

* Application name
* The location of the configuration server

Make sure to either add the Spring Cloud Starter Config dependency in your
pom.xml or to select Config Client under the Cloud Config heading as you create
your Spring project.

As always, make sure you create your spring boot applications as .jar projects.

In order to easily refresh your microservice when you update its configuration
via Git, set the

```Java
management.endpoints.web.exposure.include=*
```

property and use the

```Java
@RefreshScope
```

annotation above your Application class.

## TODO

1. Adjust Git repository endpoint in application.yml to private repo that our
other microservices can find
2. Convert from .properties to .yml maybe
