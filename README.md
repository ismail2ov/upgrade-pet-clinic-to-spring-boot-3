# Upgrade Pet Clinic Sample Application to Spring Boot 3

This repository is for the workshop on upgrading a Spring Boot 2 sample application to Spring Boot 3.

The initial code is based on a version of the classic reference application - [Spring PetClinic Sample Application](https://github.com/spring-projects/spring-petclinic)


## Building a Container

There is no `Dockerfile` in this project. You can build a container image (if you have a docker daemon) using the Spring Boot build plugin:

```
./mvnw spring-boot:build-image
```


## Database configuration

In its default configuration, Petclinic uses an in-memory database (H2) which
gets populated at startup with data. The h2 console is automatically exposed at `http://localhost:8080/h2-console`
and it is possible to inspect the content of the database using the `jdbc:h2:mem:testdb` url.

A similar setup is provided for MySQL and PostgreSQL in case a persistent database configuration is needed. Note that whenever the database type is changed, the app needs to be run with a different profile: `spring.profiles.active=mysql` for MySQL or `spring.profiles.active=postgres` for PostgreSQL.

You could start MySQL or PostgreSQL locally with whatever installer works for your OS, or with docker:

```
docker run -e MYSQL_USER=petclinic -e MYSQL_PASSWORD=petclinic -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=petclinic -p 3306:3306 mysql:5.7.8
```

or

```
docker run -e POSTGRES_USER=petclinic -e POSTGRES_PASSWORD=petclinic -e POSTGRES_DB=petclinic -p 5432:5432 postgres:14.1
```


# License

The Spring PetClinic sample application is released under version 2.0 of the [Apache License](https://www.apache.org/licenses/LICENSE-2.0).
