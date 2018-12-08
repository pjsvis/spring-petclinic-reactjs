# React Frontend for Spring Boot PetClinic demo

[![Build Status](https://travis-ci.org/spring-petclinic/spring-petclinic-reactjs.svg?branch=master)](https://travis-ci.org/spring-petclinic/spring-petclinic-reactjs)

This project is a port of the [Spring (Boot) PetClinic demo](https://github.com/spring-projects/spring-petclinic) with a frontend built using [ReactJS](https://facebook.github.io/react/) and [TypeScript](https://www.typescriptlang.org/).

I have tried to make as few modifications to the backend code as necessary to the [spring-boot branch](https://github.com/spring-projects/spring-petclinic/tree/springboot) of the original sample project. Mainly I've added the new package `org.springframework.samples.petclinic.web.api` that contains the REST Api that is used by the React frontend. In this package most of the classes are taken from the [angularjs version](https://github.com/spring-projects/spring-petclinic/tree/angularjs) of the demo.

## Related projects

Note there is another Spring PetClinic example that uses React: [spring-petclinic-graphql](https://github.com/spring-petclinic/spring-petclinic-graphql). Beside React that example uses **GraphQL** for API queries instead of the REST API.

## Contribution

If you like to help and contribute (there's lot root for improvements! I've collected a list of ideas [here: TODO.md](TODO.md)) you're more than welcome! Please open an issue or contact me on [Twitter](https://twitter.com/nilshartmann) so we can discuss together!

## Install and run

Note: Spring Boot Server App must be running before starting the client!

To start the server, launch a Terminal and run from the project's root folder (`spring-petclinic`):

```
./mvnw spring-boot:run
```

When the server is running you can try to access the API for example to query all known pet types:

```
curl http://localhost:8080/api/pettypes
```

After starting the server you can install and run the client from the `client` folder:

1. `npm install` (installs the node modules and the TypeScript definition files)
2. `PORT=4444 npm start`
3. Open `http://localhost:4444`

(Why not use the same server for backend and frontend? Because Webpack does a great job for serving JavaScript-based SPAs and I think it's not too uncommon to run this kind of apps using two dedicated server, one for backend, one for frontend)

## Feedback

In case you have any comments, questions, bugs, enhancements feel free to open an issue in this repository. If you you want to follow me on twitter, my handle is [@nilshartmann](https://twitter.com/nilshartmann).

--------------------------------------------------------------------------------

# From the original sample README file:

## Understanding the Spring Petclinic application with a few diagrams

[See the presentation here](https://speakerdeck.com/michaelisvy/spring-petclinic-sample-application)

## Running petclinic locally

```
git clone https://github.com/spring-projects/spring-petclinic.git
    cd spring-petclinic
    git checkout springboot
    ./mvnw spring-boot:run
```

You can then access petclinic here: <http://localhost:8080/>

## In case you find a bug/suggested improvement for Spring Petclinic

Our issue tracker is available here: <https://github.com/spring-projects/spring-petclinic/issues>

## Database configuration

In its default configuration, Petclinic uses an in-memory database (HSQLDB) which gets populated at startup with data. A similar setup is provided for MySql in case a persistent database configuration is needed. Note that whenever the database type is changed, the data-access.properties file needs to be updated and the mysql-connector-java artifact from the pom.xml needs to be uncommented.

You may start a MySql database with docker:

```
docker run -e MYSQL_ROOT_PASSWORD=petclinic -e MYSQL_DATABASE=petclinic -p 3306:3306 mysql:5.7.8
```

## Working with Petclinic in Eclipse/STS

### prerequisites

The following items should be installed in your system:

- Maven 3 (<http://www.sonatype.com/books/mvnref-book/reference/installation.html>)
- git command line tool (<https://help.github.com/articles/set-up-git>)
- Eclipse with the m2e plugin (m2e is installed by default when using the STS (<http://www.springsource.org/sts>) distribution of Eclipse)

Note: when m2e is available, there is an m2 icon in Help -> About dialog. If m2e is not there, just follow the install process here: <http://eclipse.org/m2e/download/>

### Steps:

1) In the command line

```
git clone https://github.com/spring-projects/spring-petclinic.git
```

2) Inside Eclipse

```
File -> Import -> Maven -> Existing Maven project
```

## Looking for something in particular?

Spring Boot Configuration    |
---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
The Main Class               | [PetClinicApplication.java](/src/main/java/org/springframework/samples/petclinic/application/PetClinicApplication.java)
Properties Files             | [application.properties](/src/main/resources/application.properties)
Caching                      | Use of EhCache [CacheConfig.java](/src/main/java/org/springframework/samples/petclinic/config/CacheConfig.java) [ehcache.xml](/src/main/resources/ehcache.xml)
Dandelion                    | DatatablesFilter, DandelionFilter and DandelionServlet registration [DandelionConfig.java](/src/main/java/org/springframework/samples/petclinic/config/DandelionConfig.java)
Spring MVC - XML integration | [CustomViewsConfiguration.java](/src/main/java/org/springframework/samples/petclinic/config/CustomViewsConfiguration.java)

Others               | Files
-------------------- | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
JSP custom tags      | [WEB-INF/tags](/src/main/webapp/WEB-INF/tags) [createOrUpdateOwnerForm.jsp](/src/main/webapp/WEB-INF/jsp/owners/createOrUpdateOwnerForm.jsp)
Bower                | [bower-install maven profile declaration inside pom.xml](/pom.xml)<br>
[JavaScript libraries are defined by the manifest file bower.json](/bower.json)<br>
[Bower configuration using JSON](/.bowerrc)<br>
[Resource mapping in Spring configuration](/src/main/resources/spring/mvc-core-config.xml#L30)<br>
[sample usage in JSP](/src/main/webapp/WEB-INF/jsp/fragments/staticFiles.jsp#L12)
Dandelion-datatables | [ownersList.jsp](/src/main/webapp/WEB-INF/jsp/owners/ownersList.jsp) [vetList.jsp](/src/main/webapp/WEB-INF/jsp/vets/vetList.jsp) [web.xml](/src/main/webapp/WEB-INF/web.xml) [datatables.properties](/src/main/resources/dandelion/datatables/datatables.properties)

## Interaction with other open source projects

One of the best parts about working on the Spring Petclinic application is that we have the opportunity to work in direct contact with many Open Source projects. We found some bugs/suggested improvements on various topics such as Spring, Spring Data, Bean Validation and even Eclipse! In many cases, they've been fixed/implemented in just a few days. Here is a list of them:

<br>
<br>

Name                                                                                                                                                                                                   | Issue
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------
Spring JDBC: simplify usage of NamedParameterJdbcTemplate                                                                                                                                              | [SPR-10256](https://jira.springsource.org/browse/SPR-10256) and [SPR-10257](https://jira.springsource.org/browse/SPR-10257)
Bean Validation / Hibernate Validator: simplify Maven dependencies and backward compatibility                                                                                                          | [HV-790](https://hibernate.atlassian.net/browse/HV-790) and [HV-792](https://hibernate.atlassian.net/browse/HV-792)
Spring Data: provide more flexibility when working with JPQL queries                                                                                                                                   | [DATAJPA-292](https://jira.springsource.org/browse/DATAJPA-292)
Eclipse: validation bug when working with .tag/.tagx files (has only been fixed for Eclipse 4.3 (Kepler)). [See here for more details.](https://github.com/spring-projects/spring-petclinic/issues/14) | [STS-3294](https://issuetracker.springsource.com/browse/STS-3294)

# Contributing

The [issue tracker](https://github.com/spring-projects/spring-petclinic/issues) is the preferred channel for bug reports, features requests and submitting pull requests.

For pull requests, editor preferences are available in the [editor config](https://github.com/spring-projects/spring-petclinic/blob/master/.editorconfig) for easy use in common text editors. Read more and download plugins at <http://editorconfig.org>.
