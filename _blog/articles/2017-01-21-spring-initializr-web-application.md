---
layout: post
title: Spring Initializr - Bootstrap Your Spring Boot Applications at F1 speed!
date: 2022-07-09 06:14:13
summary: Learn what is Spring Initializr and understand how to Bootstrap a Spring Boot Web Application quickly.
categories: SpringBoot
permalink: /spring-initialzr-bootstrap-spring-boot-applications
image: /images/spring-boot-category.png
---

![Image](/images/Spring-Initializr-Web.png 'Web, Actuator and Developer Tools')

Spring Initializr [http://start.spring.io/](http://start.spring.io/){:target="\_blank"} is great tool to bootstrap your Spring Boot projects.

![Image](/images/Spring-Initializr-Web-ApplicationStructure.png 'Spring Initializr Web Application - Folder Structure')

It allows you to create varied range of Spring Boot based Applications from a very simple UI. Some of the types of applications you can bootstrap are:

- Web Applications
- Restful Applications
- Batch Applications

Spring Boot provides a wide range of starter projects. Spring Initializr supports all of them and more. Among a varied range of starter projects and options supported are:

- spring-boot-starter-web-services : For building applications exposing SOAP Web Services
- spring-boot-starter-web - Build Web applications & RESTful applications
- spring-boot-starter-test - Write great Unit and Integration Tests
- spring-boot-starter-jdbc - Traditional JDBC Applications
- spring-boot-starter-hateoas - Make your services more RESTful by adding HATEOAS features
- spring-boot-starter-security - Authentication and Authorization using Spring Security
- spring-boot-starter-data-jpa - Spring Data JPA with Hibernate
- spring-boot-starter-cache - Enabling Spring Framework’s caching support
- spring-boot-starter-data-rest - Expose Simple REST Services using Spring Data REST

In this guide, lets consider creating a simple web application with Spring Initializr.

## Bootstrapping a Web application with Spring Initializr

Creating a Web application with Spring Initializr is very simple.

![Image](/images/Spring-Initializr-Web.png 'Web, Actuator and Developer Tools')

As shown in the image above, following steps have to be done

- Launch Spring Initializr [http://start.spring.io/](http://start.spring.io/){:target="\_blank"} and choose the following
  - Choose `com.in28minutes.springboot` as Group
  - Choose `student-services` as Artifact
  - Choose the following dependencies
    - Web - Actuator - DevTools
- Click Generate Project button at the bottom of the page.
- Import the project into Eclipse or IntelliJ

## Structure of the project created

Screenshot shows the project structure of the imported maven project.

![Image](/images/Spring-Initializr-Web-ApplicationStructure.png 'Spring Initializr Web Application - Folder Structure')

- StudentServicesApplication.java - Spring Boot Launcher. Initializes Spring Boot Auto Configuration and Spring Application Context.
- application.properties - Application Configuration file.
- StudentServicesApplicationTests.java - Simple launcher for use in unit tests.
- pom.xml - Included dependencies for Spring Boot Starter Web, Actuator, DevTools. Uses Spring Boot Starter Parent as parent pom.

## Complete Code Generated

Lets look at each of the file that is generated

### /pom.xml

Three important things that are configured in pom.xml.

- Spring Boot Parent Pom - You can read more about Spring Boot Starter Parent here - [http://www.springboottutorial.com/spring-boot-starter-parent](http://www.springboottutorial.com/spring-boot-starter-parent).
- Spring Boot Starter Web - You can read more about Spring Boot Starter Web here - [http://www.springboottutorial.com/spring-boot-starter-projects](http://www.springboottutorial.com/spring-boot-starter-projects).
- Spring Boot Starter Plugin

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<project
  xmlns="http://maven.apache.org/POM/4.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd"
>
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.in28minutes.springboot</groupId>
	<artifactId>student-services-initializr</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<packaging>jar</packaging>

	<name>student-services</name>
	<description>Demo project for Spring Boot</description>

	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>3.0.0-M3</version>
		<relativePath /> <!-- lookup parent from repository -->
	</parent>

	<properties>
		<java.version>17</java.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-actuator</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<scope>runtime</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

	<repositories>
    <repository>
      <id>spring-milestones</id>
      <name>Spring Milestones</name>
      <url>https://repo.spring.io/milestone</url>
      <snapshots>
        <enabled>false</enabled>
      </snapshots>
    </repository>
  </repositories>
  <pluginRepositories>
    <pluginRepository>
      <id>spring-milestones</id>
      <name>Spring Milestones</name>
      <url>https://repo.spring.io/milestone</url>
      <snapshots>
        <enabled>false</enabled>
      </snapshots>
    </pluginRepository>
  </pluginRepositories>


</project>
```

---

### /src/main/java/com/in28minutes/springboot/StudentServicesApplication.java

- `@SpringBootApplication` - Initializes Spring Boot Auto Configuration and Spring application context. Read more about Auto Configuration here - [http://www.springboottutorial.com/spring-boot-auto-configuration](http://www.springboottutorial.com/spring-boot-auto-configuration).
- `SpringApplication.run` - Static method to launch a Spring Boot Application.

```java
package com.in28minutes.springboot.studentservices;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class StudentServicesApplication {

  public static void main(String[] args) {
    SpringApplication.run(StudentServicesApplication.class, args);
  }
}
```

---

### /src/main/resources/application.properties

```

```

---

### /src/test/java/com/in28minutes/springboot/StudentServicesApplicationTests.java

- Integration test launches the complete Spring Boot Application. Read more about integration tests here - [http://www.springboottutorial.com/integration-testing-for-spring-boot-rest-services](http://www.springboottutorial.com/integration-testing-for-spring-boot-rest-services).

```java
package com.in28minutes.springboot.studentservices;

import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.extension.ExtendWith;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.context.junit.jupiter.SpringExtension;

@ExtendWith(SpringExtension.class)
@SpringBootTest
public class StudentServicesApplicationTests {

  @Test
  public void contextLoads() {}
}
```

---

## Running the application

Following log is generate when you run StudentServicesApplication.java as a Java Application.

```

    .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::             (v3.0.0-M3)

2022-07-09T07:31:11.653+05:30  INFO 6649 --- [  restartedMain] c.i.s.s.StudentServicesApplication       : Starting StudentServicesApplication using Java 17.0.2 on Puneeths-MacBook-Pro.local with PID 6649 (/Users/puneethsai/devworkspace/student-services/target/classes started by puneethsai in /Users/puneethsai/devworkspace/student-services)
2022-07-09T07:31:11.657+05:30  INFO 6649 --- [  restartedMain] c.i.s.s.StudentServicesApplication       : No active profile set, falling back to 1 default profile: "default"
2022-07-09T07:31:11.718+05:30  INFO 6649 --- [  restartedMain] .e.DevToolsPropertyDefaultsPostProcessor : Devtools property defaults active! Set 'spring.devtools.add-properties' to 'false' to disable
2022-07-09T07:31:11.718+05:30  INFO 6649 --- [  restartedMain] .e.DevToolsPropertyDefaultsPostProcessor : For additional web related logging consider setting the 'logging.level.web' property to 'DEBUG'
2022-07-09T07:31:13.249+05:30  INFO 6649 --- [  restartedMain] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port(s): 8080 (http)
2022-07-09T07:31:13.263+05:30  INFO 6649 --- [  restartedMain] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2022-07-09T07:31:13.263+05:30  INFO 6649 --- [  restartedMain] org.apache.catalina.core.StandardEngine  : Starting Servlet engine: [Apache Tomcat/10.0.21]
2022-07-09T07:31:13.326+05:30  INFO 6649 --- [  restartedMain] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2022-07-09T07:31:13.329+05:30  INFO 6649 --- [  restartedMain] w.s.c.ServletWebServerApplicationContext : Root WebApplicationContext: initialization completed in 1607 ms
2022-07-09T07:31:13.977+05:30  INFO 6649 --- [  restartedMain] o.s.b.d.a.OptionalLiveReloadServer       : LiveReload server is running on port 35729
2022-07-09T07:31:13.984+05:30  INFO 6649 --- [  restartedMain] o.s.b.a.e.web.EndpointLinksResolver      : Exposing 1 endpoint(s) beneath base path '/actuator'
2022-07-09T07:31:14.031+05:30  INFO 6649 --- [  restartedMain] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 8080 (http) with context path ''
2022-07-09T07:31:14.045+05:30  INFO 6649 --- [  restartedMain] c.i.s.s.StudentServicesApplication       : Started StudentServicesApplication in 3.168 seconds (process running for 4.02
```
