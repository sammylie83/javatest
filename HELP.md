# Read Me First
The following was discovered as part of building this project:

* The original package name 'com.finance.transaction-management' is invalid and this project uses 'com.finance.transaction_management' instead.

# Getting Started

### Reference Documentation
For further reference, please consider the following sections:

* [Official Apache Maven documentation](https://maven.apache.org/guides/index.html)
* [Spring Boot Maven Plugin Reference Guide](https://docs.spring.io/spring-boot/3.3.12/maven-plugin)
* [Create an OCI image](https://docs.spring.io/spring-boot/3.3.12/maven-plugin/build-image.html)
* [GraalVM Native Image Support](https://docs.spring.io/spring-boot/3.3.12/reference/packaging/native-image/introducing-graalvm-native-images.html)
* [Spring Web](https://docs.spring.io/spring-boot/3.3.12/reference/web/servlet.html)
* [Spring Data JPA](https://docs.spring.io/spring-boot/3.3.12/reference/data/sql.html#data.sql.jpa-and-spring-data)
* [Spring Security](https://docs.spring.io/spring-boot/3.3.12/reference/web/spring-security.html)
* [Validation](https://docs.spring.io/spring-boot/3.3.12/reference/io/validation.html)
* [Spring Cloud Gateway Access Control [Enterprise]](https://techdocs.broadcom.com/us/en/vmware-tanzu/spring/spring-cloud-gateway-extensions/1-0-0/scg-extensions/access-control.html)
* [Docker Compose Support](https://docs.spring.io/spring-boot/3.3.12/reference/features/dev-services.html#features.dev-services.docker-compose)

### Guides
The following guides illustrate how to use some features concretely:

* [Building a RESTful Web Service](https://spring.io/guides/gs/rest-service/)
* [Serving Web Content with Spring MVC](https://spring.io/guides/gs/serving-web-content/)
* [Building REST services with Spring](https://spring.io/guides/tutorials/rest/)
* [Accessing Data with JPA](https://spring.io/guides/gs/accessing-data-jpa/)
* [Securing a Web Application](https://spring.io/guides/gs/securing-web/)
* [Spring Boot and OAuth2](https://spring.io/guides/tutorials/spring-boot-oauth2/)
* [Authenticating a User with LDAP](https://spring.io/guides/gs/authenticating-ldap/)
* [Validation](https://spring.io/guides/gs/validating-form-input/)

### Additional Links
These additional references should also help you:

* [Configure AOT settings in Build Plugin](https://docs.spring.io/spring-boot/3.3.12/how-to/aot.html)

### Docker Compose support
This project contains a Docker Compose file named `compose.yaml`.
In this file, the following services have been defined:

* postgres: [`postgres:latest`](https://hub.docker.com/_/postgres)

Please review the tags of the used images and set them to the same as you're running in production.

## GraalVM Native Support

This project has been configured to let you generate either a lightweight container or a native executable.
It is also possible to run your tests in a native image.

### Lightweight Container with Cloud Native Buildpacks
If you're already familiar with Spring Boot container images support, this is the easiest way to get started.
Docker should be installed and configured on your machine prior to creating the image.

To create the image, run the following goal:

```
$ ./mvnw spring-boot:build-image -Pnative
```

Then, you can run the app like any other container:

```
$ docker run --rm -p 8080:8080 transaction-management:0.0.1-SNAPSHOT
```

### Executable with Native Build Tools
Use this option if you want to explore more options such as running your tests in a native image.
The GraalVM `native-image` compiler should be installed and configured on your machine.

NOTE: GraalVM 22.3+ is required.

To create the executable, run the following goal:

```
$ ./mvnw native:compile -Pnative
```

Then, you can run the app as follows:
```
$ target/transaction-management
```

You can also run your existing tests suite in a native image.
This is an efficient way to validate the compatibility of your application.

To run your existing tests in a native image, run the following goal:

```
$ ./mvnw test -PnativeTest
```


## VMware Tanzu Spring Enterprise Extensions

You have selected to add [Tanzu Spring](https://www.vmware.com/products/app-platform/tanzu-spring) enterprise extensions to your project.
In order to use these enterprise extensions you must have authorized [access to the Spring Enterprise Subscription](https://techdocs.broadcom.com/us/en/vmware-tanzu/spring/tanzu-spring/commercial/spring-tanzu/guide-artifact-repository-administrators.html) artifacts with an entitlement to Tanzu Spring.
To learn more about what is included with Tanzu Spring entitlement, check out [enterprise.spring.io](https://enterprise.spring.io/) for more information.

### Maven Parent overrides

Due to Maven's design, elements are inherited from the parent POM to the project POM.
While most of the inheritance is fine, it also inherits unwanted elements like `<license>` and `<developers>` from the parent.
To prevent this, the project POM contains empty overrides for these elements.
If you manually switch to a different parent and actually want the inheritance, you need to remove those overrides.

